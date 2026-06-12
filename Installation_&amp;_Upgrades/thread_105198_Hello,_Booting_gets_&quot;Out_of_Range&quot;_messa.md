---
title: "Hello, Booting gets &quot;Out of Range&quot; message"
date: 2005-12-17
forum: Installation &amp; Upgrades
---

### Post by noranthon on 2005-12-17
Hello to the Community Chat forum.  I installed Kubuntu 5.10 today and, coming up against a problem, joined the forum (after many unsuccessful attempts at Image Verification - how do people read those things?)  I wanted to check out Ubuntu, although for the time being I'm using another distro, partly because of the following.

I have two Ubuntu boot options: default and recovery.  I have been unable to get the login manager using either because:

1.  The standard (default) boot gets me a blank screen with the message "Out of Range".  The message is in the same format as the "No Signal" message on my screen before I boot the CPU.  Incidentally, screen display during booting is too faint to read.

2.  Recovery mode gets me a command-line screen.  "login" gets me a login prompt and I can login, but I do not know how to get the GUI.  The command "kdm" gets me the same "Out of Range" message as the default mode.

What to do?

---

### Post by towsonu2003 on 2005-12-18
[QUOTE=noranthon]
I can login, but I do not know how to get the GUI.
[/QUOTE]
```
startx
```have no idea other than that, sorry... oh, it may not be wise to use gui while in recovery mode (i.e. as root)

---

### Post by Ocxic on 2005-12-18
[QUOTE=noranthon]Hello to the Community Chat forum.  I installed Kubuntu 5.10 today and, coming up against a problem, joined the forum (after many unsuccessful attempts at Image Verification - how do people read those things?)  I wanted to check out Ubuntu, although for the time being I'm using another distro, partly because of the following.

I have two Ubuntu boot options: default and recovery.  I have been unable to get the login manager using either because:

1.  The standard (default) boot gets me a blank screen with the message "Out of Range".  The message is in the same format as the "No Signal" message on my screen before I boot the CPU.  Incidentally, screen display during booting is too faint to read.

2.  Recovery mode gets me a command-line screen.  "login" gets me a login prompt and I can login, but I do not know how to get the GUI.  The command "kdm" gets me the same "Out of Range" message as the default mode.

What to do?[/QUOTE]

I know this problem, iether your resolution or refresh rate is set too high for your monitor i suggest that you boot into your recover console and type:

sudo dpkg-reconfigure xserver-xorg

go through the steps and remove the resolutions that your monitor cannot display. that should fix your problem.
then reboot your machine normally and see what you get.

tip #1: slowly go through the list from the top down disableing each resolution one by one, that way you can find you MAX resolution that you can use. this will take some time since you'll have to restart your computer every time.

tip #2:boot normally and see if you can get to a console by hitting ctrl-alt-F1 if you can the all you will have to do is hit ctrl-alt-backspace instead of restarting you machine. (this is a gnome thing, i dunno if it will work with KDE scince i don't use it)

tip #3: get a better monitor.(this would prolly be the easiest thing to do, though expensive)

---

### Post by noranthon on 2005-12-18
Thanks for the help, which answered the question and solved the problem.

---

