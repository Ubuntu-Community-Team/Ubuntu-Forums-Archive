---
title: "Asus S530F (VivoBook S15) Randomly Hangs on Startup and Shutdown"
date: 2019-06-16
forum: Hardware
---

### Post by linuxguy2 on 2019-06-16
I have an Asus S530F (VivoBook S15) with Ubuntu 18.04 on it.
Although sometimes it starts up and shuts down normally, very frequently it will "hang" during start up/boot up and shut down.
I hold down the power button to shut it down forcibly then and try again until it boots up properly or leave it shut down if that's what I'm attempting to do.
I believe the OS is installed in EFI mode (though I am not 100% sure). I have SecureBoot turned off.
I have fiddled with Grub2- but it doesn't seem to help.
Grub is supposed to go directly to booting Ubuntu, but sometimes it displays the OS menu anyway, even though Ubuntu is the only OS on this device.
Changing the timeout setting does not help- I'm wondering if this is a related issue.
I have even uninstalled OS-Probe to see if that is interfering with bootup, but again nothing.
I have boot up and shutdown set to verbose- but when it hangs it just displays a blank screen, whether on start up or on shutdown.
I'm wondering what is going on here and if anybody can give me any clues or potential solutions.
Thank you for reading!

---

### Post by tea for one on 2019-06-16
The next time your PC starts slowly, wait until you have logged in, then open a terminal

```
systemd-analyze blame
```

When your PC hangs on shutdown, press the **Esc** key (while it is still shutting down) to see which part of the process is taking a long time.

Best wishes

---

### Post by cliffflip on 2019-06-18
Check &#8220;Disks&#8221; app and look at your disk drive(s) for any bad sectors. Last time I&#8217;ve experience this is when one of my HDD (desktop, not a laptop) is having bad sectors. Startups & shutdowns really affected by that with disk led indicator always lit.

---

### Post by linuxguy2 on 2020-03-06
> **cliffflip said:**
> Check “Disks” app and look at your disk drive(s) for any bad sectors. Last time I’ve experience this is when one of my HDD (desktop, not a laptop) is having bad sectors. Startups & shutdowns really affected by that with disk led indicator always lit.

This laptop has an NVMe SSD. It is still giving me lots of problems booting up.
Sometimes I have to start, force shutdown and restart the computer over 10 times before it will successfully boot.

Honestly, I always used to install Linux/Ubuntu without much of an issue. These days I'm not confident at all whether I'll be able to successfully install and boot Linux on a mainstream PC at all (I have another thread about another laptop, too).

---

