---
title: "Drivers"
date: 2011-09-14
forum: Hardware
---

### Post by lonewolf69 on 2011-09-14
I am a noob who just built a new machine.  I noticed that the video driver was not installed when I tried out 0 AD.  I bought a Radeon HD 6450 and dropped it in. 

-I got was some blue lines across the top 1/4" of the screen.  
-I rebooted and got a ubuntu screen with boot options. 
-Tried the standard boot option.

-Removed the card and rebooted.
-Black screen with "Input Not Supported", no options, nothing.

How do I get back to where I was?  Is there an option like Windows safe mode?  If so, how do I get to it?  I installed ubuntu 11.04 with a disk from Ubuntu magazine.

Thank you.

K

---

### Post by mikewhatever on 2011-09-15
You should try installing the proprietary ATI driver from the repositories. There is a dedicated application for that in Ubuntu, it's called Additional Drivers.
If you have the old Gnome2 interface, look for it under System->Administration.

PS: Didn't know Ubuntu had a magazine.

---

### Post by lonewolf69 on 2011-09-17
Right now I am getting a black screen with the "Input not supported", thats it right after the bios.  I put the disk back in and selected the only reasonable option - rescue system.  Other options like "try ubuntu", "install...".  

After going through the keyboard, time zone, etc.  I finally get to "Enter Rescue Mode" Options are...
-Execute a shell in /dev/sda1
-Execute a shill in the installer environment
-Reinstall GRUB boot loader
-Choose a different root file system
-Reboot the system

ALL I NEED TO DO I GET THE ONBOARD CARD BACK FOR RIGHT NOW.  I have to admit at least with windows you boot to safe mode and delete the card you tried to install.  

I want to get off windows.  What do I do now that I tried to install a video card and have this situation?


P.S. Its called Ubuntu User.  Good mag but a bit pricey: $15.99/97 pages and I think its quarterly but worth it if I can get my display working! LOL

---

