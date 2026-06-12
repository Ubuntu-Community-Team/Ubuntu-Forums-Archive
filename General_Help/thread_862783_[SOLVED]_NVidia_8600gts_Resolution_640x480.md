---
title: "[SOLVED] NVidia 8600gts Resolution 640x480"
date: 2008-07-17
forum: General Help
---

### Post by scottfmcleod on 2008-07-17
Hey all, I've been trying for the last 3 days to get my EVGA NVidia 8600gts working with the offical NVidia drivers.  The problem I'm having is that each time I install the drivers, I get a maximum resolution of 640x480.  The three methods I tired  (multiple times each)  were:

1) Click the Restricted Drivers that popped down automatically.  This instlled nvidia-glx-new.
2) Used the Envy script in automatic mode 109.* drivers, and clicked the earlier 9?.* drivers (I belive this is nvidia-glx?).
3) Manually went to nvidia.com and downloaded their sh script, killed x, stopped the gdm, and installed their drivers.

Like I said, I still was unable to change my resolution to anything higher than 640x480.

I have also tried manually editing my xorg.conf file to add both a list of resolutions and VertSync and HorSync parameters.  Unfortunately, my monitor is a 19" XEROX XR6-19dw with max res of 1440x900 and I'm having trouble finding documentation on its refresh rates.  After several tries, this ultimately resulted in no video output (Ctrl+Alt+F1 didn't get me anywhere) and I reinstalled again.

Fortunately, I don't have anything to loose (on my hdd).  It seems like most people suggest that the 8600 will work with no problems.  Am I doing something blatantly wrong?  It doesn't seem like this should be terribly complicated, but I am fairly new to linux.  Right now I've just reformatted again and am using the native generic drivers at 1440x900.  Thanks in advance.

---

### Post by Rhubarb on 2008-07-17
There are a few ways that may work for you.
In the Ubuntu desktop, press Alt + F2, and enter in:
```
gksu displayconfig-gtk
```
There you may select your monitor model, resolution and refresh rate.
Then log out, and log back in again.

-------------------------------------
If this doesn't work for you, try:
In the Ubuntu desktop, press Alt + F2, and enter in:
```
gnome-display-properties
```

-------------------------------------
If that doesn't work, it's time to get down and tell nvidia who's boss:
In the Ubuntu desktop, press Alt + F2, and enter in:
```
gnome-terminal
```
Within the terminal, enter in:
```
sudo nvidia-xconfig --add-argb-glx-visuals --depth=24 --no-logo --mode=1440x900
```
This one should work in most cases, you'll need to log out then log back in again for the changes to be made.

-------------------------------------
It is also possible to use xrandr to change your resolution too, but I'm unsure of it's usage at the moment, and haven't had the need to ever use it.

---

### Post by stitchmysmile93 on 2008-07-17
Why don't you try installing with Envy...

---

### Post by scottfmcleod on 2008-07-17
stitchmysmile93 -

Unfortunately, Envy didn't seem to do the trick for me.

Rhubarb - 

I should try these methods after I install the drivers again, correct?  Is there a preferred method?  Hardware Drivers vs. Envy vs. Nvidia sh script?

---

### Post by Rhubarb on 2008-07-17
> **stitchmysmile93 said:**
> Why don't you try installing with Envy...
scottfmcleod has tried using envy:
> **scottfmcleod said:**
> 2) Used the Envy script in automatic mode 109.* drivers, and clicked the earlier 9?.* drivers (I belive this is nvidia-glx?).
Envy is not the same as nvidia-glx.  Envy actually grabs the latest drivers from nvidia's website.
I have a feeling Ubuntu can't recognise what screen is attached to it, which is why he may have to specify manually what resolution his display can handle.

I would recommend using the envy (nvidia) drivers, just use the latest ones by running envy in Applications --> System Tools --> EnvyNG
Make sure you select the nvidia tab.  If you haven't already, try re-running envyNG.
If you don't have EnvyNG for some reason, you need to install it:
Open up a terminal, and run:
```
sudo aptitude install envyng-gtk
```

---

### Post by scottfmcleod on 2008-07-17
Rhubarb, thanks, I'm getting closer.  I tried the generic LCD 1440x900, but that resolution doesn't appear in the drop down list.

I am up to 1024x768 now which is much easier to work with at least.

The nvidia-xconfig setting you wrote also did not work to force the proper resolution.

Now I'm scanning through the vendor specific LCDs and am looking for one with 1440x900 available.

---

### Post by Rhubarb on 2008-07-17
After you've run:
```
gksu displayconfig-gtk
```
In the place where you specify your computer monitor model, make sure you check the wide screen monitor check box.
Once checked, you should find the correct resolution in the drop-down list.

---

### Post by scottfmcleod on 2008-07-17
Wow, thanks you are amazing!  That save me so many more hours of blinding editing my xorg.conf file!

Thanks again!

---

### Post by Rhubarb on 2008-07-17
Good to hear :)
You may want to mark this thread as solved (in the thread tools menu).
If you like you can thank by pressing the [IMG]http://ubuntuforums.org/images/buttons/post_thanks.gif[/IMG] button.

---

### Post by scottfmcleod on 2008-07-17
Thanks for the tips, was looking for both of those!

---

