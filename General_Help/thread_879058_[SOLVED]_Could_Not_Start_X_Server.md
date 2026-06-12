---
title: "[SOLVED] Could Not Start X Server"
date: 2008-08-03
forum: General Help
---

### Post by CheeseAndToast on 2008-08-03
Hi all, 

Need some urgent help.

I'm running Ubuntu 8.04 and windows xp (dual boot).  When I reboot my PC i get the following message:

> Could not start X server (your graphical Environment) due to internal errors. Please contact your system administrator or check your system logs to diagnose.  Int the meantime this display will be disabled.  Please restart GDM when the problem is corrected.

I've tried:

sudo dpkg-reconfigure xserver-xorg

But the system hangs, won't let me select yes to the setup

tried:

sudo etc/init.d/gdmrestart
sudo etc/init.d/gdmstart
sudo etc/init.d/gdmstop
sudo etc/init.d/gdmforce-reload

Result = command not found.

Any ideas please?

Thanks

---

### Post by phidia on 2008-08-03
I think you need a space after gdm in the commands you listed.

When you say the system hangs when trying the dpkg-reconfigure command that sort of raises a red flag-what are your system specs? Particularly RAM memory but providing your video card maker and model will be helpful too.

---

### Post by CheeseAndToast on 2008-08-03
AMD ATHLON 3000+ 1999MHZ 1.5gb DDR RAM
AIT GRAPHICS

Hope this helps.

Thanks for the quick reply.

---

### Post by phidia on 2008-08-03
The wiki guide [here]("https://help.ubuntu.com/community/Video") may be helpful.
If you are comfortable in the commandline interface (CLI) you can enter this:
> sudo nano /etc/X11/xorg.conf within that editor find the device section and the line the says driver replace whatever is in the quotes after the driver entry with "vesa" save the file and then enter this: > startx
That should get you a low res desktop you can work in-something to use until you install the ATI driver.

---

### Post by CheeseAndToast on 2008-08-03
When I try sudo nano /etc/X11/xorg.conf, the editor is blank? is it meant to be?

I've copied the xorg.conf from live cd to my windows parition, how do i go about using that one?

This command: sudo dpkg-reconfigure -phigh xserver-xorg fails on dpkg-reconfigure (command not found)

---

### Post by phidia on 2008-08-03
> When I try sudo nano /etc/X11/xorg.conf, the editor is blank? is it meant to be?
 

No it should have configuration lines & hardware details. You should be very careful with spelling or use commandline completion to autofill the path for you. For example just type "sudo /etc/X" and press the tab key the "X11" directory will be auto filled by the terminal. You would then type xo (after the /etc/X11 already there and press tab again and xorg.conf should be automatically inserted. This way of doing it makes sure typos aren't created and thereby incorrect and useless files.

> I've copied the xorg.conf from live cd to my windows parition, how do i go about using that one? 

If you have your windows partition mounted or know how to then "sudo cp /mnt/windows/xorg.conf /etc/X11/xorg.conf will work just replace the "/mnt/windows" entry I included with the actual path to the saved xorg file. If you have a problem with "cp" you can also use "mv"

I don't know why the dpkg command fails Hardy's xorg has changed but exactly what's going on there is perplexing.

---

### Post by CheeseAndToast on 2008-08-04
Thansk for your reply.

I've copied xorg.conf from the live CD to my windows partition, then tried to copy for /media/disk/xorg.conf /media/disk-1/etc/X11/xorg.conf
Got no errors when i pressed enter. Just retunred to the next line.  Am i meant to get confirmation of sucess of the command?

Also when i save the xorg.conf in nano i get this error:
"Error writing /etc/X11/xorg.conf:Read-Only File System

I get a similar message when I rung dpkg-reconfigure -phigh xserver-xorg
"cp: cannot create regular file `/etc/X11/xorg.conf.20080804233377`: read-only file system.

I'm quite keen not to reinstall ubuntu

Any help is much appreciated.

---

### Post by CheeseAndToast on 2008-08-05
Any updates?  I have to continue using windows.  I'm looking very close to re-install hardy :(

---

### Post by CheeseAndToast on 2008-08-05
fixed. 
[http://ubuntuforums.org/showthread.php?t=591664](http://ubuntuforums.org/showthread.php?t=591664)

---

