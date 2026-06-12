---
title: "Ubuntu is unable to recognize my nvidia card or unable to run nvidia drivers"
date: 2008-08-07
forum: General Help
---

### Post by SandyM on 2008-08-07
I was willing to have 4 different wallppers on my 4 different desktops and thus posted for help in this forum. I received an reply asking me to do the following

1. I was told that my icons will be gone and I have to install Avant window navigator for icon shortcut.

2. Before going further I was told to go to system > Preferences > Advanced Desktop Effect settings. then enable 'desktop cube'.Go to appearance and add any 4 wallpapers under background images. I did that.

press Alt+F2 > Enter gconf-editor > apps >nautilus > preference > Deselect 'Show Desktop'.

I did that and without closing the nautilus window I rotated The dektop cube to see if the work is done but only 3 different wallpaper were enabled and one desktop screen was blank. So I MAXIMIZED THE NAUTILUS WINDOW AND AGAIN CHECKED 'show desktop' so that I can revert to my earlier position.

This was the genesis of my problem because after that my screen went white blank and I decided to restart my PC but since then MY PC IS NOT RECOGNIZING MY NVIDIA 8800GT CARD .

I have tried three separate drivers of NVIDIA- one the older and default driver provide by ubuntu through HARDWARE DRIVERS IN ADMINISTRATION UNDER SYSTEM,  then the latest one which is 173.---(something I don't remember clearly) and atlast I tried newest beta version driver of NNIDIA (177.---something)

None of them worked and I am working on low resolution however after restarting in generic mode and then repairing my x-server I get back default resolution but NO COMPIZ EFFECTS CAN BE ENABLED. And if I install graphic drivers thole problem get restarted .

---

### Post by drs305 on 2008-08-07
Have you seen the following thread by nbayiha from 2 days ago about installing nvidia drivers. It goes through the various ways of installing them.
[http://ubuntuforums.org/showthread.php?t=880787]("http://ubuntuforums.org/showthread.php?t=880787")

---

### Post by overdrank on 2008-08-07
Ok what I can suggest is that you try what PmDematagoda suggest here
```
Do this:-
1) Open a modules file for editing with:-
Code:

sudo nano /etc/default/linux-restricted-modules-common

2) Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"

and save the file.

Then reboot the PC and see if the Nvidia driver now works.
```
Here
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)
I have not used that model of nvidia card but this suggestion has helped me and others. If this does not work then you may try and boot into recovery mode and use the xfix option. Hopefully this will return you to the desktop and then you can tackle the issue of compiz.

---

### Post by overdrank on 2008-08-07
> **drs305 said:**
> Have you seen the following thread by nbayiha from 2 days ago about installing nvidia drivers. It goes through the various ways of installing them.
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5542318]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5542318")

Hi drs305  is that the correct link? :)

---

### Post by drs305 on 2008-08-07
> **overdrank said:**
> Hi drs305  is that the correct link? :)

Don't know what happened; here it is again and I'll change the original:
[http://ubuntuforums.org/showthread.php?t=880787]("http://ubuntuforums.org/showthread.php?t=880787")

---

### Post by babylon2233 on 2008-08-07
envyng-gtk, by far, is the best way to install nvidia driver for me.

---

### Post by SandyM on 2008-08-08
> **overdrank said:**
> Ok what I can suggest is that you try what PmDematagoda suggest here
```
Do this:-
1) Open a modules file for editing with:-
Code:

sudo nano /etc/default/linux-restricted-modules-common

2) Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"

and save the file.

Then reboot the PC and see if the Nvidia driver now works.
```
Here
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)
I have not used that model of nvidia card but this suggestion has helped me and others. If this does not work then you may try and boot into recovery mode and use the xfix option. Hopefully this will return you to the desktop and then you can tackle the issue of compiz.
But u haven't told how to save. See I have already told u that I am new to ubuntu

---

### Post by drs305 on 2008-08-08
> **SandyM said:**
> But u haven't told how to save. See I have already told u that I am new to ubuntu

Once you have made the changes using nano, you save the file by selecting CTRL-O. It will display a line that starts "File name to write:". Then hit Enter to save the file. To exit nano, type CTRL-X.

---

### Post by cong06 on 2008-11-05
I tried this and it didn't work for me.

I'm having a similar problem where I know that at one point I got it working easily (a previous install). But for some reason it refuses to utilize the card now.

---

### Post by drs305 on 2008-11-05
> **cong06 said:**
> I tried this and it didn't work for me.

I'm having a similar problem where I know that at one point I got it working easily (a previous install). But for some reason it refuses to utilize the card now.

cong06,

since you mention a 'previous install' you may now be using Intrepid. If so, things have changed and what worked in previous versions may no longer apply.  It would probably be best to start a new thread.

For what it's worth, I have been able to abandon envyng-gtk with the new release and my nvidia card runs fine with the nvidia-glx-177 drivers. You can activate certain proprietary drivers via System, Administration, Hardware Drivers.

---

### Post by cong06 on 2008-11-05
No, my bad. I did mean hardy, but if I had read the link and actually tried envyng-gtk before I posted I wouldn't have wasted your time...

---

