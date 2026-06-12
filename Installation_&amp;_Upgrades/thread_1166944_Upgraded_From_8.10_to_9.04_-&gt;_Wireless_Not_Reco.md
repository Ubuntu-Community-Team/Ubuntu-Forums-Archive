---
title: "Upgraded From 8.10 to 9.04 -&gt; Wireless Not Recognized"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by amj on 2009-05-22
Hi, 

I've just done an upgrade from 8.10 to 9.04, and the only that seems to have gone wrong is my wireless adapter -- Intel PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) -- is no longer detected. 

If I do an "lspci", I can see it listed.   It appears as if the driver for the device is never loaded.  Before I did the upgrade, I tested out the LiveCD, and wireless worked fine. 

The kernel (2.6.28-11-generic) and the Network Mgr Applet (0.7.0.100) are the same following the upgrade, and on the Live CD. 

I've tried a few suggestions I've seen in the forum, such as forcing a reinstall of the Network Mgr App, and an install of WICD, but to no avail. 

I don't know if this is relevant, but when I did the installation, I was on connected via ethernet cable, not wireless.  Could this have somehow blocked visibility of the wireless adapter at setup?

Is there any way to force 9.04 to rescan the HW?

Otherwise, my only other solution will like be to install 9.04 from CD, keep my fingers crossed that my home partition stays intact (I backed it up before the upgrade), and then re-install all my additional programs.   I was looking to avoid that extra work by doing the upgrade path, but I'll reinstall if it's the only way. 

Cheers, 
AJ

---

### Post by amj on 2009-05-22
Some further info.  This is what I see when running from the live CD:

```

$ lspci | grep Wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"**********"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=98/100  Signal level:-26 dBm  Noise level=-61 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Note that I've blanked out my ESSID and MAC, but they are valid figures.

---

### Post by amj on 2009-05-22
And here is what I see with the same commands following the 8.10->9.04 upgrade:

```

$ lspci | grep Wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

```

The adapter is seen, but not enabled. 

Anything else I can post to help with debug?

---

### Post by TAFKARS on 2009-05-22
bump.

---

### Post by amj on 2009-05-22
Well, I tired of fiddling, and went for a full install.  As my /home is on it's own partition, and I had done a back-up just before the upgrade, I went for it.   I manually did the partitioning to reformat /, but leave /home alone, used the same login, and all of my files were fine.  

I'd love to hear any theories about why the wireless didn't work after upgrade, but I'm happy to report it is fine after a full install. 

Cheers, 
AJ

---

### Post by Scott M. Sanders on 2009-06-06
My Ubuntu 8's wireless had once broke on an update. It turned out that the "Linux restricted modules" that contained my Intel wireless driver had not updated in tandem, so as I still had a wired connection, and this was some days later, connecting via that connection and updating those modules finally resolved it. 

Sorry I didn't see your post earlier.

---

### Post by amj on 2009-06-06
Hi Scott, 

Thank you for taking the time to post.   I've solved the problem by doing a full install, but I'll keep that in mind for a future upgrade. 

Cheers, 
AJ

---

