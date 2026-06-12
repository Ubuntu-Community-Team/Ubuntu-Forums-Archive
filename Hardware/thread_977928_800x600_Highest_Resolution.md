---
title: "800x600 Highest Resolution"
date: 2008-11-10
forum: Hardware
---

### Post by chuggaboo on 2008-11-10
Hello there!

I have been using Xubuntu for a while. Before that I used Ubuntu, with no problems with resolution whatsoever. I decided to give Kubuntu a try last Friday. It's version 8.10, if that matters.

As far as I know, the installation went smoothly, except for the resolution being terrible.

The highest I can set it to is 800x600. My monitor is supposed to be 1440x900. It's not too fun to use in 800x600. ;-;

I'm pretty sure it's a problem with the drivers. I think I have the nvidia-glx-96 drivers installed.

I've messed around with xorg.conf to no avail. I didn't really know what I was doing to be honest. :P

So yeah, if anybody has an idea of what is wrong, I'd appreciate any help. And let me know if you need more information.

Thank you!!

---

### Post by costre on 2008-11-10
Have you tried the restricted drivers? 

If not, go to System -> Administration -> Hardware Drivers, enable the graphics adapter driver, and reboot.

If it doesn't help, try running Envy, [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck

---

### Post by chuggaboo on 2008-11-10
Okay, okay, we're making progress.

I tried Envy and it automatically installed some packages.

I rebooted like it instructed me to.

After it turned off and back on, the graphical login screen came up in the correct resolution! Woot!

After I log in, everything seems fine. Until after about 8 seconds. After this time is up, my whole monitor goes black except for a floating box that says:

"Attention:  Input Not Supported"

I can hit ctrl + alt + backspace to get back to the login screen successfully, but the same thing happens again when I try to log in again.

Thank you for your help, by the way. :)

---

### Post by chuggaboo on 2008-11-10
Not to be impatient or anything, but my computer is sort of unusable until I get this figured out... :P

---

### Post by davidgeeee on 2008-11-11
Chug

Try this solution below.  You may have to ctrl+alt+F1 to get to command prompt to edit the xorg.conf.

 Re: Where is "Screens & Graphics" in 8.10
Just in case this helps someone that found this thread, here is how I fixed my screen resolution with 8.04.

First my graphics adapter and monitor were not detected. Tried all kinds of edits to xorf.conf with no success.

The Fix for me was this:

I used a 7.04 live CD to boot into Ubuntu (not install). The resolution was set to the highest my monitor could handle. Detected my graphics card correctly. Checked in "Screen Resolution" utility and all the resolutions were there. So, I copied xorg.conf to a USB drive. Restarted 8.04 and made a backup of the current(faulty) xorg.conf file. Then I copied the sections of xorg.conf (from 7.04) that were about the graphic card and monitor and modes to the xorg.conf of the 8.04 installation. Restarted X and everything was peachy!

I may try this with 8.10 today, but I am pretty sure it will work there too.

Hope this helps someone that has been banging their head like me!

---

### Post by chuggaboo on 2008-11-14
Sweet! Thank you! I got it pretty much using this same method.

I just used an older xorg.conf file I had backed up from when I was using ubuntu, and installed a different driver and it worked like a charm.

Thanks again. :)

---

### Post by davidgeeee on 2008-12-10
Cool!!!

---

