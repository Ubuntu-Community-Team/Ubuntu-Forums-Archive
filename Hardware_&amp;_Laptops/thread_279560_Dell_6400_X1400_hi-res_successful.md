---
title: "Dell 6400 X1400 hi-res successful"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by cnbiz850 on 2006-10-18
Just got the new laptop with Core 2 Due T5600 1.83GHz 2MB L2 Cache, 667MHz FSB, 15.4" UltraSharp Wide Screen, X1400 (128MB + 128MB), 1GB (512MB + 512MB) 667MHz dual-channel, 120GB 5400RPM HD, and Intel 3945 wireless.

Installed Edgy dual-booting with XP.  Basic install went fairly smooth, though the LiveCD install didn't go through and I had to use the Alternate CD to do text-based install.  Not much problem.

One of the real headache is to get my full screen resolution (I could only have 1280X1024 after Ubuntu installation).  I spent about two days following the HOWTO's on building and installing an custom ATI driver.  I got no where -- for some reason it complains fglrx-kernel-source not built completely, and so a reboot resulted in blank screen.  I almost gave up until this afternoon when I tried Method I of this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29)

I now got my 1680X1050 screen.  Looks great!

It seems still there are some GL-related issues.  I don't know why fglrxinfo gets me the following.  Any idea please?

```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

Another big thing to configure seems the wireless capability.  I used iwconfig to get it perhaps half-way through.  The device can be seen in network manager, but I can't still ping the router yet.  Don't know why.  iwconfig out is as follows.  Anyone has any idea?

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"tp-link"  
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 02:18:DE:0D:8D:4B   
          Bit Rate:54 Mb/s   Tx-Power:13 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:99  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0

sit0      no wireless extensions.


```

---

### Post by cnbiz850 on 2006-10-19
It seems (I guess) the wireless card causes a "soft lockup detected on CPU#0" hangup.  When that happened, the system wouldn't start and I had no way of getting a console.  I don't know a way to go around but to re-install the system.  The problem is further discussed here:

[http://www.ubuntuforums.org/showpost.php?p=1634510&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1634510&postcount=8)

---

### Post by cnbiz850 on 2006-10-19
It looks that the Linux-Restricted-Modules is the problem causing the hangup.   I had to go through the procedure of building ATI driver.  Followed the following guide and it seems to work.  

[http://www.ubuntuforums.org/showthread.php?t=257684&highlight=6400](http://www.ubuntuforums.org/showthread.php?t=257684&highlight=6400)

My screen resolution is correct, but fglrxinfo still gives me the following report.  I don't understand.

```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

---

