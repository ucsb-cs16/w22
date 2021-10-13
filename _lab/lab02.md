---
layout: lab
num: lab02
ready: false
desc: "Submitting to Gradescope"
assigned: 2021-10-11 08:00
due: 2021-10-18 23:59:00.00-7
---


# NOT READY YET 

* NOT READY YET 
* NOT READY YET 
* NOT READY YET 
* NOT READY YET 

Please return to this lab after you receive an announcement that it is ready to work on. We are still making edits to account for changes that happened during the pandemic,
and to adjust to the new pace of the course (where we start with zyBooks / repl.it to get you into C++ quickly, and introduce all of the other mechanics gradually).

# Introduction

This week's lab is design to help you learn about Gradescope and GitHub, two important tools you'll use in this course and that may be used in future CMPSC courses you may take at UCSB.

# Get setup with the tools for this course

## Create a CoE (ECI/CSIL) account if you don't have one already

You should have already done this before: it's the account you use to:
* login on desktop machines in Phelps 3525
* use the `ssh cgaucho@csil.cs.ucsb.edu` command (where `cgaucho` is your username).

If you've already done that successfully, great; continue to the next step.

Otherwise, create an account online at <a href="https://accounts.engr.ucsb.edu/create" target="_blank">https://accounts.engr.ucsb.edu/create</a>.


## Add yourself to the GitHub organization

