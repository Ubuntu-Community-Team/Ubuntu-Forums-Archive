---
title: "XPS M1530 intermittent wake-from-sleep problems"
date: 2009-04-18
forum: Hardware
---

### Post by phendric on 2009-04-18
Hi everyone,

I'm hoping to probe your collective Linux knowledge as I try to understand and fix the intermittent problems my laptop is having when waking up from sleep/suspend (to RAM).  Below are the details.

**General problem**

I'm always able to successfully suspend my laptop to RAM.  However, sometimes when I try to wake it back up it works just fine, and other times it doesn't work at all, and I have to force shutdown the machine and reboot.

**Symptoms**

The times when I'm unable to successfully resume from suspend, the following things occur:

[LIST=1]
[*]The power light comes on and the fan spins up.
[*]The screen comes on but is completely dark/black.
[*]Neither the bluetooth nor the wireless are active (devices have no power).
[*]Keyboard is unresponsive.  No key combinations I press ([ctrl]+[alt]+[backspace], etc.) seem to have any effect.
[*]I'm only able to get the machine to respond by holding the power button for 2 seconds to turn it off.
[/LIST]

**The Hardware**

[LIST]
[*]Dell XPS M1530, Intel Core 2 Duo Processor T7500 (2.2GHz/800MhzFSB, 4M L2 Cache)
[*]3GB, DDR2, 667MHz 2 Dimm, for XPS M1530
[*]15.4 inch Wide Screen WSXGA+ TrueLife for XPS M1530 (1680x1050)
[*]2.0MP Camera
[*]256MB NVIDIA GeForce 8600M GT
[*]200G 7200RPM SATA Hard Drive Free Fall Sensor
[*]8X DVD+/-RW Slot Load Drive for XPSM1530
[*]Dell Wireless 1490 802.11a/g Mini Card
[*]56 WHr 6-cell Lithium Ion P Primary Battery, for XPS M1530 (the battery is only at about %35 capacity right now).
[*]Dell Wirless 355 Bluetooth Module (2.0+EDR)
[/LIST]

**The software**

I'm dual booting Ubuntu 8.10 x64 with Vista Business x64.  I've applied all updates as of about 4 days ago (4/13/09), and am running the Nvidia proprietary graphics driver (v180) and the Broadcom STA wireless driver.  I don't know if the camera works out of the box as I haven't tried using it, but I'm pretty sure that the fingerprint reader does NOT work.

**Computer usage**

When I'm at home or at school, I often run with the laptop plugged in and with an external USB mouse plugged in.  When I'm on the road between home and school, I obviously don't do either of these things.

[B]Why fixing this problem is important to me
[/B]
I'd like to wean myself off of Windows, but because I take my laptop with me between home and work/school, sleep/suspend has got to work reliably, and it's not right now.  I feel like I can't start working on anything important when I might have to quickly leave because I might have to force reboot and lose all my work.

The really funny thing is that my current laptop (XPS M1530) replaced a Dell Inspiron e1405, and it, too, had frequent resume-from-sleep problems even though the hardware was different.

Can any of you shed light on what's causing the problem and how I can fix it?  I did a search in the forums for resources to help me, but didn't find anything useful.

I'd appreciate it!

Thanks,
Phillip

---

### Post by phendric on 2009-04-18
Bump.  There's a lot of activity on the forums this weekend!

---

### Post by phendric on 2009-04-21
Bump.

Since nobody is replying, should I assume that there's no fix, and open a bug report?

---

### Post by zeug on 2009-04-29
_Bump_. I have the same problem with my laptop! Does anyone have a solution? After searching for a solution, changing the propriety drivers does not seem to work.

---

### Post by Strongman332 on 2009-04-30
bump i need this for 9.04

---

### Post by sharma337 on 2009-05-04
I have the same hardware configuration (except the wireless card and the hard drive) and had the same problem as phendric. The following fix worked for me:
[LIST=1]
[*]Remove all Nvidia drivers from your system (all the **nvidia-glx-*** packages), and fall back on the default **nv** driver -- removing the old driver seems to be important. Reboot to ensure the new driver is in use.
[*]Downlaod the latest Nvidia driver from the [official Nvidia website]("http://www.nvidia.com/Download/index.aspx?lang=en-us") and install it (edit: check [this HowTo]("https://help.ubuntu.com/community/NvidiaManual") for detailed instructions) -- the version I have is **180.44**. Again, reboot to make sure the new driver is in use -- check your **xorg.conf** file.
[*]In the Nvidia settings panel, uncheck "Sync to VBlank" in OpenGL settings.
[*]Reboot and try the suspend now.
[/LIST]

If none of this works, try disabling your wireless card to make sure that the problem is not with the card.

There are many versions of the "resume from sleep" problem and I seem to remember that googling for it turned up a lot of help on the general topic. But the specific problem you describe didn't seem to be explicitly addressed anywhere and the fix above combines several of those suggestions. Hope it works for you!

---

### Post by freonchill on 2009-05-04
same problem here (dell latitude d800)

ill have to try the different driver and see if that is the issue
dont know if it matters, but i am pretty sure that i disabled "sync to VBlank" on the default restricted driver...

---

### Post by zeug on 2009-05-08
I have uninstalled the drivers nvidia-glx* with Synaptic and rebooted.  An error message come up saying that the Nvidia drivers could not be loaded and it gave an option of reconfiguring - so I did with the generic configuration.  I started X again and downloaded the driver from Nvidia. When I tried to install it, it said that X could not be running.  So I ran it in with Ubuntu in console mode and it worked but it could not find nor download (it tried to but it said could not resolve the website address) the kernel module.  What now? How do I make sure it falls back on the nv driver? And then, how do I reinstall the driver from Nvidia?  Thanks.

---

### Post by sharma337 on 2009-05-09
> **zeug said:**
> I have uninstalled the drivers nvidia-glx* with Synaptic and rebooted.  An error message come up saying that the Nvidia drivers could not be loaded and it gave an option of reconfiguring - so I did with the generic configuration.  

At this point you were using the nv driver if X was running. Check the xorg.conf file to be sure...

> **zeug said:**
> I started X again and downloaded the driver from Nvidia. When I tried to install it, it said that X could not be running.  So I ran it in with Ubuntu in console mode and it worked but it could not find nor download (it tried to but it said could not resolve the website address) the kernel module.  What now? How do I make sure it falls back on the nv driver? And then, how do I reinstall the driver from Nvidia?  Thanks.

I'm not sure what you mean here, so instead of trying to answer this I'll point you to [this HowTo]("https://help.ubuntu.com/community/NvidiaManual") which details all the steps for a manual driver install (sorry, I should have found this link earlier -- I'll also add the link to the previous post). Let me know if it works!

---

### Post by zeug on 2009-05-22
Thanks, sharma337 !

I reinstalled with 9.04 and then installed the driver from NVIDIA using the wiki link you sent.

---

