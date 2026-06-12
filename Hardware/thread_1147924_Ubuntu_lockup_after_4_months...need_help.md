---
title: "Ubuntu lockup after 4 months...need help"
date: 2009-05-03
forum: Hardware
---

### Post by imazman on 2009-05-03
I have been using Ubuntu on my gateway laptop for several months with minimal problems.  Today booted the laptop and when it gets to the login prompt the mouse will not move and the keyboard will not work.
It almost seems like an IRQ problem, but I can boot another distro (Knoppix) from the USB without a problem.  Using a USB boot I can access the harddrive and make changes if necessary.  
I would hate to have to reinstall of the OS and loose all my OS installs, apps, and tweeks that have been made over the coarse of four monts.
PLEASE HELP...is there something I can look for? Also, I tried to do a command boot (option 'c') and it asks for a root password...but I tried all my normal passwords...is it blocked?

I appreciate all help
Tx
imazman

---

### Post by Dark_Stang on 2009-05-03
Can you do a Ctrl+Alt+F1 and get to terminal? If you can login then run
```
sudo dpkg-reconfigure xserver-xorg
```
to make sure the keyboard is setup correctly.

---

### Post by imazman on 2009-05-03
Yes, I could do that.  I went thru the config app but it did not help.  Still no keyboard nor mouse pad?  I set the BIOS IRQ settings to auto and still does not work (but usb distro does).  I had originally installed Intrepid.
Any other suggestions greatly appreciated!
imazman

---

### Post by imazman on 2009-05-03
> **imazman said:**
> Yes, I could do that.  I went thru the config app but it did not help.  Still no keyboard nor mouse pad?  I set the BIOS IRQ settings to auto and still does not work (but usb distro does).  I had originally installed Intrepid.
Any other suggestions greatly appreciated!
imazman

Also want to add that when I did this and logged in I got a bunch of "-bash: /dev/null: Permission denied" msgs scroll down the screen but the login did work.

---

### Post by Dark_Stang on 2009-05-03
> **imazman said:**
> Also want to add that when I did this and logged in I got a bunch of "-bash: /dev/null: Permission denied" msgs scroll down the screen but the login did work.
Well now that's not supposed to happen. You may have some permissions issues or some hosed startup scripts. And that could explain why you don't have any keyboard or mouse support.
Get back into it, do another Ctrl+Alt+F1 and login again. Then run
```
sudo /etc/init.d/gdm stop
startx
```
This will stop gdm, and end the GUI session. Then by running "startx" it will launch your default GUI environment and it should take you to your desktop. Do you have keyboard and mouse support in this mode? 

If not do Ctrl+Alt+F1 again. Hit Ctrl+C to close the X-session. And run
```
sudo startx
```.
Do you have keyboard and mouse support in this mode? (basically running as root)

---

### Post by imazman on 2009-05-03
I tried stopping gdm as you said (using sudo) and running startx as user.  The stop worked but the startx did not work.  It displayed a bunch of restore commands then /etc/X11/Xsession: 75 cannot create /dev/null: Permission denied
Xsession: unable to create X session log/error file; aborting.
then a bunch of restore and finally an error setting MTRR.
Lastly an xauth: error in locking authority file /home/<my home dir>/.Xauthorty

So I tried it usimg sudo and...
-while x starts up, the mouse does not move, then...
-when the gnome window mgr comes up and I can see the desktop wallpaper, but...
-a dialog window appears with title "Error" and says "User Switcher" has quit unexpectedly. If you reload a panel object, it will automatically be added back to the panel.  Buttons: Don't Reload  or   Reload  ...
- but still no mouse or keyboard...thus can't do anything here

---

### Post by Dark_Stang on 2009-05-04
It sounds like it's thoroghly hosed. I'd wait to see if somebody has an easy suggestion that I don't know about, but you may end up having to reinstall the os and your software. As long as your /home is on a seperate partition, or as long as you don't format during the reinstall, all your user settings should still be saved.

---

