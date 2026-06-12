---
title: "Help on Ubuntu Server Installation Please!"
date: 2008-10-12
forum: General Help
---

### Post by uberpower on 2008-10-12
Well, I installed it and I made the server name my username and my password.  Later on it asks me for them after that it says 

<username>@<servername>:~$ (i have both things filled out obviously) what do I type in?

---

### Post by howefield on 2008-10-12
Depends on what you want to do.

Sounds like you have booted up your shiny new server, were you expecting to see something else ?

---

### Post by uberpower on 2008-10-12
Actually, yes i am expecting something else... Haha! Well, it seems i have to put some sort of command? I just want to finish up the installtion and get to the login screen :P

---

### Post by howefield on 2008-10-12
According to your first post, you are past the login screen.

If you are expecting to see a GUI, you won't unless you install one.,

---

### Post by uberpower on 2008-10-12
How do I install a GUI? And if you know a good one send me a link.

---

### Post by howefield on 2008-10-12
There are a few you could go for, remember a GUI in a server install is usually a waste of processing cycles but you can easily toggle it on/off as required.

There are a few you could go for, ubuntu-desktop which is about another 400 meg download. xubuntu-desktop which is a lighter desktop and not so demanding of your resources.

If it were mine, (assuming I'd want a GUI in a server) I'd type at your command prompt the following three commands.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
sudo apt-get install ubuntu-desktop
```

Substitute xubuntu-desktop if you prefer. First command ensures your repository info is up to date, the second ensures all your packages are up to date, and the third installs a GUI.

---

### Post by uberpower on 2008-10-12
Thanks man. Everything is installing right now and there are no problems yet.  But i need a URL to stuff like commands and things like that to help noobs like me on Ubuntu.

---

### Post by Sam on 2008-10-12
> **uberpower said:**
> But i need a URL to stuff like commands and things like that to help noobs like me on Ubuntu.

The perfect site for you: [http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by howefield on 2008-10-12
I saved this link earlier after seeing it in another thread. Might help with the command line.

[http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php](http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php)

Also, I'm trying to remember if you'll need xorg as well as the desktop. If you do, simply type the following at the command prompt.

```
sudo apt-get install xorg
```

---

### Post by uberpower on 2008-10-12
Hey thanks for your help. Are you going to be around because i might need more help, really appreciate it.

---

### Post by howefield on 2008-10-12
Will be around for a little while, but there are a load of helpful posters around here, I don't think you'll be stuck.

---

### Post by uberpower on 2008-10-12
Nah, I'll never in my lufe be stuck if im really that desperate to make it work i'll somehow teach myself! :D

---

### Post by howefield on 2008-10-12
I did just that yesterday, install Ubuntu server to act as a file server. Great way of learning command line ;-)

---

### Post by uberpower on 2008-10-12
The reason why i'm using Ubuntu to make a server is because i want to host games like Couter Strike: Source and Garry's Mod, you know stuff like that.

---

### Post by Sam on 2008-10-12
> **uberpower said:**
> But i need a URL to stuff like commands and things like that to help noobs like me on Ubuntu.

You might also find this handy: [http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/) (once you studied the website [previously posted](http://ubuntuforums.org/showpost.php?p=5954132&postcount=8))

---

### Post by uberpower on 2008-10-12
> **Sam said:**
> You might also find this handy: [http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/) (once you studied the website [previously posted](http://ubuntuforums.org/showpost.php?p=5954132&postcount=8))
Thanks :D:popcorn:

---

### Post by uberpower on 2008-10-13
Hey, everything finished installing now i need to know how to get the what Windows calls the command promt to install more things like the xorg.  And also I need to know how to install certain things to host servers. Thanks ahead of time...(Need a program for Ubuntu that can open .bin files.)

---

### Post by uberpower on 2008-10-13
bump :O

---

