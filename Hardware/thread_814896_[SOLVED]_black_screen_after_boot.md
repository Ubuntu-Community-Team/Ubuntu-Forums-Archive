---
title: "[SOLVED] black screen after boot"
date: 2008-06-01
forum: Hardware
---

### Post by ichigo on 2008-06-01
I'm trying to help a friend with her computer. She's got both, Vista and OpenSuse 10.2, installed on a Vaio VGN-N21Z notebook. 
Until yesterday Suse worked without any problems. But then all of a sudden, when she booted, the screen went black and seemed to be reset several times (looks similar to what happens when you've messed up your xorg.conf) just a second or so after the login screen showed up.
I've tried to at least save her data with a live CD, but i've got similar problems (black screen/screen lockup right after getting to the GUI) with the Live Versions of Ubuntu 8.04, Kubuntu 8.04, OpenSuse 10.3.
This made me think that the problem doesn't seem to distribution dependent...
The only liveCD that worked was Suse 9.1, but that couldn't detect the hard-drive.

I've read in another thread that somebody had similar issues that were caused by bad RAM. So I've run memtest, but it has finished without any errors..

I've finally managed to get her data with a reiserfs-driver in vista (which works flawlessly), but I am not sure whether I should try to reinstall Linux (some distribution) or if this is a hardware issue and reinstalling wouldn't make sense... Any suggestions?

---

### Post by housam on 2008-06-01
Try to boot from ubuntu live CD and see how it works with you. play with it , connect to the net and use as may programs as you can . if it is ok then it is not a hardware issue.

---

### Post by ichigo on 2008-06-01
Well, I already tried to. The Ubuntu liveCD locked up, just when i got to the graphical interface - as did the LiveCDs of OpenSuse, and Kubuntu...

Since I had no other idea I've just installed ubuntu via text mode. Now I can log in, but after that I can't interact with anything on the desktop. The only thing that works is moving the mouse pointer.
(even Ctrl+Alt+Backspace and Ctrl+Alt+Del won't work)

---

### Post by ichigo on 2008-06-01
Figured out that the problem is caused by the graphic card (either the driver or the hardware). I managed to make ubuntu work (install via text-mode; substituting the xorg.conf and updating the system in recovery mode). The only remaining problem is that the resolution is just 800x600. I've tried many drivers, but every setting with more than 800x600 made the system crash...

EDIT: I have marked the thread as solved, since I gave the laptop back to my friend about 2h ago, so she can work with it. However, if you have a suggestion how to get a better resolution, I'd appreciate your input!

---

### Post by housam on 2008-06-02
try this :
System > Preferences > Screen Resolution
If you didn't find your settings , try the following :

```
sudo nano /etc/usplash.conf
```
 you will got something like that 


> # Usplash configuration file
# These parameters will only apply after running update-initramfs.
  

add the required resolution 


> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=[COLOR="Red"]1280[/COLOR]
yres=[COLOR="red"]800[/COLOR] 
 

set [COLOR="red"]x & y[/COLOR] as you want then reboot and type :


```
sudo dpkg-reconfigure usplash
```
 then check for the new settings -- System > Preferences > Screen Resolution and select the new one.
__________________

---

