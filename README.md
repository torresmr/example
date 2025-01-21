<h1 align="center">Hands-on Tutorial: Introduction to Git and GitHub </h1>

Hello everybody

This tutorial aims to provide an in-depth introduction to version control systems using `git` and `GitHub`. It is designed to equip you with the necessary skills to effectively use these tools, regardless of your experience level.

We will use the Command Line Interface (CLI) (i.e. `Bash` for Windows and `Terminal` in Linux and MacOS) to perform essential command line techniques.


## Git: An Overview

`Git` is a free and open-source version control software that was created by Linus Torvalds, the creator of Linux. It helps software developers track changes made to their code over time, making it easier to collaborate with others and revert changes when necessary.

All files in a project directory, or a `repository` (repo for short), are tracked by a hidden `.git` file located in the root directory. You can create a new repository on your local machine by navigating to the directory where you want your project to live and typing the `git init` command. 

<br>

Let's delve into some common `git` commands. 

| Command                            | Description                                                                                                                                                                    |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `git init`                         | Initializes a new Git repository in the current directory. This creates a hidden `.git` directory which is used to track changes. |
| `git status`                       | Provides information about any untracked files. |
| `git add FILE-NAME` or `git add .` | The `git add` command adds a file or all files (`.`) to the staging area. |
| `git commit -m "Description"`      | This command takes a snapshot of all changes in the staging area and saves them as a new commit in the repository. The `-m` flag is followed by a message that should briefly describe the changes made in this commit. |

The process described above happens on your local machine. This is perfect for solo projects, but if you want to collaborate with others or create a backup of your code, you'll need to use **GitHub**.

## GitHub: An Overview

GitHub is a platform that allows developers to host and share their Git repositories online. It's a fantastic tool for collaboration, allowing multiple developers to work on the same project simultaneously without overwriting each other's changes. GitHub repositories are just like Git repositories, but with some added features. For example, GitHub allows for `pull requests`, where one developer can propose changes to a project that another developer can review and approve. GitHub also includes tools for project management, such as issue tracking and project boards.


## To Get Started with Git and GitHub

Here's a step-by-step guide to get you started with Git and GitHub:

