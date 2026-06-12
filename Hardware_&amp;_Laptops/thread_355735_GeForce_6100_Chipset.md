---
title: "GeForce 6100 Chipset"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by jesse_ccwis on 2007-02-07
Hey Everyone,
I am a reseller and sell many basic computers here at the office. We are wanting to sell a basic computer system with the Ubuntu LTS option so the customer can save some money rather then going with XP Home. The problem is finding a motherboard that is fully supported with the Ubuntu LTS support option. 

Here is a good budget board I was thinking of using: ECS GeForce6100SM-M (1.0) [http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?DetailID=685&DetailName=Feature&MenuID=46&LanID=9]("http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?DetailID=685&DetailName=Feature&MenuID=46&LanID=9")

It uses the GeForce 6100 video controller and the nForce 405 Chipset. We were going to bundle this board with a Sempron processor and then 512 MB of RAM. 

So, does anyone see a problem with this setup and Ubuntu? Also, is there any performance differences if going with a 64 bit optimized kernel for the sempron cpu? Is there then going to be application compatibility issues then as well if running in 64 bit?

Any help would be great!
Jesse

---

### Post by logos34 on 2007-02-07
I'm running pretty much the same hardware specs (nvidia Geforce 6100/410, Sempron 64-bit, 512mb).  Everything works out of the box.  No issues aside from the fact that the newer 97xx nvidia forceware driver kept failing after reboot...Had to go with the 8776 nvidia-glx in the repo and it works just fine.  Even with this modest amount of ram (was running a gig until my other dimm slots broke), gnome is very responsive and kubuntu desktop even quicker.  Xubuntu just flies.  I'm using 32-bit edgy.  Although I'm only familiar with x64 Suse 10.1, I would advise against 64-bit--it offers no real performance gain for the average user (I can't tell the diff) and lacks support for windows streaming media (w32codecs), flashplayer and java in firefox, etc.   (Although in windows there does seem to be a diff bewteen x86 and x64--I dual-boot Winxp Pro x64 with Ubuntu, and it seems to be a tad bit faster than Winxp home on my my other pc, which is Pentium 4, dual-channel, sata, etc). 

My adsl connection works flawlessly--probably due to the fact I use a wired router, which makes all the difference.  Support for wireless is still one of Ubuntu's weak spots, and config can be a nightmare.  Just read through the networking posts...

And this [little fix]("http://ubuntuforums.org/showthread.php?t=208396&highlight=calande") worked wonders for my font rendering. 

Good luck selling oodles of linux boxes!

---

### Post by jesse_ccwis on 2007-02-07
Thanks for the post logos.
That is good to hear that geforce and nforce chipset works fine with Ubuntu. I will probably stick with Ubuntu LTS. I really like that this version will be supported with auto updates for a while. 

I was actually thinking the other way around with KDE and GNOME. I guess I am probably wrong, but I always thought of KDE being the more visual rich desktop and being more of a resorce hog then GNOME. Anyways, thanks for your input! 

I have noticed XP 64 bit to boot up quicker but other then that, more problems then anything else...

---

### Post by logos34 on 2007-02-07
> I have noticed XP 64 bit to boot up quicker but other then that, more problems then anything else...
Yes, it boots in around 30 sec for me (which is a lot quicker than ubuntu), but other than that not really a speed demon...Although I have to admit mine's been pretty stable and relatively glitch-free (for windows that is), and I've found drivers for just about everything.  But I hardly ever use it anymore!  

> I was actually thinking the other way around with KDE and GNOME. I guess I am probably wrong, but I always thought of KDE being the more visual rich desktop and being more of a resorce hog then GNOME

Yeah, KDE applications (like K3B, Amarok which I cannot live without) do have a ton of dependencies and take forever to load, but I've noticed Konquerer filebroweser accesses files and directories almost instantaneously, and in general kde seems peceptably faster than gnome even though it probably does use more system resources than gnome (probably because there is nothing you CAN'T configure in kde!).  Personally, though, I've never liked it, although I am planning to give it another shot one of these days, maybe with a QT makeover.

---

### Post by jonpackard on 2007-03-23
Hi Jesse. I just purchased the motherboard you were discussing (ECS 6100S chipset). I'm having some problems with it in Ubuntu. The sound and Ethernet devices are not recognized properly. Here is the listing of my PCI devices:

ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 03ea (rev a1)
00:01.0 ISA bridge: nVidia Corporation Unknown device 03e0 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 03eb (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 03f5 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 03f1 (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 03f2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 03f3 (rev a1)
00:05.0 Audio device: nVidia Corporation Unknown device 03f0 (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 03ec (rev a2)
00:07.0 Bridge: nVidia Corporation Unknown device 03ef (rev a2)
00:08.0 IDE interface: nVidia Corporation Unknown device 03f6 (rev a2)
00:09.0 PCI bridge: nVidia Corporation Unknown device 03e8 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation Unknown device 03d1 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

So far I have not found a solution. If you have not purchased this yet, you may want to research this first. I will post again if I make any progress.

---

### Post by ArtificialSynapse on 2007-03-26
Yes, I'm having an issue with my xorg when I install the nvidia drivers. No one seems to want to help... grrrr ( I run 6100 )

---

### Post by rajeev1204 on 2007-03-26
i have 2 machines running the same chipset and they work super. 

There are 2 simple steps to be completed after installing nvidia-glx from repository.

type in terminal " sudo nvidia-glx-config enable"

this enables the driver .

Then do this "sudo gedit /etc/X11/xorg.conf" and look for an entry called nv , change that to nvidia. save and exit

reboot.

 thats it. If for any reason X does not start then do this 

"sudo dpkg-reconfigure xserver-xorg"

it will prompt u for a few things. at the driver prompt select nvidia, and for the rest just press enter


Regards

rajeev

---

