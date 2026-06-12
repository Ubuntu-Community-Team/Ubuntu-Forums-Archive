---
title: "Intel Core i7"
date: 2008-11-27
forum: Hardware
---

### Post by dpol2 on 2008-11-27
Does anyone have any experience with Ubuntu and the Intel Core i7 series of CPUs? I am about to order a new computer, and am eager to go with a new Core i7 CPU given the reported performance advantage.

My local computer shop is recommending the Asus P6T Deluxe motherboard, but I can't find any information on whether this motherboard works well with Linux. The network interface card of the Asus P5Q motherboard was not supported in Linux until 2.6.27, supposedly, so I am wary of just going with the Asus product and hoping for the best.

If you have experience with a different motherboard supporting the Intel Core i7 series of CPUs, I'd be interested in hearing about that as well.

Thanks.

---

### Post by stefangr1 on 2008-11-30
I am also very interested in the experiences of users of the new core i7. I'm considering building a htpc with Asus P6T mobo and Core i7 920 proc.

On my current pc with Core 2 E6750 (m-ATX mobo doesn't support overclocking) most h264 1080p movies do not play well, at least: not without skipping loopfilters etc.. According to the web sources core i7 provides an enormous improvement, the 2,667Ghz variant should be substantially faster then the 'old' 3,2Ghz Quad.

So: anyone?

---

### Post by dpol2 on 2008-12-01
Stefan,

I have also heard great things about Intel's new micro-architecture. I have decided to take the plunge and order a new computer with the Asus P6T motherboard. I did look up the [specifications for the board]("http://www.asus.com/products.aspx?l1=3&l2=179&l3=815&l4=0&model=2593&modelmenu=2") and the Linux compatibility of the individual chips Asus uses. The network chip should be OK, and the sound chip should also work fine. The SATA/PATA I/O controller chip, a Marvell 88SE6111, is known to be problematic. My impression, from reading all that I could find on this chip, is that it is only used for legacy PATA (IDE) devices, while the Intel ICH10R chip (the "Southbridge") should handle SATA. I have asked my vendor to use only SATA devices, and I'm hoping that should be sufficient to make everything work.

---

### Post by rbmorse on 2008-12-03
You need a late 2.6.26 series kernel to get support for the Marvell 88SE111 controller...similar to the problem experienced by early purchasers of motherboards with the Intel iCH9 chipset/jMicron 363B outboard RAID/SATA/IDE controllers. 

Intrepid Ibex (8.10) has the 2.6.27- series kernel and should support the Marvell chip right out of the (motherboard) box.

---

### Post by stefangr1 on 2008-12-04
> **dpol2 said:**
> Stefan,

I have also heard great things about Intel's new micro-architecture. I have decided to take the plunge and order a new computer with the Asus P6T motherboard. I did look up the [specifications for the board]("http://www.asus.com/products.aspx?l1=3&l2=179&l3=815&l4=0&model=2593&modelmenu=2") and the Linux compatibility of the individual chips Asus uses. The network chip should be OK, and the sound chip should also work fine. The SATA/PATA I/O controller chip, a Marvell 88SE6111, is known to be problematic. My impression, from reading all that I could find on this chip, is that it is only used for legacy PATA (IDE) devices, while the Intel ICH10R chip (the "Southbridge") should handle SATA. I have asked my vendor to use only SATA devices, and I'm hoping that should be sufficient to make everything work.


That sounds ok: sata cd/dvd-drives are well available now, and I wasn't going to use ide disks anyway. I would really appreciate to hear from you how your system works when it has arrived.

Thanks in advance, and good luck with your system!

---

### Post by TheEclypse on 2008-12-06
I just set up a system with Core i7, Asus P6T and ATI HD 4870, and when I boot the Ubuntu 8.10 CD and select install or livecd, it I get a blank white screen after the splash screen goes away.

---

### Post by stefangr1 on 2008-12-07
> **TheEclypse said:**
> I just set up a system with Core i7, Asus P6T and ATI HD 4870, and when I boot the Ubuntu 8.10 CD and select install or livecd, it I get a blank white screen after the splash screen goes away.

Did you already try the alternate-cd, which has somewhat better hardware support?

---

### Post by miket3115 on 2008-12-07
> **TheEclypse said:**
> I just set up a system with Core i7, Asus P6T and ATI HD 4870, and when I boot the Ubuntu 8.10 CD and select install or livecd, it I get a blank white screen after the splash screen goes away.

I had a similar problem except my LCD screen would go black and have random white flashing horizontal lines.  I thought it might be the monitor so I hooked up an older CRT monitor.  I got a picture but it was so shaky I couldn't read it or make anything out.  I may be going out on a limb but i think it has to do with the ATI video card you are running as I am running a Radeon HD card as well.  I have no Idea how to fix this from the install disk.

---

### Post by bonestonne on 2008-12-07
> **stefangr1 said:**
> I am also very interested in the experiences of users of the new core i7. I'm considering building a htpc with Asus P6T mobo and Core i7 920 proc.

On my current pc with Core 2 E6750 (m-ATX mobo doesn't support overclocking) most h264 1080p movies do not play well, at least: not without skipping loopfilters etc.. According to the web sources core i7 provides an enormous improvement, the 2,667Ghz variant should be substantially faster then the 'old' 3,2Ghz Quad.

So: anyone?

there are weaker systems available that don't have problems with HD content, as most of the work is offloaded onto the GPU, if you use integrated graphics (especially intel's) HD playback will bite. discrete graphics are the way to go with HD. the CPU actually plays a very small role.

as for i7 itself, i wouldn't dive in just yet, as the price compared to the performance itself is not really worth it right now.

you get the integrated memory controller, which will be a huge step up, however past that, triple channel yields very little performance over dual channel, not to mention the price of that. also, seeing as there's still only one dedicated x16 PCI-e slot on the board, even running the SLI and tri-SLI configs will not give you peak performance. they run in a 16-8-8 config, which is pretty weak. not mentioning the fact that the x1 slot cannot be used unless you put graphics in a lower PCI-e slot, which lowers it's bandwidth.

the technology is great, but the average home user, and even the hardcore gamer will still be running overkill with a Q9xxx Core 2 Quad and 6-8gb of DDR2-1066 RAM.

---

### Post by stefangr1 on 2008-12-07
> **bonestonne said:**
> there are weaker systems available that don't have problems with HD content, as most of the work is offloaded onto the GPU, if you use integrated graphics (especially intel's) HD playback will bite. discrete graphics are the way to go with HD. the CPU actually plays a very small role.

