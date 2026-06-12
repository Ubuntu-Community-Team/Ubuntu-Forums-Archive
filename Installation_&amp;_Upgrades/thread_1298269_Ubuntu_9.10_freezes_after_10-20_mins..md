---
title: "Ubuntu 9.10 freezes after 10-20 mins."
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by gbrethen on 2009-10-22
OK, I have installed Ubuntu 9.10 Beta twice, did the update to get latest packages.  After approx 10 - 20 minutes, the system freezes.  I am unable to do anything.  I can't even get to a console.  I have to do a hard reboot.

Also, wireless - when downloading updates, only getting about 40 kb/s.  Now on my Ubuntu 9.04 system, I get upto 5 - 10 mb/s.

Is anyone else getting the freeze problem?

---

### Post by gbrethen on 2009-10-23
anyone?  Any Ideas?

---

### Post by gbrethen on 2009-10-24
Installed the RC and no difference.  System still locks up after approx 10 - 20 mins.  Can't do anything but a hard reboot.

Toshiba A505-S6965
Ubuntu 9.10 - 64bit

---

### Post by xflow on 2009-10-25
I also have this problem. I have to start gnome in failsafe mode.

---

### Post by TheFounder on 2009-10-25
> **xflow said:**
> I also have this problem. I have to start gnome in failsafe mode.

I have to do the exact same thing.. now it runs fine in Gnome Failsafe... and it runs fine in KDE ... and Xfice.. but Gnome standard... that thing freezes on boot...  I can't even get the mouse to move... meaning I don't even know where to start to try to submit a bug.. mostly because the computer bricks at that moment...

Also worth noting,  my transfer rate also hits the toilet... only when using Gnome standard...  transfer rates using any other interface are fine...

This is a bugger.. because I have no freaking idea what transfer rates have to do with the interface... but I can duplicate this problem without fail.

---

### Post by Sef on 2009-10-25
What are your system specs?

---

### Post by jennyjenny on 2009-10-25
I get the same behaviour...

AMD64
Delta66 sound card
2GB RAM
500 GB  drive
ubuntu 9.10  *with issues from trying to get Pulse to work,and (foolishly!) hitting that "partial upgrade" option.

---

### Post by will22 on 2009-10-26
I have upgraded to 9.10 on my dell dimension 4600.
It freezes right after log on. Previous versions were working fine...

I hope that final release will work for me

---

