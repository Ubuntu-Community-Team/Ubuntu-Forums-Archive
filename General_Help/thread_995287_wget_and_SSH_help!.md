---
title: "wget and SSH help!?"
date: 2008-11-27
forum: General Help
---

### Post by calrogman on 2008-11-27
Hello, I have read lot's of things about how you can use SSH to tell your home computer to download a file while you're at work or whatever but is their anyway to start downloading a file, log out of SSH and get back to whatever and still have the remote computer download the file using wget?

Thanks in advance!

---

### Post by Peter09 on 2008-11-27
Use FreeNX, it will maintain a session on the server even when you are not logged in.

[http://freenx.berlios.de/download.php](http://freenx.berlios.de/download.php)

---

### Post by HoppingWombat on 2008-11-27
Another way you can do it is to write a shell script like:

```

#!/usr/bin/sh
sleep 10
wget yourfilehere

```

The first line is part of shell scripting -- it tells the program where the shell is

The second line, "sleep 10", tells the terminal to "sleep" for 10 seconds, thus delaying wget.

You can run that with the command "sh shellscripthere &" The "&" tells it to run it in the background. You then can log out and in 10 seconds the file will start downloading.

Have a nice day!

---

### Post by geirha on 2008-11-27
There's also [apt://screen](apt://screen). Start a screen by running ```
screen
``` Then run whatever (non-gui) program you like inside screen, and detach the screen by hitting ctrl+a+d or simply closing the terminal window. The program(s) you run in screen will keep running in the background after you detach. To get back to the program(s), log back in to the server and run the following to reattach ```
screen -r
```. You can run several screens at a time, and you can have several windows inside the screen, so you can run several programs inside the screen at the same time.

---

### Post by reality1011 on 2008-11-27
> **calrogman said:**
> Hello, I have read lot's of things about how you can use SSH to tell your home computer to download a file while you're at work or whatever but is their anyway to start downloading a file, log out of SSH and get back to whatever and still have the remote computer download the file using wget?

Thanks in advance!



SSh  is a way of connecting securely to your computer.  Setup an ssh server on your computer, openssh is very popular...

here is a configuration link:
[http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/](http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/)



Wget is a command line utility to download things from the web... read more here....

[http://linux.about.com/od/commands/l/blcmdl1_wget.htm](http://linux.about.com/od/commands/l/blcmdl1_wget.htm)



Once you install ssh then its like working on your local computer via terminal...  If you don't know how to use the terminal then I strongly suggest getting familiar with common unix commands

[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

---

