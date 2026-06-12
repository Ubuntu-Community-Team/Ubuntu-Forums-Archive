---
title: "Realtek 8172"
date: 2011-01-12
forum: Hardware
---

### Post by EdakX on 2011-01-12
Hey everyone,

Now, I've searched and searched and can't find the solution to my problem. I've tried countless tutorials and read dozens of postings, but my wireless card just won't work. It's always disabled even if I try to enable it.

Toshiba Satellite laptop
Ubuntu 32bit 10.4 Lucid
AMD Athlon II dual core
Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

What more is needed to help me find my solution? Thank you!

---

### Post by EdakX on 2011-01-13
I've continued my search. I've my drivers (look below) and tried to enable my wireless (sudo iwconfig wlan0 down/up AND right clicking in the task bar on top and selecting enable wirelss) neither work. 

My wireless indicator light is off, dunno if it has to be connected before that works or not. My keyboard shortcut FN+F8 doesn't do anything

My conclusion: My wireless card is in the 'off' or 'power saving' mode.

I plan on booting off a windows live USB so I can enable it that way and see if it will work in Ubuntu, but if there's an easier way to turn my card's power on, please let me know as I have searched to web for a method and to no avail. Thank you all!

sudo lshw -C network:

........
vgastate                8961  1 vga16fb
uvcvideo               57150  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
**r8192se_pci**    467967  0 
psmouse                63245  0 
serio_raw               3978  0 
i2c_piix4               8527  0
.......


sudo lshw -C network:

*-network DISABLED      
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 88:25:2c:0d:86:4c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=**rtl819xSE** driverversion=0019.1207.2010 firmware=63 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:18 ioport:d000(size=256) memory:ff600000-ff603fff

Scanning gets me nothing.

---

### Post by Hippytaff on 2011-01-13
Have you tried
```

rfkill unblock all

```
and
```

sudo ifconfig eth0 up

```
where eth0 is the name of your wirless connection. You can find the name out with iwconfig.

---

### Post by EdakX on 2011-01-14
Yeah I tried sudo iwconfig wlan0 down then sudo iwconfig wlan0 up, but I just gave rfkill unblock all a try and still nothing. When I do down first, then up it will allow me to keep the check-mark on 'Enable Wireless' in the drop down but even though the check-mark is there nothing changes. Still won't scan.

WiFi radar doesn't recognize any wireless cards

Oh and also, rfkill list all returns nothin..

---

### Post by hsoulen on 2011-01-14
> **EdakX said:**
> Hey everyone,

Now, I've searched and searched and can't find the solution to my problem. I've tried countless tutorials and read dozens of postings, but my wireless card just won't work. It's always disabled even if I try to enable it.

Toshiba Satellite laptop
Ubuntu 32bit 10.4 Lucid
AMD Athlon II dual core
Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

What more is needed to help me find my solution? Thank you!

Looks like you are showing an 8192se, if this is indeed the card have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1401219]("http://ubuntuforums.org/showthread.php?t=1401219")

Cheers,

Hank

---

### Post by EdakX on 2011-01-14
Thanks for the help guys!

If you notice in my second post I believe the wireless divers it's picking up (rtl819xSE) is the 8192se you're referring to hsoulen. But please correct me if I'm wrong.

Again like I said my wireless indicator light is off, so will that light not work until I've actually connected to a network or does that have anything to do with my card's current power situation?

EDIT: Oh and also I've already made and installed the drivers for my wireless card (rtl8192se_linux_2.6.0019.1207.2010) as the post you linked suggested

---

### Post by Hippytaff on 2011-01-15
You might need to blacklist some drivers - [http://ubuntuforums.org/archive/index.php/t-468793.html](http://ubuntuforums.org/archive/index.php/t-468793.html)

---

### Post by Hippytaff on 2011-01-15
You might need to blacklist some drivers - [http://ubuntuforums.org/archive/index.php/t-468793.html](http://ubuntuforums.org/archive/index.php/t-468793.html)

---

### Post by EdakX on 2011-01-16
Just wanted to finish this post with my solution.  Turns out the Wireless card was not receiving power. I still haven't fixed my keyboard short cut to turn it on but I instead used the Toshiba 'Flash Cards' application, it has a setting for the mouse to show them across the top and from there I just clicked wireless then turned it from off to on. Now anyone that may run into this problem should be able to fix it.

support.toshiba.com < Download < input your computer model you'll find the software.

---

### Post by hsoulen on 2011-01-17
> **EdakX said:**
> Just wanted to finish this post with my solution.  Turns out the Wireless card was not receiving power. I still haven't fixed my keyboard short cut to turn it on but I instead used the Toshiba 'Flash Cards' application, it has a setting for the mouse to show them across the top and from there I just clicked wireless then turned it from off to on. Now anyone that may run into this problem should be able to fix it.

support.toshiba.com < Download < input your computer model you'll find the software.

Thanks for following up with your solution, glad you got it worked out.

Enjoy the "nix"!

Hank

---

