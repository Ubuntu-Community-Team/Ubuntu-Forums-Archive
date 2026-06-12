---
title: "Help - Newbie - Incorrect screen resolution..."
date: 2009-03-25
forum: Hardware
---

### Post by mattcinders on 2009-03-25
Hi Everyone,

I’m new to Linux so please go easy.  I’m MSCE and have only been using MS Windows over the past 14 years!  I decided to start to take the plunge and try and learn/get familiar with Linux.  This really is a different ball game.

I’m running the latest version of Kubuntu (8.10) on a Intel Motherboard which is using the G41 express chipset with onboard Intel X4500 graphics.

The installation went well.  I even managed to setup software Raid-1 on my dual drive setup.  However my only issue is the screen resolution.  

My monitor is Samsung 23” with native resolution of 1920x1080 connected via VGA Port.

I’ve seen many people on the forums are having problems with this chipset, is this the cause of my incorrect resolution?..  or is Kubuntu not detecting my monitor correctly?...

I looked at the xorg.conf file but it doesn’t contain any entries.  I understand that this is the new version of Xserver which uses HAL to identify hardware.

If I run xrandr –q from the console I don’t see 1920x1080 listed. Just 5 default 4:3 resolutions.

I have checked out the xorg.0.log and it looks like it is using the VESA driver.

Can anyone help me out as to what I should check/do next?... 

I'm guessing I need to upgrade to use the intel driver, but I can't find out how to do that.  I did try the apt-get command for the latest and it said I'm using them already. 

Any help is appreciated!

Cinders.

---

### Post by dagoth_pie on 2009-03-25
[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)
this should have all the information you need to configure the X server, you'll probably want to read it, but to simplify things, if you go to the terminal and run the command

sudo gedit /etc/X11/xorg.conf

then go down and find the "monitor" section and add at the bottom 

DisplaySize 1920 1080

make sure you save it, then restart the x server (ctrl + alt + backspace will do this leaving you at the login screen, closing any applications you're running so save anything your working on etc etc)

if that doesnt work, post something on here

Good luck

---

### Post by mattcinders on 2009-03-25
Hmmm...  didn't work.  On reboot it asked me to re-setup the graphics.  

Now I have no network connectivity...   Help?

Cinders.

---

### Post by dagoth_pie on 2009-03-25
odd, just out of curiosity, have your tried installing the 915resolution?
```
sudo apt-get install 915resolution
```
It's an bios hack for intel gpus, to support extra resolutions, to be honest I've never needed to use it, or know how it works, I don't have any PC's with intel gpus, and all the ones I've worked on have had 4:3 screens.

If you go into the terminal and run the command
```
lspci
```
it will list all devices connected on the pci/agb/pcie bus, its easy to remember if you think of it as list pci, just seeing as I get the feeling that your wanting to learn everything that could possibly help you, the lsusb command, does the same thing for the usb bus. If you enter it and it comes up with an unidentified chipset message somewhere in the printout, you know what isn't working properly, but if it's named the device, then it's found drivers and should be working properly, so if you could copy the printout of lspci here, it may be helpful.

---

### Post by NT4usB on 2009-03-25
Good luck!
Here's a couple [threads]("http://ubuntuforums.org/search.php?searchid=57134001") on the subject.
I have a GA-EG41M-S2H with G41 on board.
Tried lots of stuff to get it going. Finally have a useable config via VGA. No joy at all for the DVI out.
I'll post up my xorg tonight for you to look at.

---

