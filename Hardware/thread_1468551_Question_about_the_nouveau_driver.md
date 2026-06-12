---
title: "Question about the nouveau driver"
date: 2010-05-01
forum: Hardware
---

### Post by mcgodx on 2010-05-01
Hey all;

I am not sure if I am just not searching this right, but it seems like I am having a hard time finding the answer on this...

I just installed Ubuntu 10.04 on my desktop and I know that it now has kernel modesetting with the nouveau driver, but it seems like some things don't work with it unless I am mistaken.  I tried applying the "Normal" visual effects because without it opening and closing windows is kinda hard on the eyes.  It said it couldn't do this without the proprietary nVidia driver.  When I ran glxgears, it did 3094 frames in 5 seconds, and animation was very smooth, but I don't know if CPUs can make that smooth nowadays or not.

Here are my computer's specs (it is a desktop)
> Intel Core i7 920 @ 4.0GHz
ASUS Rampage II Extreme
Kingston SSDnow 64GB x2 (was in RAID, couldn't get that to work in Linux)
nVidia GTX260

The rest probably isn't relevant.

If you guys have any way to clear this up that'd be great.  The kernel modesetting is cool so I'd like to not lose that by installing the proprietary driver, but if I have to I can live with that I guess.

I do plan on doing some gaming if I can get some games to work in Wine.

Thanks

---

### Post by UrbenLegend on 2010-05-01
Nouveau will not work with most games. It's suitable for some tech demos like glxgears, but not anything practical for now.

Good luck trying to disable it...I've been trying to figure that part out for the good part of yesterday. Blacklisting nouveau and vga16fb doesn't seem to work, because the KMS loads nouveau at startup. And once Nouveau has its teeth in the system its hard to unload it.

I've been trying to install the nvidia driver from the nvidia.com site, but the script keeps failing because it detects nouveau. Yeah I know you can install the nvidia package from repo but its outdated.

If anyone knows how to fix this issue it would be greatly appreciated.

---

### Post by mcgodx on 2010-05-01
> **UrbenLegend said:**
> Nouveau will not work with most games. It's suitable for some tech demos like glxgears, but not anything practical for now.

Good luck trying to disable it...I've been trying to figure that part out for the good part of yesterday. Blacklisting nouveau and vga16fb doesn't seem to work, because the KMS loads nouveau at startup. And once Nouveau has its teeth in the system its hard to unload it.

I've been trying to install the nvidia driver from the nvidia.com site, but the script keeps failing because it detects nouveau. Yeah I know you can install the nvidia package from repo but its outdated.

If anyone knows how to fix this issue it would be greatly appreciated.

Thanks for the heads up about nouveau.  I'll get to work on trying to disable it then it seems.

---

### Post by UrbenLegend on 2010-05-01
I figured out a workaround.

You have to blacklist nouveau and vga16fb in /etc/modprobe.d/blacklist.conf. THEN boot into recovery mode to run the install script for the nvidia driver.

Booting into normal mode with nouveau blacklisted WILL NOT WORK. My guess is that the new Plymouth boot screen loads nouveau on startup for KMS support.

Anyways, hope this helps until they fix this stupid "feature". Good luck!

---

### Post by mcgodx on 2010-05-01
> **UrbenLegend said:**
> I figured out a workaround.

You have to blacklist nouveau and vga16fb in /etc/modprobe.d/blacklist.conf. THEN boot into recovery mode to run the install script for the nvidia driver.

Booting into normal mode with nouveau blacklisted WILL NOT WORK. My guess is that the new Plymouth boot screen loads nouveau on startup for KMS support.

Anyways, hope this helps until they fix this stupid "feature". Good luck!

Thank you, I got it to work using that tip.  I now have the 195 series drivers working perfectly :)  It gave me a warning about installing it from runlevel 1 but it worked anyway.

I'm not sure why they would use nouveau by default when it's not even really ready anyway... Bragging rights I guess.

---

### Post by UrbenLegend on 2010-05-01
> **mcgodx said:**
> 
I'm not sure why they would use nouveau by default when it's not even really ready anyway... Bragging rights I guess.

Yeah, open source guys sometimes have a little too much pride. I wouldn't mind nouveau if it wasn't so hard to override.

Btw, you might not need to blacklist vga16fb when you boot into recovery mode, although I have not tested this. You also need vga16fb for the Plymouth bootloader, so make sure to un-blacklist it.

---

### Post by mcgodx on 2010-05-01
> **UrbenLegend said:**
> Yeah, open source guys sometimes have a little too much pride. I wouldn't mind nouveau if it wasn't so hard to override.

Btw, you might not need to blacklist vga16fb when you boot into recovery mode, although I have not tested this. You also need vga16fb for the Plymouth bootloader, so make sure to un-blacklist it.

I was wondering why it wasn't coming up.  Thanks.

---

