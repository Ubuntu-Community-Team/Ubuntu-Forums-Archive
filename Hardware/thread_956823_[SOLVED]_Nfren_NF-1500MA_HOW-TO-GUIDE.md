---
title: "[SOLVED] Nfren NF-1500MA HOW-TO-GUIDE"
date: 2008-10-23
forum: Hardware
---

### Post by starcannon on 2008-10-23
I have 3 of these old 15.1" TFT-LCD Monitor's that I am responsible for. After much wailing and gnashing of teeth I have an xorg.conf file that works, yes even with the log in screen.

I know that there are not a lot of people dealing with these monitors any longer as they are quite old; that said, for those of us who are, heres the quick fix, along with the guide if your curious how I did it.

These monitors do work out of the box on a vesa driver; however, after installing an accelerated driver for an nvidia card, the login screen was a mess. I tried everything, messing with things like adding vga=791 to menu.lst, or adding an xrandr mode line to /etc/gdm/Init/Default, none of that worked. In the end it was a simple xorg.conf tweak.

I will include the xorg.conf file that I have assembled, along with how I assembled it here in this post. 

For these machines, because I need them to "just work" even after a kernel update, I went ahead and used the nvidia drivers from the synaptic package manager. On a fresh install the easiest way to do this is

[LIST]
[*] Run the "Update Manager" first, located at:
[LIST]
[*]{System}-->{Administration}-->{Update Manager}
[*]install the updates.
[*]reboot when prompted
[/LIST]
 
[*]Then run the "Hardware Drivers" utility located at:
[LIST]
[*]{System}-->{Administration}-->{Hardware Drivers}
[*]Enable your proprietary graphics card, mine are nvidia 6600gt's
[*]reboot when prompted
[/LIST]
 
[/LIST]
**Okay your now going to likely get a blurry screen**, don't dispair, this guide is all about fixing that. If sound is working, press CTRL-ALT-F1 after you hear the bongo's.

[LIST]
[*]Press CTRL+ALT+F1(even if you didn't hear the bongos)
[*]login:your_user_name
[*]password:your_pword
[/LIST]
**Backup the current xorg.conf**
Type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/OLD_xorg.conf_backup
```
[LIST]
[*]Press Enter
[*]Give your password again.
[/LIST]
**Remove the current xorg.conf**
Type:
```
sudo rm /etc/X11/xorg.conf
```
[LIST]
[*]Press Enter
[/LIST]
[SIZE=4]**Using the xorg.conf I attatched to this post**[/SIZE](the easy way)
**Copy my xorg.conf into your X11 folder**, assuming you saved mine to your Desktop.
```
sudo cp ~/Desktop/xorg.txt /etc/X11/xorg.conf
```**Now reboot **the computer.
```
sudo reboot
```If your setup worked like mine, the blur should be gone, you'll be greeted with a nice crisp login screen. Enjoy.

**[SIZE=4]Do it your Self[/SIZE]**(the hard way)

**Create a new xorg.conf**
Type:
```
sudo nvidia-xconfig
```
[LIST]
[*]Press Enter
[/LIST]
**Now we need to tweak the xorg.conf file** slightly for this old monitor, we'll be using the nano cli text editor:
```
sudo nano /etc/X11/xorg.conf
```
[LIST]
[*]Press Enter
[*]Using the arrow keys, navigate your way down the document till you find:
[LIST]
[*]Section "Monitor"
[*]Now add this Modeline to the bottom of Section "Monitor":
[LIST]
[*]    Modeline "1024x768@60" 64.56 1024 1056 1296 1328 768 783 791 807
[/LIST]
 
[/LIST]
 
[*]Using the arrow keys, navigat your way to:
[LIST]
[*]Section "Screen"
[LIST]
[*]Subsection "Display"
[*]Now add this to Subsection "Display"
[LIST]
[*] Modes      "1024x768@60"
[*] Virtual    1024 768
[/LIST]
 
[/LIST]
 
[/LIST]
 
[*]Press CTRL+X
[*]Press "Y"
[*]Press Enter
[/LIST]
**Now we need to reboot the computer**
```
sudo reboot
```If your setup worked like mine, the blur should be gone, you'll be greeted with a nice crisp login screen. Enjoy.

---