as for i7 itself, i wouldn't dive in just yet, as the price compared to the performance itself is not really worth it right now.

you get the integrated memory controller, which will be a huge step up, however past that, triple channel yields very little performance over dual channel, not to mention the price of that. also, seeing as there's still only one dedicated x16 PCI-e slot on the board, even running the SLI and tri-SLI configs will not give you peak performance. they run in a 16-8-8 config, which is pretty weak. not mentioning the fact that the x1 slot cannot be used unless you put graphics in a lower PCI-e slot, which lowers it's bandwidth.

the technology is great, but the average home user, and even the hardcore gamer will still be running overkill with a Q9xxx Core 2 Quad and 6-8gb of DDR2-1066 RAM.

Well, there are some efforts to get mpeg-4 hardware support working in linux, like VAAPI from Intel and the beta's that just arrived from NVIDIA, but at the present time the CPU still has to do everything. Almost all h264 movies have to be decoded in a single tread. On a c2d@2,67Ghz 2/3 of the 1080p movies can't be played, while the remaining part is usually played with between 50 and 100% cpu load.

About the i7 performance: h264 performance is suppozedly about 50% better! For the rest, on almost all benchmarks the i920 it performs better than the current 3,2Ghz QX9770, which is selling at over EUR.1000,--.

About the price of the i7: I don't think it's that expensive... Compared to, let's say the E8600 I could buy otherwise (has about 30% more performance than my current proc and would hopefully perform reasonably on 1080p h264), the processor is equally expensive, while the IO-board will be 150, and the memory 100 euro (for 6Gb) more expensive. On the total price of the system, therefore, it doesn't add that much. 