You should have already done this in [H04](https://ucsb-cs16.github.io/f21/hwk/h04/), but if not, please do it now:

* <https://ucsb-cs16.github.io/f21/hwk/h04/>

## Get setup with gradescope

We will use gradescope to grade all your homeworks, exams and lab/programming assignments. I have manually added everyone (using your @umail.ucsb.edu accounts) 
currently enrolled in the course to the Gradescope system. 
You should have received an email notification with instructions about logging into gradescope. 
Once you follow the instructions to set your password, you should have access to our course on Gradescope. 

* You should see "CMPSC 16" in your courses for this quarter.
* The lab assignment `lab02` should appear in your Gradescope dashboard under CMPSC 16.  You'll be submitting your assignment using Gradescope this week.

If you don't have `CMPSC 16` and `lab02` on Gradescope, please contact the staff for assistance.


## Set up git and ssh keys on CSIL

In lecture, we covered two simple steps you should have done to prepare for today, listed below.  If you've already done them, great!  If not, now's the time:

* <https://ucsb-cs16.github.io/topics/git_csil_configuration/>
* <https://ucsb-cs16.github.io/topics/github_ssh_keys/>



# Implement and submit a simple C++ program 

## Step 1: Open a Terminal and write a "Hello World" program 

In this assignment, we'll be working on your CSIL/ECI/CoE to edit and compile a simple C++ program.

The first step in every assignment where you work on CSIL/ECI/CoE is to open a <b>terminal window on CSIL</b>.

* If you are working on a desktop machine in Phelps 3525, this is super easy; open a terminal window, and you are there. 
* If you are working on your own machine:
  - Windows: You can use Powershell 
  - MacOS: You can use Terminal
  - Linux/Unix: Any terminal shell
  
The command to open a terminal on CSIL is this, where `USERNAME` is your CSIL/ECI/CoE username (e.g. the one you created at <https://accounts.engr.ucsb.edu>:
  
```
$ ssh USERNAME@csil.cs.ucsb.edu
```

The name `csil.cs.ucsb.edu` is actually a "front end" to a collection of machines with names such as these:
* `csilvm-01.cs.ucsb.edu`
* `csilvm-02.cs.ucsb.edu`
* etc.

The system will choose one of these for you (to try to spread the load over multiple machines), and then connect you to it.

The first time you connect to a particular machine, ssh may first ask you a question which looks like this

```
The authenticity of host 'csil-[01-48].cs.ucsb.edu (128.111.43.14)' can't be established.
RSA key fingerprint is 90:ab:6a:31:0b:81:62:25:9b:11:50:05:18:d3:1a:b5.
Are you sure you want to continue connecting (yes/no)?

```

Type <b>yes</b> and then ENTER to continue. It will next ask for your CoE account password. When you type it in, nothing will show on the screen (not even dots). However what you type is still being sent and once you are finished with your password, you can press ENTER to login.

<b>You should now be remotely connected to CSIL!</b> You can make sure by typing the following command (which will tell you what machine you are currently issuing commands to):

```
$ hostname

```

This should show the name of one of the virtual machines such as `csilvm-01.cs.ucsb.edu`. You can now do anything you could normally do in a terminal window in CSIL or the Phelps lab, with the exception of programs that use graphics.

Note: While it isn't required for this lab, if you are interested in running programs that use graphics, you can use something called
the Remote Desktop Protcol (RDP), which is explained in [this article](https://ucsb-engr.atlassian.net/wiki/spaces/EPK/pages/602046589/Remote+Access+to+ECI+Computing+Labs).   But I suggest that you skip over that for now, and just continue with the rest of this lab.  We'll return to RDP as and when it's needed for something in this course.

## Step 3: Create cs16 and lab00 directories<a name="step3"></a>

Now that your environment is set up, you will need to create a directory (a folder is also called <i>directory</i> in Linux) that will contain all your work for the course. Then, inside that directory, you will need to create another directory to contain your work for this assignment.

To create your CS16 directory, use the <b>mkdir</b> command. Type the following in the terminal and press enter:

```
$ mkdir cs16
```

The <b>$</b> represents the terminal prompt; <i>you won't type this character</i>. Whenever you see it, that means that the following command is intended to be typed into the terminal window and run by pressing enter.

You can see list of files and directories in the current directory with <b>ls</b> command. Type the following in the terminal and press enter:

```
$ ls
```

You should be able to see the directory you just created i.e. **cs16**

Now move into that new cs16 directory with the <b>cd</b> command as follows:

```
$ cd cs16
```

And create and move into a lab00 directory:

```
$ mkdir lab00
$ cd lab00   
```

At any time, you can check what directory you are current in with the command **pwd**. It will output the full path of the current directory. For example, if you are inside your <b>lab00</b> directory, you might see:

```
/cs/student/yourcsilname/cs16/lab00
```

Knowing how to navigate a UNIX environment and issue UNIX commands is VERY valuable to computer scientists and engineers. To learn more UNIX commands, there are lot of cool Web resources and books on the topic. This is one website with a good introductory page: [Useful unix commands](http://mally.stanford.edu/~sr/computing/basic-unix.html).

## Step 4: Editing text files for programming <a name="step4"></a>

Let's take a little detour on how to best create and modify text files. These will carry all the code (regardless of computer language) that we want to assemble, compile, and execute.

You are likely familiar with Microsoft Word as a widely-used "word processor", but please DO <b>NOT</b> USE MS WORD TO WRITE PROGRAMS!!!

Instead, for programming, you have access to a very large number of excellent text editors&mdash;and most of them are free to use! All software developers have their preferences, but learning the basics of a Unix-based command line text editor is very important. Every student who intends to study computer science should learn a popular Unix-based text editor (such as vim or emacs), since it is not uncommon that the machine you need to work on does not have a Graphical User Interface (GUI), and you may be forced to use a command-line editor. 

The two most popular Unix-based command line editors are <b>vim</b> and <b>emacs</b>.   Some developers tend to get a little passionate about text editors, and will endlessly argue the benefits of vim over emacs, or emacs over vim.  But it is widely acknowledged even among <b>emacs</b> fans then <b>vim</b> has this advantage over <b>emacs</b>: it is more widely available, i.e.
it tends to be installed by default on most Unix-based systems, while <b>emacs</b> is a separate install.  

Three of the CS instructors (Professors Diba Mirza, Richert Wang, and Phill Conrad) did an very informal survey of a number of UCSB CS alums working in the software industry, and the consensus was this: students should learn:
* Enough `vim` to be able to make simple edits to files
* Then transition to an open source, full-fledged editor with IDE type features, VS Code being the leading contender.

Therefore, in this class:
* For the first couple labs in this class, we will be using <b>vim</b> to work on our programs.
* We'll then show you how you can transition to VS Code if you like.

Ultimately, the choice of text editor is a personal one, and if you are already familiar with an editor you prefer (e.g. Atom, XCode, Eclipse, etc.) it's perfectly fine for you to continue using that editor, though we will expect every CS16 student to develop at least
*basic* profciency with vim.   We have a list of eight things you need to know how to do in vim in this article:
* <https://ucsb-cs16.
## <b>vim</b> for UNIX-based OS

vim (or sometimes called vi) is a popular editor that's also available on just about every UNIX machine (including the ones that you're using in the CS labs) and UNIX-based machines (like MacOS computers).

To create or make changes to a file (let's say it's called "filename.cpp"), you'd type the following at the prompt. (Throughout these instructions, the `$` represents the command line prompt, and is not part of the command you type.)

```
	$ vim filename.cpp
```



## Brief overview of vim

Even if you are already getting comfortable with vim, please read through the following.  It may help give you some vocabulary to talk about `vim`, and also help you get more comfortable with how `vim` works.

The most important things to know about vim is that `vim` has various modes, including "normal" mode, `INSERT` mode, and "command" mode.
* In "normal" mode, each key on your keyboard may do some editor command.
* In `INSERT` mode, you see `INSERT` at the bottom of the screen.  This is the mode in which you type in text, use the arrow keys, and can use the delete key to delete the characters immediately before the cursor.
* In "command" mode, the cursor jumps to the bottom of the screen, and you see a colon `:` where you can type commands.

How do you move between modes?
* To move from normal mode into insert mode: type the letter `i`.  You should see `INSERT` appear at the bottom of the screen.
* To move from insert mode back to normal mode: press the "escape" key (usually labelled `esc`, and at the top left of your keyboard).  The word `INSERT` should disappear.
* To move from normal mode to command mode: type the colon, i.e. `:`.  The cursor shoudl jump to the bottom of the screen where you see a colon (`:`).  To get out of command mode, you type in a command (such as `w` to save the file, or `q` to quit) and press enter.  You can also just press enter by itself to get back to normal mode.

How do you enter text?
* You enter text by going into `INSERT` mode and just typing.  You can move the cursor around with the arrow keys.
* You can also use the delete key to remove text.

How do you do delete an entire line at once?
* To delete an entire line at once, go into "normal" mode (use the `esc` key to get out of `INSERT` mode), and then press the `d` key twice, i.e. type `dd`.   This should remove an entire line.
* If you want to put that line back, move your cursor up one line with the arrow key, and then press `p` to put the line back. (Note that `p` always puts the line back on the line below the cursor, so to undo the `dd` command, you need to move the cursor one line up first.)

How do you save the file?
* Get to normal mode (press `esc` if you in `INSERT` mode)
* Type `:` to go to command mode
* Use the `w` command ("write") to write out the file to the disk.

How do you save the file?
* Get to normal mode (press `esc` if you in `INSERT` mode)
* Type `:` to go to command mode
* Use the `q` command ("quit") to leave `vim`

Can you save and exit all at once?
* Yes.  Get to normal mode (press `esc` if you in `INSERT` mode)
* Type `:` to go to command mode
* Use the `wq` ("write", then quit") to leave `vim`

To learn more, including how to quit without saving, do search/replace, and copy/paste, see:  <https://ucsb-cs16.github.io/topics/vim_basic_eight/>

## What do we need to know about vim for CS16?

While we stress that ultimately the choice of text editor is a personal choice, that we leave up to you, we do want every CS16 student to at the very least develop basic vim skills for a minimal set of commands, which we call the "basic eight".

Those are documented here: <https://ucsb-cs16.github.io/topics/vim_basic_eight/>

There will be an assignment where you need to do a live demo for one of the TAs or LAs demonstrating that you know these basic eight skills in vim.

Again, to learn how to use vim, there is no substitute for PRACTICE!!! There are multiple online resources that you can look at and here are some of them:

* [About vim (from vim.org)](http://www.vim.org/about.php)
* [Vim "how to" from engadget.com](https://www.engadget.com/2012/07/10/vim-how-to/)
* [vim commands - a handy reference card](http://tnerual.eriogerg.free.fr/vimqrc.html)
* [another reference cheat sheet for vim](https://www.fprintf.net/vimCheatSheet.html)

In addition, there is the [Vim Adventures Game](https://vim-adventures.com/) that helps you learn vim while playing a video game.

## Step 5: Create and edit a file containing a C++ program <a name="step5"></a>

This assignment only needs you to write a program that prints out two lines on the display, and nothing else. <b>The output should look EXACTLY as follows</b> (no space before or after each line, except the 2 newlines):

```
Hello, world!
I am ready for CS16!
```

Start with a "skeleton program" (or template) that contains the necessary structure but that does not do anything:

```cpp
#include <iostream>

using namespace std;

int main() {
    // Your printing code should go here

    return 0;
}
```
Go ahead and type this in to the `hello.cpp` file. Alternatively, you can copy and paste it directly from this page.

Next, you will need to replace the comment with code to print out the expected output. Comments in C++ are lines that start with <b>//</b> or text between <b>/*</b> and <b>*/</b>. The second type can span multiple lines.

Important note: For students familiar with Python, remember that lines starting with the <b>#</b> character are not comments in C++. Rather, they are important `include` lines that allow your program to use the input and output functionality. Make sure to copy those lines in your program as well. Only `//` or `/* */` create comments in C++.

To print out text to the terminal, you can use the `cout` stream. To output something use the `<<` operator as shown below:</p>

```
cout << "This will be printed out to the terminal" << endl;
```

The `endl` stream manipulator will cause a newline (i.e. a carriage return) to be printed so that the next thing printed
goes on the next line.  

You can adapt this line to achieve the objective of the assignment. <b>Remember that we need to print two lines, each with a newline at the end.</b> You can do this with one or two statements.

## Step 6: Compile the Code <a name="step6"></a>

Now that the code is written, we need to <em>compile</em> it. This will be done using a special program called a <em>compiler</em>.

Before moving on, <b>make sure you save your code</b> and close the text editor. The following step will be done in the terminal.

For C++ code we will use the <b>g++</b> compiler that's built into many UNIX machines (it even works on most MacOS terminal programs). You can compile the <b>hello.cpp</b> file into an executable called <b>hello</b> with the following command:

```
	$ g++ hello.cpp -o hello
```


This will compile your code and make an executable version of it. Specifically, it will tell the compiler to take the source code file <b>hello.cpp</b> and compile and link it to an executable called <b>hello</b>.

Alternatively, you can use this shortcut:

```
	$ make hello
```

The `make` program is a piece of software that helps you make software with C and C++.   It has automatic rules for generating compiler commands, one of which is that by default, to make an executable program called `hello`, the default compiler command is the one shown here.

Ultimately, you will need to know the long versions of the commands, but it's fine to use the shortcut for the time being.

If the compilation is successful, you won't see any output from the compiler, but if you issue a UNIX <b>ls</b> command, you should see a new file has appeared: one called <b>hello</b>. You can then use the following command to run your program:

```
	$ ./hello
```

Which means "in the current directory, as represented by the <b>.</b> character, run the program <b>hello</b>". You should then see the program output the two expected lines.

The other possibility is that the program may <b>not compile successfully</b>. What to do then?<br>
If you run the <b>g++</b> command and are unsuccesful with your compilation, then you might see an output that looks like this:

```
	hello.cpp: In function ‘int main()’:
	hello.cpp:10:1: error: expected ‘;’ before ‘}’ token
 	}
```

The compiler will try to give you hints on the line (in this case, it's complaining about line 10) where the error occurs, and also about what the error is (in this case a missing semicolon). You will also note that, in this case, an output executable file is not produced.

If you encounter an error, use the compiler hints and examine the line in question. If the compiler messsage is not sufficient to identify the error (which happens more than sometimes), you can search online to see when the error occurs in general. Once you have fixed the error, run the compilation command again. <i>Debugging</i> a program code is a necessary ritual in almost all programs written (even those written by expert coders). More on that in a later class.

## Step 5: Submitting your code to Gradescope
  
You will need to turn in your correct <code>hello.cpp</code> file to Gradescope.

The lab assignment `lab02` should appear in your Gradescope dashboard. If you haven't submitted anything for this assignment yet, Gradescope will prompt you to upload your files.

For this lab, you will need to upload your `hello.cpp` file. You either can navigate to your file, "drag-and-drop" them into the "Submit Programming Assignment" window, or even use a GitHub repo to submit your work. For now choose either of the first two options and follow the steps to upload `hello.cpp` to gradescope.

If you already submitted something on Gradescope, it will take you to their "Autograder Results" page. There is a "Resubmit" button on the bottom right that will allow you to update files for your submission.

For this lab, if everything is correct, you'll see a successful submission passing all of the autograder tests and receive a 100/100.

Congratulations on completing your first C++ program!

If you are logged in remotely, you can log out using the <b>exit</b> command in UNIX:

<pre>$ exit</pre>