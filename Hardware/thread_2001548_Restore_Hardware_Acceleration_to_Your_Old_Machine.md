---
title: "Restore Hardware Acceleration to Your Old Machine"
date: 2012-06-11
forum: Hardware
---

### Post by Laysan_A on 2012-06-11
I've been trying, off and on, for more years than I care to admit, to get my old i8000 working with Linux as well (or nearly) as it does with windows. I've been using Ubuntu exclusively on my desktop for the last few years and have to say I really miss it when I'm forced to boot into windows to use my old laptop. Well, after my last attempt, giving Puppy (Macpup) a try, I decided to check out Lubuntu - so far so good - I like it! Imagine my disappointment when I discovered that Lubuntu couldn't use my graphic card's capabilities (such as they are). Sometime in August of 2011 the Mesa devs (mesa provides the Open GL drivers for our graphics chips - hardware acceleration for graphics) decided to remove the drivers for some older hardware, which included support for my i8000's ATI Mobility M4 - the r128_dri.so driver.

Without the hardware driver, the system uses software rendering, which is very slow. With software rendering I get an output of somewhare around 70 frames per second in GLX Gears, and the output is a bit choppy. With direct rendering I get over 700 fps.

Here's a bit from my /var/lib/xorg.log file showing the direct renderer failing and the software renderer being loaded:
> [    41.785] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    41.787] (EE) AIGLX error: dlopen of /usr/lib/i386-linux-gnu/dri/r128_dri.so failed (/usr/lib/i386-linux-gnu/dri/r128_dri.so: cannot open shared object file: No such file or directory)
[    41.787] (EE) AIGLX: reverting to software rendering
[    41.873] (II) AIGLX: Loaded and initialized swrast
[    41.873] (II) GLX: Initialized DRISWRAST GL provider for screen 0Now, I'm not a coder, and I'm not even very familiar or comfortable with the command line, and the package management system seems not unlike a tangled ball of yarn, so I was really feeling overwhelmed at the prospect of trying to downgrade one part of the xorg system to get my direct renderer back. I didn't even know which part I needed, or if I would have to revert my entire xorg installation to an earlier state (assuming I could find the packages),  or whether my Lubuntu installation would even accept a different version with potentially different dependencies.

[This thread]("https://bbs.archlinux.org/viewtopic.php?id=137666") helped some in describing the issue and at least one strategy that worked, though because it's an Arch Linux discussion the package names are different and the package management is different. Most helpful was [this link]("http://lists.freedesktop.org/archives/mesa-dev/2012-March/019628.html") in the fourth post from the Mesa devs mail list. It mentions the correct package name and provides reassurrance that a driver roll-back won't break your system.

Still wrestling with package management issues associated with downgrading a single part of a larger package (package management=ball of yarn), I lucked upon [ this package]("http://www.ubuntuupdates.org/package/xorg-edgers/oneiric/main/base/libgl1-mesa-dri-legacy") from the xorg-edgers PPA (HURRAY!!!). It does everything AUTOMATICALLY! It separates out the required package and puts it where it needs to go, and disables the shared drivers (software rendering). I really want to thank the folks over there at xorg-edgers - and especially Tormod Volden for building this package for Ubuntu.

Here's the description:
> **Name:**     libgl1-mesa-dri-legacy                      
**Description:**              free implementation of the OpenGL API -- legacy DRI1 modules 
This version of Mesa provides GLX and DRI capabilities: it is capable of 
both direct and indirect rendering.  For direct rendering, it can use DRI 
modules from the libgl1-mesa-dri package to accelerate drawing.
  This package does not include the OpenGL library itself, only the DRI 
modules for accelerating direct rendering.
  For a complete description of Mesa, please look at the 
libgl1-mesa-swx11 package.
  The tdfx DRI module needs libglide3 to enable direct rendering.
  NOTE: This package provides old DRI1 drivers to be used with mesa 8.x
 I know it was built for Oneiric, but it installed and appears to be running fine on my 12.04 installation. It includes the following drivers: savage mga r128 tdfx sis unichrome.

To install it, download the deb file for your system type and install with GDebi. Easy as pie. Restart X - or reboot, then check your /var/lib/xorg.log file to see if it's working.

Here's the relevent bit from mine after installation:
>     37.514] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    37.514] (II) AIGLX: Loaded and initialized r128
[    37.514] (II) GLX: Initialized DRI GL provider for screen 0I know there are other folks out there who are either too broke or too cheap (or maybe you just don't like planned obsolescence) to spring for new equipment, and, like me, you want to continue using your computers for as long as they're useful. I found precious little information in my search for a solution. Hopefully this post will let people know they don't have to stay stuck in the mud because of the mesa devs decision, and help them keep their old machines working at their full potential for a bit longer.

---

### Post by flamboyant on 2012-10-05
i'm glad to know you've managed to solve the problem. i tried to do the same, but nothing's changed. here's my short story: [http://ubuntuforums.org/showthread.php?p=12272014#post12272014](http://ubuntuforums.org/showthread.php?p=12272014#post12272014)

can you help me, please?

---

### Post by Laysan_A on 2012-12-11
Hi flamboyant! Sorry I'm so late getting this - I check my email like NEVER!

I'm not sure how much help I can be - I'm really not very knowledgeable about this stuff. You've said you tried what I did and it didn't help? What's your xorg.log have to say in the relevant sections?

---

### Post by flamboyant on 2012-12-15
> **Laysan_A said:**
> Hi flamboyant! Sorry I'm so late getting this - I check my email like NEVER!

I'm not sure how much help I can be - I'm really not very knowledgeable about this stuff. You've said you tried what I did and it didn't help? What's your xorg.log have to say in the relevant sections?

hello Laysan! thank you for the reply. it's always better late than never ;-)

after that post i got in touch with the developers of the driver and it turned out that 4 MiB of video memory is not sufficient to get a hardware 3D acceleration enabled for a desired 1024x768 resolution.

---

### Post by Laysan_A on 2012-12-15
Oh! Well, that's too bad. Yeah, my card has 32. 

You know, if you don't mind throwing a little money at your old fujitsu, you might consider looking around on ebay for a compatible graphics card. Considering its age I imagine you could get one for next to nothing. I bought a few parts for my I8000 on ebay. It seems these after-market parts guys never throw anything away.

Anyway, good luck!

---

### Post by flamboyant on 2012-12-22
> **Laysan_A said:**
> You know, if you don't mind throwing a little money at your old fujitsu, you might consider looking around on ebay for a compatible graphics card. Considering its age I imagine you could get one for next to nothing. I bought a few parts for my I8000 on ebay. It seems these after-market parts guys never throw anything away.

Anyway, good luck!

thank you for the suggestion, but i have never used ebay and, frankly, don't want to. i'm not even sure if it's available here in Russia. since no one plays any games on the book, i think we can get along without the 3D hardware acceleration pretty well.

---