### Post by xflow on 2009-10-26
System specs using lshw:

  description: Computer
  width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2005MiB
     *-cpu
          product: Genuine Intel(R) CPU            2160  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.2
          serial: 0000-06F2-0000-0000-0000-0000
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fea80000-feafffff ioport:dc00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fea40000-fea7ffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fea38000-fea3bfff
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d880(size=32)
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d800(size=32)
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d480(size=32)
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d400(size=32)
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fea37c00-fea37fff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:e000(size=4096) memory:feb00000-febfffff
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:01:05.0
                logical name: eth0
                version: 10
                serial: 00:18:37:02:8c:b9
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.64 latency=64 maxlatency=64 mingnt=32 multicast=yes
                resources: irq:20 ioport:e800(size=256) memory:febffc00-febffcff
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GSA-H50L
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                serial: [HL-DT-STDVD-RAM GSA-H50L1.0007/01/29
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:d080(size=8) ioport:d000(size=4) ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
  *-scsi:0
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=usb-storage

---

### Post by Shawn Reist on 2009-10-26
I have been trying to install 9.10 RC x64 on my computer.

MSI K8N Neo4 (MS-7125) motherboard
AMD Athalon 64 3000+ processor
1 Gig Ram
Samsung SP1213C 120 gig SATA


I have found I can't run the live CD for 9.10 RC.  just after the desktop starts to show the system freezes. have to do a hard reboot.

I managed to run the install from the Live CD but when I reboot the computer the system freezes after the Ubuntu start sound and then I have to do a hard reboot. 

I can't do a safe/recovery mode.. I get red line across the screen and I can make out Press CTRL-D to reboot.

can't do anything, too green for linux...

any assistance would be nice or I have to reinstall 9.04 which I know runs or possibly 8.04 LTS

Tried the alternate build have some logs even with an attempt at a daily build system froze after start-up.

---

### Post by gbrethen on 2009-10-27
ok, so where do we go from here?  Has anyone else tried KDE with success?  can we narrow this down to a gnome issue?

---

### Post by sgelsot on 2009-10-27
Same problem here mouse moves but system freezes. If computer is left alone and scrrensaver comes on no sign of mouse, have to hard restart. While using computer system will freeze and screensaver  wont come on but will be able to move mouse. Tried removing compiz from package manager, no luck. dell sx260 with pentium4 and intel graphics.

---

### Post by kenden on 2009-10-29
I have the same problem (X freezes, but not the mouse) since upgrading to 9.04 and now still in 9.10...

Have a look in those two pages, it might help :
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

[https://wiki.ubuntu.com/X/Bugs/IntelDriver](https://wiki.ubuntu.com/X/Bugs/IntelDriver)

---

### Post by gbrethen on 2009-10-29
ok, according to the info from the link, when the caps lock key blinks, then this is a kernel failure!  So mine must be a kernel failure.

What next?

---

### Post by yester64 on 2009-10-31
actually, after i installed everything the panel frooze. I was able to do anything else but werent able to click anything from the panel.
weired....

now it works again. perhaps random freeze.

---

### Post by rp3 on 2009-10-31
> **gbrethen said:**
> ok, according to the info from the link, when the caps lock key blinks, then this is a kernel failure!  So mine must be a kernel failure.

What next?

Same Here

Toshiba A305 laptop.  9.10 AMD64 release.

Fresh install, worked fine, rebooted once all.  

I configured my linkstation (SMBFS, CIFS) and updated fstab.

Reboot, cap lock key flashes.  I saw once some message about CIFS so I commented out those lines in the fstab, to no avail.  I am not sure how to remove smbfs when I can't get the system to run :)...

I can boot from live cd just fine, so it has to be something I 'turned on'.  I also enabled the restricted driver for the ATI card as well..  Not much else...

I just noticed that my GRUB screen never appears?  It flashes and just goes away so I can't even try a 'failsafe' boot...hmmmm


Oh well...

*** UPDATE ***

Ok I figured the grub thing out, if you hold down the Shift key you get the menu, so no problem there.  I have been able to get the machine (Toshiba Laptop A305) with no issues.  It seems to be the restricted driver for the ATI card is the issue that is causing the Kernel Panic (Flashing Caps Lock Key).  I have reloaded a couple times, and have decided it's not SMBFS (CIFS), or any other things.  As long as I don't update that restricted driver it seems to be just fine.  Sound works well too. Wireless does seem to be slow but only for UBUNTU stuff/updates?  I can assume it's due to demand, etc..  As I did a quick Torrent download and it seems to be going at close to normal speed.

So for now it is working, and I am happy...

---

### Post by billv6 on 2009-11-01
I've had the same problema here, system freezes about 10 seconds started... :(

Someone found the fix for the problem?

Here is my hardware:

description: Motherboard
       product: PW-945GCX
       vendor: PCWARE

description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012 (04/02/2008)
          size: 64KiB
          capacity: 448KiB

description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: CPU 1
          size: 1203MHz
          capacity: 1203MHz
          width: 64 bits
          clock: 200MHz

Thanks!!!

---

### Post by yester64 on 2009-11-01
acutally my freeze is gone. Could not tell why, its just gone and the system works now. weird.:confused:

---

### Post by kaarecc on 2009-11-01
i'm also having freeze problems on my Dell Latitude 620with core 2 duo t5600, 2 gb ram, intel graphics, broadcom network, intel PRO/Wireless 3945ABG wifi

IT hits randomly, everything freezes, can't move mouse etc. have to do hard reset. I have tried both ubuntu 9.10 and kubuntu 9.10. same thing as to freezes

When it stops responding, there are small blue lines on the screen, like the contours of a window about to be opened or moved.

regards

Kaare

---

### Post by aris.petridis on 2009-11-02
I am having the same problem and can provide a bit more detail. My laptop is a pretty old one - Toshiba A45 S151, P4 2.8GHz, 1GB ram etc.

I was running kubuntu since 8.10 and then gradually upgraded to 9.04 - up to that point everything was fine. When I went to 9.10 I started getting freezes at random times - like most people said on this thread usually 10-20 minutes after booting on average... but it could be 2 minutes after booting as well sometimes.

After this, I decided to dump the whole kubuntu 9.04 system and downloaded and installed ubuntu 9.10 hoping that it might have been something I had set up over the last 6 months or so or something specific to 9.10 kubuntu distro. At first I went 20-30 minutes without a freeze so thought it got fixed but it didn't turn out to be the case. Sure enough I got another freeze. And then another one.. etc...

The freezes seem to be just X crashing as mouse still moves, hard disk seems to have activity and I think everything else seems to work in the background. Sometimes if I am playing something on VLC, the picture freezes but the sound of the vid keeps playing.

HELP! :)

A.

---

### Post by aris.petridis on 2009-11-02
Found this in the ubuntu bugs (launchpad):
[INDENT]I found a workaround to this issue for those of you who have an intel graphic card (which is what HP Pavillion PCs come with).
you must revert to an older version of the graphic card driver by following these instructions:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
The instructions were intended for Jaunty but they also work for 9.10
Of course, since the system hangs, you need to start in recovery mode to run those instruction from the command line.
[/INDENT]

Seems to be a problem that a lot of people with Intel graphics chipsets are having. Will try it this evening when I get home. Hope it helps everyone.


A.

---

### Post by gbrethen on 2009-11-03
how about issues with the ati graphics cards?  does it work without the proprietary driver?  Has anyone had success with ati graphics/compiz on 9.10?  without the kernel freezes?

---

### Post by to3000 on 2009-11-04
i tried installing nvidia-kernel-common

its worked so far

---

### Post by gbrethen on 2009-11-05
ok, I just did a fresh install of ubuntu 9.10 again.  I did not install the proprietary ati driver, and still the system froze (kernel panic
) caps lock blinks.  I had to do a hard reboot.  The only thing I had done was open firefox to browse internet when it froze!

Any ideas?

Toshiba A505-S6965, ATI Mobility Radeon HD 4570, Intel Core 2 duo P7350

---

### Post by aris.petridis on 2009-11-06
The procedure described in the link I've pasted in my previous comment worked for me! No more freezes!

Hope it works for other people too.

A.

---

### Post by razorxpress on 2009-11-09
Same problem here. I installed fresh copy of ubuntu 9.10 on intel 845 with cpuinfo 

vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.40GHz
stepping        : 9
cpu MHz         : 2399.413
cache size      : 512 KB
MemTotal:        2053640 kB             
MemFree:         1075600 kB 

When i run ubuntu for some time it freezes. There is no specific software that would cause that, because on any instance it would freeze. Sometimes even booting. The frequency of freezing was too high so i removed ubuntu-desktop and installed kubunt-desktop. After that the frequency has removed by greater extent, but still there are some instances of freezing. I previously submited a problem from totem but i don't know what is causing the freezing. This instance of kubuntu does not contain any application from gnome.

---

### Post by openBA on 2009-11-10
very similar problem here. Small apps are working, big one, like Firefox not. 

 [http://ubuntuforums.org/showthread.php?p=8278204#post8278204](http://ubuntuforums.org/showthread.php?p=8278204#post8278204)

Thinkpad R51 ATI Radeon M 9000 RV250

As it freezes, it produces very big log file, so even "ubuntu-bug" fail forwarding it.

---

### Post by QueenZ on 2009-11-10
Same problem here. My keyboard and mouse freezes after a while.. This is hapening all over the qorld in all new versions of linux!

---

### Post by sgelsot on 2009-11-10
> **aris.petridis said:**
> Found this in the ubuntu bugs (launchpad):
[INDENT]I found a workaround to this issue for those of you who have an intel graphic card (which is what HP Pavillion PCs come with).
you must revert to an older version of the graphic card driver by following these instructions:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
The instructions were intended for Jaunty but they also work for 9.10
Of course, since the system hangs, you need to start in recovery mode to run those instruction from the command line.
[/INDENT]

Seems to be a problem that a lot of people with Intel graphics chipsets are having. Will try it this evening when I get home. Hope it helps everyone.


A.

That was it for me thanks very much OP!

---

### Post by gbrethen on 2009-11-15
any updates for people using ati drivers?  or is there an updated kernel?

---

### Post by druid99999 on 2009-11-17
> **sgelsot said:**
> That was it for me thanks very much OP!
Rolling back to the 2.4 intel video driver seems to have worked here as well.

---

### Post by gbrethen on 2009-11-18
upgrading the kernel to 2.6.31-15-generic seems to have solved my problem!

---

### Post by GnEeErKd on 2009-12-09
I have an OCZ DIY laptop with the nvidia geforce 8600 GT, core 2 duo, and upgraded from 9.04 to 9.10

My system was doing a similar freeze (everything still displayed, no cursor movement or keystrokes, hard shut down required to continue) randomly every couple of days. After looking into it, I found that for some odd reason 1) firefox would spontaneously start using sick amounts of CPU power, which in turn heated up my CPU and 2) my cpu fan never turned on to cool it back down...

