---
title: "ATI Driver woes..."
date: 2009-04-25
forum: Hardware
---

### Post by docdraino on 2009-04-25
Ok, so in intrepid ubuntu recognized my ATI Card right away.

Now that I upgraded to jaunty, it can't find the damn thing anymore.

i know this might not be at all helpful, because i forget what exactly my card is outside of it's probably a Radeon x300 128mb card, that's what i believe.

this is so sad, because jaunty runs TEN TIMES better than intrepid, so this is really the only hiccup in the system.

oh and i checked ATI's website and apparently they have become legacy drivers and were all bundled into one bulky pack. after executing it in terminal i get this:

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

any help would be greatly appreciated.

---

### Post by Renan Decarlo on 2009-04-25
Same here... got ati x300 and it doesn't work anymore on jaunty... no 3D acceleration, wrong max resolution


the driver provided at the ati website do only support the old xorg, before the 1.6...


somebody help us :icon_frown:

---

### Post by PKabooo69 on 2009-04-26
Exact same problem here.  Please help.

---

### Post by Monsuco on 2009-04-26
Yes my card has issues too. Here is what I see in LSPCI
```
monsuco@Earthbound:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)                                             
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)                                       
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)                                       
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)                                       
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA                                                         
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
monsuco@Earthbound:~$

```
I used to use the normal ATI driver provided for me by restricted drivers manager, but this time it doesn't seem to provide them in the manager. I can't do anything in 3D without those, this won't work.

Is this some issue with Kubuntu, or does Ubuntu have this problem too?

---

