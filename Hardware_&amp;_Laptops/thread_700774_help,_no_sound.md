---
title: "help, no sound"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by matchet on 2008-02-18
I have installed ubuntu 7.10 on a brand new Gateway MT3707 laptop.
There is no sound at all, even when I do the sound test in the Sound Preferences.
I think I may need drivers?  Also, how can I tell if I need video drivers?
I am brand new at this sort of thing, do not know my way around computers that great.
Thanks.

---

### Post by arkara on 2008-02-18
my friend you dont need drivers
all linux drivers are built in the kernel..
now if the laptop is a new model then it might not be supported. YET...
anyway
one thing is to try and to boot with acpi=off this can be done by modifying the file
/boot/grub/menu.lst this can be done with this command.
```
sudo gedit /boot/grub/menu.lst
```
and then make is look like this. This is in line number 130 in my system see the highlighted line and make yours to look like this.
and aslo be sure to keep a backup in case sth goes wrong.

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d2a4282a-f5ba-4320-94b3-4e08e404023e***_ ro splash acpi=off_***
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

about the drivers.
ubuntu already has installed the open source driver.
but this does not support 3-d graphics.
in case you want to install the driver it is very easy by going to
system-->Administration-->restricted driver manager
that's all. i believe that you wont have any problem.
if you need anything else post is here and welcome to the ubuntu community.

---

### Post by matchet on 2008-02-18
Thanks, I installed the graphics driver, but I do not know where I enter that command, or to double-check line 130, or how to make a 'backup'.

---

### Post by arkara on 2008-02-18
you can enter commands by using the terminal.
this can be done by going to.apps-->accessories-->terminal.
this terminal is a command line interface. and it is very useful and powerful in linux so DO NOT BE AFRAID OF THE TERMINAL.
be sure to get a shortcut of it on your desktop in order to use it easier. this can be done by right clicking to it.
now
after you see the command line interface(cli) give the following commands.
```
cd /boot/grub
``` (this will get you to the folder)(cd is the command for CHANGE DIRECTORY)
then give
```
sudo cp menu.lst menu.lst.bak
``` (sudo will make you super user for the command only because you are messing with critical system files. and cp is the command you use for copying the file menu.lst to the file menu.lst.bak. well the second one does not exist and so linux will create it for you, so dont worry.)
then give
```
 sudo gedit menu.lst
``` gedit is the text editor you will use and menu.lst is the file that you will edit.

WARNING:by booting with acpi=off will disable basic laptop functions such as power management. you will also experience a prolem when you poweroff. the system will come to a halt and then you will switch your machine off by hand.(you dont need to worry about that it wont harm your system) i am using acpi=off on my laptop. because of a sound problem too.

---

### Post by zami on 2008-02-18
If the following is remedial for you I apologize.  I just wiped and reinstalled on a Dell Laptop yesterday, and when I fired up Ubuntu my volume was the exact opposite of yours - it was stuck at full volume! (The boot-up tune scared the heyhey out of my kids and ran one of our cats right out the house!)  It took me about an hour of fiddling to get the volume back in my control, and the speakers to stop sounding like they were buried in mud.

Anyhow for me it was just settings, and I suggest you tinker in three locations.

1. Menu > System > Preferences > Sound 

2. In your toolbar (assuming your using Gnome) double click your Volume Control (if you don't have this applet, right click the toolbar, click "add to panel" and double click on the Volume Control applet).  This should open up your volume control.

3. Also in volume control look in File > Change Device   
(Yay!  *More* possible settings.)

I had to set everything to ALSA in both sound preferences and volume control, and the keyboard control to PCM (NOT master surprisingly).

Good luck with everything!  

-zami

---

### Post by arkara on 2008-02-19
so matchet? what about your sound was is fixed??

---

### Post by ctlongley on 2008-02-28
I created a thread for the numerous people having the same problem. This fixed my sound card on a 3707. Hope it works for you as well.

[http://ubuntuforums.org/showthread.php?t=710343]("http://ubuntuforums.org/showthread.php?t=710343")

---

