---
title: "Can't get dual monitor on 12.04"
date: 2012-04-29
forum: Hardware
---

### Post by Th3Alchemist on 2012-04-29
I recently installed Ubuntu 12.04 (64bits) in my laptop, and I can't get an external monitor (dual monitors) working.

I installed with success the latest NVIDIA driver but still no success.

On the Displays option when I click on "Detect Displays", nothing happens either.

```

marcsoler@R510:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1)

```

---

### Post by _asc_ on 2012-04-30
Hello,

I have the same issue. I have an ASUS N55S notebook with an nVidia Geforce GT 555M (Optimus Technology) graphics card and an additional Samsung 24-inch monitor and I would like to use both monitors. Unfortunately, when I press the "Detect Displays" button in System Settings->Displays, nothing happens and the Samsung monitor is not detected.

I'm running Ubuntu 12.04 (64 Bit) and lsmod shows me that the Nouveau driver is used. Do I need to install the driver from nVidia to get dual monitor support, or should it also work with the Nouveau driver?

Can anybody help me with this issue?

---

### Post by jjaivars on 2012-05-06
Same proplem here

lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G73 [GeForce Go 7700] (rev a1)

I hate this 12.04, I'm having too much issues with this version

---

### Post by bebopiiam on 2012-05-26
Hi.  I had a similar problem but got my system working.  

I have an ATI display card and the proprietary drivers fail to install but I had the same system working with  11.04 with non-proprietary drivers.

I have an AOC 23" moniter in DVI mode and an old Sony 19" VGA.

Liveboot  correctly found both the AOC and SONY but install identified the AOC as a Laptop.  On Liveboot I was able to configure the monitors correctly but on liveboot the mouse didn't work.  My thought was to use the generated liveboot xorg.conf file,  however and it turns out that for Liveboot there is no xorg.conf file so I don't know what's going on for graphics.

Finally in desperation I copied the working 11.04 xorg.conf file from /etc/X11 into the 12.04 directory, rebooted and reconfigured the displays and everything works although the AOC is still identified as a LAPTOP.

So that said, if you're feeling lucky, you might try the same: copy the /etc/X11/xorg.conf from your previously working system to your new install.  I have no idea what this could do to your monitor if things fail however... :)

Steve S.

---

### Post by etricks on 2012-07-15
Any update?  I am having the exact same issue.  I'll report back if I find anything on it today, but so far I haven't had any luck...

---