### Post by ilmar on 2009-04-26
I have mobility x2300 card and same troubles with driver. Compiz work perfectly, but game performance is horrible, also i have screen filled with tildes when shut down or re-login.
Install of ati-driver-installer-9-3-x86.x86_64.run from ati.amd.com gives this: 
> Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro
Begging for some help with this :(

---

### Post by StuartN on 2009-04-26
There are several thread about this. ATI has moved a large number of cards, some relatively recent, to the "legacy" category and they are not supported in Catalyst 9.4 (see which cards at [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English)). If you have one of these cards then Ubuntu should install one of the older, open source drivers appropriate to your card - but you will see a decline in speed and some features will not be supported.

If you attempt to install Catalyst 9.3 or earlier (as some people have) then it will probably break your Ubuntu 9.04 and give you a black or garbled screen.

If you have not upgraded to Ubuntu 9.04 then burn a Live CD and test the performance with glxgears, video playback, YouTube etc before proceeding to replace an earlier distribution.

---

### Post by notanerd on 2009-04-26
I have an ati mobility radeon 9600 and stupidly upgraded to jaunty without knowing about the issues related to this. My system is practically unusable. My background image is coming through clean, but all the icons and programs are blurred by black pixels. This is what used to happen to me when I tried to enable compiz on intrepid, however i do not have any effects enabled.

Does anyone know of a way to get around this?

---

### Post by notanerd on 2009-04-26
OK so i can watch avi files with M Player and it is coming through clearly, this is strange

---

### Post by StuartN on 2009-04-26
> **notanerd said:**
> I have an ati mobility radeon 9600 and stupidly upgraded to jaunty without knowing about the issues related to this. My system is practically unusable. My background image is coming through clean, but all the icons and programs are blurred by black pixels. This is what used to happen to me when I tried to enable compiz on intrepid, however i do not have any effects enabled.

Does anyone know of a way to get around this?

You need to sudo apt-get remove xorg-driver-fglrx:

[http://ubuntuforums.org/showthread.php?t=1133931&highlight=fglrx+sudo](http://ubuntuforums.org/showthread.php?t=1133931&highlight=fglrx+sudo)

---

### Post by notanerd on 2009-04-26
i have already removed it, thanks for your help though

---

### Post by Renan Decarlo on 2009-04-26
I've got a 15" monitor, the max resolution is 1152x864, and with the driver that Ubuntu automatically installed to me is only recognizing it as 14", max resolution 1024x768... what do I do? Isn't there an open source driver that can make 3d acceleration work for ati x300? Or at least to get the right resolution? :(:confused:

---

### Post by Monsuco on 2009-04-26
> **StuartN said:**
> There are several thread about this. ATI has moved a large number of cards, some relatively recent, to the "legacy" category and they are not supported in Catalyst 9.4 (see which cards at [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English)). If you have one of these cards then Ubuntu should install one of the older, open source drivers appropriate to your card - but you will see a decline in speed and some features will not be supported.
Well, how do I get the old driver back? The one that worked in 8.10?

---

### Post by StuartN on 2009-04-26
> **Monsuco said:**
> Well, how do I get the old driver back? The one that worked in 8.10?

You can not use an earlier version of Catalyst with Ubuntu 9.04. If you install Catalyst version 9.3 or earlier then you will break this distribution. The older open-source drivers should work, but with lower performance and fewer features.

If you want your old driver then you will have to stick with Ubuntu 8.10. ATI state that they will not be adding support for these "legacy" cards, so this is going to rely on some community effort going into the open source drivers.

---

### Post by PKabooo69 on 2009-04-26
guess I'm going to roll back to intrepid for the time being.  Id really love to keep Jaunty but this is a big problem.  I need to be able to play ma games haha. Somone let me know if someone has a working driver.  Ill be much appreciative.

---

### Post by Monsuco on 2009-04-26
> **StuartN said:**
> You can not use an earlier version of Catalyst with Ubuntu 9.04. If you install Catalyst version 9.3 or earlier then you will break this distribution. 
What exactly is it that stops me from using 9.3 on Jaunty? How is it that it works perfectly fine on 8.10 but breaks on 9.04? I mean, I should be able to manually install them somehow.

> The older open-source drivers should work, but with lower performance and fewer features.
They don't. They provide terrible performance and are horribly choppy. How on earth can a laptop that is about a year and a half old be considered "legacy" in any way?

---

### Post by drplix on 2009-04-26
I'm in the same boat - upgraded from Hardy without realising that ATI have decided that 18months is "legacy".  I had terrible trouble with the standard repository drivers but managed to find and install a recent build of the open source radeon driver...

[http://ubuntuforums.org/showthread.php?t=1136640](http://ubuntuforums.org/showthread.php?t=1136640)

Not exactly fast, no 3D and video is no good.  But at least I have a functioning desktop.

Would like to know how we can hack an install of catalyst 9.3 drivers.

---

### Post by StuartN on 2009-04-26
> **drplix said:**
> Would like to know how we can hack an install of catalyst 9.3 drivers.

The Catalyst 9.3 and earlier drivers are not compatible with X server 1.6, and can not be made compatible. If you try to install an earlier driver (there are plenty of threads from people who have) then you will not be able to boot into a graphical desktop in Ubuntu 9.04 and will need to uninstall it (sudo apt-get remove xorg-driver-fglrx) and possibly reconfigure other settings.

One thread ([http://ubuntuforums.org/showthread.php?t=1058243](http://ubuntuforums.org/showthread.php?t=1058243)) suggests that ATI might release the 3D elements of its "legacy" drivers for community development.

---

### Post by Renan Decarlo on 2009-04-26
> **Monsuco said:**
> What exactly is it that stops me from using 9.3 on Jaunty? How is it that it works perfectly fine on 8.10 but breaks on 9.04? I mean, I should be able to manually install them somehow.


They don't. They provide terrible performance and are horribly choppy. How on earth can a laptop that is about a year and a half old be considered "legacy" in any way?

Ubuntu 8.10 = xorg server 1.5
Catalyst 9.3 = support until xorg server 1.5
Ubuntu 9.04 = xorg server 1.6

Bah, why did the hell AMD bought ATI? I used to like AMD, but now it f*cked up everythig -.-'

I managed to install xserver-xorg-video-radeonhd to try to get the chip working and now i can't even turn on my computer :( crashed screen

---

### Post by rodbotic on 2009-04-26
I did a fresh install with 9.4  everything works but dualscreen.
I have a ATI 9550.

I love how fast everything is, but I need dual screen.

I am thinking I am just going to dual boot it, with 8.10, and 9.04 and keep trinkering 9.04, and using 8.10 for the dual screens.

---

### Post by Monsuco on 2009-04-26
> **Renan Decarlo said:**
> Ubuntu 8.10 = xorg server 1.5
Catalyst 9.3 = support until xorg server 1.5
Ubuntu 9.04 = xorg server 1.6

Well then, what about simply downgrading to xorg 1.5?

---

### Post by HavocXphere on 2009-04-26
> **Monsuco said:**
> Well then, what about simply downgrading to xorg 1.5?
This works. I saw a report somewhere of someone who did this. The catch is that the stuff has to be compiled by hand.

---

### Post by ilmar on 2009-04-26
I really dont understand ati polytics. My laptop, and it's graphic card, is only 8 month old - bloody hell, why it considered "legacy"? :(
The wierdest thing is that my compiz vorking on 9.04 without driver absolutely perfect, better than in 8.10 with catalyst. But i have horrible performance in Guild Wars, and glitches in Blender.

---

### Post by Renan Decarlo on 2009-04-26
> **HavocXphere said:**
> This works. I saw a report somewhere of someone who did this. The catch is that the stuff has to be compiled by hand.

can you find that for us? :D

---

### Post by notanerd on 2009-04-26
I went back to intrepid, this is all way over my head

---

### Post by Duo Maxwell on 2009-04-26
> **ilmar said:**
> I really dont understand ati polytics. My laptop, and it's graphic card, is only 8 month old - bloody hell, why it considered "legacy"? :(
The wierdest thing is that my compiz vorking on 9.04 without driver absolutely perfect, better than in 8.10 with catalyst. But i have horrible performance in Guild Wars, and glitches in Blender.

It's the fact that hte are strapped for cash in a down economy, they where already  taking heavy losses since the C2D came out and only with the R700 GPUs have had a really competitive lineup of GPUs at all price points.

They've had to make allot of cuts to keep from going out of business, and are still trying to claw back performance dominance against both Intel and Nvidia, not an easy task.

Look at it this way, even though AMD makes CPUS, GPUs and motherboard chipsets how many laptops do you currently see on the market featuring an all AMD layout? How many netbooks? They have virtually nothing in these markets which are massively profitable for their competition.

On the bright side, the HD4 series cards are very good, the Phenom2 overclocks well and they have been releasing tons of docs and sample code for thei GPUs.

It's just that to get the benefits of the open source drivers you're going to have to build them yourself.

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature) Looks like the RS690 and R400 series are fairly complete in terms of features and the R500 series is mostly there. A fair amount of software tests out as well [http://wiki.x.org/wiki/RadeonProgram](http://wiki.x.org/wiki/RadeonProgram) though allot of bits need to be filled in, maybe someone here can fill in the gaps?

---

### Post by Monsuco on 2009-04-26
> **notanerd said:**
> I went back to intrepid, this is all way over my head
I will wait a while before doing that. It takes too long to set all this up so I want to try to avoid having to do that again. I'll give it a few weeks and see if someone comes up with a fix.

---

### Post by Renan Decarlo on 2009-04-26
> **Monsuco said:**
> I will wait a while before doing that. It takes too long to set all this up so I want to try to avoid having to do that again. I'll give it a few weeks and see if someone comes up with a fix.

Yeah. I'm gonna do that too. I'll try to keep with the weird 1024x768 resolution, while i could keep with 1152x864... 

If they don't release a good driver in a couple of weeks, than i'll get back to 8.04.

When the 8.10 was released, i had the same problem, the driver didn't work, and I think a few weeks later the open source community have managed to get support for that driver... it may happen on 9.04 too.


Btw, i'll try to do what maxwell supposed too :)

I can try to use my onboard video card too, the ATI X300 is offboard. My onboard is an Intel G945 128mb, but this video card don't work the game i play, dunno if it has better performance or not as the X300... but the driver for that on 9.04 it's even worse than the X300 driver...

---

### Post by ilmar on 2009-04-27
Well, it seems that downgrading xorg is rather simple task - just remove current and install old via synaptic ([http://ubuntuforums.org/showthread.php?t=252921](http://ubuntuforums.org/showthread.php?t=252921)). I'm confused a bit with versions of xorg, so could anyone please tell what version is on 8.10?
On 9.04 i have this:
> ~$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.6.0-0ubuntu14
  Candidate: 2:1.6.0-0ubuntu14
  Version table:
 *** 2:1.6.0-0ubuntu14 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
        100 /var/lib/dpkg/status


---

### Post by StuartN on 2009-04-27
> **ilmar said:**
> I'm confused a bit with versions of xorg, so could anyone please tell what version is on 8.10?
On 9.04 i have this:

I have version 1.5.2 on Ubuntu 8.10:
```
apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.5.2-2ubuntu3.1
  Candidate: 2:1.5.2-2ubuntu3.1
  Version table:
 *** 2:1.5.2-2ubuntu3.1 0
        500 http://ie.archive.ubuntu.com intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     2:1.5.2-2ubuntu3 0
        500 http://ie.archive.ubuntu.com intrepid/main Packages
```

---

### Post by gocek on 2009-04-27
> **ilmar said:**
> Well, it seems that downgrading xorg is rather simple task - just remove current and install old via synaptic ([http://ubuntuforums.org/showthread.php?t=252921](http://ubuntuforums.org/showthread.php?t=252921)). I'm confused a bit with versions of xorg, so could anyone please tell what version is on 8.10?
On 9.04 i have this:

Are you sure it's that simple?
I personally believe that you won't find packages for Jaunty. Of course, there're packages for X.Org 1.5 for Intrepid and 1.6 for Jaunty but they won't work when mixed.

I see two options:
1.) wait for somebody to make a .deb package with X.Org Server 1.5 for Jaunty
2.) download the sources and compile it yourself, but I bet you'll run in many dependency problems.

correct me if I'm wrong

---

### Post by zampes on 2009-04-27
Hey everyone!
I've got a similar problem: I just bought an HP DV4 1220, ATi Radeon HD 3200. As I had just downloaded U9.4 to try it on my old Acer Aspire 3050, I also tried it on the HP. I'm migrating from U8.10, which worked so well for me. Now, 9.04 worls well on the Acer, but on my HP the screen flicker at the native 1200x800 resolution (16:10), but if I bring it down to the horrible 1280x764 it works well. This happens on my HP with both 8.10 and 9.04. I tried Mandriva Powerpack, and this doesn't happen, it works well. OpenSUsE 11.1 also works well, but I want Ubuntu 9.04!!!!!
Help, anyone?

Thx!:confused:

---

### Post by ilmar on 2009-04-27
So, anyone tried downgrade? I'll do it tommorow and report here, but if anyone have experience in it - please speak :) It seems that alot of people suffers from this problem...and we really need solution

---

### Post by peppers on 2009-04-27
I have a HP dc5850 which has a ATI Radeon 3100 (on board), if i'm not wrong it's not on the list of legacy drivers ([http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English))

When I try to download the newest driver from the website it says that 9.4 is compatible. But when I install this driver I get the black screen after splash. 

To get it to work again I have to remove and go back to the open-source driver.
Normaly I wouldn't complain, but i'm getting horrible performance issues. 
Xorg process regulary get to over 90%, i'm thinking it's because of that open-source driver.

Does anyone have a solution?

---

### Post by Renan Decarlo on 2009-04-27
> **ilmar said:**
> So, anyone tried downgrade? I'll do it tommorow and report here, but if anyone have experience in it - please speak :) It seems that alot of people suffers from this problem...and we really need solution

I tried to do it in my manner today. I've added the 8.04 Hardy repositories into sources.list, removed xserver-xorg-core, and then tried to install the version 1.4.1 from the Hardy repository... It didn't work, it says that needs xserver-xorg to work together... and when I try to install it, it says that it's going to remove a lot of packages, almost all the ones that come with Ubuntu (ubuntu-desktop, brasero, gnome, etc...). So I installed the normal version of xserver-xorg-core again.

Later I'm gonna try to do the way Maxwell supposed. Actually, I don't know what I should do to compile it by myself. :D

---

### Post by ilmar on 2009-04-28
> **Renan Decarlo said:**
> I tried to do it in my manner today. I've added the 8.04 Hardy repositories into sources.list, removed xserver-xorg-core, and then tried to install the version 1.4.1 from the Hardy repository... It didn't work, it says that needs xserver-xorg to work together... and when I try to install it, it says that it's going to remove a lot of packages, almost all the ones that come with Ubuntu (ubuntu-desktop, brasero, gnome, etc...). So I installed the normal version of xserver-xorg-core again.

Later I'm gonna try to do the way Maxwell supposed. Actually, I don't know what I should do to compile it by myself. :D

Oh thanks :) Damn, googling again

---

### Post by gocek on 2009-04-28
seems it just like I've predicted :p

> **gocek said:**
> Are you sure it's that simple?
I personally believe that you won't find packages for Jaunty. Of course, there're packages for X.Org 1.5 for Intrepid and 1.6 for Jaunty but they won't work when mixed.

I see two options:
1.) wait for somebody to make a .deb package with X.Org Server 1.6 for Jaunty
2.) download the sources and compile it yourself, but I bet you'll run in many dependency problems.

correct me if I'm wrong

Anyways:
option 2) isn't easy, just so you know. You'll probably crash your system, so I strongly recommend playing with X.Org compilation on a fresh Ubuntu install (might be by Wubi or VMware or something similar).

But the source is here:
[http://xorg.freedesktop.org/wiki/Releases/Download?action=show&redirect=Mirrors](http://xorg.freedesktop.org/wiki/Releases/Download?action=show&redirect=Mirrors)
the main page is: [http://xorg.freedesktop.org/](http://xorg.freedesktop.org/)

And the version you need is 7.4, it has xorg-server-1.5.1.tar.bz2 if you look closely. But as far as I know it's required to compile everything else and there is a lot of packages :D

EDIT:
I found this interesting guide: [http://damnsmalllinux.org/f/topic-3-26-16260-0.html](http://damnsmalllinux.org/f/topic-3-26-16260-0.html)
It's not really a HowTo for ubuntu nor for X.Org 7.4 but it gives you and idea where to start.
So basically: 
1) get packages for compiling things: sudo apt-get install build-essential
2) download the everything directory from e.g. [ftp://ftp.freedesktop.org/pub/xorg/X11R7.4/src/](ftp://ftp.freedesktop.org/pub/xorg/X11R7.4/src/)
3) unpack them and configure :p that's the most tricky step :>
I'm still not sure whether you need all the packages or maybe just some of them. Probably most of them depend on each other and won't work with newer versions. BUT, you might try to download only [ftp://ftp.freedesktop.org/pub/xorg/X11R7.4/src/xserver/](ftp://ftp.freedesktop.org/pub/xorg/X11R7.4/src/xserver/) configure it and try to install and check what happens ;)

EDIT2:
two more interesting links:
some hints about dependency: [http://ubuntuforums.org/showthread.php?t=764778](http://ubuntuforums.org/showthread.php?t=764778)
installing instructions: [http://www.linuxfromscratch.org/blfs/view/svn/x/installing.html](http://www.linuxfromscratch.org/blfs/view/svn/x/installing.html)

---

### Post by zampes on 2009-04-28
Hello again, dunno if this'll help.
I've been tinkering with Ubuntu 9.4. True, when I had just installed it, it didn't show any sings of realizing there was an ATi card in the system. So, I just went right ahead and installed the latest ATi driver from their website, version 9.4. A reboot later, everything was working a-ok.
I guess that's the way to go, just use the ATi drivers -new or legacy- you have and install them even w/o prompt. Then reboot and post again. Thx for reading!

---

### Post by Renan Decarlo on 2009-04-28
> **zampes said:**
> Hello again, dunno if this'll help.
I've been tinkering with Ubuntu 9.4. True, when I had just installed it, it didn't show any sings of realizing there was an ATi card in the system. So, I just went right ahead and installed the latest ATi driver from their website, version 9.4. A reboot later, everything was working a-ok.
I guess that's the way to go, just use the ATi drivers -new or legacy- you have and install them even w/o prompt. Then reboot and post again. Thx for reading!

Not all ATI drivers are unsupported. What's yours?
The old one doesn't work, as it do only support xorg-server 1.5 and Ubuntu 9.04 is using xorg-server 1.6.

---

### Post by ilmar on 2009-04-30
> **zampes said:**
> Hello again, dunno if this'll help.
I've been tinkering with Ubuntu 9.4. True, when I had just installed it, it didn't show any sings of realizing there was an ATi card in the system. So, I just went right ahead and installed the latest ATi driver from their website, version 9.4. A reboot later, everything was working a-ok.
I guess that's the way to go, just use the ATi drivers -new or legacy- you have and install them even w/o prompt. Then reboot and post again. Thx for reading!

I did such thing - after it i cannot boot in graphic mode at all.

---

### Post by buck2825 on 2010-01-24
to whom it may concern mint 8 has this same issue.

I have a Dell Dimension E510 with 128MB ATI Radeon X300 SE

I really wish I could get a video driver that supports OpenGL this PC is a media center PC and would really like use linux instead of Winblows.  

until there is a fix I will roll back to the previous LTS.

---

