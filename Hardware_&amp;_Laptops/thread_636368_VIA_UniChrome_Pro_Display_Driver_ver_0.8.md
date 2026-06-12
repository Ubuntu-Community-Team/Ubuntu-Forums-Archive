---
title: "VIA UniChrome Pro Display Driver ver 0.8"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by tech0007 on 2007-12-09
VIA recently released their binary driver for their integrated graphics for linux.  To install it:

1.  I downloaded the driver from [http://www.viaarena.com/default.aspx?PageID=2&Type=3](http://www.viaarena.com/default.aspx?PageID=2&Type=3).  
2.  Choose your distro.  
3.  Then pick Integrated Graphics.  
4.  Pick the appropriate driver category.  If you are not sure which one, check this site [http://www.viaarena.com/default.aspx?PageID=5&ArticleID=68&P=5](http://www.viaarena.com/default.aspx?PageID=5&ArticleID=68&P=5).
5.  Click on "Click here to begin free download."  Save it.
6.  Unzip the file.
7.  Make a backup of your xorg.conf.
8.  CD to the directory where you unzipped the file to.
9.  Execute the *.run file.  example "sudo sh VIA_U710_UniChrome-GFX-v40072d.run"
10.  Ctrl-Alt-Bckspce

That's it.  You should be able to run wine and other 3D applications.

UPDATED:  Openchrome driver in hardy repo works, and that's what I'm using right now.

---

### Post by Matataki on 2007-12-10
The driver seems like it wants to work, but I get an odd error when I go to glxinfo or run any 3D app.

libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering

I have glx, dri, GLcore, and v4l enabled in my modules, so I'm not too sure what's up.

When I run s3utility, it claims my via_dri.so is "Old than 1.2.x0.62", so I'm thinking this may be the cause of my woes. Anybody know how I could possibly update my dri file easily?

---

### Post by tech0007 on 2007-12-11
> **Matataki said:**
> The driver seems like it wants to work, but I get an odd error when I go to glxinfo or run any 3D app.

libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering

I have glx, dri, GLcore, and v4l enabled in my modules, so I'm not too sure what's up.

When I run s3utility, it claims my via_dri.so is "Old than 1.2.x0.62", so I'm thinking this may be the cause of my woes. Anybody know how I could possibly update my dri file easily?

Hi,

If you get:

libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering

then you are trying to run as a user that doesn't have permission to use the DRI (root is the default allowed user). To let all users access the DRI, add the following section to your xorg.conf:

Section "DRI"
    Mode 0666
EndSection

The binary driver works with the default kernel and libraries of gutsy/feisty.  If you compiled your kernel or libraries, you may want to revert back to the default by installing them from the repos.

---

### Post by Matataki on 2007-12-11
Ahh, I thought that was my problem as well when I was trying to diagnose it last night, but the DRI section in xorg.conf actually didn't help. I think it may have been because I have a K8M800, which isn't listed in the supported chipsets. A recompilation of the via_dri.so and my DRM files helped me though, I have partially working 3D now.

The only problem I have now is a lengthly list of :
libGL warning: 3D driver claims to not support visual 0x22
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29

... whenever I run a 3D app now. Glxgears and ZSNES work fine with OpenGL, but most 3D applications freeze up my system. I read on the openchrome website that many of the issues with unichrome and 3D are due to a lack of support in MESA, which I could believe as I used to have fully working 3D several Ubuntu releases back. I'm going to attempt to install an older version of MESA and see what happens.

---

### Post by tech0007 on 2007-12-12
Hi,

According to VIA's list, K8M800 is supported and is using S3 Graphics UniChrome™ Pro IGP Series (the same as mine, I have P4M800 Pro).  I can't use Picasa (google), Wine 0.9.50, any of the GL screensavers, nor F-Spot, but that was before I installed ver. 0.8.

I also get a lot of these messages:
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29

but it doesn't freeze my system anymore.  I'm trying to search for a solution to this one.

---

### Post by Matataki on 2007-12-12
After a bunch of reading around, it appears that the reason we have such difficulties with 3D is a result of the Unichrome branch not being maintained in Mesa. Apparently Via is pretty unsupportive, so it is difficult for development to take place for these cards.

My idea of rolling back the Mesa to an earlier version that Openchrome devs claimed was supported gave me less error messages, but I still experienced frequent freezes.

Sadly, it appears that there is little we can do in order to fix this problem.

---

### Post by xanmoo on 2007-12-12
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/xserver-xorg-driver-via/+bug/43154/+index](https://launchpad.net/ubuntu/+source/xserver-xorg-driver-via/+bug/43154/+index) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I tried to install the *via_ubuntu710_unichrome-v40072d-kernel-bin-_v0.80* driver . When  the xserver is restarted, only the vesa driver is set with a 800x600 resolution.

my computer is an acer 1362LMI 
lspci gives:
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
00:0b.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
00:0b.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
00:0b.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01
```
and uname -a:
```
Linux xanmoo 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux 
```

---

### Post by muusikko on 2007-12-12
For K8M800 there's also new driver, released in November 2007. But it's not a binary package, only source code is available.

[http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=109](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=109)

---

### Post by Matataki on 2007-12-12
Hmm. I'll give compiling the source a try since the K8M800 is explicity listed there. I've got a feeling it'll do little for the 3D problems, but I guess it won't hurt. I'll update in a bit.

EDIT: The script really dislikes Ubuntu. I think I'll give up for a bit, as I doubt recompiling would fix the idea that Mesa is to blame for all of our 3D woes.

---

### Post by mahousaru on 2007-12-15
I've got a PN800 and glxgears works fine, but it gives errors about AIGLX not being able to display a mode.  GoogleEarth says my graphics card doesn't have enough memory even if I hard set the memory in device options.  s3utility says it has 64MB available.  The worst thing is xv video causes my lappie to freeze :(.  

Only benefit apart from glxgears working is that wine doesn't free with it.

I reverted back to the ubuntu drivers, but now dri won't load at all.  I tried removing the ubuntu via drivers totally and reinstalling but no joy.  I also reinstalled every thing associated with mesa too.

Now in the log dri is no longer loaded and drm says it failed to load the kernel module via.

*Edit*
I read the PDF properly that came with it and at the very bottom is says that SAMM causes video to freeze, so I disabled the CRT device using 23utility and I can play back video with no freeze.  Totem gives a green garbled screen that is far too large, but MPlayer and VLC work fine.  Compiz also kinda of works, but I get a black box which can be reduced by making shadows = 1 (shame can't set it to 0).  

Google Earth still refuses to believe that is has more the 16MB available

---

### Post by Ordhaj on 2007-12-18
I followed the instructions and downloaded and ran the package. When I restarted, it reverted to VESA. While that still works better than the driver that comes with Ubuntu (i.e., I can run Wine), I can't run any 3D applications, including Google earth.

I received no error messages that would be of any use whatsoever.

And I can no longer read DVDs, which has nothing to do with the video driver, but with this version of Ubuntu. I'm considering downgrading to Ubuntu 7.04, where I could:

a) use Wine,
b) use DVDs,
c) use Picasa and Gthumb (neither of which work well in this version).

cheesed,

Mark

---

### Post by gary4gar on 2007-12-18
i also tried this driver, and as soon as run glxgears, my system hangs & a slower 80FPS are observed.

whereas with openchrome driver i get around 500FPS:(


is there anything that one needs to do apart from sudo sh *.run??

---

### Post by gary4gar on 2007-12-18
users of Unichrome chipset, use VEMP
                VIA enhanced MPlayer(VeMP), which uses hardware-specific acceleration in decoding for better MPEG2/4 performance.
[http://sourceforge.net/projects/vemp](http://sourceforge.net/projects/vemp)
its better than mplayer in repo of gusty

---

### Post by effenberg0x0 on 2008-01-23
After a lot of time trying to use my Laptop (with a VIA VN800 Graphics Chipset) and trying the official driver as well as the good efforts from Openchrome and Unichrome projects, I gave up and tried to get help at VIA Technologies Official Forum (see [http://www.tkarena.com/forums/linux-...hat-going.html](http://www.tkarena.com/forums/linux-...hat-going.html)).

The idea of a petition came out from that thread. I have started this petition at [http://www.petitiononline.com/vialinux/](http://www.petitiononline.com/vialinux/) .

If you plan on using your VIA based hardware on Linux, with a decent performance, stability and security and if you think Linux users should have the same support as Windows users receive from the company, I ask you to sign this petition as well as help me spread this URL to your friends, family and coworkers.

Regards,
Effenberg

---

### Post by Djainette on 2008-03-06
Vote !
[http://brainstorm.ubuntu.com/idea/1313/](http://brainstorm.ubuntu.com/idea/1313/)

---

