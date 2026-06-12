---
title: "How can I force the correct screen resolution?"
date: 2008-10-31
forum: General Help
---

### Post by dpaint4 on 2008-10-31
My Acer AL1716 is 1280x1024 at 60hz, but it's not detected properly for whatever reason and neither nVidia configuration or 'Screen Resolutions' give me that option.

Tried editing xorg.conf, but got no results in my attempts. Two versions of Ubuntu ago, there was an application called something like 'Monitors and Screens' or something like that and it allowed me to pick my specific model. That doesn't exist anymore, hidden or otherwise, and now I'm stuck with a disturbingly low resolution. :confused: I'm tired of finding a new way to deal with this every time I upgrade.

I'm a graphics guy -- can somebody save me?

I'm posting because there seem to be lots of *related* posts, but none that are specifically this issue.

---

### Post by valentin.dumitran on 2008-10-31
In 8.04: sudo displayconfig-gtk
It should work in older versions too, I don't know about 8.10

---

### Post by dpaint4 on 2008-10-31
> **valentin.dumitran said:**
> In 8.04: sudo displayconfig-gtk
It should work in older versions too, I don't know about 8.10
Thanks, but I guess that doesn't apply to 8.10. I'm getting this:

```
sudo: displayconfig-gtk: command not found
```

---

### Post by coolethan on 2008-11-03
> **dpaint4 said:**
> Thanks, but I guess that doesn't apply to 8.10. I'm getting this:

```
sudo: displayconfig-gtk: command not found
```

take out the colon 

sudo displayconfig-gtk

---

### Post by ktkoma on 2008-11-04
I had the same problem and the same error.  the command issued to terminal:

 sudo displayconfig-gtk 
(with no ":" )

yields the error message that does have the :

sudo: displayconfig-gtk:  command not found

resolution worked great on NVIDIA GeForce 6100 nForce405 upon the initial install of 8.10 (From the install CD for AMD64), but now I can not configure for high resolution after applying the latest updates.

---

### Post by meastwood on 2008-11-08
First check what screen resolutions you can use - 
From the desktop/gui open a xterm or terminal and run
~$ xrandr
Screen 0: minimum 320 x 240, **current 1440 x 900**, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0*    51.0  
   1280x800       52.0  
   1280x768       53.0  
.......

the ouput may also look like this 
SZ:    Pixels          Physical       Refresh
 *0   1600 x 1200   ( 406mm x 305mm )  *75   70   65   60    (your current res)
  1   1280 x 1024   ( 406mm x 305mm )   85   75   60  
.....

You can the try any resolution listed by typing
~$ xrandr -s 1024x768             (or if the output is like that just above)
~$ xrandr -s 1                    (will set res to 1280x1024)
You can then close your terminal or whatever.  This resolution will remain in effect for the current session only.  Once you logout or stop the Xserver the res. will revert back to what you had before.

To make the screen res. change permanent you need something like 
Section "Screen"
 .....
 SubSection "Display"
               Depth           24
               Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
       EndSubSection
 ....
in your /etc/X11/org.conf.  The first mode (1600x1200) will be used first, failing that the next and so on.

Having said this :-), I'm having a similar problem on a USB Pen installation of Hardy 8.0.4.1.  I'm using Fluxbox as I wanted something lightweight. Inspite of having a Modes line in my xorg.conf, X defaults to a mode of 720x400, I'm getting no errors in xorg.log etc.. though have a work around for it.

Anyway - for Hardy, if xorg.conf misbehaves, from the desktop open a xterm or terminal 
~$ touch .xprofile
~$ echo "/usr/bin/xrandr -s 1024x768         (if you want 1024x768)

Logout and then back in again.

If you have any problems logging back in use the 'options' -> select session on the login screen, select failsafe session, shell, terminal or whatever - login then delete your .xprofile file and all will be as before

---

### Post by meastwood on 2008-11-08
ooops
~$ echo "/usr/bin/xrandr -s 1024x768" > .xprofile

---

