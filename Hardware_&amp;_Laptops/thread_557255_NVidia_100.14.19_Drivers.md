---
title: "NVidia 100.14.19 Drivers"
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by Max Luebbe on 2007-09-22
Just installed the newest drivers, which are a big deal to me because they eliminate the bug with turbocache that will allow me to use Beryl - but after a successful installation, my settings only work for about 1 X session. The next time I start the machine, X refuses to start and the system complains that the settings in xorg.conf are no good.

At this point I rerun the NVidia binary installer, which gets things working again for another session.

I don't want to have to do this everytime I use my machine - what could be causing this.

I previously used envy, is this causing a conflict?

---

### Post by PmDematagoda on 2007-09-22
Did you try reconfiguring your xorg.conf file with ```
sudo dpkg-reconfigure xserver-xorg
```?

---

### Post by Max Luebbe on 2007-09-22
I have not, but the nvidia script alters my xorg.conf

Which works for 1 session.

Should I still reconfigure my xorg file as you suggested?

---

### Post by PmDematagoda on 2007-09-22
> **Max Luebbe said:**
> I have not, but the nvidia script alters my xorg.conf

Which works for 1 session.

Should I still reconfigure my xorg file as you suggested?

Yes, give it a try. I remember I tried using Envy to fix my graphic problems, but in the end it just destroyed X, so after a quick reconfiguration everything returned to the way it was.:)

---

### Post by mooscape on 2007-09-23
Similar problem here.

Everything was working perfectly yesterday, but today I cann't even get into the GUI.  I get a funny looking blue screen in the text window that says: > API mismatch ... NVIDIA DRIVER 100.14.19 but kernel module's version does not match...    Linux 2.6.20-16-generic#2

 I am currently typing this from the same machine, using the installation CD. Everything works well, so I do not think there is any hardware problem.

 Is there anything I can do to get this working again? I am new to this kind of problem, any clear pointers will be much appreciated.

---

### Post by mooscape on 2007-09-23
I am currently limping along with a compromise solution. I couldn't get the GUI up, so I had to work in the comand line level.  I used the following to call up the settings and selected VESA instead of nVidia. 
> 
sudo dpkg-reconfigure -phigh xserver-xorg

I still cannot get the nVidia driver to work.  ](*,)

---

### Post by kiran_aryan on 2007-09-24
Try the method that is described here - [http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)

Just replace 100.14.11 to 100.14.19 for the drivers. His method definitely works.

---

### Post by Max Luebbe on 2007-09-24
Followed his instructions to the letter.
Drivers now load up everytime, but trying anything that requires 3d acceleration (glxgears, glscreensavers) results in a seg fault.

Any ideas on where to go from here?

---

### Post by rybu on 2007-09-24
Try disabling compiz -- go to system -> preferences -> desktop effects and turn them off.

---

### Post by Max Luebbe on 2007-09-24
Compiz is off, it's never been on.

With the new drivers, anytime I try and use something that requires 3d acceleration, I get a segmentation fault.

I am not running Compiz/Beryl/XGL etc. Just a vanilla Gnome desktop.

---

### Post by dabl on 2007-09-24
Once you have got the Nvidia driver installed (by whatever means -- I use Envy), then you need to open a console and do this:

```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

This will write a new xorg.conf file, and if you're lucky it will auto-detect your display/monitor in the process.

When it's done (2 seconds later), restart your xserver with Ctrl-Alt-Backspace, and log back in.

Now, open the console again and enter ```
sudo nvidia-settings
```
this will open the Nvidia driver utility.  On the "X Server Configuration" panel, set your screen resolution and refresh rates, and do a "detect display" if it is not already showing your display or CRT.  I leave refresh set to "Auto", but you can try to force it to your favorite rate.

When you have it the way you want it, click the "Save to X Configuration File" button in the lower right, then "x" "merge" and click "save". This will add the necessary entries to xorg.conf.

You should now be in business with your default settings.  To verify that glx is working, open the console and enter ```
glxgears
``` You should see a graphic, and if you drag it off the console window, you should see the computed "frames per second" performance for your Nvidia chip.  :guitar:

---

### Post by mooscape on 2007-10-06
Dear All 

I have tried the recommendations given above.   I have got the graphics driver working perfectly, but only within the session I am in.  When I start the machine the next day, I am back to square one and the driver won't load.   I then have to start in VESA mode, rerun nvidia-settings and then restart x as per **dabl**.   

Is there a problem with GRUB or the kernel that anyone knows about? 

Any ideas would be much appreciated.  Some people appear to have got things working properly by reloading Feisty onto their machines from scratch. I use my machine for work and  would rather not do this if I can help it.

---

