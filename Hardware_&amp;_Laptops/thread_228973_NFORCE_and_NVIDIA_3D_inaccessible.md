---
title: "NFORCE and NVIDIA 3D inaccessible"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by kargath64 on 2006-08-03
Hi, I really need some help in order to get Dapper functioning at a basic level.


My computer specs:
ASUS A8N-VM-CSM mobo (NFORCE based, with inbuilt ethernet and sound)
AMD64 3800+ dual core CPU
160GB HDD
NVIDIA 6600GT graphics card
I also dual-boot with WinXP Home.

What I need to do is get the 3D acceleration up and running, whilst I also need the nFORCE ethernet working so that I can use apt-get/Synaptic so that my system can be used for stuff other than just basic gcc.

All the NVIDIA drivers wouldn't install in the last version of Ubuntu (5.10), because the kernel was compiled with a different GCC to the gcc that came with the system.  So, I just managed to move most of my work over to windows, and worked as much as I could in it.  Now, I recently got the AMD64 Dapper Desktop install CD and wiped my computer, did a fresh install of Windows and Dapper, and now I'm presented with a similar problem.  The ethernet STILL isn't recognised (at least the sound works this time), and the 3D graphics are no-go.  I tried downloading the x64 install .run driver thingies off the NVIDIA site (in Windows), and installing those first killed the X server the first time around, and post another fresh Dapper install, just installing the NFORCE one killed the X server in an even bloodier way.  (I do not have the technical skill to fix a broken X server, so broken server=wipe again for me.)

So my problem is - how do I install the drivers to get nFORCE working and the NVIDIA card working, when I can't use apt-get?

(As an aside, it looks like this guy ](*,) is kissing the wall rather than banging against it.)

---

### Post by zxee on 2006-08-04
> **kargath64 said:**
> Hi, I really need some help in order to get Dapper functioning at a basic level.


My computer specs:
ASUS A8N-VM-CSM mobo (NFORCE based, with inbuilt ethernet and sound)
AMD64 3800+ dual core CPU
160GB HDD
NVIDIA 6600GT graphics card
I also dual-boot with WinXP Home.

  (I do not have the technical skill to fix a broken X server, so broken server=wipe again for me.)

So my problem is - how do I install the drivers to get nFORCE working and the NVIDIA card working, when I can't use apt-get?

(As an aside, it looks like this guy ](*,) is kissing the wall rather than banging against it.)

Maybe the best thing to do? is to first get your network up so you can use apt-get.

There's a how to on nvidia here: [http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)
There is also a specific network section here: [http://www.ubuntuforums.org/forumdisplay.php?f=136](http://www.ubuntuforums.org/forumdisplay.php?f=136) 
I'm pretty sure your ethernet setup is addressed there.
Hope that helps.

---

