---
title: "ATi Rage 128 Pro AIW Tv-IN with Gatos?"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by recover82 on 2005-07-01
I've been trying to get the ati.2 driver from gatos to install for a while now and I'm having some issues.  The ati.2 driver allows you to take advantage of video and TV playback features of particular ATi cards (including my Rage 128 Pro AIW)  

Gatos provides a package for users of x.org (like us here at ubuntu/kubuntu) on their sourceforge page but they instructions included are less than informative.  

On the gatos installer page it states the following:
```

Installing ati.2 binaries

    * Download tarfile from our download area
    * Backup your /usr/X11R6/ directory (or wherever you installed XFree 4.3.0)
    * Make sure that /usr/X11R6 points to the directory where you installed XFree 4.3.0. It could be a symlink, it could be a hardlink.
```

I don't understand how to point /usr/X11R6 to anything if I'm using x.org...

I tried following the README file in the x.org driver package they provide but when I checked my x.log file the drivers are obviously not installing correctly.  The output looks like this

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 root@terranova.war
thogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux kubuntu-box 2.6.10-5-386 #1 Tue Apr 5 12:12:40 U
TC 2005 i686
Build Date: 05 April 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Deb
ian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul  1 18:05:36 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No sym
bols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No sym
bols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No sy
mbols found
(EE) R128(0): No DFP detected
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!
```

Any ideas how to get the driver installed.

---

### Post by recover82 on 2005-07-03
No ideas??

come on guys. i feel like rodney dangerfield when i visit this place.
no respect.

---

### Post by trinaryouroboros on 2005-09-21
[QUOTE=recover82]No ideas??

come on guys. i feel like rodney dangerfield when i visit this place.
no respect.[/QUOTE]

Man...no respect for the olesk00l...damn.

I got a ATI All-in-Wonder Pro 128 myself, and I haven't the foggiest on how to enable direct rendering without crashing the whole system.

Sure it's an AMD64...but n00bs are broke these days...perm.

Anyone out there? Anyone at all? Come help us out now, c'man.

---

### Post by bruno on 2005-09-23
I try too understand how to have tv with AIW128
and the only way I find is to install an very old package (not maintain) from synaptic. and tv works.

package name:  gatos
good luck

---

### Post by pumuckly on 2008-05-09
I have an ATI All-In-Wonder 128 AGP video card with 32MB RAM. Yesterday I installed Ubuntu 8.04 (Hardy). I got GATOS from ubuntu package but I couldn't watch TV with this card. I watched TV with this card earlier with XFree86 4.2/4.3 and Linux kernel 2.4.
Unfortunately I found descriptions only on Gatos main site, where I read that gatos ati.2 module built in xorg from version 7.0. That files helps me earlier in XFree86. I couldn't find descriptions for ATI AIW 128 TV settings on Xorg.

I try to run gatos-conf but nothing happened on computer. Somewhere found to load theatre module in xorg.conf, but I got error message (not found).

I try to download gatos v4l project, compiled it, and contact with gatos v4l developer who said the code works only PCI card (I have AGP :( ).

If somebody can please help me to enable my TV tuner.

Here are some program output.

The **xatitv** result:
```
:~$ xatitv
GATOS: gatos_initb()
GATOS:  bt829_init(): No such device
GATOS: bt829_init failed: No such device
GATOS: gatos_initb(): No such device
xatitv: gatos_init(): No such device
```

**lspci** result:
```
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP
```

**lspci -n** result:
```
01:00.0 0300: 1002:5246
```

**xawtv** output:
```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-16-generic)
xinerama 0: 1024x768+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
```


**dmesg** results for VGA card:
```
[   43.919155] system 00:00: iomem range 0xcd800-0xcffff has been reserved
[   43.919164] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   43.919171] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   43.919178] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   43.919186] system 00:00: iomem range 0x1fff0000-0x1fffffff could not be reserved
[   43.919194] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   43.919201] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   43.919208] system 00:00: iomem range 0x100000-0x1ffeffff could not be reserved
[   43.919215] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[   43.919237] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   43.919244] system 00:02: ioport range 0x294-0x297 has been reserved
[   43.950403] PCI: Bridge: 0000:00:01.0
[   43.950410]   IO window: d000-dfff
[   43.950420]   MEM window: d8000000-d9ffffff
[   43.950427]   PREFETCH window: d4000000-d7ffffff
[   45.721187] Boot video device is 0000:01:00.0
[   64.631129] Linux agpgart interface v0.102
[   64.742170] agpgart: Detected an Intel 440BX Chipset.
[   64.758624] agpgart: AGP aperture is 64M @ 0xd0000000
[   76.405943] Linux video capture interface: v2.00
[   88.140939] [drm] Initialized drm 1.1.0 20060810
[   88.163028] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   88.163047] PCI: setting IRQ 10 as level-triggered
[   88.163055] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   88.167296] [drm] Initialized r128 2.5.0 20030725 on minor 0
[   88.169675] mtrr: base(0xd4000000) is not aligned on a size(0x1f00000) boundary
[   88.170238] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[   88.170268] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   88.170296] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[ 4950.216065] mtrr: base(0xd4000000) is not aligned on a size(0x1f00000) boundary
[ 4950.218344] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[ 4950.219717] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[ 4950.220775] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode

```


**scantv**:
```
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no grabber device available
```

**scanpci.gatos**:
```
Probing for devices on PCI bus 1:

pci bus 0x1 cardnum 0x00 function 0x0000: vendor 0x1002 device 0x5246
 ATI  Device unknown
```


**part of /var/log/Xorg.0.log**:
```
X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux xxxxxxxxxx.hu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(==) No device specified for screen "Default Screen".
        Using the first device section listed.
(**) |   |-->Device "ATI Technologies Inc Rage 128 RF/SG AGP"
(--) PCI:*(1:0:0) ATI Technologies Inc Rage 128 RF/SG AGP rev 0, Mem @ 0xd4000000/26, 0xd9000000/14, I/O @ 0xd000/8

```

---

### Post by pumuckly on 2008-05-12
So I looking for lot's forum. I found km and avview (gatos) programs which enable TV on my ATI card. I make some small modification on sources (I found lots help on forums), and actually I can compile both module (km and avview). Unfortunately not working my TV. I found a very similar description from my problems on [http://www.linuxquestions.org/questions/linux-software-2/unable-to-set-up-video-capture-composite-in-with-ati-rage-fury-pro-card-403758/](http://www.linuxquestions.org/questions/linux-software-2/unable-to-set-up-video-capture-composite-in-with-ati-rage-fury-pro-card-403758/)

That was the following (i modified outputs for my results):

I can't get video capture to work under linux with my ATI AIW 128 - 32MB card.
I performed the necessary driver/software installations but nothing seems to work. I installed the KM drivers and make sure the 3 modules are loaded at boot (videodev, km_drv, km_api_drv). From there I try running one of the video capture apps provided on the gatos project page. I tried both XawTV and AVView. XawTv quits with a "no data available" when it tries to read from the /dev/video0 device.
Avview quits on startup with a "Bad request" message and error 141.

Here is the output of start_avview:

```
libzvbi available export modules:
        HTML:keyword "html" mimetype "text/html" extension "html,htm"
        PNG:keyword "png" mimetype "image/png" extension "png"
        PPM:keyword "ppm" mimetype "image/x-portable-pixmap" extension "ppm"
        Text:keyword "text" mimetype "text/plain" extension "txt"
        VTX:keyword "vtx" mimetype "application/videotext" extension "vtx"
        XPM:keyword "xpm" mimetype "image/xpm" extension "xpm"
NUM_ADAPTORS=1
Adaptor 0: ATI Rage128 Video Overlay
                type input image
                ports 73
73 ATI Rage128 Video Overlay
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  14 ()
  Serial number of failed request:  1557
  Current serial number in output stream:  1557
```

And this is the output of XawTV:

```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-16-generic)
xinerama 0: 1024x768+0+0
can't open /dev/video0: No data available
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No data available
v4l2: open /dev/video0: No data available
v4l: open /dev/video0: No data available
no video grabber device available
```

```
v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
mode: 1024x768, depth=24, bpp=32, bpl=5120, base=0xd0000000
can't open /dev/video0: No data available
```

dmesg result:
```
[200700.425528] Kmultimedia API module version alpha-6.0 loaded
[200700.646297] Kmultimedia module version alpha-6.0 loaded
[200700.646315] Page size is 4096 sizeof(bm_list_descriptor)=16 sizeof(KM_STRUCT)=748
[200700.646455] km: probing 0000:01:00.0
[200700.646467] km: using irq 10
[200700.646472] Register aperture is 0xd5000000 0x00004000
[200700.646498] kms variables: reg_aperture=0xe0be0000
[200700.646600] sizeof(kmfl_template)=780 sizeof(KM_FIELD)=52
[200700.646645] Device 0000:01:00.0 (0x1002:0x5246) corresponds to /dev/video0
[200700.646658] kms variables: reg_aperture=e0be0000
[200700.741578] Processing "VIDEO_STREAM_ACTIVE"="1" int_value=1
[200700.741605] Purging transfer queue
[200700.741613] km: no data is available until AVview or xawtv is started (start video capture)
```

I've searched the web for a while now and I can't figure it out. In the rare instances that I found someone who posted a message on some forum with the same problems, the problem was never really resolved.

By the way, if I also get cat "/dev/video0: No data available" message when i issue a "cat /dev/video0" command. If everything was working properly, am I supposed to get some sort of data on the terminal when I issue that command?

Thanks in advance!

---