I have reinstalled firefox to try and calm it down, and enabled my fan control using [http://ubuntuforums.org/showthread.php?t=1297008&page=5](http://ubuntuforums.org/showthread.php?t=1297008&page=5)

Hasn't frozen since, but I will post if it does again

---

### Post by GnEeErKd on 2009-12-11
False hope, computer froze again last night and my CPU temperature was nothing above normal, now I am monitoring my video card temp to see if it is possibly related to that instead...

---

### Post by fracan on 2009-12-11
Rolling back to 2.4 driver worked for me too, but now I can't enable Compiz. Any ideas?

---

### Post by Spooky257 on 2009-12-11
> **gbrethen said:**
> ok, so where do we go from here?  Has anyone else tried KDE with success?  can we narrow this down to a gnome issue?

Tried kubuntu 9.10 with the same results. Freezes after 10-20 minutes.  This happens on both my Dells with both Gnome and KDE.  Optiplex GX150 & Dell Dimension 2400.

---

### Post by GnEeErKd on 2009-12-12
I have NVIDIA drivers 173 and 185 available, Im going to try rolling back to 173 and see how long it takes to freeze, I'm glad mine isnt 10-20 minutes...its just completely random every couple days or so

---

### Post by Spooky257 on 2009-12-16
> **Spooky257 said:**
> Tried kubuntu 9.10 with the same results. Freezes after 10-20 minutes.  This happens on both my Dells with both Gnome and KDE.  Optiplex GX150 & Dell Dimension 2400.

4 days ago I ran the work around found in post #21 of this thread and I have not experienced a single freezing issue since.

Thank you

---

### Post by kinemagician on 2009-12-25
I am having the same problem!
My hardware is the following:
AMD Athlon 2600+ 1.5 Gb RAM
Nvdia GEFORCE4 MX400 VBIos 04.18.20.38.05

I noticed that the CPU load is very heavy (90%), although only the browser is opened.
Does UBUNTU 9.10 suffer the same disease of Vista (i.e. sucks CPU
without doing nothing)?

These serious pitfalls do not encourage the spread of 
UBUNTU among desktop users.

---

### Post by GnEeErKd on 2009-12-25
I went into hardware drivers and went back to the 173 nvidia driver instead of 185 and it hasnt frozen since...i think that did it for me, give it a shot?

---

### Post by mdeschane on 2009-12-25
I just installed 9.10 Remix on my EEE PC1000HE. The install hung on configuring apt and installing language packages, I skipped them and the install seems to have proceeded ok without them. I suspect these were instances of the default source being server bound as I have noticed on my 8.xx systems, I reconfigured them to pull from another server (mirror.anl.gov) and the download rate went from ~4K/s to ~400K/s.

It is great to see that evolution is better behaved in 9.10 than it was in previous versions with configuration windows hanging inaccessibly off the bottom of the screen and some calendar functions do a great impression of frogger. I was forced to use Thunderbird on my 8.xx install which is ok but not as well integrated or feature rich as evolution.

But it is disappointing to see that the network manager tool is still brain dead. It wants to auto configure my wifi as an ad hoc network and just doesn't work when I reconfigure it correctly, still working on this one. 

Bluetooth works out of the box, yippee!

I haven't figured out the "pam authentication failure" when I do su - yet either.

No complaints (except network manager), still working my way through the upgrade potholes.

---

### Post by chrisjomarmayor on 2010-01-13
[SIZE=2]For those with ATI Drivers:

Since yesterday I've been having problems because of the occasional freezing of Ubuntu 9.10. I've tried all the advices from this thread. But still the freeze still occurs after 10-20 minutes. I tried to look for some updates from Synaptic Package Manager: **xorg-driver-fglrx-dev**  it's just a development file for the driver accelerator, I really don't have an idea how it fixed the freezing but, for about an hour and a half my system does not freeze or crash. I'm not sure if this does fixed it, but this is what I updated after the last crash/freeze I had today. I hope this works for others, and hope that someone could explain how it fixed the problem(if ever it really fixed the problem). [/SIZE]

---

### Post by spants on 2010-01-21
_[chrisjomarmayor]("http://ubuntu-ky.ubuntuforums.org/member.php?u=996147")_: Has your system frozen since you updated?

I tried what you suggested and it's still freezing.

---

