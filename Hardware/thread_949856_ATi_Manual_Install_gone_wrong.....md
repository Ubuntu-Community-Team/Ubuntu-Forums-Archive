---
title: "ATi Manual Install gone wrong...."
date: 2008-10-16
forum: Hardware
---

### Post by boosted on 2008-10-16
I was on IRC #ubuntu and someone was helping me out with getting my ATi card working on my HP laptop.  I think it's an older card lspci listed it as a RS200M.  The person sent me a link with a manual install of the ati drivers because nothing else was working.  I can't give the website because my laptop has crashed now.  But I got all the through install and rebooted.  Upon reboot X crashed.  It said is was possibly due to xorg.conf error.  I know it made a backup of the original xorg file.  So I opened a terminal and went to the /etc/X11 directory and these files were there:
xorg.conf (the ****** up one)
xorg.conf~
xorg.conf.fglrx-0

I tried renaming the file...

rename xorg.conf xorg.conf.ati
so I know that file was for the ati stuff

I got this error
Bareword "xorg" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "conf" not allowed while "strict subs" in use at (eval 1) line 1. 

what are these errors and how do I correct it so I can rename these files?

---

### Post by markbuntu on 2008-10-16
When the ati driver was intitally configured it saved your old xorg.conf as xorg.conf.fglrx-0 so that is the one you need to rename. 

You should also have a xorg.conf.failsafe which will get you back to the failsafe VESA driver that gnome-safe mode uses. You can copy that to xorg.conf but do not mess around with it or your gnome-safe mode will no longer work.

---

### Post by boosted on 2008-10-16
I tried rename xorg.conf.fglrx-0 xorg.conf
I got the same error message as above.  What is this error and how do I fix it?  I also tried sudo then the command and got the same thing.

---

### Post by markbuntu on 2008-10-16
You need to be root to change those files. Try gksudo nautilus.

---

### Post by boosted on 2008-10-16
gksudo
Gtk-WARNING cannot open display

???



I tried logging in as root and renaming the file and got the same error code as I first got.  The Bareword thing.... ?

---

### Post by Yellow Pasque on 2008-10-16
There is no "rename" command. Use mv to rename a file.
EDIT: I suggest skimming through the mv man page to make sure you don't do anything you'll regret later.

---

### Post by boosted on 2008-10-16
this isn't a rename command?

[http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=r/rename](http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=r/rename)



so how do I use mv (move) to rename the file?

---

### Post by boosted on 2008-10-16
alright I replaced the messed up xorg file with the back up and rebooted and still X failed to start.
It asks if I would like to view the X server output to diagnose the problem.



(EE) No devices detected

Fatal server error:
no screens found


Please help

---

### Post by boosted on 2008-10-16
I tried rebooting and logging in as root.  Then startx

it failed.

looks like it's trying to use a radeon driver?

I guess that driver is messing everything up... so how do I go back to the default driver.  mesa or whatever it's called?


edit:
I found the website I used to install the ati stuff
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I used method 2
I remember getting to almost the last thing here:
sudo aticonfig --initial -f

and I got 
segmentation fault

I rebooted then that is when X went FUBAR

---