1. **Create a GitHub Account**: Visit [github.com](https://github.com/) and register for an account.

2. **Install Git**: The Olin 124 computer labs are already installed with Git. Just for your information, you can go to step 3. Depending on your operating system, download and install Git using one of the following methods:
    - Windows users: Download and install [Git for Windows](https://gitforwindows.org/).
    - Mac users: Download and install [Git for MacOS](https://git-scm.com/download/mac) or use Homebrew by typing `brew install git` in the Terminal.
    - Linux users: Download and install `sudo apt install git'

3. **Configure Git**: Once Git is installed, you'll need to configure it with your name and email address. This information is used to track who made each commit in a project. Open your Terminal or Command Prompt and type the following commands, replacing "FirstName LastName" and "email@example.com" with your Whitman name and email:

    ```bash
    # Enter YOUR NAME to set your name
    git config --global user.name "FirstName LastName"

    # Enter YOUR EMAIL to set your email. Make sure it is the email associated with your GitHub account!
    git config --global user.email "email@example.com"
    ```
    You can verify that the configuration worked by typing `git config --list`. The output should include your name and email. Ensure you use the email associated with your GitHub account. This is important because Git will use this information when you work on a project.

4. **Set up SSH Keys**: SSH (Secure Shell) keys are a way to identify yourself to GitHub without needing to provide your username and password every time. They are a pair of encryption keys that work together to secure your connection. The public key is stored on GitHub and the private key is stored on your local machine. 

    Here are the steps to generate a new SSH key and add it to your GitHub account:

- **Check for existing SSH keys:** Open your Terminal or Command Prompt and type `ls -al ~/.ssh`. If you see files named `id_rsa.pub` or `id_ed25519.pub`, you already have an SSH key. If not, you'll need to create one.
    
- **Generate a new SSH key:** In your Terminal or Command Prompt, type `ssh-keygen -t ed25519 -C "your email address"`, replacing "your email address" with the email you used to sign up for GitHub. Press `Enter` to accept the default file location. When asked to enter a passphrase, either type a secure passphrase or press `Enter` to proceed without a passphrase.
    
- **Add your SSH key to the ssh-agent:** First, start the ssh-agent in the background by typing `eval "$(ssh-agent -s)"`. Then, add your SSH private key to the ssh-agent by typing `ssh-add ~/.ssh/id_ed25519` (or `ssh-add ~/.ssh/id_rsa` if you're using an RSA key).
    
- **Add your SSH key to your GitHub account:** Type `cat ~/.ssh/id_ed25519.pub` (or `cat ~/.ssh/id_rsa.pub` for RSA keys) and press `Enter` to display your public key. Select and copy the key. Then, go to the GitHub website, click your profile photo, select **Settings**, then **SSH and GPG keys**, then **New SSH key**. Paste your key into the "Key" field and click **Add SSH key**.
    
- **Test your SSH connection:** Go back to your Terminal or Command Prompt and type `ssh -T git@github.com`. If you see a message saying `"You've successfully authenticated, but GitHub does not provide shell access"`, then everything is working!


## Workflow Example

Here is _one_ example of a workflow you may choose when working on a project. Let's imagine that there's a repository online that you want to use as a starting point for a project. First, you may want **your own cloud copy** of a repository on GitHub. In order to start working on the files, you'll need to get them on your computer. To do so, you will clone **your repository** to your machine. This will create a local copy of the files **as well as their entire history** on your local machine. We'll use the terminal to clone the repository, but we need to get some information about it first. To get the URL location of the repository, click the **Code** button, then click on the clipboard icon to copy the SSH URL to your clipboard:

Then, on your terminal, you could use the `git clone` command described below.  Here is a diagram of the full process:

![git with github diagram](imgs/full-git-process.png)

<br>


## Collaborating with Git and GitHub

Now that we've covered the basics of Git and GitHub, let's take a look at how they can be used for collaboration.

Let's imagine you find a repository on GitHub that you'd like to contribute to. The first step is to create your own copy of the repository on GitHub, known as a **fork**. This gives you a version of the project that you have full control over, allowing you to make changes without affecting the original project.

Once you have forked the repository, you'll want to **clone** it to your local machine. This creates a copy of the project files on your computer, allowing you to work on the project even when you're offline. To clone a repository, navigate to the main page of the repository on GitHub, click the **Code** button, then click on the clipboard icon to copy the SSH URL to your clipboard. Then, open your Terminal or Command Prompt, navigate to the directory where you want the project to live, and type `git clone URL`.

Now that you have a local copy of the project, you can start making changes. Remember to commit your changes frequently with clear, descriptive commit messages. This will make it easier for others to understand what you've done.

When you're ready to share your changes with others, you'll need to **push** your commits to GitHub. This uploads your changes to the GitHub repository, making them available to others. To push your changes, open your Terminal or Command Prompt, navigate to your project directory, and type `git push origin main`, replacing "master" with the name of the branch you want to push.

Finally, to propose that your changes be merged into the original project, you can create a **pull request**. To do this, navigate to the main page of the original repository on GitHub, click the "Pull requests" tab, then click the "New pull request" button. Select your fork on the right-hand side, review the changes, then click the "Create pull request" button. The project owner will be able to review your changes and decide whether to merge them into the project.

Here are some additional `git` commands that allow you to interact easily with GitHub:

| Command                  | Description                                                                                                                                                                                                                              |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `git clone REPO-URL`     | Creates a new copy of a source repository, usually hosted on a remote server. Use this when you want to clone a GitHub repository. This command creates a new subdirectory named after the source repository.                           |
| `git push origin main` | Pushes all commits on the `main` branch made since the last push to another repository (`origin`), typically across the network (e.g., to GitHub).                                                                                     |
| `git pull`               | Pulls all commits made since the last pull from another repository, and attempts to merge those changes into your current files. This is useful when collaborating with others, as it allows you to incorporate their changes into your project. |
| `git config`             | Configure your GitHub account. You should run `git config --global user.name "Your Full Name"` and `git config --global user.email your-github-email` to initially set up.                                                                |




## \U0001f5a5\ufe0f Git Commands Cheat Sheet

**Set configuration values for your username and email** 

```bash
git config --global user.name YOUR NAME
git config --global user.email YOUR EMAIL
```



**Set default branch to main**

```bash
git config --global init.default branch main
```



**Get help on a command**




```bash
git help COMMAND
git COMMAND -h
```



**Initialize a new git repository**

```bash
git init
```



**Clone a repository**

```bash
git clone REPOSITORY URL
```

**Add a file to the staging area**

```bash
git add FILE
```

**Add all file changes to the staging area**

```bash
git add --all
git add -A
git add .
```

**Check the unstaged changes**

```bash
git diff
```

**Commit the staged changes**

```bash
git commit -m "MESSAGE"
```

**Reset staging area to the last commit**

```bash
git reset
```

**Check the state of the working directory and the staging area**

```bash
git status
```

**Remove a file from the index and working directory**

```bash
git rm FILENAME
```

**Rename a file**

```bash
git mv (OLD NAME) (NEW NAME)
```

**List the commit history**

```bash
git log
```

**List all the local branches**

```bash
git branch
```

**Create a new branch**

```bash
git branch BRANCH NAME
```

**Rename the current branch**

```bash
git branch -m NEW BRANCH NAME
```

**Delete a branch**

```bash
git branch -d BRANCH NAME
```

**Switch to another branch**

```bash
git switch BRANCH NAME
```

**Merge specified branch into the current branch**

```bash
git merge BRANCH NAME
```

**Create a connection to a remote repository**

```bash
git remote add (NAME) (REPOSITORY URL)
```

**Push the committed changes to a remote directory**

```bash
git push (REMOTE) (BRANCH)
```

**Download the content from a remote repository**

```bash
git pull REMOTE
```
