---
title: "Troubling terminal behavior..."
date: 2008-11-12
forum: General Help
---

### Post by swordthrower on 2008-11-12
This problem is a first for me, after having used linux distros for many years both for research and on my personal computers...

I have Intrepid x64 on an Asus laptop, and have just noticed that if I open a program from the terminal (gnome-terminal) and send it to background with a '&', and then close the terminal the program closes as well! This has never been the case as far as I can remember.

For example, if I open a terminal, start up, say, gedit with ```
gedit &
``` and then close the terminal, I don't expect it to take my gedit with it!

Am I crazy, or is this not the way it usually works? And it just seems dangerous, because if I have multiple terminals up and close one, I don't want to have to remember which processes are tied to it and will go bye-bye too...

Any idea how to fix this?

Thanks in advance! Ubuntu forums has saved my *** so many times, I just hope it has one more fix in it for the Gipper.

---

### Post by john183 on 2008-11-12
try 
```
gedit & disown
```

or close the terminal via typing "exit" rather than clicking the 'x' in the upper corner.
i just read about it in another thread.

---

### Post by Portmanteaufu on 2008-11-12
This is actually the normal behavior. For an explanation, take a look at the first post in [this thread,]("http://ubuntuforums.org/showthread.php?t=405575") which explains the concept of fork / exec.

A lot of window managers will provide a "Run Program" option in the mouse-click menu to allow you to run a command that won't be tied to a particular shell. I use Enlightenment, though, so my recollection of gnome's offerings in that area aren't that great.

Does anybody know if gnome provides something like that?

---

### Post by john183 on 2008-11-12
> **Portmanteaufu said:**
> This is actually the normal behavior. For an explanation, take a look at the first post in [this thread,]("http://ubuntuforums.org/showthread.php?t=405575") which explains the concept of fork / exec.

A lot of window managers will provide a "Run Program" option in the mouse-click menu to allow you to run a command that won't be tied to a particular shell. I use Enlightenment, though, so my recollection of gnome's offerings in that area aren't that great.

Does anybody know if gnome provides something like that?

In GNOME you can run most programs by finding their icon in the menus, those that don't have an icon you can press alt+f2 and type in the same command as you would in a terminal window to run the program.

---

### Post by bodhi.zazen on 2008-11-12
This very same topic has already been discussed today :twisted:

[http://ubuntuforums.org/showpost.php?p=6160308&postcount=6](http://ubuntuforums.org/showpost.php?p=6160308&postcount=6)

---

### Post by spibou on 2008-11-12
> **Portmanteaufu said:**
> This is actually the normal behavior. For an explanation, take a look at the first post in [this thread,]("http://ubuntuforums.org/showthread.php?t=405575") which explains the concept of fork / exec.
The thread you linked does not explain why background processes die when you close the terminal. Furthermore it gets completely wrong what a zombie is. A zombie process is one that has terminated but its parent has not waited for it yet. When the parent terminates a process does not become zombie, contrary to what the thread claims, it simply gets inherited by the init process.

From 'man 2 wait'
> 
A child that terminates, but has not been waited for becomes a "zombie".  The kernel maintains a minimal set of information about the zombie process (PID, termination status,  resource  usage  information)  in order  to  allow the parent to later perform a wait to obtain information about the child.  As long as a zombie is not removed from the system via a wait, it will consume a slot in the  kernel  process  table, and  if this table fills, it will not be possible to create further processes.  If a parent process terminates, then its "zombie" children (if any) are adopted by init(8), which automatically performs a wait to remove the zombies. 

I hope that clears things with regards to zombies (which are not relevant to the present discussion anyway). Let's return now to background processes. When you close the terminal the shell will receive SIGHUP. HUP stands for "terminal hang-up" and basically indicates that the connection with the terminal has been lost.

From [http://www.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap11.html](http://www.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap11.html)
> If a modem disconnect is detected by the terminal interface for a controlling terminal, and if CLOCAL is not set in the c_cflag field for the terminal (see Control Modes), the SIGHUP signal shall be sent to the controlling process for which the terminal is the controlling terminal.
The "controlling process" is the shell you started. The default behaviour for when a process receives SIGHUP is that it gets terminated. However a process can create a signal handler for SIGHUP. I presume that's what BASH does and in that signal handler it sends SIGHUP to all its child processes unless you have used disown. Note that this is a design choice of the BASH programmers, as far as the operating system is concerned it would be perfectly acceptable for BASH to simply terminate without sending SIGHUP to its children. That's what the C-shell does and I believe it is preferable behaviour. 

Now when the children receive SIGHUP and unless they themselves have set up a signal handler or have blocked SIGHUP, they will terminate. When you start a process like 'nohup programme' then nohup itself arranges for SIGHUP to be blocked and then starts the process. The process inherits the block for SIGHUP so although BASH will send to the process SIGHUP when you close the window, it will have no effect and the process will continue running.

Here are some little tests. Make the following script executable
```

#!/bin/bash

trap 'echo > received-sighup' HUP
sleep 100000

```
Make sure that there's no file called received-sighup in your working directory. Now open a new terminal and from the terminal run the script. Check again that there is no file received-sighup. Now close the terminal. You will see that now there is a file received-sighup. The reason is that the trap command created a signal handler so when the script received SIGHUP it executed **echo > received-sighup**

Now erase received-sighup, open a terminal and run the script with **nohup script**  Now close the terminal. You will see that this time there's no file received-sighup. The reason is that nohup arranged for SIGHUP to be blocked so the script never received SIGHUP. Note what the BASH man page says:
> Signals ignored upon entry to the shell cannot be trapped or reset.

I hope this explains things. By the way, due to the above experiments you will now have a few processes running so you might want to kill them.

I note that some text editors upon receiving SIGHUP save the file which is being edited and exit. This is useful if there is some problem with the windowing system and you cannot directly access the editor. You go to console, use ps -elf to find the PID of the editor and you send it SIGHUP. If memory serves me right emacs behaves like this.

---

### Post by geirha on 2008-11-13
bash will disown the processes you've sent to the background upon exit, so if you exit the shell by doing "exit", "logout" or ^d instead of closing gnome-terminal, your background processes should keep running.

---

### Post by mcduck on 2008-11-13
You can alo use "nohup".

```
nohup gedit &
```

---