Another option would off cause be to get a htpc with windows vista, but I'm not sure if that's what I want.

---

### Post by dpol2 on 2008-12-08
There's a [great thread on phoronix.com]("http://www.phoronix.com/forums/showthread.php?t=13898") that seems to indicate that the Asus P6T should work fine with Linux.

---

### Post by dpol2 on 2008-12-17
I have now received my new computer, and much to my amazement, everything seems to work very well. I installed the system using the live CD (x86-64). The network and audio chips are properly detected, and work out of the box. The only problem I'm experiencing is with the audio -- the sound works, but the volume is very low. I'll try switching to S/PDIF and see if that works better (which I was planning on doing anyway, now that my motherboard supports it).

All in all, everything works fine, and I would recommend this setup to anyone. Note that I have not tried connecting any PATA (IDE) devices, nor have I tried Firewire.

If I encounter any problems, I'll post an update on this board.

---

### Post by dpol2 on 2008-12-18
S/PDIF sound output does not work. The support is [broken]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/300937/+viewstatus"), and will likely be [fixed in Linux 2.6.28]("http://robbat2.livejournal.com/232122.html"). Adventurous users can probably get this to work today by applying the patch I linked to; me, I'll just stick around for 2.6.28 to be released.

---

### Post by AKADAP on 2008-12-21
> **TheEclypse said:**
> I just set up a system with Core i7, Asus P6T and ATI HD 4870, and when I boot the Ubuntu 8.10 CD and select install or livecd, it I get a blank white screen after the splash screen goes away.

I had a similar problem with an ATI HD4850 board. Work around was to install ubuntu with the safe video mode (one of the function keys listed on the bottom of the last viewable screen). Then install the ATI proprietary drivers once Ubuntu is installed.

---

### Post by AKADAP on 2008-12-21
> **dpol2 said:**
> S/PDIF sound output does not work. The support is [broken]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/300937/+viewstatus"), and will likely be [fixed in Linux 2.6.28]("http://robbat2.livejournal.com/232122.html"). Adventurous users can probably get this to work today by applying the patch I linked to; me, I'll just stick around for 2.6.28 to be released.

Thank you for that link. Now I can stop screwing up my system and just wait until the next kernel comes out. That was driving me nuts.

---

### Post by FrankVdb on 2008-12-22
I wouldn't buy an i7 Core system yet for an expensive rig. There are bound to be initial problems...

---

### Post by Swerve1000 on 2008-12-29
I'm really torn. The Intel 9550 Quad is now tested technology and would do me fine, BUT the i7 is only a little more money and performs so much better.

I'm just concerned that I'll have issues with Ubuntu. I've only just made the switch from XP to Linux full time and there's no way I'm going back.

---

### Post by Leo.F on 2008-12-30
I just wanted to let you know that the SAS (Serial Attached SCSI) controller on the Asus P6T Deluxe is not recognized by Ubuntu 8.10. Even if the BIOS is set up to boot from the SAS Drive, during install the partitioner only shows the SATA drive which is connected to the Intel controller.

This seems to be a bug in the kernel as it also happens for Fedora just as this bug report states and offers a solution:

[https://bugzilla.redhat.com/show_bug.cgi?id=474482](https://bugzilla.redhat.com/show_bug.cgi?id=474482)

"...There are some problems using the sas drive however because rc.sysinit and/or the init script in the initrd try to use it before the mvsas driver has finished making the device appear. This means that partitions on it may fail to fsck or logical volumes fail to appear during rc.sysinit, depending on the timing. 

To fix this, what I needed to do was add a delay loop into rc.sysinit. In my case I just hacked a loop waiting for /dev/sdc to appear just before rc.sysinit does the "lvm vgchange -a y" to set up the logical volumes. This works fine. 

To make the sas drive usable as the root file system we need a similar delay for the device to appear before init tries to mount it as the new root, otherwise the mount fails and the system will not boot. mkinitrd already has a list of drivers for which it turns on a "wait_for_scsi" loop in init, but mvsas isn't on the list. I added mvsas to the list, created a new initrd and now / is fine on the sas drive. I have not tried /boot on the sas drive yet..."

There is no SAS driver for Linux on Asus' download page:

[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)

They do have one for XP and Vista.

Is there a way to use the above solution for Ubuntu? Could the files on the 8.10 installation CD be patched and a new one created to install from on the SAS drive? 

I've been using Hardy x64 on a 3 year old Pentium 4 for about 6 months and would hate not to be able to install 8.10 on the SAS drive (Fujitsu 15k RPM) of my new i7. Going back to XP (which can install on the SAS drive thanks to the driver provided) is not an option, and installing on the SATA drive will be a waste of a 15k RPM drive that I bough only for the OS.

I'm still using my old PC, so I can experiment on the new one and will gladly share my findings in this forum. It would be great if someone with enough skills could give directions as to what to try. As I said above I've only been full time on Linux for about 6 months, but I'm eager to learn and improve my skills.

Could someone please shed some light as to how to install Intrepid on a SAS drive? Any and all comments will be greatly appreciated.

Thank you in advance for your help, and for the great resource this forum provides.

---

### Post by snorkius on 2009-01-23
Any luck/news with Ubuntu on a SAS (88SE6320 Marvell controller) disk?

I just got a P6T WS pro, and I want to try installing 8.10 on a SAS Raid.

---

### Post by Sef on 2009-01-23
> Any luck/news with Ubuntu on a SAS (88SE6320 Marvell controller) disk?

I just got a P6T WS pro, and I want to try installing 8.10 on a SAS Raid.

Run the Live CD and see how it works.

---

### Post by snorkius on 2009-01-23
> **Sef said:**
> Run the Live CD and see how it works.

Besides a (very) flickering screen, it loads just fine. But this doesn't have anything to do with the SAS, I don't think. 

The SAS disk RAID is not listen anywhere in the devices, however. Also, running install from the Live CD stops on the partitioning step (there is just a blank form where the disks are supposed to be) 

When installing Ubuntu Server 8.10, on the step "Detecting Disks", a dialog pops up with the following message "One or more drives containing Serial ATA RAID configurations have been found. Do you wish to activate these RAID devices? Yes/No" Clicking "Yes" returns "An installation step failed blah blah yadda yadda" 

Interestingly enough, I tried installing WUBI on the SAS RAID (from Vista, also located on the SAS RAID) and, while it didn't exactly work, it did load grub and BusyBox (the files for which are located on the SAS disk I assume)

> To fix this, what I needed to do was add a delay loop into rc.sysinit. In my case I just hacked a loop waiting for /dev/sdc to appear just before rc.sysinit does the "lvm vgchange -a y" to set up the logical volumes. This works fine.

To make the sas drive usable as the root file system we need a similar delay for the device to appear before init tries to mount it as the new root, otherwise the mount fails and the system will not boot. mkinitrd already has a list of drivers for which it turns on a "wait_for_scsi" loop in init, but mvsas isn't on the list. I added mvsas to the list, created a new initrd and now / is fine on the sas drive. I have not tried /boot on the sas drive yet..."


Hmm... I'm not "hard-core" enough to know exactly how to do all that. Could someone please explain how one goes about putting a delay loop into rc.sysinit?

---

### Post by Leo.F on 2009-01-27
> **snorkius said:**
> Any luck/news with Ubuntu on a SAS (88SE6320 Marvell controller) disk?

I just got a P6T WS pro, and I want to try installing 8.10 on a SAS Raid.

Hi snorkius,

   I've tried Jaunty x64 Alpha 2 Desktop and Alternate with the same results, Alpha 3 (both Desktop and Alternate) breaks after the the initial screen (after choosing language, keyboard & Install). This could be due to bad discs, but I've checked Mod5Sums and they match.

> **snorkius said:**
> Hmm... I'm not "hard-core" enough to know exactly how to do all that. Could someone please explain how one goes about putting a delay loop into rc.sysinit?

   I'm in the same position. I guess we need to modify the kernel and make a new install CD to boot from so that it can recognize the SAS drive(s), I just don't know where to start.

   Is there some place to make the Jaunty developers aware of this situation (in case they aren't already) hoping to have it fixed for the next release?

   Intrepid runs just fine on the P6T Deluxe, I'm running the 177 driver from nVdia on a GeForce 9800 GTX+ with no trouble since December (on a SATA instalation). 

   Please post back if you find a solution, I'll do the same.

   Be Well

---

### Post by snorkius on 2009-01-30
Fedora recognizes the SAS disks (although not the RAID device) and installs w/o problems. 

So the problem is fixable - I just don't know how to fix it. :confused:

---

### Post by Leo.F on 2009-01-30
> **snorkius said:**
> Fedora recognizes the SAS disks (although not the RAID device) and installs w/o problems. 

So the problem is fixable - I just don't know how to fix it. :confused:

The original bug report refers to Fedora 10:

[Harddisk attached to onboard Marvell SAS controller on Asus P6T Deluxe not detected under Fedora 10]("https://bugzilla.redhat.com/show_bug.cgi?id=474482")

and that is the most current version, which version of Fedora were you able to install on the SAS drive and which version of the Kernel does it use?

Have you tried Jaunty Alpha 3? I really would like to stay with Ubuntu and I'm hoping Jaunty will have this fixed as the main Kernel tree has been patched.

Thanks for your feedback.

Be Well!

---

### Post by snorkius on 2009-01-30
> **Leo.F said:**
> The original bug report refers to Fedora 10:

[Harddisk attached to onboard Marvell SAS controller on Asus P6T Deluxe not detected under Fedora 10]("https://bugzilla.redhat.com/show_bug.cgi?id=474482")

and that is the most current version, which version of Fedora were you able to install on the SAS drive and which version of the Kernel does it use?

Have you tried Jaunty Alpha 3? I really would like to stay with Ubuntu and I'm hoping Jaunty will have this fixed as the main Kernel tree has been patched.

Thanks for your feedback.

Be Well!

uname -a gives:  2.6.27.12-170.2.5.fc10.x86_64 (I just downloaded (the 26 Jan) the latest version on the Fedora site) 

I'm downloading Jaunty right now.

---

### Post by r m h on 2009-02-02
Back in December I built my new super workstation from parts off of NewEgg.

I am running the following:

Intel Core i7 2.93GHz CPU
6x2GB triple channel DDR3 PC3 12800 RAM (12GB total)
Asus Rampage II Extreme Mainboard
3Ware 9650SE RAID controller
8x250GB SATA II disks (6x250 RAID5 hot swap array + 2 hot spare)
ABS Canyon 695 case
1300W Tagan ITZ series PS
2xSAPPHIRE Radeon HD 4850 Video cards (dual dual DVI cards)
2x HP LP2465 24" LCD monitors
2x HP LP2065 20" LCD monitors

I installed Ubuntu 8.10 desktop x86_64 and all upgrades and I've been running rock-solid with super performance from day 1.

In the event that I need to spin up a Windows XP instance in VirtualBox, I boot a VM in about 15 seconds and can shut it down even faster.

The 4 hyper threaded CPUs in this i7 chip show up as 8 CPUs in Linux:

```
~$ grep -i bogomips  /var/log/dmesg
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5879.99 BogoMIPS (lpj=11759996)
[    0.004000] Calibrating delay using timer specific routine.. 5879.87 BogoMIPS (lpj=11759744)
[    0.004000] Calibrating delay using timer specific routine.. 5879.87 BogoMIPS (lpj=11759754)
[    0.004000] Calibrating delay using timer specific routine.. 5879.87 BogoMIPS (lpj=11759756)
[    0.004000] Calibrating delay using timer specific routine.. 5845.57 BogoMIPS (lpj=11691156)
[    0.004000] Calibrating delay using timer specific routine.. 5879.87 BogoMIPS (lpj=11759740)
[    0.004000] Calibrating delay using timer specific routine.. 5915.95 BogoMIPS (lpj=11831911)
[    0.004000] Calibrating delay using timer specific routine.. 5879.87 BogoMIPS (lpj=11759742)
[    0.976054] Total of 8 processors activated (47040.89 BogoMIPS).

```

---

### Post by aktiwers on 2009-02-03
> **r m h said:**
> Back in December I built my new super workstation from parts off of NewEgg.

I am running the following:

Intel Core i7 2.93GHz CPU
6x2GB triple channel DDR3 PC3 12800 RAM (12GB total)
Asus Rampage II Extreme Mainboard
3Ware 9650SE RAID controller
8x250GB SATA II disks (6x250 RAID5 hot swap array + 2 hot spare)
ABS Canyon 695 case
1300W Tagan ITZ series PS
2xSAPPHIRE Radeon HD 4850 Video cards (dual dual DVI cards)
2x HP LP2465 24" LCD monitors
2x HP LP2065 20" LCD monitors

I installed Ubuntu 8.10 desktop x86_64 and all upgrades and I've been running rock-solid with super performance from day 1.

In the event that I need to spin up a Windows XP instance in VirtualBox, I boot a VM in about 15 seconds and can shut it down even faster.

The 4 hyper threaded CPUs in this i7 chip show up as 8 CPUs in Linux:

```
~$ grep -i bogomips  /var/log/dmesg
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5879.99 BogoMIPS (lpj=11759996)
[    0.004000] Calibrating delay using timer specific routine.. 5879.87 BogoMIPS (lpj=11759744)
[    0.004000] Calibrating delay using timer specific routine.. 5879.87 BogoMIPS (lpj=11759754)
[    0.004000] Calibrating delay using timer specific routine.. 5879.87 BogoMIPS (lpj=11759756)
[    0.004000] Calibrating delay using timer specific routine.. 5845.57 BogoMIPS (lpj=11691156)
[    0.004000] Calibrating delay using timer specific routine.. 5879.87 BogoMIPS (lpj=11759740)
[    0.004000] Calibrating delay using timer specific routine.. 5915.95 BogoMIPS (lpj=11831911)
[    0.004000] Calibrating delay using timer specific routine.. 5879.87 BogoMIPS (lpj=11759742)
[    0.976054] Total of 8 processors activated (47040.89 BogoMIPS).

```

Could you run a super_pi and post results?
Lucky *******! :D

---

### Post by srae88 on 2009-02-22
Hi all,

I've been pleased to learn that Linux (Intrepid or later, at least)
seems to be running well on recent ASUS X58 motherboards - provided
they are running pure SATA.  Many thanks to those who have filled in
details regarding the P6T-Deluxe and Rampage II Extreme.

What I haven't seen anywhere yet is any mention of the plain old P6T 
(no "Deluxe") board.  That 88SE6111 controller on the Deluxe makes me
a bit nervous (looks like it handles eSATA), but on the other hand there
seem to be a number of issues with the Realtek network and sound chips
on the vanilla P6T as well.

Anyone out there running a recent release on a (non-Deluxe) ASUS P6T
who might share their experiences  - successes, issues, etc. ?

For that matter, can anyone confirm if eSATA works with the P6T-Deluxe?

Thanks!
Steph

---

### Post by Leo.F on 2009-02-26
Update: tried Ubuntu 9.04 Alpha **4** and still the SAS Drive is not recognized.

Any luck snorkius?

---

### Post by weaktight on 2009-02-26
I've got the P6T Deluxe and was able to install Fedora from the Live CD; however, when I boot up, it says "missing operating system".

Anyone know how to set the BIOS on the P6T deluxe to see the SAS drive on boot?  I only have the single SAS drive and 2 DVD drives.

---

### Post by Leo.F on 2009-03-02
Hello weaktight, just press F8 during POST and select your SAS drive from the available bootable devices list, it'll make it your default boot disk from then on.

What version of Fedora did you install? Was it Fedora 11?

Please keep us posted.

Be Well

> **weaktight said:**
> I've got the P6T Deluxe and was able to install Fedora from the Live CD; however, when I boot up, it says "missing operating system".

Anyone know how to set the BIOS on the P6T deluxe to see the SAS drive on boot?  I only have the single SAS drive and 2 DVD drives.

---

### Post by weaktight on 2009-03-02
I had to change the Storage config from IDE to AHCI in the BIOS and then the OS was able to load off the SAS drive.

I'm actually running sabayon v4r2 now.  Everything worked off of the install.  It even detected my SAS drive without having to fiddle with drivers.

---

### Post by linuxfueled on 2009-04-01
Raid SAS is a no go so far, but you cant beat a 920 @ 4.30GHz stable w/ DVD::RIP 6min transcoding on a 2hr movie

i7 920/2.67GHz @ 4.30Ghz water cooled
12 gigs ram
Ubuntu IDE 7200RPM

---

### Post by oxboood on 2009-05-14
If you are having trouble installing or running the live CD with this architecture try adding this boot option

```
pci=nomsi
```

---

### Post by prgsdw on 2009-05-16
> **r m h said:**
> 
In the event that I need to spin up a Windows XP instance in VirtualBox, I boot a VM in about 15 seconds and can shut it down even faster.


This is about ~20% faster (18 seconds) than it takes to spin up a Windows XP Pro instance on my Opteron 185 dual core system (2.6 gigahertz / core, 1mb L2 cache / core + 4 gig DDR400 RAM). I was curious as to a point of comparison.

---

### Post by balddogger on 2009-08-10
i am running 9.04 on a studio xps 435mt, no problems.  virtual box w/ a vista guest os, itunes (USB and Audio).

---

### Post by ManFromMars on 2009-09-17
Has anyone had any bad experiences with overclocking (stability-wise)? I installed 9.04 on a vanilla core i7 920 setup and all was going well, then overclocked to 3.8GHz, still all seemed fine... managed to screw my graphics drivers and after reinstall things seemed to be going awry. Trying to reinstall Ubuntu I had various problems - sessions spontaneously logging out straight after log-in, a couple of failed installs (installer hanging at various percentage completes). I'm now running at 3.4GHz and it seems much happier with me, no problems whatsoever so far... seems a bit odd, but I'm not experienced with overclocking so I don't know what the usual problems are.

---

### Post by kaibob on 2009-10-05
I need a new computer, and I'm considering one with an Intel Core i7 or i5 processor. I wondered if anyone has had any problems running this processor with Ubuntu. I will purchase a stock computer--probably one of the new Dell Vostro 430 mini-towers. 

BTW, I searched the forum on i7 and got no hits and searched on Intel i7 and got too many. Apparently the forum doesn't recognize i7 (perhaps too short).

Thanks for the help.

EDIT:

Well, I just found another thread on the i5 processor. One of the Ubuntu developers commented that:

> I just bought one [an Intel Core i5] and will get it sometime next week so hopefully I can manage to make it work. I doubt it will work on anything other than karmic if it does work at all.

[http://ubuntuforums.org/showthread.php?t=1258912&highlight=intel+core](http://ubuntuforums.org/showthread.php?t=1258912&highlight=intel+core)

This doesn't sound good :(

---

### Post by AppleBonker on 2009-10-06
I don't have any experience with the i5 750, but I'm running the i7 860 (they're both lynnfield architecture) without problems.  I haven't tried the karmic beta on my desktop yet.  I'm toying with karmic on my laptop, but running jaunty for the time being on my desktop.  The only major issue I've seen so far is lm_sensors doesn't function with the lynnfield cpus (at least as far as I can tell right now).  I've been perfectly stable for the last two weeks or so running this setup.  Any more specific questions, let me know.

---

### Post by kaibob on 2009-10-07
AppleBonker. Thanks for the response. I don't want to risk getting something incompatible with Ubuntu and don't really need a fast processor, so I decided to buy a computer with a Core 2 Duo processor. This will save me some money as well. Thanks again.

---

### Post by Morten ML on 2010-04-23
Hi all

I know this is a bit late. But this is for anybody still worrying whether or not ubuntu supports i7. 
There is no problem there. 

I am running Ubuntu amd64 9.10 on I7 960 with the asus P6T Deluxe motherboard and having no problems whatsoever. I am not sure about the turbo boost though but i will look into it.

---

### Post by xandercage17 on 2011-03-09
Delete My account

---

### Post by fjgaude on 2011-03-09
> **kaibob said:**
> AppleBonker. Thanks for the response. I don't want to risk getting something incompatible with Ubuntu and don't really need a fast processor, so I decided to buy a computer with a Core 2 Duo processor. This will save me some money as well. Thanks again.

Gosh, I had a Core 2 running at 4.0GHz and now have an Intel i5-655K running at the same speed. The i5 is so much quicker because of the multi-thread features. It's amazing to simply watch, with all four threads doing their thing!

---

### Post by jjonnynitro138 on 2012-01-11
I hope this helps. I am using the MSI P67A-c43 motherboard and the i7 with Ubuntu11.10. The system works very very well, I have no complaints, the sound graphics and overall system is a super fast and strong system, I highly recommend using these two together, they merge like ice cream in a cone. Plus (not to be an advertiser) I would check out tigerdirect.com for components at a better price.

---

### Post by JRV on 2012-01-11
I have a i7 920 in a EVGA X58 SLI motherboard with Ubuntu 10.04.
It runs great, my only complaint is that it is very slow to POST.  Once it is done POSTing it boots fast, and runs great.

---

### Post by haemphyst on 2012-02-09
JRV...  I seem to have the very same issue.  I have the same board, but the i7 930 CPU, and 24GB RAM in triple channel mode.  Running 64-bit 11.10 takes FOREVER to boot.  Can anybody shed any light on this?

Also...  for anybody thinking about an OCZ RevoDrive?  (Newegg part number: N82E16820227661)  I have the 240GB X2 and even in stripe mode, Ubuntu sees it natively as a 240GB hard drive, and NOT an SSD.  Striaght up - O. M. G.  Can you say "so fast, it does all my work without me even asking"?  Dual boot with Win7, I have the Windows swap file on the three-drive Velociraptor RAID on the ICH10R, which I still can't make Ubuntu see.  Truly bumming me out, because I want to make WoW and LoL run in Ubuntu, and those installs are on that array.

Oh, crap...  Never mind.  The Velociraptors are native SATA drives, NOT RAID.  The RAID is Windows software RAID, not even the ICH10R fakeRAID.  LOL  I *just this very second* remembered that.  The BIOS cannot boot from the RevoDrive, AND support the RAID functions of the ICH10R controller.  Oops.  I am a moron, my name is deese guy!  :lolflag:  Please forgive my stupididity.  (or my brain fade...)

Anyway...  It's still slow to boot, but insanely fast once running.  Can we check anything on that?

---

### Post by Kiyamudeen on 2012-02-11
Using Ubuntu 11.10 on a laptop with Intel Core i7 720QM here... No problems at all... everything works fine, no lag or anything of the sort..

---

