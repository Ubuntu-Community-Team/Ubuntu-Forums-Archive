---
title: "Cannot resume from suspend Ubuntu 10.10"
date: 2010-10-14
forum: Hardware
---

### Post by Roby86 on 2010-10-14
Cheers,

Here's the problem, my Ubuntu 10.10 can't wake from standby/suspend, there is just blank screen and nothing happens, only forced shutdown takes it down.

I have laptop Toshiba Satellite A210-128, and Ubuntu is installed on external hard drive(Seagate FreeAgent 2.5' 500 GB).

Other than that, everything works great. :) Please help!

Thx in advance! :)

---

### Post by dabl on 2010-10-14
I'm not sure what you're trying to do is possible.  Doesn't that external drive get its power from the USB connector?  Is the USB connector powered on while the computer is hibernated?

---

### Post by odysseus2k7 on 2010-10-14
> **Roby86 said:**
> Cheers,

Here's the problem, my Ubuntu 10.10 can't wake from standby/suspend, there is just blank screen and nothing happens, only forced shutdown takes it down.

I have laptop Toshiba Satellite A210-128, and Ubuntu is installed on external hard drive(Seagate FreeAgent 2.5' 500 GB).

Other than that, everything works great. :) Please help!

Thx in advance! :)

I'm getting the same problem running 10.10 on my Toshiba NB305 from the internal HDD.  It's very annoying; so far the only option I've found is shutting it down every time I put it away.  Has anyone else noticed this problem?  Have you found a workaround or patch for this?

Thanks,:guitar:

---

### Post by Roby86 on 2010-10-14
Hmm dabl, I haven't thought of that to be honest, that may be the main problem. Yes, external usb disc is powered with one USB port, but this laptop don't have possibility to power USB devices while in standby. Thx for advice, I think that I can handle without standby. :)

---

### Post by dabl on 2010-10-14
> **odysseus2k7 said:**
> I'm getting the same problem running 10.10 on my Toshiba NB305 from the internal HDD. 

Are you trying to do "hibernate" (Suspend to Disk) or "sleep" (Suspend to RAM)"?  I have a Tosh NB205 with aptosid installed, and KDE, and it does not appear to have any problem with either S2RAM or S2Disk.  If you are trying S2Disk, then you do need a swap partition that is about as large as your memory.  For S2RAM, you shouldn't need anything special.

I'm a KDE user, but somewhere in your Gnome desktop are configuration settings for "powermanager" or "power devil" or whatever they call it -- better check and see what it is set to do when you "sleep" and/or "hibernate".

---

### Post by pizzystrizzy on 2010-10-14
Yes, same exact problem on my HP HDX 16.  The computer will not wake up from either suspension or hibernation.  I really hope this bug gets fixed sooner rather than later..

---

### Post by rohrbach on 2010-10-15
> **pizzystrizzy said:**
> Yes, same exact problem on my HP HDX 16.  The computer will not wake up from either suspension or hibernation.  I really hope this bug gets fixed sooner rather than later..

I ve got the same problem on workstation - Asus P5Q Deluxe motherboard and Nvidia 8800 graphic card. Before Ubuntu 10.10 everything was OK on previous Ubuntu editions. This is not Ok this is downgrading of distro

---

### Post by Cole119 on 2010-10-15
I have this problem, too. I'm using an Asus N61Jv laptop with nVidia GeForce GT 325M graphics.

---

### Post by phelin4 on 2010-10-15
I have a Sony Vaio VPCCW1S1E and with Ubuntu 10.10 I cannot resume from suspend anymore. With 9.10 and 10.04 it worked as supposed to, but no more. I did try the fix presented in a thread here which suggested using boot parameter acpi_sleep=nonvs. That does prevent the laptop from rebooting, but makes it unusable after resume in any case.

---

### Post by yanaek on 2010-10-15
no  good
i cannot resume after suspend on my MSI Wind U100
on 10.04 resume worked flawlessly
so who broke what in new release and why

maybe we need to tell ubuntu to unload some modules in /etc/default/acpi-support ?

---

### Post by yanaek on 2010-10-15
well it has something to do with wireless network drivers

i get kernel panic message and some complains about modules r8180 , r8187se (funny thing, because i don't use it), and some complains about re-adding existing pci device

---

### Post by faden on 2010-10-15
The same here with Samsung N220 plus (Marvel) Netbook.
After wake up from sleep screen remains black although blue power and wlan led's are lit again. While sleeping only the power led blinks.
Wake up from hibernate seems to work fine...

NB: Standard configuration, no special hardware. Any help appreciated.

---

### Post by rkylain24 on 2010-10-16
Same problem Dell Latitude D600

---

### Post by Muster Mark on 2010-10-16
similar issue on dell latitude E6510 with nvidea chipset.  sometimes it wakes up fine, sometimes it gives nothing but blank screen.  when it gives nought but a blank screen, the power LED stops pulsing and assumes its 'on' mode and the wifi LED comes on, so something is waking up, but not the screen.

It's a good thing ubuntu boots quickly.

---

### Post by goonix on 2010-10-16
Same problem on a HP Pavilion dv3-2230ea with nVidia  GeForce G105M .

---

### Post by Covi on 2010-10-16
Same problem here: M4A89GTD Pro USB3 / nVidia GTS250 / HDD Maxtor SATA1 160G / USB 2.0 external multimedia disc connected or disconnected (doesn't matter).

- Problem: Resume outputs a **black screen with just a cursor waiting**. I must restart from power button.
* Logs (powersave and suspend) seems ok.
* 8GB of swap and 8GB RAM.

- Reproduce:
-- Wait to, or press "Suspend" in panel power menu.
-- Wait for complete suspend state.
-- Move mouse to resume and... black screen, keyboard numpad seems works but system don't receive any signal, I can't write, restart... and cursor still in black screen waiting for.

Virtual consoles runs but I can't write, keyborad through USB; I think not but... maybe this is the problem?
MA4GTD have no PS/2 connection for keyboard.
:(

Edit: Ups... and audio is deactivated: PulseAudio problem?
Log seems ok:
```
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
```

PS: Plz, excuse my poor english.

---

### Post by Worp8d on 2010-10-17
Same problem here, Asus N61J, ATI Radeon HD 5730.  Can't resume from either a suspend or hibernate, have to do forced shutdown.

---

### Post by beric on 2010-10-17
Same here. HP dv9000 Nvidia chipset.

The only suspicious log message I can see is 
 ACPI handle has no context!
I get no kernel panic.
It seems that the kernel is doing it's job and by taking a look at pm-suspend.log I can guess that even acpid finished it's resume procedure   it says "finished" .

Maybe nouveau?

---

### Post by johanPO on 2010-10-17
Same here on a Belinea 1320.

Can not see anything in the log file that reveals what causes the freeze. Worked perfect in 10.04

---

### Post by sgosnell on 2010-10-17
Install the package 'hibernate' from the repositories.  That seems to make suspend work properly.  Why it is not included by default I have no idea.  I found it through a search on Launchpad.  It's available there, but it's also in the Maverick repositories.

---

### Post by StickAForkInMe on 2010-10-17
Same problem here on a Sony Vaio SZ2HP. Suspend to disk used to work fine on 10.04 but since upgrading it just freezes when trying to resume again, it just stays on the Ubuntu loading screen and requires a reboot to get it to work again. :(

---

### Post by Strawp on 2010-10-17
Same issue here. Dell Inspiron 6400.

The last time I had some error messages appear on the screen about btusb - don't know if it's related or if I should have left something in modprobe from before the upgrade but I assume it's having an issue dealing with the bluetooth hardware I have on an internal USB connection.

A real shame this - I was marvelling at the excellent power management in 10.04 before the upgrade.

---

### Post by johanPO on 2010-10-17
Thanks, but unfortunantly that did not do the trick

---

### Post by Strawp on 2010-10-17
> **sgosnell said:**
> Install the package 'hibernate' from the repositories.  That seems to make suspend work properly.  Why it is not included by default I have no idea.  I found it through a search on Launchpad.  It's available there, but it's also in the Maverick repositories.

Fantastic, this seems to replace the default hibernate functionality with something that actually works.

---

### Post by yanaek on 2010-10-17
anyway it's not a solution for our problem with suspend

after resume i get those messages (in a loop, many of them per second)

r8180 ..blabla.. WW:nic has lost pointer

i think the problem lays in kernel, or in general - which version is used and how it's configured in 10.10

---

### Post by mordoc on 2010-10-17
I can't find it, but several versions ago my wifi card could not be shutdown prior to a suspend or hibernate while it would try to enter the mode it would not awake.  The fix was some sort of blacklist for the driver to tell power management to modprobe remove it and then on awake restart the driver.

---

### Post by sgosnell on 2010-10-17
I had the same problem with the 2.6.34 kernel with Maverick.  That kernel suspended without issues in 10.04, so I don't think it's the kernel.  Installing the new hibernate script, which also does suspend, fixed the problem for me, as far as I can tell.

---

### Post by Worp8d on 2010-10-17
I just installed package hibernate and it didn't fix the (suspend) problem.  

When the computer goes into suspend and I bring it back out the password sign appears, I enter the password and then the desktop appears but the wireless network has been dropped.  The screen then goes black again and the computer is frozen.  Hence it seems that (for me at least) the solution will be something like what mordoc suggested.  Haven't found find it yet, but the problem does seem to be a [common one]("http://brainstorm.ubuntu.com/item/94/").

---

### Post by Worp8d on 2010-10-17
Found a [blog post]("http://anarchocyclist.ca/2007/11/16/suspend-and-hibernate-on-ubuntu-gutsy/") from a while ago detailing a very not-lazy attempt to fix the problem, the conclusion of which was:

> Ok, now that i’ve spent an hour running through all possible solutions and they all didn’t work, i decided on a whim to try a different kernel and it worked. I was using the ubuntu kernel package for version 2.6.22-14-generic and it would never suspend to ram, and once i switched back to the slightly older 2.6.20-16-generic then everything worked just fine

So it's a kernel issue?  10.04 worked fine for me while 10.10 which has a new kernel doesn't.  Makes sense and also makes me despair of doing anything but waiting for an update to fix the problem.  I'm simply setting the power management options all to "blank screen" rather than hibernate/suspend.

---

### Post by Dans564 on 2010-10-18
same problem here:
mb: p7p55d evo
cpu: i5-760
ram: 4gb
swap: 8gb (overkill i know)
hd: 1.5tb
ubuntu ver.: 10.10
kernel: 2.6.35-22-generic-pae

---

### Post by knuton on 2010-10-18
Same problem with my Samsung N210. The `hibernate` package did not change anything for me. It worked fine using 10.04.

---

### Post by naskopopov on 2010-10-18
Hi, 
Same problem here - laptop hp4310s. 

Adding SUSPEND_MODULES="xhci" to /etc/pm/config.d/unload_module fixed it for me.

Cheers

---

### Post by gesquive on 2010-10-18
You can find more info in [this thread]("http://ubuntuforums.org/showthread.php?t=1586178&page=2") and [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656631"). But the following worked for me on my  Dell Latitude E6510 (Intel Core i7-720QM, 4GB RAM, NVIDIA NVS 3100M) running 10.10 64bit:

Use the editor of your choice to edit /etc/default/grub
```
sudo nano /etc/default/grub
```

next, change
```
GRUB_CMDLINE_LINUX=""
```
to
```
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"
```

then run:
```
sudo update-grub
```

After restarting, I can now suspend without any problems again.

---

### Post by RiffRaff06078 on 2010-10-18
> **naskopopov said:**
> Hi, 
Same problem here - laptop hp4310s. 

Adding SUSPEND_MODULES="xhci" to /etc/pm/config.d/unload_module fixed it for me.

Cheers

Same problem.  Toshiba Satellite L305D AMD Athlon X2 64-bit with 4 GB RAM and ATI Radeon video chipset.  Running 64-bit version of Meerkat.

Very disappointing, Ubuntu! For the first time since version 6 I went in search of other distributions.  You guys need to get some of the basics back under control and leave the eye candy alone.

The above quoted fix may have worked for me.  Problem is my resume issues seem to manifest themselves after I've used the system for some hours, and I tested this after only a few minutes of uptime.  I'll re-post after I test it at work tomorrow.

---

### Post by Muster Mark on 2010-10-19
I have had success on my dell latitude E6510 by simply using an older kernel.  Booting with 2.6.32-25-generic-pae, everything works fine; if I use 2.6.35 it will not work after about the third time.  I think it has to do with the proprietary graphics drivers (working for the first few times is pretty strange though).  I will try gesquive's GRUB fix though, and see if that works with the latest kernel.

---

### Post by gesquive on 2010-10-19
Yeah, I should have stated earlier. I am running the latest (2.6.35-22-generic) kernel. The previous version did not need the fix.

The nonvs fix made my suspend work the same way it did in the previous kernel.

---

### Post by yanaek on 2010-10-19
> **naskopopov said:**
> Hi, 
Same problem here - laptop hp4310s. 

Adding SUSPEND_MODULES="xhci" to /etc/pm/config.d/unload_module fixed it for me.

Cheers

suspend/resume now works after this FIX on MSI wind U100
thanks a lot ;)

BUT, if i make the second patch (changing kernel options) it's NOT working - so remember, for MSI Wind U100 only one patch fixes the problem, two of them NOT

---

### Post by knuton on 2010-10-19
Neither naskopopov’s nor gesquive’s fix worked for my Samsung N210. Still, thanks for sharing!

---

### Post by Sunflower1970 on 2010-10-19
Thought I'd just add to the woes here. Thinkpad R40, tried all fixes in this thread and throughout the forum and nothing worked. Didn't work on 10.04 either. Don't really want to go back to 9.10, but might have to....

---

### Post by dh390 on 2010-10-19
I had a similar problem on my Averatec 7170 when I was running it off the CD. And I experienced a similar problem while trying to finish the install on to the internal harddrive. Both times I had to force a full power down by holding down the power button. This was with the 64 Bit version of 10.10
 
Now after the last time I can't turn on my laptop. I have pulled the power cord & batt, removed the DVD+RW drive, memory & wi-fi card. The only thing left is to open the laptop up & pulling the cmos batt.

---

### Post by ABaconBusAflame on 2010-10-19
Damn, I thought I had it fixed earlier but once again I'm stuck with a blank screen after I open my laptop's lid and try to bring it back from suspend. (I have a HP tx2000 laptop and am running Maverick.) I've tried both jesquive and nopopopov's solutions and neither worked.

EDIT: For some reason, every once and a while suspend actually works normally. Then I restart my laptop to see if the problem is permanently fixed and then things bugger up again. I have a sneaking suspicion that it might have something to do with my video card drivers. (I have an HD 3200 and I'm using the proprietary drivers.)

EDIT #2: I think the problem might be related to using suspend too soon after logging in. I'm still doing some testing.

---

### Post by beric on 2010-10-20
Switching from nouveau to NVidia's proprietary driver seems to  solve the issue for me.

---

### Post by djsimmonds on 2010-10-20
hi, i also had this problem after upgrading from 10.04 to 10.10, whereby the screen remains off when trying to resume from suspend. i have a dell mini 1012. i tried all the solutions (install hibernate, suspend_modules="xhci", and the grub one), none of those worked - although, strangely, the xhci one seemed to do something (the screen turned on for a few seconds and some code flashed that i couldn't see, before turning back off). what did work was using the older kernel (.32 instead of .35), although i still briefly see a few lines of code before the password box appears, which i never did in 10.04. hope this helps someone.
dani

---

### Post by naskopopov on 2010-10-21
Could you please check your kernel log for 

```

[ 80.559102] EXT4-fs (sda1): re-mounted. Opts: commit=600
[ 80.942445] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe
[ 80.942452] ata2.00: irq_stat 0x40000001
[ 80.942457] ata2: SError: { PHYRdyChg }

```

or similar errors. I feel the problem is somehow related with this one :

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/610055]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/610055")

---

### Post by sunil.rana on 2010-10-22
I have the same problem with my HP DV 5 series.
Hope this get fixed soon.
Thanks

---

### Post by Eugenian on 2010-10-22
Same problem on my Dell Latitude D600 running 10.10 off internal HD (dual boot w/XP).

---

### Post by knuton on 2010-10-22
> **naskopopov said:**
> Could you please check your kernel log for 

```

[ 80.559102] EXT4-fs (sda1): re-mounted. Opts: commit=600
[ 80.942445] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe
[ 80.942452] ata2.00: irq_stat 0x40000001
[ 80.942457] ata2: SError: { PHYRdyChg }

```

or similar errors. I feel the problem is somehow related with this one :

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/610055]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/610055")

I can find no such errors, in fact every log message after ```
EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
``` looks like everything was working correctly.

---

### Post by yanaek on 2010-10-22
funny thing, if i do 1st patch (SUSPEND_MODULES="xhci") everything's fine
but when i also do
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"
resume/sleep breaks down again ;) keep it in mind

only one of those methods work at one time

---

### Post by NikoC on 2010-10-22
Changing GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX="acpi_sleep=nonvs" in /etc/default/grub and updating grub (sudo update-grub) did the trick for me on a Sony Vaio VGN-NS21Z and Ubuntu 10.10.

Thanks for the tip

---

### Post by ABaconBusAflame on 2010-10-22
> **naskopopov said:**
> Could you please check your kernel log for 

```

[ 80.559102] EXT4-fs (sda1): re-mounted. Opts: commit=600
[ 80.942445] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe
[ 80.942452] ata2.00: irq_stat 0x40000001
[ 80.942457] ata2: SError: { PHYRdyChg }

```

or similar errors. I feel the problem is somehow related with this one :

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/610055]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/610055")

I do get one of these right after closing my laptop lid:

```
[  887.152201] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
```

However, this line pops up even when my laptop returns from suspend successfully.

After closing the lid once yesterday, I got these:

```
[  176.632545] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[  176.656244] ata4: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x10
[  176.656244] ata4: irq_stat 0x40000001
```

---

### Post by deech on 2010-10-22
> **NikoC said:**
> Changing GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX="acpi_sleep=nonvs" in /etc/default/grub and updating grub (sudo update-grub) did the trick for me on a Sony Vaio VGN-NS21Z and Ubuntu 10.10.

Thanks for the tip

My problem was that after suspend my vaio rebooted. But this worked for me! Thanks a lot.
deech

---

### Post by Patxi Gortázar on 2010-10-23
Same problem on my hp Pavilion dv3000. Solved by means of modifying the grub as in [this comment]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656631/comments/8") of [bug #656631]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656631"):

Changing:
GRUB_CMDLINE_LINUX=”"
to
GRUB_CMDLINE_LINUX=”acpi_sleep=nonvs"
in /etc/default/grub
and runing:
sudo update-grub

---

### Post by Freezewarp on 2010-10-23
Same problem with Compaq CQ62. I upgraded from Ubuntu 10.04 to 10.10 shortly after the official release. I tried to install the "hibernate" and "suspend" packages (didn't notice anything different), running "s2ram -f" directly from the console (note that it doesn't recognize my computer so I had to force it - relevant?), using the grub boot flags, and the "/etc/pm/config.d/unload_module" hack.

I got a message like this before the grub hack (kern.log and syslog):
```
Oct 23 13:57:30 joseph-laptop kernel: [ 3239.402763] snapshot_ioctl: ioctl '80083308' is deprecated and will be removed soon, update your suspend-to-disk utilities
```

And, if I shutdown from the suspend operation (by holding the power button), I get this on the next boot:
```
Invalidating stale software suspend images... done.
```

No clue how much of that is relevant.


Edit: By I think removing the /etc/pm/config.d/unload_module hack and by installing fglrx (works great in 10.10, btw) it now seems to be working. Only the latter may be relevant, though.

---

### Post by aruake on 2010-10-24
> **gesquive said:**
> You can find more info in [this thread]("http://ubuntuforums.org/showthread.php?t=1586178&page=2") and [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656631"). But the following worked for me on my  Dell Latitude E6510 (Intel Core i7-720QM, 4GB RAM, NVIDIA NVS 3100M) running 10.10 64bit:

Use the editor of your choice to edit /etc/default/grub
```
sudo nano /etc/default/grub
```next, change
```
GRUB_CMDLINE_LINUX=""
```to
```
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"
```then run:
```
sudo update-grub
```After restarting, I can now suspend without any problems again.

Hi folks! 

I tried this trick in a Toshiba Satellite M40X (Pentium 1.6GHz, 80GB, 32 bits, 1GB RAM, 3GB SWAP), but unfortunately it didn't work. Thanks anyway gesquive!I was using the version 10.04 and all was working fine, but after I installed the version 10.10 (no wubi installation) my laptop can't resume from suspend nor from hibernate anymore. :confused:

This is the message I get after I try to resume from suspend:

[PHP](process: 276) GLib-WARNING **:getpwuid_r(): failed due to unknown used id (0)[/PHP]I hope we all find a solution for this problem soon... This new version rocks! 
:guitar:


BTW, this is my lshw output:

[PHP]description: Notebook
    product: Satellite M40X
    vendor: TOSHIBA
    version: PSM4XE-00U00CGR
    serial: 45417737K
    width: 32 bits
    capabilities: smbios-2.34 dmi-2.34
    configuration: boot=oem-specific chassis=notebook uuid=20E65ADF-AB88-11D9-B8A2-000FB06952C2
  *-core
       description: Motherboard
       product: EAL30
       vendor: TOSHIBA
       physical id: 0
       version: Null
       serial: 0123456789AB
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.60 (06/09/2005)
          size: 104KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: U1
          size: 1600MHz
          capacity: 2GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 2MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: M1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: M2
             size: 512MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:b0080000-b00fffff ioport:1800(size=8) memory:c0000000-cfffffff memory:b0000000-b003ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:44000000-4407ffff
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:b0040000-b00403ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:3000(size=4096) memory:b0100000-b01fffff ioport:40000000(size=67108864)
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:06:01.0
                logical name: eth0
                version: 10
                serial: 00:0f:b0:69:52:c2
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.107 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:21 ioport:3000(size=256) memory:b0106000-b01060ff
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:06:02.0
                logical name: eth1
                version: 05
                serial: 00:12:f0:10:90:2c
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.2.103 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:22 memory:b0107000-b0107fff
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:b0108000-b0108fff ioport:3400(size=256) ioport:3800(size=256) memory:40000000-43ffffff memory:48000000-4bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:11 memory:b0106800-b0106fff memory:b0100000-b0103fff
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: irq:17 memory:b0104000-b0105fff
           *-generic
                description: SD Host controller
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
                vendor: Texas Instruments
                physical id: 4.4
                bus info: pci@0000:06:04.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=57 maxlatency=4 mingnt=7
                resources: irq:19 memory:b0109400-b01094ff memory:b0109000-b01090ff memory:b0106400-b01064ff
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:1c00(size=256) ioport:18c0(size=64) memory:b0040800-b00409ff memory:b0040400-b00404ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18b0(size=16)
           *-disk
                description: ATA Disk
                product: TOSHIBA MK8025GA
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: KA02
                serial: 35BL7589S
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0006ad1a
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: b8d81f29-28b6-434a-893f-59be885c3a75
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-10-22 19:35:11 filesystem=ext4 lastmountpoint=/&#65533; &#65533;&#65533;0^&#65533;&#65533;L&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;P~&#65533;&#65533;&#65533;l!&#65533;&#65533;L&#65533;&#65533;@~&#65533;&#65533;`&#65533;&#65533;&#65533;`&#65533;&#65533;&#65533;0^&#65533;h~&#65533;&#65533;yo!&#65533;&#65533;d modified=2010-10-22 20:17:43 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered mounted=2010-10-24 11:45:03 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2998MiB
                   capacity: 2998MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2998MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-831S
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.90
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:20a0(size=32)
  *-battery
       description: Lithium Ion Battery
       product: PA3395U
       vendor: TOSHIBA
       physical id: 1
       version: 03/25/2005
       serial: 3658Q
       slot: 1st Battery
       capacity: 31500mWh
       configuration: voltage=14.8V
[/PHP]

---

### Post by olaf grossebaf on 2010-10-25
> **faden said:**
> The same here with Samsung N220 plus (Marvel) Netbook.
After wake up from sleep screen remains black although blue power and wlan led's are lit again. While sleeping only the power led blinks.
Wake up from hibernate seems to work fine...
NB: Standard configuration, no special hardware. Any help appreciated.

Exactly same problem with Samsung N210 :(

> **gesquive said:**
> 
```
sudo nano /etc/default/grub
```
```
GRUB_CMDLINE_LINUX=""
```
```
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"
```
```
sudo update-grub
```

Didn't solved the problem :-(

---

### Post by ratson on 2010-10-28
I have same mobo, cpu, ram, running 64bit 10.10. did you find a fix? (i had no chance to try out everything supposed in this forum, maybe this afternoon) my machine doesn't even goes to suspend. it fails somewhere. which log files can contain corresponding info?

> **Dans564 said:**
> same problem here:
mb: p7p55d evo
cpu: i5-760
ram: 4gb
swap: 8gb (overkill i know)
hd: 1.5tb
ubuntu ver.: 10.10
kernel: 2.6.35-22-generic-pae

---

### Post by mlord on 2010-10-31
I've just ordered a N210 from NCIX (CDN$299, w/external USB DVD-RW drive).  It should arrive later this coming week.  My plan is to install 10.10 Desktop edition on it.

If these are still having suspend/resume issues, I imagine I'll have to investigate and fix it, unless somebody else here beats me to it.

Cheers
Mark (kernel developer)

---

### Post by jamiekrug on 2010-10-31
The GRUB_CMDLINE_LINUX="acpi_sleep=nonvs" workaround did not work for me.

My System76 Serval laptop suspends fine, and usually resumes fine, but occasionally the resume follows this sequence: power lights come on when I open laptop lid to resume, the blank screen illuminates (albeit basically black), then the screen goes completely blank (as if it's off, as opposed to on but black) and nothing else. The power lights remain on, but the screen is completely blank--no lit pixels, and no keystrokes seem to do anything.

A successful resume follows the same sequence as above, but instead of the screen remaining completely powerless at the end, it illuminates black again and then shows the password dialog (to unlock).

I do have one hunch. After attempted the GRUB_CMDLINE_LINUX="acpi_sleep=nonvs" change as a potential fix, I was paying very close attention. I suspended and resumed successfully a number of times over the course of 2-3 days. I'm pretty sure each successful resume was when I did so in the same power state as the suspend (i.e., either battery for both suspend and resume or AC power for both suspend and resume). The first time I was aware of changing that pattern, I got the failure upon resume. I had suspended with AC power plugged in. I then unplugged my power cord and then opened the laptop lid to resume, and I got the power lights followed by a blank screen. I could do nothing but hold down the power button for a hard shut off :(

I can try reproducing this. Can anyone suggest a useful log to review or capture to assist with a bug fix? Thanks!

---

### Post by eruheru on 2010-10-31
Same problem on an Acer 3935. It's been happening with increased frequency and I have yet to find a pattern to it.

---

### Post by jamiekrug on 2010-11-01
No luck reproducing by suspending, unplugging power cord, then resuming--it worked fine on my first attempt to reproduce. I did, however, also have a failure when trying to suspend (happens more often upon resume). I was using my laptop (on battery power, FWIW), and when I went to suspend it (Ctrl+Alt+Del/Alt+u), the screen went blank, but the power lights and wifi indicator light remained on (as did the fan, I believe).

---

### Post by jeduffey on 2010-11-02
The /etc/default/grub edit did nothing for me.

Compaq Presaario SR1820NX desktop.

Suspend / Resume last worked Koala 9.04, it worked perfectly. I could use the keyboard suspend button, and get a blinking light on the tower. One press of the power button and it was up and ready in one or two seconds.
Suspend / Resume broke on installation of 10.04 Lynx. Failure was a known bug.
I was expecting it to be fixed with the upgrade to 10.10. Arrggg!!

---

### Post by JMB74 on 2010-11-03
Exactly the same problem here with the 2.6.35 kernel.

If I boot with the lucid 2.6.32 kernel that is still installed after the upgrade to maverick, then suspend/resume works perfectly.

---

### Post by Crazedpsyc on 2010-11-03
I have never been able to resume from suspend. I have gone through two computers and 4 versions of ubuntu without using it. it seems to think I have a suspend button and I need to press it. I have Fn+F1 and Fn+SPACE and neither work. I have tried almost every key combination possible and still it won't resume

---

### Post by rmcewen on 2010-11-04
On my Thinkpad T61 I was having intermittent suspend/resume issues after installing 10.10.  Sometimes it wouldn't suspend, sometimes it would resume with a blank screen, sometimes with the keyboard and/or mouse locked, sometimes it worked fine.

Tried the "nonvs" kernel option, no change.  Not loading xhci module so no need to unload it.

Couple of days ago I upgraded the kernel to 2.6.36 from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/)

So far seems to have solved the issue.

---

### Post by bad_astronaut on 2010-11-04
I am having a similar problem but mine is directly related to whether or not I am running on AC power.  I have no issues when plugged in.  When running on batter power I cannot wake from suspend, I cannot boot up or shut down, and I cannot put it into suspend mode.

---

### Post by FreeMinded on 2010-11-07
hi all,

I'm also suffering from this issue since some kernel update while still on Kubuntu 10.04 (now fresh install of 10.10 with existing home). Before suspend worked flawlessly.
I tried both suggested fixes without success. BTW: I didn't have a unload_module file in /etc/pm/config.d/ so I created one. Not sure if that is the right aproach. Should this file be there on al installations? There are also the folders power.d and sleep.d.

Any help or fix would be appreciated. Thanx!
FM

---

### Post by jon.reeve on 2010-11-08
Hi, MSI Wind U100 here. None of the above fixes worked for me, unfortunately. Also, as with bad_astronaut, my ability to resume from suspend is directly related to whether I'm running on AC power or on battery power. When on AC power, I can resume from suspend with no problems (from what I can tell). While on battery power, I cannot resume from suspend. Interestingly, I get a couple of seconds of time when trying to resume from suspend when I can move the mouse and such before it freezes and requires a hard reset. Even more interestingly, if I suspend and resume from AC power, and then unplug the AC cord much later, I get the same freeze and have to do a hard reset.

---

### Post by jon.reeve on 2010-11-08
I think this may be related to the Realtek wireless card. I've seen a lot of stuff about rtl modules and such in this thread. 

If people who have this problem could post the output of ```
lspci | grep Wireless
``` and ```
lsmod | grep r8
``` maybe we could get closer to solving this mystery. 

I removed my r8187se module with ```
sudo rmmod r8187se
``` and then suspended my laptop. Then after I resumed, I ran ```
sudo modprobe r8187se
``` to get wireless working.

---

### Post by jon.reeve on 2010-11-08
I think I figured it out, for my MSI Wind, at least. For me, the problem was probably the r8187se (realtek wireless) module. As a variation on the first suggested fix, I edited /etc/pm/config.d/unload_module and added ```
SUSPEND_MODULES="r8187se"
``` and now I got suspend to work. (It was the only line in that file, BTW). If you have r8187se or something similar listed when you run ```
lsmod
``` then maybe this will work for you, too. Otherwise maybe find the module that's acting up, or see if removing a module enables you to suspend, and then list that module in the file above, and then maybe that'll work.

Hope it helps! :)

---

### Post by jamiekrug on 2010-11-08
@jon.reeve: Sorry to be slow on the details here. Can you explain what you're doing with your edit to /etc/pm/config.d/unload_module fix? Does the still unload your wireless module, and do you need to manually load it again after resume?

Also, when you say "maybe find the module that's acting up," can you explain in a n00b friendly way how to go about that? ;-)

It does look like I have a Realtek wireless controller in my Serval laptop:
```
$ lspci | grep Wireless
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
$ lsmod | grep r8
r8192se_pci           507324  0 
r8169                  42222  0 
mii                     5261  1 r8169
```

---

### Post by isantop on 2010-11-08
I don't think it's necessarily linked to the realtek module, as I'm running a Sys76 PanP7 with an Intel Centrino Advanced-N 6200, and I can reproduce this on my system as well.

---

### Post by jon.reeve on 2010-11-09
> **jamiekrug said:**
> @jon.reeve: Sorry to be slow on the details here. Can you explain what you're doing with your edit to /etc/pm/config.d/unload_module fix? Does the still unload your wireless module, and do you need to manually load it again after resume?

Also, when you say "maybe find the module that's acting up," can you explain in a n00b friendly way how to go about that? ;-)

It does look like I have a Realtek wireless controller in my Serval laptop:
```
$ lspci | grep Wireless
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
$ lsmod | grep r8
r8192se_pci           507324  0 
r8169                  42222  0 
mii                     5261  1 r8169
```

This fix might work for you if you're using a Realtek card. Open a terminal and type ```
gksu gedit /etc/pm/config.d/unload_module
``` This will ask you for your password and open a text editor. In text editor, add the line ```
SUSPEND_MODULES="r8192se_pci"
``` and save. 

As far as I can tell, that unloads the realtek module, and then loads it again when you resume from suspend. You don't have to load/unload anything manually. 

If that doesn't work, you can try checking your system log files (System -> Administration -> Log File Viewer) for clues. Put your computer in suspend, take note of the time, then try to resume. When it doesn't resume, hard-reset it as usual, and then check the "messages" or "kernel" system log files for events that happened around that time. If there are a lot of errors related to a particular module, then try using the above method, replacing "r8192se_pci" with the name of the module that's giving errors. I wish I could tell you what a resume error might look like, but I didn't actually succeed in finding any myself--I just saw that people in this thread were noticing some errors in their system logs about their wireless cards. 

Good luck, and let me know if it works!

---

### Post by hodgkinr on 2010-11-09
Im having the same issues on my Acer Aspire 5536.  Here is my output to lspci | grep wireless: 

Code:
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

So the Realtek fix wont work for me.

---

### Post by Y_Ernst on 2010-11-10
After reading the kernel-patchwork acpi list I decided to set the "acpi_sleep=nonvs" option on my Sony Vaio VGN-FW41j.

System "suspend" and "resume" is now working.   

(Interestingly the Windows 7 acpi works without a problem. The windows compatible mode should work.)

It seems to be a continuous problem with 2.6.35 and 2.6.36 kernels.

---

### Post by jamiekrug on 2010-11-10
> **jon.reeve said:**
> This fix might work for you if you're using a Realtek card. Open a terminal and type ```
gksu gedit /etc/pm/config.d/unload_module
``` This will ask you for your password and open a text editor. In text editor, add the line ```
SUSPEND_MODULES="r8192se_pci"
``` and save.

I don't want to speak too soon and jinx this, but I think this fix may be working for me! It's also had another pleasant side effect. A minor nuisance I'd noticed is that my wireless connection gets a little confused when I resume--particularly when I've moved to a different location. It used to tend to spin for a few minutes before finally disconnecting from the network of my prior (suspend) location before connecting to my current (resume) location's wireless network. I would usually just disconnect the old and connect to a current one myself. Since adding the above unload of my Realtek module, I always connect immediately upon resume! I assume this is because the unloading of that module at suspend "clears things out," so when I resume the wifi module is loaded and needs to find a new network connection.

Anyway, with the suspend/resume issue having been intermittent for me, it's tough to say if this is definitely a solid fix, but it's looking very good. Over the past 48 hours or so, I've probably gone through about a dozen suspend/resume cycles, and have had no problems. I didn't seem to see the issue much if I always kept AC power plugged in for suspend and resume, but since I've put this fix in place I've continually varied the combinations (suspend with/without power, resume with/without power, suspend and resume on battery, etc.). Here's hoping! Thanks!

---

### Post by svlad cjelli on 2010-11-12
Hi,

same here! Ubuntu Maverick on Samsung N210!

```
lspci | grep Wireless
05:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

I have an Atheros wirelesscard.

I already tried the solution postet here:

[http://ubuntuforums.org/showpost.php?p=9992908&postcount=33](http://ubuntuforums.org/showpost.php?p=9992908&postcount=33)


But the problem remains...

Any other solutions?

---

### Post by aruake on 2010-11-14
Hi! This is my output for **lspci | grep Wireless**

[PHP]06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
[/PHP]It doesn't look like that the problem is only related to Realtek wireless cards. I edited the grub anyway to GRUB_CMDLINE_LINUX="acpi_sleep=nonvs" but I'm still getting the message below after I try to resume from suspend... :(

[PHP](process: 276) GLib-WARNING **:getpwuid_r(): failed due to unknown used id (0) [/PHP]Did anyone try to post this bug in the launchpad? I'm still waiting for a miraculous update before I get back to lucid... 

> **aruake said:**
> Hi folks! 

I tried this trick in a Toshiba Satellite M40X (Pentium 1.6GHz, 80GB, 32 bits, 1GB RAM, 3GB SWAP), but unfortunately it didn't work. Thanks anyway gesquive!I was using the version 10.04 and all was working fine, but after I installed the version 10.10 (no wubi installation) my laptop can't resume from suspend nor from hibernate anymore. :confused:

This is the message I get after I try to resume from suspend:

[PHP](process: 276) GLib-WARNING **:getpwuid_r(): failed due to unknown used id (0)[/PHP]I hope we all find a solution for this problem soon... This new version rocks! 
:guitar:


BTW, this is my lshw output:

[PHP]description: Notebook
    product: Satellite M40X
    vendor: TOSHIBA
    version: PSM4XE-00U00CGR
    serial: 45417737K
    width: 32 bits
    capabilities: smbios-2.34 dmi-2.34
    configuration: boot=oem-specific chassis=notebook uuid=20E65ADF-AB88-11D9-B8A2-000FB06952C2
  *-core
       description: Motherboard
       product: EAL30
       vendor: TOSHIBA
       physical id: 0
       version: Null
       serial: 0123456789AB
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.60 (06/09/2005)
          size: 104KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: U1
          size: 1600MHz
          capacity: 2GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 2MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: M1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: M2
             size: 512MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:b0080000-b00fffff ioport:1800(size=8) memory:c0000000-cfffffff memory:b0000000-b003ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:44000000-4407ffff
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:b0040000-b00403ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:3000(size=4096) memory:b0100000-b01fffff ioport:40000000(size=67108864)
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:06:01.0
                logical name: eth0
                version: 10
                serial: 00:0f:b0:69:52:c2
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.107 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:21 ioport:3000(size=256) memory:b0106000-b01060ff
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:06:02.0
                logical name: eth1
                version: 05
                serial: 00:12:f0:10:90:2c
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.2.103 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:22 memory:b0107000-b0107fff
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:b0108000-b0108fff ioport:3400(size=256) ioport:3800(size=256) memory:40000000-43ffffff memory:48000000-4bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:11 memory:b0106800-b0106fff memory:b0100000-b0103fff
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: irq:17 memory:b0104000-b0105fff
           *-generic
                description: SD Host controller
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
                vendor: Texas Instruments
                physical id: 4.4
                bus info: pci@0000:06:04.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=57 maxlatency=4 mingnt=7
                resources: irq:19 memory:b0109400-b01094ff memory:b0109000-b01090ff memory:b0106400-b01064ff
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:1c00(size=256) ioport:18c0(size=64) memory:b0040800-b00409ff memory:b0040400-b00404ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18b0(size=16)
           *-disk
                description: ATA Disk
                product: TOSHIBA MK8025GA
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: KA02
                serial: 35BL7589S
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0006ad1a
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: b8d81f29-28b6-434a-893f-59be885c3a75
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-10-22 19:35:11 filesystem=ext4 lastmountpoint=/&#65533; &#65533;&#65533;0^&#65533;&#65533;L&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;P~&#65533;&#65533;&#65533;l!&#65533;&#65533;L&#65533;&#65533;@~&#65533;&#65533;`&#65533;&#65533;&#65533;`&#65533;&#65533;&#65533;0^&#65533;h~&#65533;&#65533;yo!&#65533;&#65533;d modified=2010-10-22 20:17:43 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered mounted=2010-10-24 11:45:03 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2998MiB
                   capacity: 2998MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2998MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-831S
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.90
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:20a0(size=32)
  *-battery
       description: Lithium Ion Battery
       product: PA3395U
       vendor: TOSHIBA
       physical id: 1
       version: 03/25/2005
       serial: 3658Q
       slot: 1st Battery
       capacity: 31500mWh
       configuration: voltage=14.8V
[/PHP]

---

### Post by jamiekrug on 2010-11-15
> **svlad cjelli said:**
> Any other solutions?

See my post #75, and some before that on that particular solution. That solution seems to be working for me.

---

### Post by jamiekrug on 2010-11-15
> **svlad cjelli said:**
> I already tried the solution postet here:

[http://ubuntuforums.org/showpost.php?p=9992908&postcount=33](http://ubuntuforums.org/showpost.php?p=9992908&postcount=33)

But the problem remains...

Any other solutions?

See my post #75, which is working for me. It may be worth a try, even if you don't have a Realtek module. I really don't know, but seems worth a try!

> Did anyone try to post this bug in the launchpad? I'm still waiting for a miraculous update before I get back to lucid...

[LP Bug #656631]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656631") seems the closest I've found, but please post here if you find a better fit.

---

### Post by svlad cjelli on 2010-11-19
Sadly the workaround does not work for me here on Samsung N210 and Atheros wireless:

```
Originally Posted by jon.reeve View Post
This fix might work for you if you're using a Realtek card. Open a terminal and type
Code:

gksu gedit /etc/pm/config.d/unload_module

This will ask you for your password and open a text editor. In text editor, add the line
Code:

SUSPEND_MODULES="r8192se_pci"

and save.
```

I really don't know what do do now :D

---

### Post by svlad cjelli on 2010-11-21
:(

---

### Post by jamiekrug on 2010-11-21
Unfortunately, the SUSPEND_MODULES workaround did not work for me after all. I went almost a week without suspend/resume problems, but the problems have appeared again. A few days ago I had a new one, where trying to suspend did not fully suspend--yet I was able to get the login screen, so no freeze-up. But the same old failure to resume occurred again as well. In this case, I opened my laptop lid to resume, power and lights came on, but nothing else happened--blank screen, and unable to anything but force a hard power-off.

I looked through all sorts of log files after the failed resume, and there's absolutely **nothing** recorded in **any** log at that time. This suggests that the kernel never gets any sort of message to begin a resume, or if it does, whatever this problem is, it's rendering the system completely frozen and unable to log a single message :(

*UPDATE (2010-11-22)*: I also want to report that I've occasionally had a suspend fail to fully suspend. Specifically, it appears that all suspend hooks are run, and the laptop "thinks" it is indeed suspended, if you will--but the power lights do not go off, and the fan is sometimes still running. This is essentially much like the failed resume. So, it seems there's a missing communication between the BIOS and the kernel (my uninformed speculation!). Yet one more issue I experienced yesterday (this one new and the first and only time): I resumed, logged in, then Ubuntu completely froze--no cursor movement or typing, but I could see the display (and it was not a kernel panic, because Caps Lock was not blinking).

---

### Post by emeyal on 2010-11-23
Updating grub to
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs" Did it on a Dell e6410, kernel 2.6.35-22-generic, Ubuntu 10.10
:)
Thanks,
Eyal

---

### Post by irishfury on 2010-11-25
> **rmcewen said:**
> On my Thinkpad T61 I was having intermittent suspend/resume issues after installing 10.10.  Sometimes it wouldn't suspend, sometimes it would resume with a blank screen, sometimes with the keyboard and/or mouse locked, sometimes it worked fine.

Tried the "nonvs" kernel option, no change.  Not loading xhci module so no need to unload it.

Couple of days ago I upgraded the kernel to 2.6.36 from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/)

So far seems to have solved the issue.

This is the only fix that worked for me.  Lenovo Thinkpad T510

---

### Post by DogMatix on 2010-11-25
I have the fail to resume from suspend issue on my netbook when running on battery only.

Acer One ZG8 531 - Ubuntu 10.10 (2.6.35-23)

```
$ lspci | grep Wireless
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

---

### Post by pfunkman on 2010-11-27
Still happening here on my sammy n220.

None of the "fixes" work, like the above poster i have the atheros ar9285.

Kind of silly to have no support for some of the most common netbook hardware on the market.

---

### Post by Peter09 on 2010-11-27
Yep, I have a Sammy n150, no wireless or resume from suspend. As you say, a very common lump of hardware to suffer such regressions.

---

### Post by kempo on 2010-11-27
> **sgosnell said:**
> Install the package 'hibernate' from the repositories.  That seems to make suspend work properly.  Why it is not included by default I have no idea.  I found it through a search on Launchpad.  It's available there, but it's also in the Maverick repositories.

Thank you! this worked for me - Sony VGN-SR19XN.

---

### Post by wyattmengy on 2010-12-04
> **rmcewen said:**
> On my Thinkpad T61 I was having intermittent suspend/resume issues after installing 10.10.  Sometimes it wouldn't suspend, sometimes it would resume with a blank screen, sometimes with the keyboard and/or mouse locked, sometimes it worked fine.

Tried the "nonvs" kernel option, no change.  Not loading xhci module so no need to unload it.

Couple of days ago I upgraded the kernel to 2.6.36 from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/)

So far seems to have solved the issue.

Hi, I'm a newbie on Ubuntu yet. I'm experiencing almost exactly the same issue as you stated above. But due to my limit experience of Linux, I'm not sure how to "install" the stuff shown in the page from your hyper link. It has bunch ".patch", ".log", and ".deb" files that I have no idea what they are. What should I download and how can I install the newer version of kernel?

---

### Post by sgosnell on 2010-12-04
What you want are .deb files.  They're standard Debian package files, which can be installed from the command line with dpkg, or through the GUI frontend, gdebi.  The easiest way for an inexperienced user is probably to right-click on the .deb file in Nautilus, and select "install with gdebi package installer".  From the command line, use "sudo dpkg -i filename.deb", replacing filename with the actual filename.  You can type the first few letters of the filename and then press Tab, which will autocomplete the filename.  If there are multiple files with the same characters in the filename, nothing happens, and you have to enter more characters to get autocompletion, because bash can't tell which file to select until there is no duplication.

---

### Post by rybajz on 2010-12-10
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"

Works for me. It is perfect. I have spent lot of time searching for this solution for my SONY VAIO VPCEB1E1E

---

### Post by hnrkg on 2010-12-10
Unfortunately none of the provided solutions work for me (on Ubuntu 10.10). My symptoms are the same: the laptop seems to wake up but the screen is off. Actually, it sounds like my laptop is booting up. It is checking the DVD drive and the HDD led glows steadily. The laptop is not responding at all and I am forced to do a hard reboot.

However, I have found "solution" to my problem. If I downgrade grub 2 to grub legacy (0.97?) I can suspend as much as I like without any problems what so ever. I follow this guide: [https://help.ubuntu.com/community/Grub2#Uninstalling](https://help.ubuntu.com/community/Grub2#Uninstalling) GRUB 2

The problem is somehow related to grub 2, but is it a grub 2 bug?

---

### Post by bspujari on 2010-12-12
Adding "acpi_sleep=nonvs" in GRUB_CMDLINE_LINUX did the trick for me!:p

Sony VAIO VPCEB11FD
Intel core i3
Kernel : 2.6.35-23-generic


cheers! :)

---

### Post by spykEee on 2010-12-18
> **bspujari said:**
> Adding "acpi_sleep=nonvs" in GRUB_CMDLINE_LINUX did the trick for me!

I'd like to try this, but I'm a rube and can't figure out what you're talking about. I tried searching for a file named GRUB_CMDLINE_LINUX or a directory named GRUB, but obviously I'm barking up tther wrong tree. Can you give me a clue where to look?

---

### Post by sgosnell on 2010-12-18
Edit /etc/default/grub as root.  Find the following line: ```
GRUB_CMDLINE_LINUX=""
```
There may be other stuff between the quotes, and if so, keep them as they are, and add ```
acpi_sleep=nonvs
``` between the quotes.

---

### Post by spykEee on 2010-12-18
thanks:D

Confirmed that this happens only when on battery power, not on AC power. Symptoms are same as many others report: goes to sleep (Suspend) normally, "tries" to wake up normally but with a blank display. I can go through the motions of typing password/Enter, but to no avail. Have to do a hard shutdown. Problem started when upgrading to 10.10, but I've had it before when upgrading, though it went away eventually. I'm going to try playing with some of the Power Management settings and will report back if that makes a difference. I'm using a Asus Eee PC 1000 with a "solid state" hard drive.

---

### Post by spykEee on 2010-12-19
> **sgosnell said:**
> Edit /etc/default/grub as root.

I don't have a file named Grub (or grub or anything starting  with g or G) in /etc/default Poked around a bit, found a bunch of files in various locations named grub.somethingorother, but nothing that looked too promising. Can you give me some more clues what to look for?

Power management settings didn't help (seemed to at first, but nada;  problem is intermittent and variable; last time display came up but  cursor was frozen and computer was unresponsive to any input).

---

### Post by punkybouy on 2010-12-19
It's grub not Grub  linux/unix is case sensitive on file names

---

### Post by spykEee on 2010-12-19
> **punkybouy said:**
> It's grub not Grub  linux/unix is case sensitive on file names
Right. Don't have either one.

---

### Post by sgosnell on 2010-12-19
If you don't have grub, how are you booting?  What happens if you run ```
gksu gedit /etc/default/grub
```  Do you get a text file, or a blank file?

---

### Post by spykEee on 2010-12-20
I get a blank file. If I  ls /etc/default I see a bunch of files, but none named grub or anything like it. I'm sure I have grub, but it's not there; it has to be somewhere or named something else. If I search for "grub" i find a lot of files with the letters grub in their name (eg.grub.triggers and grub-common.confiles) but only two named just plain grub. One is a binary, the other is a shell script that says:
#!/bin/sh

. /usr/share/recovery-mode/l10n.sh

if [ "$1" = "test" ]; then
  echo $(eval_gettext "Update grub bootloader")
  exit 0
fi

# FIXME: add this too? how to find out boot device?
#        add menu to ask?
#grub-install
update-grub

exit 0

---

### Post by dineshchaturvedi on 2010-12-20
I have the same problem, hope someone looks at it. Right now I am feeling like Orphan.

---

### Post by Mishootka on 2010-12-23
Hey,
if you have troubles with waking up from suspend/hibernate
try this solution:

[http://ubuntuforums.org/showthread.php?t=1596159&page=3]("http://ubuntuforums.org/showthread.php?t=1596159&page=3")

- worked for my Dell mini 1012.

---

### Post by dzegarra on 2010-12-28
I solved the problem installing the package hibernate. 

```
sudo apt-get install hibernate
```

The suspension and hibernation is more slow now but at least works well.

---

### Post by -jay- on 2010-12-29
> **jeduffey said:**
> The /etc/default/grub edit did nothing for me.

Compaq Presaario SR1820NX desktop.

Suspend / Resume last worked Koala 9.04, it worked perfectly. I could use the keyboard suspend button, and get a blinking light on the tower. One press of the power button and it was up and ready in one or two seconds.
Suspend / Resume broke on installation of 10.04 Lynx. Failure was a known bug.
I was expecting it to be fixed with the upgrade to 10.10. Arrggg!!


same here cant resume at all

---

### Post by bez654 on 2011-01-01
Hi. 
Thanks for the tips guys, its good to know your not the only one with this problem and that work arounds do exist.

I was getting a blank screen on resume from suspend to ram

to get suspend to ram to work I added
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"
to grub as detailed elsewhere in this forum.
This is on a eee 1000H with the only difference from stock being additional ram (up to 2gb). running ubuntu 10.10 running 2.6.35-24

Hibernate has always worked for me - I do have a swap partition which is larger than the size of my ram. I had to do a manual partition during install to get this arrangement - I suspect that some peoples problems with hibernate are do to an adequate swap partition not existing. 

Also, installing "hibernate" has sped up my restore from hibernate much faster. 
This also produced a different response during resume from suspend to ram. Previously I had to reboot the computer after resume from ram as it froze during restore. After installing "hibernate" I still had a blank screen but the computer automatically cycled the power and booted normally. Not a solution but it was changing something. 

In my case adding SUSPEND_MODULES="xhci-hcd" to /etc/pm/config.d (as described in 10.10 release notes) failed to get restore from suspend to work. In fact it made the computer freeze completely during restore - such that I had to remove the battery (with no mains) to power down the computer and allow me restart it using the power button.

Thanks again for your help.

---

### Post by bez654 on 2011-01-01
after a bit more playing i've discovered that resume from hibernate is in fact slower with "hibernate" installed.

editing grub works for me whether or not "hibernate" is installed.

---

### Post by spykEee on 2011-01-01
> **bez654 said:**
> Hi. 

to get suspend to ram to work I added
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"
to grub as detailed elsewhere in this forum.


I'm still stuck in the same place, namely I have nearly identical hardware as bez, would like to add this to my grub file, but I can't find it (see my earlier posts). I'm obviously using grub, but I simply can not find the file. There must be some way of determining where it is and what it's named. (I'm guessing it has to be named something else or I would have found it by searching for "grub"; again, please see my earlier posts.) Can someone please help me figure this out? There must be a script somewhere that calls grub(?)

---

### Post by sgosnell on 2011-01-01
What do you get from ```
whereis grub
``` I see grub is also in /usr/share/grub/default/grub on my system, for some reason.  Not sure how it got there, but I'm running Linux Mint Debian Edition, FWIW.

---

### Post by spykEee on 2011-01-01
whereis grub returns:
/usr/sbin/grub (a 145 KB executable, can't open)
/etc/grub.d (a directory with a number of shell scripts and a readme. Looks promising.  Could this be what I'm looking for?)
/usr/lib/grub (another directory)
/usr/share/grub (another [same?] 145 KB executable, can't open)
/usr/share/man/man8/grub.8.gz (doesn't look promising)

---

### Post by sgosnell on 2011-01-01
Grub should also be in /usr/share/grub/default/.  As far as I can tell it's just a dummy file, but you can copy it to /etc/default and have a working grub file.  After you modify it, you have to run "sudo update-grub" for the changes to take effect.

---

### Post by spykEee on 2011-01-02
> **sgosnell said:**
> Grub should also be in /usr/share/grub/default/..

Nope.  usr/share/grub has three files (ascii.h, ascii.pf2, & unicode.pf2) and no default directory.

---

### Post by sgosnell on 2011-01-02
Well, I give up.  I have no idea how you got to your current status, nor how to get you out of it.  Good luck.

---

### Post by logangorence on 2011-01-02
When the Computer sleeps, it may not give power to the external drive, and it forces it to wake back up to give power back to drive.
Good luck!

---

### Post by charles.F on 2011-01-03
The same state on Satellite M40 Notebook with ATI EXPRESS 200M UMA.
RC401MB + SB400
Black screen after wake from Suspend to RAM.:confused:
Can not see anything in the log file
Anyone can help me deal with this problem?
 
attached my syslog as follows:
Jan  5 00:46:27 chit-desktop NetworkManager: <info>  Sleeping...
Jan  5 00:46:27 chit-desktop NetworkManager: <info>  (eth0): now unmanaged
Jan  5 00:46:27 chit-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
Jan  5 00:46:27 chit-desktop NetworkManager: <info>  (eth0): cleaning up...
Jan  5 00:46:27 chit-desktop NetworkManager: <info>  (eth0): taking down device.
Jan  5 00:46:27 chit-desktop init: anacron main process (955) killed by TERM signal
Jan  5 00:46:27 chit-desktop kernel: [  713.231798] [drm] Num pipes: 1
Jan  5 00:47:19 chit-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Jan  5 00:47:19 chit-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="586" x-info="[http://www.rsyslog.com](http://www.rsyslog.com)"] (re)start
Jan  5 00:47:20 chit-desktop rsyslogd: rsyslogd's groupid changed to 102
Jan  5 00:47:20 chit-desktop rsyslogd: rsyslogd's userid changed to 101

wish someone can help me

---

### Post by FaithHopeLove on 2011-01-06
In post #103 above Mishootka pointed to this link. 
[http://ubuntuforums.org/showthread.php?t=1596159&page=3](http://ubuntuforums.org/showthread.php?t=1596159&page=3)

It has a script for you to install that starts one processor/core only for a few seconds when waking up. I had tried a few of the suggestions in this thread with no luck until I read this one. It worked a treat on my new Lenovo S10-3 Ideapad which would never wake up for me since I installed Ubuntu 10.10.
Hopefully this could fix your problem.

---

### Post by charles.F on 2011-01-06
> **FaithHopeLove said:**
> In post #103 above Mishootka pointed to this link. 
[http://ubuntuforums.org/showthread.php?t=1596159&page=3](http://ubuntuforums.org/showthread.php?t=1596159&page=3)
 
It has a script for you to install that starts one processor/core only for a few seconds when waking up. I had tried a few of the suggestions in this thread with no luck until I read this one. It worked a treat on my new Lenovo S10-3 Ideapad which would never wake up for me since I installed Ubuntu 10.10.
Hopefully this could fix your problem.
 
 
 
Thanks for your help.
But the CPU of my platform is Intel P6 single processor/core.

---

### Post by Byb on 2011-01-07
Hi all
Same wake from RAM issue here (I don't use/forgive hibernate feature as I have my home encrypted).
I read about the half of this thread and felt puzzled (I newb) so I decided to install the hibernate package with synaptic.
Now when the system reboots it is different : the screen keeps stuck purple indefinitely. I have to Ctrl+Alt+F1, then I see
[PHP][    3.272074] [drm_intel_panel_get_max_backlight] *ERROR* fixme: max PWM is zero[/PHP]that I ~unlock~ with "Enter", then boot goes on seamlessly to the gdm login popup.
My default config is:
[PHP]uname -a
Linux Amilo-M7405 2.6.37-020637rc8-generic #201012290905 SMP Wed Dec 29 10:16:26 UTC 2010 i686 GNU/Linux
[/PHP] but I also have the 2.6.37-020637-generic #201101050908 and many previous and also things from the repo [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) (xserver-xorg-vdeo-intel locked release 2:2.12.0-1ubuntu5.1) that a guy told me to install to have the video effects working.

resume from ram still does't work

Please what do I do now ?

---

### Post by vidwarren on 2011-01-07
> **naskopopov said:**
> Hi, 
Same problem here - laptop hp4310s. 

Adding SUSPEND_MODULES="xhci" to /etc/pm/config.d/unload_module fixed it for me.

Cheers

I'm having the same problem on a Samsung NC10 Plus. I've tried the **GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"** workaround. Didn't fix it.

I undid that and tried the **sudo apt-get install hibernate** workaround. Didn't fix it.

My /etc/pm/config.d/ folder is empty. Could the missing 'unload_module' file be the problem? Where can I find it?

I'm fairly new to Ubuntu. Is it likely that a fix for this would be included in the updates soon?

Thanks in advance.

---

### Post by jamiekrug on 2011-01-07
> **vidwarren said:**
> My /etc/pm/config.d/ folder is empty. Could the missing 'unload_module' file be the problem? Where can I find it?

You can just create the file and add the SUSPEND_MODULES configuration variable. Both steps can be accomplished quickly by entering this at a terminal (Applications > Accessories > Terminal) prompt:

```
echo "SUSPEND_MODULES=xhci" | sudo tee -a /etc/pm/config.d/unload_module
```

If you're interested in reading about the files under /etc/pm/config.d/, have a look at [this man page]("http://manpages.ubuntu.com/manpages/maverick/man8/pm-action.8.html").

---

### Post by vidwarren on 2011-01-07
Thanks, unfortunately it didn't work but I'll post here if I can find a solution through the Manpage.

For now, at least I can hibernate :)

---

### Post by Byb on 2011-01-08
I have try the 4 ways but no one worked (hibernate, xhci, unload_module and grub).
Please, could some gentle people tell me how I could track the issue for my computer. I created a launcher on my desktop for the gksudo gnome-system-log because from the menu the viewer said I'm not allowed to read (although it shows). But there is so much things here inside that I can't know what/where to search.

Thanks for any help

---

### Post by Snappa on 2011-01-08
Like vidwarren, I have a Samsung netbook (mine is an NB30), and won't come out of suspend.  I am running 10.10, but not the netbook version. (Had wireless problems with that.) Following this and other threads, I've tried
 
1) Adding the file /etc/pm/config.d/unload_module
2) Adding the file /ec/pm/sleep.d/00CPU (Those are zeros.)
and
3) Installing hibernate, which did not appear to go well.

I'm just starting linux, so a failed install is beyond me.  If it was a guaranteed fix, I'd persist with the install.

When I use the power switch to come out of suspend, I see the hard disk LED light for a couple of seconds, and the wireless LED lights and stays lit, but nothing else.  Screen remains blank (black).

Should I have undone each fix before trying the next ?  Seems like is is all "suck it and see", rather than an actual fix.

Seems like this is quite a major issue.  I hope the experts are looking at it.  Does anyone have any idea when it might be resolved ?

Thanks. :(

---

### Post by alienfluid on 2011-01-08
Just came across this thread - I am having similar issues with my new HP dm4 (core i5, 6GB). I'll try changing the power options to hibernate instead of suspend. Pretty annoying though - weird that it doesn't happen every time.

---

### Post by Byb on 2011-01-09
Suspend to RAM initiated 12:20PM with Fn+F1
Here are the logs::popcorn:
[COLOR=Red]**Xorg.0.log**[/COLOR]
[PHP][    26.914] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    26.914] X Protocol Version 11, Revision 0
[    26.914] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    26.914] Current Operating System: Linux Amilo-M7405 2.6.37-020637-generic #201101050908 SMP Wed Jan 5 10:17:13 UTC 2011 i686
[    26.914] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637-generic root=UUID=53f4ad58-f05f-4972-b816-4105751cba54 ro quiet splash
[    26.914] Build Date: 16 September 2010  05:39:22PM
[    26.914] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    26.925] Current version of pixman: 0.18.4
[    26.925]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    26.925] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.925] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan  9 13:16:31 2011
[    26.961] (==) Using config file: "/etc/X11/xorg.conf"
[    26.961] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.068] (==) No Layout section.  Using the first Screen section.
[    27.068] (**) |-->Screen "Default Screen" (0)
[    27.068] (**) |   |-->Monitor "Configured Monitor"
[    27.068] (**) |   |-->Device "Configured Video Device"
[    27.069] (==) Automatically adding devices
[    27.069] (==) Automatically enabling devices
[    27.182] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.182]     Entry deleted from font path.
[    27.239] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    27.239] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.239] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    27.239] (II) Loader magic: 0x81f8e00
[    27.239] (II) Module ABI versions:
[    27.239]     X.Org ANSI C Emulation: 0.4
[    27.239]     X.Org Video Driver: 8.0
[    27.239]     X.Org XInput driver : 11.0
[    27.239]     X.Org Server Extension : 4.0
[    27.240] (--) PCI:*(0:0:2:0) 8086:3582:1734:106a rev 2, Mem @ 0xd8000000/134217728, 0xe0380000/524288, I/O @ 0x0000ec00/8
[    27.240] (--) PCI: (0:0:2:1) 8086:3582:1734:106a rev 2, Mem @ 0xd0000000/134217728, 0xe0300000/524288
[    27.240] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    27.240] (II) LoadModule: "extmod"
[    27.314] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    27.334] (II) Module extmod: vendor="X.Org Foundation"
[    27.334]     compiled for 1.9.0, module version = 1.0.0
[    27.334]     Module class: X.Org Server Extension
[    27.334]     ABI class: X.Org Server Extension, version 4.0
[    27.334] (II) Loading extension MIT-SCREEN-SAVER
[    27.334] (II) Loading extension XFree86-VidModeExtension
[    27.334] (II) Loading extension XFree86-DGA
[    27.334] (II) Loading extension DPMS
[    27.334] (II) Loading extension XVideo
[    27.334] (II) Loading extension XVideo-MotionCompensation
[    27.334] (II) Loading extension X-Resource
[    27.334] (II) LoadModule: "dbe"
[    27.335] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    27.338] (II) Module dbe: vendor="X.Org Foundation"
[    27.338]     compiled for 1.9.0, module version = 1.0.0
[    27.338]     Module class: X.Org Server Extension
[    27.338]     ABI class: X.Org Server Extension, version 4.0
[    27.338] (II) Loading extension DOUBLE-BUFFER
[    27.338] (II) LoadModule: "glx"
[    27.339] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    27.357] (II) Module glx: vendor="X.Org Foundation"
[    27.357]     compiled for 1.9.0, module version = 1.0.0
[    27.357]     ABI class: X.Org Server Extension, version 4.0
[    27.358] (==) AIGLX enabled
[    27.358] (II) Loading extension GLX
[    27.358] (II) LoadModule: "record"
[    27.359] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    27.369] (II) Module record: vendor="X.Org Foundation"
[    27.369]     compiled for 1.9.0, module version = 1.13.0
[    27.369]     Module class: X.Org Server Extension
[    27.369]     ABI class: X.Org Server Extension, version 4.0
[    27.369] (II) Loading extension RECORD
[    27.369] (II) LoadModule: "dri"
[    27.370] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    27.450] (II) Module dri: vendor="X.Org Foundation"
[    27.450]     compiled for 1.9.0, module version = 1.0.0
[    27.450]     ABI class: X.Org Server Extension, version 4.0
[    27.450] (II) Loading extension XFree86-DRI
[    27.450] (II) LoadModule: "dri2"
[    27.451] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.451] (II) Module dri2: vendor="X.Org Foundation"
[    27.451]     compiled for 1.9.0, module version = 1.2.0
[    27.451]     ABI class: X.Org Server Extension, version 4.0
[    27.451] (II) Loading extension DRI2
[    27.451] (II) LoadModule: "intel"
[    27.452] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    27.506] (II) Module intel: vendor="X.Org Foundation"
[    27.506]     compiled for 1.9.0, module version = 2.12.0
[    27.506]     Module class: X.Org Video Driver
[    27.506]     ABI class: X.Org Video Driver, version 8.0
[    27.506] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    27.506] (++) using VT number 7

[    27.514] drmOpenDevice: node name is /dev/dri/card0
[    27.514] drmOpenDevice: open result is 8, (OK)
[    27.514] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    27.514] drmOpenDevice: node name is /dev/dri/card0
[    27.514] drmOpenDevice: open result is 8, (OK)
[    27.514] drmOpenByBusid: drmOpenMinor returns 8
[    27.514] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    27.514] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    27.514] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    27.514] (==) intel(0): RGB weight 888
[    27.514] (==) intel(0): Default visual is TrueColor
[    27.514] (II) intel(0): Integrated Graphics Chipset: Intel(R) 855GME
[    27.514] (--) intel(0): Chipset: "852GM/855GM"
[    27.514] (==) intel(0): video overlay key set to 0x101fe
[    27.593] (II) intel(0): Output LVDS1 using monitor section Configured Monitor
[    27.925] (II) intel(0): Output VGA1 has no monitor section
[    27.952] (II) intel(0): Output DVI1 has no monitor section
[    27.952] (II) intel(0): EDID for output LVDS1
[    27.952] (II) intel(0): Manufacturer: QDS  Model: 11  Serial#: 0
[    27.952] (II) intel(0): Year: 2094  Week: 29
[    27.952] (II) intel(0): EDID Version: 1.2
[    27.952] (II) intel(0): Digital Display Input
[    27.952] (II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 23
[    27.952] (II) intel(0): Gamma: 2.20
[    27.952] (II) intel(0): No DPMS capabilities specified
[    27.952] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    27.952] (II) intel(0): First detailed timing is preferred mode
[    27.952] (II) intel(0): redX: 0.591 redY: 0.325   greenX: 0.314 greenY: 0.562
[    27.952] (II) intel(0): blueX: 0.137 blueY: 0.119   whiteX: 0.312 whiteY: 0.328
[    27.952] (II) intel(0): Manufacturer's mask: 0
[    27.952] (II) intel(0): Supported detailed timing:
[    27.952] (II) intel(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
[    27.952] (II) intel(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[    27.952] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[    27.952] (II) intel(0): Unknown vendor-specific block f
[    27.952] (II) intel(0):  JFM4712152326
[    27.952] (II) intel(0):  QD15XL061
[    27.952] (II) intel(0): EDID (in hex):
[    27.952] (II) intel(0):     00ffffffffffff004493110000000000
[    27.952] (II) intel(0):     1d680102801e17780a58209753509023
[    27.953] (II) intel(0):     1e505400000001010101010101010101
[    27.953] (II) intel(0):     01010101010164190040410026301888
[    27.953] (II) intel(0):     360030e4100000190000000f0004c02e
[    27.953] (II) intel(0):     c00211111176c0126301000000fe004a
[    27.953] (II) intel(0):     464d34373132313532333236000000fe
[    27.953] (II) intel(0):     0051443135584c3036310a20202000a5
[    27.953] (II) intel(0): EDID vendor "QDS", prod id 17
[    27.953] (II) intel(0): Printing DDC gathered Modelines:
[    27.953] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.953] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    27.953] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    27.953] (II) intel(0): Printing probed modes for output LVDS1
[    27.953] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.953] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.953] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    27.954] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.285] (II) intel(0): EDID for output VGA1
[    28.308] (II) intel(0): EDID for output DVI1
[    28.308] (II) intel(0): Output LVDS1 connected
[    28.308] (II) intel(0): Output VGA1 disconnected
[    28.308] (II) intel(0): Output DVI1 disconnected
[    28.308] (II) intel(0): Using exact sizes for initial modes
[    28.308] (II) intel(0): Output LVDS1 using initial mode 1024x768
[    28.308] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    28.308] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    28.308] (**) intel(0): Display dimensions: (300, 230) mm
[    28.308] (**) intel(0): DPI set to (86, 84)
[    28.308] (II) Loading sub module "fb"
[    28.308] (II) LoadModule: "fb"
[    28.308] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.339] (II) Module fb: vendor="X.Org Foundation"
[    28.339]     compiled for 1.9.0, module version = 1.0.0
[    28.339]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.339] (==) Depth 24 pixmap format is 32 bpp
[    28.340] (II) intel(0): [DRI2] Setup complete
[    28.340] (II) intel(0): [DRI2]   DRI driver: i915
[    28.340] (**) intel(0): Tiling enabled
[    28.340] (**) intel(0): SwapBuffers wait enabled
[    28.340] (==) intel(0): VideoRam: 131072 KB
[    28.340] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    28.369] (II) UXA(0): Driver registered support for the following operations:
[    28.369] (II)         solid
[    28.369] (II)         copy
[    28.369] (II)         composite (RENDER acceleration)
[    28.369] (II)         put_image
[    28.369] (II)         get_image
[    28.369] (==) intel(0): Backing store disabled
[    28.369] (==) intel(0): Silken mouse enabled
[    28.373] (II) intel(0): Initializing HW Cursor
[    28.392] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.392] (==) intel(0): DPMS enabled
[    28.392] (==) intel(0): Intel XvMC decoder disabled
[    28.392] (II) intel(0): Set up overlay video
[    28.392] (II) intel(0): direct rendering: DRI2 Enabled
[    28.392] (--) RandR disabled
[    28.392] (II) Initializing built-in extension Generic Event Extension
[    28.392] (II) Initializing built-in extension SHAPE
[    28.392] (II) Initializing built-in extension MIT-SHM
[    28.392] (II) Initializing built-in extension XInputExtension
[    28.392] (II) Initializing built-in extension XTEST
[    28.392] (II) Initializing built-in extension BIG-REQUESTS
[    28.392] (II) Initializing built-in extension SYNC
[    28.392] (II) Initializing built-in extension XKEYBOARD
[    28.393] (II) Initializing built-in extension XC-MISC
[    28.393] (II) Initializing built-in extension SECURITY
[    28.393] (II) Initializing built-in extension XINERAMA
[    28.393] (II) Initializing built-in extension XFIXES
[    28.393] (II) Initializing built-in extension RENDER
[    28.393] (II) Initializing built-in extension RANDR
[    28.393] (II) Initializing built-in extension COMPOSITE
[    28.393] (II) Initializing built-in extension DAMAGE
[    28.393] (II) Initializing built-in extension GESTURE
[    28.550] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    28.550] (II) AIGLX: enabled GLX_INTEL_swap_event
[    28.550] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    28.550] (II) AIGLX: enabled GLX_SGI_make_current_read
[    28.551] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    28.551] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[    28.551] (II) GLX: Initialized DRI2 GL provider for screen 0
[    28.552] (II) intel(0): Setting screen physical size to 270 x 203
[    28.794] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.825] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    28.825] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.825] (II) LoadModule: "evdev"
[    28.826] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.876] (II) Module evdev: vendor="X.Org Foundation"
[    28.876]     compiled for 1.9.0, module version = 2.3.2
[    28.876]     Module class: X.Org XInput Driver
[    28.876]     ABI class: X.Org XInput driver, version 11.0
[    28.876] (**) Power Button: always reports core events
[    28.876] (**) Power Button: Device: "/dev/input/event3"
[    28.876] (II) Power Button: Found keys
[    28.876] (II) Power Button: Configuring as keyboard
[    28.876] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.876] (**) Option "xkb_rules" "evdev"
[    28.876] (**) Option "xkb_model" "evdev"
[    28.876] (**) Option "xkb_layout" "fr"
[    28.886] (II) XKB: reuse xkmfile /var/lib/xkb/server-1773A72ADF3912178EB836318CC241E672AD6AB1.xkm
[    28.910] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    28.910] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    28.910] (**) Video Bus: always reports core events
[    28.910] (**) Video Bus: Device: "/dev/input/event5"
[    28.910] (II) Video Bus: Found keys
[    28.910] (II) Video Bus: Configuring as keyboard
[    28.910] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    28.910] (**) Option "xkb_rules" "evdev"
[    28.910] (**) Option "xkb_model" "evdev"
[    28.910] (**) Option "xkb_layout" "fr"
[    28.920] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    28.920] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.920] (**) Power Button: always reports core events
[    28.920] (**) Power Button: Device: "/dev/input/event2"
[    28.920] (II) Power Button: Found keys
[    28.920] (II) Power Button: Configuring as keyboard
[    28.920] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.920] (**) Option "xkb_rules" "evdev"
[    28.920] (**) Option "xkb_model" "evdev"
[    28.920] (**) Option "xkb_layout" "fr"
[    28.921] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    28.921] (II) No input driver/identifier specified (ignoring)
[    28.922] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    28.922] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    28.922] (**) Sleep Button: always reports core events
[    28.922] (**) Sleep Button: Device: "/dev/input/event1"
[    28.922] (II) Sleep Button: Found keys
[    28.922] (II) Sleep Button: Configuring as keyboard
[    28.922] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    28.922] (**) Option "xkb_rules" "evdev"
[    28.922] (**) Option "xkb_model" "evdev"
[    28.922] (**) Option "xkb_layout" "fr"
[    28.936] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    28.937] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    28.937] (**) AT Translated Set 2 keyboard: always reports core events
[    28.937] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    28.937] (II) AT Translated Set 2 keyboard: Found keys
[    28.937] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    28.937] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    28.937] (**) Option "xkb_rules" "evdev"
[    28.937] (**) Option "xkb_model" "evdev"
[    28.937] (**) Option "xkb_layout" "fr"
[    28.938] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    28.938] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    28.938] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    28.938] (II) LoadModule: "synaptics"
[    28.938] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    28.939] (II) Module synaptics: vendor="X.Org Foundation"
[    28.939]     compiled for 1.9.0, module version = 1.2.2
[    28.939]     Module class: X.Org XInput Driver
[    28.939]     ABI class: X.Org XInput driver, version 11.0
[    28.939] (II) Synaptics touchpad driver version 1.2.2
[    28.940] (**) Option "Device" "/dev/input/event6"
[    28.940] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    28.940] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    28.940] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    28.940] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    28.940] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    28.940] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    28.940] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    28.940] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    28.940] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    28.940] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    28.940] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    28.940] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    28.940] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    28.941] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    28.941] (II) No input driver/identifier specified (ignoring)
[    31.812] (II) intel(0): EDID vendor "QDS", prod id 17
[    31.813] (II) intel(0): Printing DDC gathered Modelines:
[    31.813] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    32.156] (II) intel(0): EDID vendor "QDS", prod id 17
[    32.156] (II) intel(0): Printing DDC gathered Modelines:
[    32.156] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    32.546] (II) intel(0): EDID vendor "QDS", prod id 17
[    32.546] (II) intel(0): Printing DDC gathered Modelines:
[    32.546] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    32.891] (II) intel(0): EDID vendor "QDS", prod id 17
[    32.891] (II) intel(0): Printing DDC gathered Modelines:
[    32.891] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   157.449] (II) intel(0): EDID vendor "QDS", prod id 17
[   157.449] (II) intel(0): Printing DDC gathered Modelines:
[   157.449] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   157.768] (II) intel(0): EDID vendor "QDS", prod id 17
[   157.768] (II) intel(0): Printing DDC gathered Modelines:
[   157.768] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   158.081] (II) intel(0): EDID vendor "QDS", prod id 17
[   158.081] (II) intel(0): Printing DDC gathered Modelines:
[   158.081] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   162.068] (II) intel(0): EDID vendor "QDS", prod id 17
[   162.068] (II) intel(0): Printing DDC gathered Modelines:
[   162.068] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   165.741] (II) intel(0): EDID vendor "QDS", prod id 17
[   165.741] (II) intel(0): Printing DDC gathered Modelines:
[   165.741] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[/PHP][COLOR=Red][B]Xorg.1.log
[/B][/COLOR][PHP][   517.569] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   517.569] X Protocol Version 11, Revision 0
[   517.569] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   517.569] Current Operating System: Linux Amilo-M7405 2.6.37-020637rc7-generic #201012221342 SMP Wed Dec 22 14:58:33 UTC 2010 i686
[   517.569] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637rc7-generic root=UUID=53f4ad58-f05f-4972-b816-4105751cba54 ro quiet splash
[   517.570] Build Date: 16 September 2010  05:39:22PM
[   517.570] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   517.570] Current version of pixman: 0.18.4
[   517.570]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   517.570] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   517.570] (==) Log file: "/var/log/Xorg.1.log", Time: Fri Dec 24 20:08:53 2010
[   517.570] (==) Using config file: "/etc/X11/xorg.conf"
[   517.570] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   517.570] (==) No Layout section.  Using the first Screen section.
[   517.570] (**) |-->Screen "Default Screen" (0)
[   517.570] (**) |   |-->Monitor "Configured Monitor"
[   517.571] (**) |   |-->Device "Configured Video Device"
[   517.571] (==) Automatically adding devices
[   517.571] (==) Automatically enabling devices
[   517.571] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   517.571]     Entry deleted from font path.
[   517.571] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   517.571] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   517.571] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   517.571] (II) Loader magic: 0x81f8e00
[   517.571] (II) Module ABI versions:
[   517.571]     X.Org ANSI C Emulation: 0.4
[   517.571]     X.Org Video Driver: 8.0
[   517.571]     X.Org XInput driver : 11.0
[   517.571]     X.Org Server Extension : 4.0
[   517.573] (--) PCI:*(0:0:2:0) 8086:3582:1734:106a rev 2, Mem @ 0xd8000000/134217728, 0xe0380000/524288, I/O @ 0x0000ec00/8
[   517.573] (--) PCI: (0:0:2:1) 8086:3582:1734:106a rev 2, Mem @ 0xd0000000/134217728, 0xe0300000/524288
[   517.573] (II) Open ACPI successful (/var/run/acpid.socket)
[   517.573] (II) LoadModule: "extmod"
[   517.574] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   517.574] (II) Module extmod: vendor="X.Org Foundation"
[   517.574]     compiled for 1.9.0, module version = 1.0.0
[   517.574]     Module class: X.Org Server Extension
[   517.574]     ABI class: X.Org Server Extension, version 4.0
[   517.574] (II) Loading extension MIT-SCREEN-SAVER
[   517.574] (II) Loading extension XFree86-VidModeExtension
[   517.574] (II) Loading extension XFree86-DGA
[   517.574] (II) Loading extension DPMS
[   517.574] (II) Loading extension XVideo
[   517.574] (II) Loading extension XVideo-MotionCompensation
[   517.574] (II) Loading extension X-Resource
[   517.574] (II) LoadModule: "dbe"
[   517.575] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   517.575] (II) Module dbe: vendor="X.Org Foundation"
[   517.575]     compiled for 1.9.0, module version = 1.0.0
[   517.575]     Module class: X.Org Server Extension
[   517.575]     ABI class: X.Org Server Extension, version 4.0
[   517.575] (II) Loading extension DOUBLE-BUFFER
[   517.575] (II) LoadModule: "glx"
[   517.576] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   517.576] (II) Module glx: vendor="X.Org Foundation"
[   517.576]     compiled for 1.9.0, module version = 1.0.0
[   517.576]     ABI class: X.Org Server Extension, version 4.0
[   517.576] (==) AIGLX enabled
[   517.576] (II) Loading extension GLX
[   517.576] (II) LoadModule: "record"
[   517.576] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   517.577] (II) Module record: vendor="X.Org Foundation"
[   517.577]     compiled for 1.9.0, module version = 1.13.0
[   517.577]     Module class: X.Org Server Extension
[   517.577]     ABI class: X.Org Server Extension, version 4.0
[   517.577] (II) Loading extension RECORD
[   517.577] (II) LoadModule: "dri"
[   517.577] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   517.578] (II) Module dri: vendor="X.Org Foundation"
[   517.578]     compiled for 1.9.0, module version = 1.0.0
[   517.578]     ABI class: X.Org Server Extension, version 4.0
[   517.578] (II) Loading extension XFree86-DRI
[   517.578] (II) LoadModule: "dri2"
[   517.578] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   517.578] (II) Module dri2: vendor="X.Org Foundation"
[   517.578]     compiled for 1.9.0, module version = 1.2.0
[   517.578]     ABI class: X.Org Server Extension, version 4.0
[   517.578] (II) Loading extension DRI2
[   517.578] (II) LoadModule: "intel"
[   517.579] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   517.579] (II) Module intel: vendor="X.Org Foundation"
[   517.579]     compiled for 1.9.0, module version = 2.12.0
[   517.579]     Module class: X.Org Video Driver
[   517.579]     ABI class: X.Org Video Driver, version 8.0
[   517.579] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[   517.580] (--) using VT number 8

[   517.674] drmOpenDevice: node name is /dev/dri/card0
[   517.674] drmOpenDevice: open result is 9, (OK)
[   517.674] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   517.674] drmOpenDevice: node name is /dev/dri/card0
[   517.674] drmOpenDevice: open result is 9, (OK)
[   517.674] drmOpenByBusid: drmOpenMinor returns 9
[   517.674] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   517.674] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[   517.674] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   517.674] (==) intel(0): RGB weight 888
[   517.674] (==) intel(0): Default visual is TrueColor
[   517.674] (II) intel(0): Integrated Graphics Chipset: Intel(R) 855GME
[   517.674] (--) intel(0): Chipset: "852GM/855GM"
[   517.674] (==) intel(0): video overlay key set to 0x101fe
[   517.674] (II) intel(0): Output LVDS1 using monitor section Configured Monitor
[   518.060] (II) intel(0): Output VGA1 has no monitor section
[   518.078] (II) intel(0): Output DVI1 has no monitor section
[   518.079] (II) intel(0): EDID for output LVDS1
[   518.079] (II) intel(0): Manufacturer: QDS  Model: 11  Serial#: 0
[   518.079] (II) intel(0): Year: 2094  Week: 29
[   518.079] (II) intel(0): EDID Version: 1.2
[   518.079] (II) intel(0): Digital Display Input
[   518.079] (II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 23
[   518.079] (II) intel(0): Gamma: 2.20
[   518.079] (II) intel(0): No DPMS capabilities specified
[   518.079] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   518.079] (II) intel(0): First detailed timing is preferred mode
[   518.079] (II) intel(0): redX: 0.591 redY: 0.325   greenX: 0.314 greenY: 0.562
[   518.079] (II) intel(0): blueX: 0.137 blueY: 0.119   whiteX: 0.312 whiteY: 0.328
[   518.079] (II) intel(0): Manufacturer's mask: 0
[   518.079] (II) intel(0): Supported detailed timing:
[   518.079] (II) intel(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
[   518.079] (II) intel(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[   518.079] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[   518.079] (II) intel(0): Unknown vendor-specific block f
[   518.079] (II) intel(0):  JFM4712152326
[   518.079] (II) intel(0):  QD15XL061
[   518.079] (II) intel(0): EDID (in hex):
[   518.079] (II) intel(0):     00ffffffffffff004493110000000000
[   518.079] (II) intel(0):     1d680102801e17780a58209753509023
[   518.079] (II) intel(0):     1e505400000001010101010101010101
[   518.079] (II) intel(0):     01010101010164190040410026301888
[   518.079] (II) intel(0):     360030e4100000190000000f0004c02e
[   518.079] (II) intel(0):     c00211111176c0126301000000fe004a
[   518.079] (II) intel(0):     464d34373132313532333236000000fe
[   518.079] (II) intel(0):     0051443135584c3036310a20202000a5
[   518.079] (II) intel(0): EDID vendor "QDS", prod id 17
[   518.079] (II) intel(0): Printing DDC gathered Modelines:
[   518.079] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   518.084] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[   518.084] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[   518.084] (II) intel(0): Printing probed modes for output LVDS1
[   518.084] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   518.084] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   518.084] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   518.084] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   518.422] (II) intel(0): EDID for output VGA1
[   518.459] (II) intel(0): EDID for output DVI1
[   518.459] (II) intel(0): Output LVDS1 connected
[   518.459] (II) intel(0): Output VGA1 disconnected
[   518.459] (II) intel(0): Output DVI1 disconnected
[   518.459] (II) intel(0): Using exact sizes for initial modes
[   518.459] (II) intel(0): Output LVDS1 using initial mode 1024x768
[   518.459] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   518.459] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[   518.459] (**) intel(0): Display dimensions: (300, 230) mm
[   518.460] (**) intel(0): DPI set to (86, 84)
[   518.460] (II) Loading sub module "fb"
[   518.460] (II) LoadModule: "fb"
[   518.460] (II) Loading /usr/lib/xorg/modules/libfb.so
[   518.460] (II) Module fb: vendor="X.Org Foundation"
[   518.460]     compiled for 1.9.0, module version = 1.0.0
[   518.460]     ABI class: X.Org ANSI C Emulation, version 0.4
[   518.460] (==) Depth 24 pixmap format is 32 bpp
[   518.461] (II) intel(0): [DRI2] Setup complete
[   518.461] (II) intel(0): [DRI2]   DRI driver: i915
[   518.461] (**) intel(0): Tiling enabled
[   518.461] (**) intel(0): SwapBuffers wait enabled
[   518.461] (==) intel(0): VideoRam: 131072 KB
[   518.461] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[   518.461] (II) UXA(0): Driver registered support for the following operations:
[   518.461] (II)         solid
[   518.461] (II)         copy
[   518.461] (II)         composite (RENDER acceleration)
[   518.461] (II)         put_image
[   518.461] (II)         get_image
[   518.461] (==) intel(0): Backing store disabled
[   518.461] (==) intel(0): Silken mouse enabled
[   518.461] (II) intel(0): Initializing HW Cursor
[   518.491] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   518.492] (==) intel(0): DPMS enabled
[   518.492] (==) intel(0): Intel XvMC decoder disabled
[   518.492] (II) intel(0): Set up overlay video
[   518.492] (II) intel(0): direct rendering: DRI2 Enabled
[   518.493] (--) RandR disabled
[   518.493] (II) Initializing built-in extension Generic Event Extension
[   518.493] (II) Initializing built-in extension SHAPE
[   518.493] (II) Initializing built-in extension MIT-SHM
[   518.493] (II) Initializing built-in extension XInputExtension
[   518.493] (II) Initializing built-in extension XTEST
[   518.493] (II) Initializing built-in extension BIG-REQUESTS
[   518.493] (II) Initializing built-in extension SYNC
[   518.493] (II) Initializing built-in extension XKEYBOARD
[   518.493] (II) Initializing built-in extension XC-MISC
[   518.493] (II) Initializing built-in extension SECURITY
[   518.493] (II) Initializing built-in extension XINERAMA
[   518.493] (II) Initializing built-in extension XFIXES
[   518.493] (II) Initializing built-in extension RENDER
[   518.493] (II) Initializing built-in extension RANDR
[   518.493] (II) Initializing built-in extension COMPOSITE
[   518.493] (II) Initializing built-in extension DAMAGE
[   518.493] (II) Initializing built-in extension GESTURE
[   518.558] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   518.558] (II) AIGLX: enabled GLX_INTEL_swap_event
[   518.558] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   518.558] (II) AIGLX: enabled GLX_SGI_make_current_read
[   518.558] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   518.559] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[   518.559] (II) GLX: Initialized DRI2 GL provider for screen 0
[   518.560] (II) intel(0): Setting screen physical size to 270 x 203
[   518.653] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   518.679] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   518.679] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   518.679] (II) LoadModule: "evdev"
[   518.690] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   518.690] (II) Module evdev: vendor="X.Org Foundation"
[   518.690]     compiled for 1.9.0, module version = 2.3.2
[   518.690]     Module class: X.Org XInput Driver
[   518.690]     ABI class: X.Org XInput driver, version 11.0
[   518.690] (**) Power Button: always reports core events
[   518.690] (**) Power Button: Device: "/dev/input/event3"
[   518.690] (II) Power Button: Found keys
[   518.690] (II) Power Button: Configuring as keyboard
[   518.691] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   518.691] (**) Option "xkb_rules" "evdev"
[   518.691] (**) Option "xkb_model" "evdev"
[   518.691] (**) Option "xkb_layout" "fr"
[   518.695] (II) XKB: reuse xkmfile /var/lib/xkb/server-1773A72ADF3912178EB836318CC241E672AD6AB1.xkm
[   518.707] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[   518.709] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   518.709] (**) Video Bus: always reports core events
[   518.709] (**) Video Bus: Device: "/dev/input/event5"
[   518.710] (II) Video Bus: Found keys
[   518.710] (II) Video Bus: Configuring as keyboard
[   518.710] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   518.710] (**) Option "xkb_rules" "evdev"
[   518.710] (**) Option "xkb_model" "evdev"
[   518.710] (**) Option "xkb_layout" "fr"
[   518.711] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   518.711] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   518.711] (**) Power Button: always reports core events
[   518.711] (**) Power Button: Device: "/dev/input/event2"
[   518.711] (II) Power Button: Found keys
[   518.711] (II) Power Button: Configuring as keyboard
[   518.711] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   518.712] (**) Option "xkb_rules" "evdev"
[   518.712] (**) Option "xkb_model" "evdev"
[   518.712] (**) Option "xkb_layout" "fr"
[   518.712] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   518.712] (II) No input driver/identifier specified (ignoring)
[   518.713] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   518.713] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   518.713] (**) Sleep Button: always reports core events
[   518.713] (**) Sleep Button: Device: "/dev/input/event1"
[   518.713] (II) Sleep Button: Found keys
[   518.713] (II) Sleep Button: Configuring as keyboard
[   518.713] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   518.713] (**) Option "xkb_rules" "evdev"
[   518.713] (**) Option "xkb_model" "evdev"
[   518.713] (**) Option "xkb_layout" "fr"
[   518.729] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   518.729] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   518.729] (**) AT Translated Set 2 keyboard: always reports core events
[   518.729] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   518.729] (II) AT Translated Set 2 keyboard: Found keys
[   518.730] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   518.730] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   518.730] (**) Option "xkb_rules" "evdev"
[   518.730] (**) Option "xkb_model" "evdev"
[   518.730] (**) Option "xkb_layout" "fr"
[   518.730] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[   518.730] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   518.730] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   518.730] (II) LoadModule: "synaptics"
[   518.731] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   518.731] (II) Module synaptics: vendor="X.Org Foundation"
[   518.731]     compiled for 1.9.0, module version = 1.2.2
[   518.731]     Module class: X.Org XInput Driver
[   518.731]     ABI class: X.Org XInput driver, version 11.0
[   518.731] (II) Synaptics touchpad driver version 1.2.2
[   518.731] (**) Option "Device" "/dev/input/event6"
[   518.731] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[   518.731] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[   518.731] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   518.731] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   518.731] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[   518.741] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   518.742] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   518.742] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   518.742] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   518.742] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[   518.742] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   518.742] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   518.742] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   518.742] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   518.742] (II) No input driver/identifier specified (ignoring)
[   519.424] (II) intel(0): EDID vendor "QDS", prod id 17
[   519.424] (II) intel(0): Printing DDC gathered Modelines:
[   519.424] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   519.783] (II) intel(0): EDID vendor "QDS", prod id 17
[   519.783] (II) intel(0): Printing DDC gathered Modelines:
[   519.783] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   520.126] (II) intel(0): EDID vendor "QDS", prod id 17
[   520.126] (II) intel(0): Printing DDC gathered Modelines:
[   520.126] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   520.428] (II) intel(0): EDID vendor "QDS", prod id 17
[   520.428] (II) intel(0): Printing DDC gathered Modelines:
[   520.428] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   521.288] (II) intel(0): EDID vendor "QDS", prod id 17
[   521.288] (II) intel(0): Printing DDC gathered Modelines:
[   521.288] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   537.614] (II) intel(0): EDID vendor "QDS", prod id 17
[   537.614] (II) intel(0): Printing DDC gathered Modelines:
[   537.615] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   537.928] (II) intel(0): EDID vendor "QDS", prod id 17
[   537.928] (II) intel(0): Printing DDC gathered Modelines:
[   537.928] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   538.241] (II) intel(0): EDID vendor "QDS", prod id 17
[   538.241] (II) intel(0): Printing DDC gathered Modelines:
[   538.241] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   538.557] (II) intel(0): EDID vendor "QDS", prod id 17
[   538.557] (II) intel(0): Printing DDC gathered Modelines:
[   538.557] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   539.128] (II) intel(0): EDID vendor "QDS", prod id 17
[   539.128] (II) intel(0): Printing DDC gathered Modelines:
[   539.128] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   540.683] (II) intel(0): EDID vendor "QDS", prod id 17
[   540.684] (II) intel(0): Printing DDC gathered Modelines:
[   540.684] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   544.064] (II) intel(0): EDID vendor "QDS", prod id 17
[   544.064] (II) intel(0): Printing DDC gathered Modelines:
[   544.064] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   599.865] (II) AIGLX: Suspending AIGLX clients for VT switch
[   676.383] (II) Open ACPI successful (/var/run/acpid.socket)
[   676.383] (II) AIGLX: Resuming AIGLX clients after VT switch
[   676.393] (II) intel(0): EDID vendor "QDS", prod id 17
[   676.393] (II) intel(0): Printing DDC gathered Modelines:
[   676.393] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   676.806] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   676.912] (II) Power Button: Device reopened after 1 attempts.
[   676.912] (II) Video Bus: Device reopened after 1 attempts.
[   676.912] (II) Power Button: Device reopened after 1 attempts.
[   676.912] (II) Sleep Button: Device reopened after 1 attempts.
[   676.912] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[/PHP][COLOR=Red]**Xorg.2.log**[/COLOR]
[PHP][   658.539] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   658.539] X Protocol Version 11, Revision 0
[   658.539] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   658.539] Current Operating System: Linux Amilo-M7405 2.6.37-020637rc7-generic #201012221342 SMP Wed Dec 22 14:58:33 UTC 2010 i686
[   658.539] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637rc7-generic root=UUID=53f4ad58-f05f-4972-b816-4105751cba54 ro quiet splash
[   658.539] Build Date: 16 September 2010  05:39:22PM
[   658.539] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   658.539] Current version of pixman: 0.18.4
[   658.539]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   658.539] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   658.539] (==) Log file: "/var/log/Xorg.2.log", Time: Fri Dec 24 20:11:14 2010
[   658.539] (==) Using config file: "/etc/X11/xorg.conf"
[   658.539] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   658.540] (==) No Layout section.  Using the first Screen section.
[   658.540] (**) |-->Screen "Default Screen" (0)
[   658.540] (**) |   |-->Monitor "Configured Monitor"
[   658.540] (**) |   |-->Device "Configured Video Device"
[   658.540] (==) Automatically adding devices
[   658.540] (==) Automatically enabling devices
[   658.540] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   658.540]     Entry deleted from font path.
[   658.540] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   658.540] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   658.540] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   658.540] (II) Loader magic: 0x81f8e00
[   658.540] (II) Module ABI versions:
[   658.540]     X.Org ANSI C Emulation: 0.4
[   658.540]     X.Org Video Driver: 8.0
[   658.540]     X.Org XInput driver : 11.0
[   658.540]     X.Org Server Extension : 4.0
[   658.541] (--) PCI:*(0:0:2:0) 8086:3582:1734:106a rev 2, Mem @ 0xd8000000/134217728, 0xe0380000/524288, I/O @ 0x0000ec00/8
[   658.542] (--) PCI: (0:0:2:1) 8086:3582:1734:106a rev 2, Mem @ 0xd0000000/134217728, 0xe0300000/524288
[   658.542] (II) Open ACPI successful (/var/run/acpid.socket)
[   658.542] (II) LoadModule: "extmod"
[   658.543] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   658.543] (II) Module extmod: vendor="X.Org Foundation"
[   658.543]     compiled for 1.9.0, module version = 1.0.0
[   658.543]     Module class: X.Org Server Extension
[   658.543]     ABI class: X.Org Server Extension, version 4.0
[   658.543] (II) Loading extension MIT-SCREEN-SAVER
[   658.543] (II) Loading extension XFree86-VidModeExtension
[   658.543] (II) Loading extension XFree86-DGA
[   658.543] (II) Loading extension DPMS
[   658.543] (II) Loading extension XVideo
[   658.543] (II) Loading extension XVideo-MotionCompensation
[   658.543] (II) Loading extension X-Resource
[   658.543] (II) LoadModule: "dbe"
[   658.544] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   658.544] (II) Module dbe: vendor="X.Org Foundation"
[   658.544]     compiled for 1.9.0, module version = 1.0.0
[   658.544]     Module class: X.Org Server Extension
[   658.544]     ABI class: X.Org Server Extension, version 4.0
[   658.544] (II) Loading extension DOUBLE-BUFFER
[   658.544] (II) LoadModule: "glx"
[   658.544] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   658.545] (II) Module glx: vendor="X.Org Foundation"
[   658.545]     compiled for 1.9.0, module version = 1.0.0
[   658.545]     ABI class: X.Org Server Extension, version 4.0
[   658.545] (==) AIGLX enabled
[   658.545] (II) Loading extension GLX
[   658.545] (II) LoadModule: "record"
[   658.545] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   658.545] (II) Module record: vendor="X.Org Foundation"
[   658.545]     compiled for 1.9.0, module version = 1.13.0
[   658.545]     Module class: X.Org Server Extension
[   658.545]     ABI class: X.Org Server Extension, version 4.0
[   658.545] (II) Loading extension RECORD
[   658.545] (II) LoadModule: "dri"
[   658.546] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   658.546] (II) Module dri: vendor="X.Org Foundation"
[   658.546]     compiled for 1.9.0, module version = 1.0.0
[   658.546]     ABI class: X.Org Server Extension, version 4.0
[   658.546] (II) Loading extension XFree86-DRI
[   658.546] (II) LoadModule: "dri2"
[   658.547] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   658.547] (II) Module dri2: vendor="X.Org Foundation"
[   658.547]     compiled for 1.9.0, module version = 1.2.0
[   658.547]     ABI class: X.Org Server Extension, version 4.0
[   658.547] (II) Loading extension DRI2
[   658.547] (II) LoadModule: "intel"
[   658.547] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   658.548] (II) Module intel: vendor="X.Org Foundation"
[   658.548]     compiled for 1.9.0, module version = 2.12.0
[   658.548]     Module class: X.Org Video Driver
[   658.548]     ABI class: X.Org Video Driver, version 8.0
[   658.548] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[   658.549] (--) using VT number 9

[   658.656] drmOpenDevice: node name is /dev/dri/card0
[   658.656] drmOpenDevice: open result is 9, (OK)
[   658.656] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   658.656] drmOpenDevice: node name is /dev/dri/card0
[   658.656] drmOpenDevice: open result is 9, (OK)
[   658.656] drmOpenByBusid: drmOpenMinor returns 9
[   658.656] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   658.656] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[   658.656] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   658.656] (==) intel(0): RGB weight 888
[   658.656] (==) intel(0): Default visual is TrueColor
[   658.656] (II) intel(0): Integrated Graphics Chipset: Intel(R) 855GME
[   658.656] (--) intel(0): Chipset: "852GM/855GM"
[   658.656] (==) intel(0): video overlay key set to 0x101fe
[   658.657] (II) intel(0): Output LVDS1 using monitor section Configured Monitor
[   659.029] (II) intel(0): Output VGA1 has no monitor section
[   659.053] (II) intel(0): Output DVI1 has no monitor section
[   659.053] (II) intel(0): EDID for output LVDS1
[   659.053] (II) intel(0): Manufacturer: QDS  Model: 11  Serial#: 0
[   659.053] (II) intel(0): Year: 2094  Week: 29
[   659.053] (II) intel(0): EDID Version: 1.2
[   659.053] (II) intel(0): Digital Display Input
[   659.053] (II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 23
[   659.053] (II) intel(0): Gamma: 2.20
[   659.053] (II) intel(0): No DPMS capabilities specified
[   659.053] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   659.053] (II) intel(0): First detailed timing is preferred mode
[   659.053] (II) intel(0): redX: 0.591 redY: 0.325   greenX: 0.314 greenY: 0.562
[   659.053] (II) intel(0): blueX: 0.137 blueY: 0.119   whiteX: 0.312 whiteY: 0.328
[   659.053] (II) intel(0): Manufacturer's mask: 0
[   659.053] (II) intel(0): Supported detailed timing:
[   659.053] (II) intel(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
[   659.053] (II) intel(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[   659.053] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[   659.053] (II) intel(0): Unknown vendor-specific block f
[   659.053] (II) intel(0):  JFM4712152326
[   659.053] (II) intel(0):  QD15XL061
[   659.053] (II) intel(0): EDID (in hex):
[   659.053] (II) intel(0):     00ffffffffffff004493110000000000
[   659.053] (II) intel(0):     1d680102801e17780a58209753509023
[   659.053] (II) intel(0):     1e505400000001010101010101010101
[   659.053] (II) intel(0):     01010101010164190040410026301888
[   659.054] (II) intel(0):     360030e4100000190000000f0004c02e
[   659.054] (II) intel(0):     c00211111176c0126301000000fe004a
[   659.054] (II) intel(0):     464d34373132313532333236000000fe
[   659.054] (II) intel(0):     0051443135584c3036310a20202000a5
[   659.054] (II) intel(0): EDID vendor "QDS", prod id 17
[   659.054] (II) intel(0): Printing DDC gathered Modelines:
[   659.054] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   659.054] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[   659.054] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[   659.054] (II) intel(0): Printing probed modes for output LVDS1
[   659.054] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   659.054] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   659.054] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   659.054] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   659.349] (II) intel(0): EDID for output VGA1
[   659.377] (II) intel(0): EDID for output DVI1
[   659.377] (II) intel(0): Output LVDS1 connected
[   659.377] (II) intel(0): Output VGA1 disconnected
[   659.377] (II) intel(0): Output DVI1 disconnected
[   659.377] (II) intel(0): Using exact sizes for initial modes
[   659.377] (II) intel(0): Output LVDS1 using initial mode 1024x768
[   659.377] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   659.377] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[   659.377] (**) intel(0): Display dimensions: (300, 230) mm
[   659.377] (**) intel(0): DPI set to (86, 84)
[   659.377] (II) Loading sub module "fb"
[   659.377] (II) LoadModule: "fb"
[   659.378] (II) Loading /usr/lib/xorg/modules/libfb.so
[   659.378] (II) Module fb: vendor="X.Org Foundation"
[   659.378]     compiled for 1.9.0, module version = 1.0.0
[   659.378]     ABI class: X.Org ANSI C Emulation, version 0.4
[   659.378] (==) Depth 24 pixmap format is 32 bpp
[   659.378] (II) intel(0): [DRI2] Setup complete
[   659.378] (II) intel(0): [DRI2]   DRI driver: i915
[   659.378] (**) intel(0): Tiling enabled
[   659.379] (**) intel(0): SwapBuffers wait enabled
[   659.379] (==) intel(0): VideoRam: 131072 KB
[   659.379] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[   659.379] (II) UXA(0): Driver registered support for the following operations:
[   659.379] (II)         solid
[   659.379] (II)         copy
[   659.379] (II)         composite (RENDER acceleration)
[   659.379] (II)         put_image
[   659.379] (II)         get_image
[   659.379] (==) intel(0): Backing store disabled
[   659.379] (==) intel(0): Silken mouse enabled
[   659.379] (II) intel(0): Initializing HW Cursor
[   659.413] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   659.414] (==) intel(0): DPMS enabled
[   659.414] (==) intel(0): Intel XvMC decoder disabled
[   659.414] (II) intel(0): Set up overlay video
[   659.414] (II) intel(0): direct rendering: DRI2 Enabled
[   659.414] (--) RandR disabled
[   659.414] (II) Initializing built-in extension Generic Event Extension
[   659.414] (II) Initializing built-in extension SHAPE
[   659.414] (II) Initializing built-in extension MIT-SHM
[   659.414] (II) Initializing built-in extension XInputExtension
[   659.414] (II) Initializing built-in extension XTEST
[   659.414] (II) Initializing built-in extension BIG-REQUESTS
[   659.414] (II) Initializing built-in extension SYNC
[   659.414] (II) Initializing built-in extension XKEYBOARD
[   659.414] (II) Initializing built-in extension XC-MISC
[   659.414] (II) Initializing built-in extension SECURITY
[   659.414] (II) Initializing built-in extension XINERAMA
[   659.414] (II) Initializing built-in extension XFIXES
[   659.414] (II) Initializing built-in extension RENDER
[   659.414] (II) Initializing built-in extension RANDR
[   659.414] (II) Initializing built-in extension COMPOSITE
[   659.414] (II) Initializing built-in extension DAMAGE
[   659.414] (II) Initializing built-in extension GESTURE
[   659.475] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   659.475] (II) AIGLX: enabled GLX_INTEL_swap_event
[   659.475] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   659.475] (II) AIGLX: enabled GLX_SGI_make_current_read
[   659.475] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   659.475] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[   659.475] (II) GLX: Initialized DRI2 GL provider for screen 0
[   659.480] (II) intel(0): Setting screen physical size to 270 x 203
[   659.571] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   659.606] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   659.606] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   659.606] (II) LoadModule: "evdev"
[   659.606] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   659.607] (II) Module evdev: vendor="X.Org Foundation"
[   659.607]     compiled for 1.9.0, module version = 2.3.2
[   659.607]     Module class: X.Org XInput Driver
[   659.607]     ABI class: X.Org XInput driver, version 11.0
[   659.607] (**) Power Button: always reports core events
[   659.607] (**) Power Button: Device: "/dev/input/event3"
[   659.607] (II) Power Button: Found keys
[   659.607] (II) Power Button: Configuring as keyboard
[   659.607] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   659.607] (**) Option "xkb_rules" "evdev"
[   659.607] (**) Option "xkb_model" "evdev"
[   659.607] (**) Option "xkb_layout" "fr"
[   659.625] (II) XKB: reuse xkmfile /var/lib/xkb/server-1773A72ADF3912178EB836318CC241E672AD6AB1.xkm
[   659.626] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[   659.626] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   659.626] (**) Video Bus: always reports core events
[   659.626] (**) Video Bus: Device: "/dev/input/event5"
[   659.626] (II) Video Bus: Found keys
[   659.626] (II) Video Bus: Configuring as keyboard
[   659.626] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   659.626] (**) Option "xkb_rules" "evdev"
[   659.626] (**) Option "xkb_model" "evdev"
[   659.626] (**) Option "xkb_layout" "fr"
[   659.638] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   659.638] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   659.638] (**) Power Button: always reports core events
[   659.638] (**) Power Button: Device: "/dev/input/event2"
[   659.638] (II) Power Button: Found keys
[   659.638] (II) Power Button: Configuring as keyboard
[   659.638] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   659.638] (**) Option "xkb_rules" "evdev"
[   659.638] (**) Option "xkb_model" "evdev"
[   659.638] (**) Option "xkb_layout" "fr"
[   659.639] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   659.639] (II) No input driver/identifier specified (ignoring)
[   659.639] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   659.639] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   659.639] (**) Sleep Button: always reports core events
[   659.639] (**) Sleep Button: Device: "/dev/input/event1"
[   659.639] (II) Sleep Button: Found keys
[   659.639] (II) Sleep Button: Configuring as keyboard
[   659.639] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   659.639] (**) Option "xkb_rules" "evdev"
[   659.639] (**) Option "xkb_model" "evdev"
[   659.639] (**) Option "xkb_layout" "fr"
[   659.659] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   659.659] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   659.660] (**) AT Translated Set 2 keyboard: always reports core events
[   659.660] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   659.660] (II) AT Translated Set 2 keyboard: Found keys
[   659.660] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   659.660] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   659.660] (**) Option "xkb_rules" "evdev"
[   659.660] (**) Option "xkb_model" "evdev"
[   659.660] (**) Option "xkb_layout" "fr"
[   659.661] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[   659.661] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   659.661] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   659.661] (II) LoadModule: "synaptics"
[   659.661] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   659.661] (II) Module synaptics: vendor="X.Org Foundation"
[   659.661]     compiled for 1.9.0, module version = 1.2.2
[   659.661]     Module class: X.Org XInput Driver
[   659.661]     ABI class: X.Org XInput driver, version 11.0
[   659.661] (II) Synaptics touchpad driver version 1.2.2
[   659.661] (**) Option "Device" "/dev/input/event6"
[   659.662] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[   659.662] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[   659.662] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   659.662] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   659.662] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[   659.662] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   659.662] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   659.662] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   659.662] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   659.662] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[   659.662] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   659.662] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   659.662] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   659.663] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   659.663] (II) No input driver/identifier specified (ignoring)
[   660.414] (II) intel(0): EDID vendor "QDS", prod id 17
[   660.414] (II) intel(0): Printing DDC gathered Modelines:
[   660.414] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   660.751] (II) intel(0): EDID vendor "QDS", prod id 17
[   660.751] (II) intel(0): Printing DDC gathered Modelines:
[   660.751] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   661.086] (II) intel(0): EDID vendor "QDS", prod id 17
[   661.086] (II) intel(0): Printing DDC gathered Modelines:
[   661.086] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   661.396] (II) intel(0): EDID vendor "QDS", prod id 17
[   661.396] (II) intel(0): Printing DDC gathered Modelines:
[   661.396] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   662.288] (II) intel(0): EDID vendor "QDS", prod id 17
[   662.288] (II) intel(0): Printing DDC gathered Modelines:
[   662.288] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   676.381] (II) AIGLX: Suspending AIGLX clients for VT switch
[/PHP][B][COLOR=Red]alternatives.log
[/COLOR][/B][PHP]empty[/PHP][B][COLOR=Red]alternatives.log.1
[/COLOR][/B][PHP]empty[/PHP][B][COLOR=Red]
auth.log
[/COLOR][/B][PHP]Jan  9 12:20:01 Amilo-M7405 su[1886]: Successful su for fab by root
Jan  9 12:20:01 Amilo-M7405 su[1886]: + ??? root:fab
Jan  9 12:20:01 Amilo-M7405 su[1886]: pam_unix(su:session): session opened for user fab by (uid=0)
Jan  9 12:20:01 Amilo-M7405 su[1886]: pam_unix(su:session): session closed for user fab
Jan  9 12:20:02 Amilo-M7405 su[1899]: Successful su for fab by root
Jan  9 12:20:02 Amilo-M7405 su[1899]: + ??? root:fab
Jan  9 12:20:02 Amilo-M7405 su[1899]: pam_unix(su:session): session opened for user fab by (uid=0)
Jan  9 12:20:02 Amilo-M7405 su[1899]: pam_unix(su:session): session closed for user fab
Jan  9 12:20:02 Amilo-M7405 su[1916]: Successful su for fab by root
Jan  9 12:20:02 Amilo-M7405 su[1916]: + ??? root:fab
Jan  9 12:20:02 Amilo-M7405 su[1916]: pam_unix(su:session): session opened for user fab by (uid=0)
Jan  9 12:20:02 Amilo-M7405 su[1916]: pam_unix(su:session): session closed for user fab
Jan  9 12:20:02 Amilo-M7405 su[1945]: Successful su for fab by root
Jan  9 12:20:02 Amilo-M7405 su[1945]: + ??? root:fab
Jan  9 12:20:02 Amilo-M7405 su[1945]: pam_unix(su:session): session opened for user fab by (uid=0)
Jan  9 12:20:02 Amilo-M7405 su[1945]: pam_unix(su:session): session closed for user fab
Jan  9 12:20:02 Amilo-M7405 su[1957]: Successful su for fab by root
Jan  9 12:20:02 Amilo-M7405 su[1957]: + ??? root:fab
Jan  9 12:20:02 Amilo-M7405 su[1957]: pam_unix(su:session): session opened for user fab by (uid=0)
Jan  9 12:20:02 Amilo-M7405 su[1957]: pam_unix(su:session): session closed for user fab
Jan  9 12:20:02 Amilo-M7405 su[1975]: Successful su for fab by root
Jan  9 12:20:02 Amilo-M7405 su[1975]: + ??? root:fab
Jan  9 12:20:02 Amilo-M7405 su[1975]: pam_unix(su:session): session opened for user fab by (uid=0)
Jan  9 12:20:02 Amilo-M7405 su[1975]: pam_unix(su:session): session closed for user fab
Jan  9 12:20:02 Amilo-M7405 su[1990]: Successful su for fab by root
Jan  9 12:20:02 Amilo-M7405 su[1990]: + ??? root:fab
Jan  9 12:20:02 Amilo-M7405 su[1990]: pam_unix(su:session): session opened for user fab by (uid=0)
Jan  9 12:20:02 Amilo-M7405 su[1990]: pam_unix(su:session): session closed for user fab
Jan  9 12:20:02 Amilo-M7405 su[2006]: Successful su for fab by root
Jan  9 12:20:02 Amilo-M7405 su[2006]: + ??? root:fab
Jan  9 12:20:02 Amilo-M7405 su[2006]: pam_unix(su:session): session opened for user fab by (uid=0)
Jan  9 12:20:02 Amilo-M7405 su[2006]: pam_unix(su:session): session closed for user fab
Jan  9 12:20:02 Amilo-M7405 su[2021]: Successful su for fab by root
Jan  9 12:20:02 Amilo-M7405 su[2021]: + ??? root:fab
Jan  9 12:20:02 Amilo-M7405 su[2021]: pam_unix(su:session): session opened for user fab by (uid=0)
Jan  9 12:20:02 Amilo-M7405 su[2021]: pam_unix(su:session): session closed for user fab
Jan  9 13:17:01 Amilo-M7405 CRON[1263]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 13:17:01 Amilo-M7405 CRON[1263]: pam_unix(cron:session): session closed for user root
Jan  9 13:18:30 Amilo-M7405 gdm-session-worker[1047]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "fab"
Jan  9 13:18:38 Amilo-M7405 gdm-session-worker[1047]: pam_unix(gdm:session): session opened for user fab by (uid=0)
Jan  9 13:18:38 Amilo-M7405 gdm-session-worker[1047]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  9 13:18:44 Amilo-M7405 polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.29 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale fr_FR.utf8)
Jan  9 13:18:58 Amilo-M7405 dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.38" (uid=1000 pid=1399 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=734 comm="/usr/sbin/console-kit-daemon))
Jan  9 13:20:55 Amilo-M7405 sudo:      fab : TTY=unknown ; PWD=/home/fab ; USER=root ; COMMAND=/usr/bin/gnome-system-log
[/PHP] [B][COLOR=Red]boot
[/COLOR][/B][PHP](Nothing has been logged yet.)[/PHP]  [B][COLOR=Red]boot.log
  [/COLOR][/B][PHP]FATAL: Error inserting crc32c_intel (/lib/modules/2.6.37-020637-generic/kernel/arch/x86/crypto/crc32c-intel.ko): No such device 
init: ureadahead main process (258) terminated with status 5  
fsck de util-linux-ng 2.17.2 
/dev/sda1 : propre, 211914/4882432 fichiers, 2001549/19513856 blocs (vérification dans 5 montages) 
 * Starting AppArmor profiles       [128G Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.) 
Warning from /etc/apparmor.d/gdm-guest-session (/etc/apparmor.d/gdm-guest-session line 48): profile /usr/share/gdm/guest-session/Xsession network rules not enforced 
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.) 
Warning from /etc/apparmor.d/sbin.dhclient3 (/etc/apparmor.d/sbin.dhclient3 line 73): profile /sbin/dhclient3 network rules not enforced 
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.) 
[/PHP]**[COLOR=Red]bootstrap.log[/COLOR]**[PHP]warning, in file '/var/lib/dpkg/status' near line 3 package 'dpkg':
 missing description
warning, in file '/var/lib/dpkg/status' near line 3 package 'dpkg':
 missing maintainer
Selecting previously deselected package base-files.
dpkg: regarding .../base-files_5.0.0ubuntu23_i386.deb containing base-files, pre-dependency problem:
 base-files pre-depends on awk
  awk is not installed.
dpkg: warning: ignoring pre-dependency problem!
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_5.0.0ubuntu23_i386.deb) ...
Selecting previously deselected package base-passwd.
Unpacking base-passwd (from .../base-passwd_3.5.22_i386.deb) ...
dpkg: base-passwd: dependency problems, but configuring anyway as you requested:
 base-passwd depends on libc6 (>= 2.8); however:
  Package libc6 is not installed.
Setting up base-passwd (3.5.22) ...
dpkg: base-files: dependency problems, but configuring anyway as you requested:
 base-files depends on awk; however:
  Package awk is not installed.
 base-files depends on libpam-modules (>= 0.79-3ubuntu3); however:
  Package libpam-modules is not installed.
Setting up base-files (5.0.0ubuntu23) ...
warning, in file '/var/lib/dpkg/status' near line 48 package 'dpkg':
 missing description
warning, in file '/var/lib/dpkg/status' near line 48 package 'dpkg':
 missing maintainer
dpkg: regarding .../dpkg_1.15.8.4ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on libbz2-1.0
  libbz2-1.0 is not installed.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../dpkg_1.15.8.4ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on libc6 (>= 2.11)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../dpkg_1.15.8.4ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on libselinux1 (>= 1.32)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../dpkg_1.15.8.4ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on zlib1g (>= 1:1.1.4)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../dpkg_1.15.8.4ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on coreutils (>= 5.93-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../dpkg_1.15.8.4ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on xz-utils
  xz-utils is not installed.
dpkg: warning: ignoring pre-dependency problem!
(Reading database ... 108 files and directories currently installed.)
Preparing to replace dpkg 1.15.8.4ubuntu3 (using .../dpkg_1.15.8.4ubuntu3_i386.deb) ...
Unpacking replacement dpkg ...
dpkg: dpkg: dependency problems, but configuring anyway as you requested:
 dpkg depends on libbz2-1.0; however:
  Package libbz2-1.0 is not installed.
 dpkg depends on libc6 (>= 2.11); however:
  Package libc6 is not installed.
 dpkg depends on libselinux1 (>= 1.32); however:
  Package libselinux1 is not installed.
 dpkg depends on zlib1g (>= 1:1.1.4); however:
  Package zlib1g is not installed.
 dpkg depends on coreutils (>= 5.93-1); however:
  Package coreutils is not installed.
 dpkg depends on xz-utils; however:
  Package xz-utils is not installed.
Setting up dpkg (1.15.8.4ubuntu3) ...
Selecting previously deselected package libc6.
(Reading database ... 354 files and directories currently installed.)
Unpacking libc6 (from .../libc6_2.12.1-0ubuntu6_i386.deb) ...
dpkg: libc6: dependency problems, but configuring anyway as you requested:
 libc6 depends on libc-bin (= 2.12.1-0ubuntu6); however:
  Package libc-bin is not installed.
 libc6 depends on libgcc1; however:
  Package libgcc1 is not installed.
 libc6 depends on tzdata; however:
  Package tzdata is not installed.
 libc6 depends on findutils (>= 4.4.0-2ubuntu2); however:
  Package findutils is not installed.
Setting up libc6 (2.12.1-0ubuntu6) ...
Selecting previously deselected package perl-base.
(Reading database ... 661 files and directories currently installed.)
Unpacking perl-base (from .../perl-base_5.10.1-12ubuntu2_i386.deb) ...
Setting up perl-base (5.10.1-12ubuntu2) ...
Selecting previously deselected package mawk.
(Reading database ... 1300 files and directories currently installed.)
Unpacking mawk (from .../mawk_1.3.3-15ubuntu2_i386.deb) ...
Setting up mawk (1.3.3-15ubuntu2) ...
Selecting previously deselected package debconf.
(Reading database ... 1319 files and directories currently installed.)
Unpacking debconf (from .../debconf_1.5.32ubuntu3_all.deb) ...
dpkg: debconf: dependency problems, but configuring anyway as you requested:
 debconf depends on debconf-i18n | debconf-english; however:
  Package debconf-i18n is not installed.
  Package debconf-english is not installed.
Setting up debconf (1.5.32ubuntu3) ...
Selecting previously deselected package adduser.
(Reading database ... 1481 files and directories currently installed.)
Unpacking adduser (from .../adduser_3.112ubuntu1_all.deb) ...
Preparing to replace base-files 5.0.0ubuntu23 (using .../base-files_5.0.0ubuntu23_i386.deb) ...
Unpacking replacement base-files ...
Preparing to replace base-passwd 3.5.22 (using .../base-passwd_3.5.22_i386.deb) ...
Unpacking replacement base-passwd ...
Selecting previously deselected package bash.
dpkg: regarding .../bash_4.1-2ubuntu4_i386.deb containing bash, pre-dependency problem:
 bash pre-depends on dash
  dash is not installed.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../bash_4.1-2ubuntu4_i386.deb containing bash, pre-dependency problem:
 bash pre-depends on libncurses5 (>= 5.7+20100313)
dpkg: warning: ignoring pre-dependency problem!
Unpacking bash (from .../bash_4.1-2ubuntu4_i386.deb) ...
The bash upgrade discovered that your /bin/sh link points to dash.
As bash for Debian is destined to provide a working /bin/sh (pointing to
/bin/bash) your link will be overwritten by a default link.

If you don't want further upgrades to overwrite your customization, please
read /usr/share/doc/bash/README.Debian.gz for a more permanent solution.

[Press RETURN to continue]
Selecting previously deselected package bsdutils.
Unpacking bsdutils (from .../bsdutils_1%3a2.17.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package busybox-initramfs.
Unpacking busybox-initramfs (from .../busybox-initramfs_1%3a1.15.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package coreutils.
dpkg: regarding .../coreutils_8.5-1ubuntu3_i386.deb containing coreutils, pre-dependency problem:
 coreutils pre-depends on libacl1 (>= 2.2.11-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../coreutils_8.5-1ubuntu3_i386.deb containing coreutils, pre-dependency problem:
 coreutils pre-depends on libattr1 (>= 2.4.41-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../coreutils_8.5-1ubuntu3_i386.deb containing coreutils, pre-dependency problem:
 coreutils pre-depends on libselinux1 (>= 1.32)
dpkg: warning: ignoring pre-dependency problem!
Unpacking coreutils (from .../coreutils_8.5-1ubuntu3_i386.deb) ...
Selecting previously deselected package cpio.
Unpacking cpio (from .../cpio_2.11-4ubuntu1_i386.deb) ...
Selecting previously deselected package dash.
Unpacking dash (from .../dash_0.5.5.1-7ubuntu1_i386.deb) ...
Adding 'diversion of /bin/sh to /bin/sh.distrib by dash'
Adding 'diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash'
Preparing to replace debconf 1.5.32ubuntu3 (using .../debconf_1.5.32ubuntu3_all.deb) ...
Unpacking replacement debconf ...
Selecting previously deselected package debconf-i18n.
Unpacking debconf-i18n (from .../debconf-i18n_1.5.32ubuntu3_all.deb) ...
Selecting previously deselected package debianutils.
Unpacking debianutils (from .../debianutils_3.2.3_i386.deb) ...
Selecting previously deselected package diffutils.
Unpacking diffutils (from .../diffutils_1%3a3.0-1_i386.deb) ...
dpkg: regarding .../dpkg_1.15.8.4ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on libbz2-1.0
  libbz2-1.0 is not installed.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../dpkg_1.15.8.4ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on libselinux1 (>= 1.32)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../dpkg_1.15.8.4ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on zlib1g (>= 1:1.1.4)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../dpkg_1.15.8.4ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on coreutils (>= 5.93-1)
  coreutils is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../dpkg_1.15.8.4ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on xz-utils
  xz-utils is not installed.
dpkg: warning: ignoring pre-dependency problem!
Preparing to replace dpkg 1.15.8.4ubuntu3 (using .../dpkg_1.15.8.4ubuntu3_i386.deb) ...
Unpacking replacement dpkg ...
Selecting previously deselected package e2fslibs.
Unpacking e2fslibs (from .../e2fslibs_1.41.12-1ubuntu2_i386.deb) ...
Selecting previously deselected package e2fsprogs.
dpkg: regarding .../e2fsprogs_1.41.12-1ubuntu2_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on e2fslibs (= 1.41.12-1ubuntu2)
  e2fslibs is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../e2fsprogs_1.41.12-1ubuntu2_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libblkid1 (>= 1.34-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../e2fsprogs_1.41.12-1ubuntu2_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libcomerr2 (>= 1.34-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../e2fsprogs_1.41.12-1ubuntu2_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libss2 (>= 1.34-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../e2fsprogs_1.41.12-1ubuntu2_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libuuid1 (>= 1.34-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../e2fsprogs_1.41.12-1ubuntu2_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on util-linux (>= 2.15~rc1-1)
dpkg: warning: ignoring pre-dependency problem!
Unpacking e2fsprogs (from .../e2fsprogs_1.41.12-1ubuntu2_i386.deb) ...
Selecting previously deselected package findutils.
Unpacking findutils (from .../findutils_4.4.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package gcc-4.5-base.
Unpacking gcc-4.5-base (from .../gcc-4.5-base_4.5.1-7ubuntu2_i386.deb) ...
Selecting previously deselected package grep.
Unpacking grep (from .../archives/grep_2.6.3-3_i386.deb) ...
Selecting previously deselected package gzip.
Unpacking gzip (from .../gzip_1.3.12-9ubuntu1.1_i386.deb) ...
Selecting previously deselected package hostname.
dpkg: regarding .../hostname_3.04ubuntu1_i386.deb containing hostname, pre-dependency problem:
 hostname pre-depends on upstart-job
  upstart-job is not installed.
dpkg: warning: ignoring pre-dependency problem!
Unpacking hostname (from .../hostname_3.04ubuntu1_i386.deb) ...
Selecting previously deselected package ifupdown.
Unpacking ifupdown (from .../ifupdown_0.6.10ubuntu3_i386.deb) ...
Selecting previously deselected package initramfs-tools.
Unpacking initramfs-tools (from .../initramfs-tools_0.98.1ubuntu6_all.deb) ...
Selecting previously deselected package initramfs-tools-bin.
Unpacking initramfs-tools-bin (from .../initramfs-tools-bin_0.98.1ubuntu6_i386.deb) ...
Selecting previously deselected package initscripts.
Unpacking initscripts (from .../initscripts_2.87dsf-4ubuntu18_i386.deb) ...
Selecting previously deselected package insserv.
Unpacking insserv (from .../insserv_1.14.0-2_i386.deb) ...
Selecting previously deselected package klibc-utils.
Unpacking klibc-utils (from .../klibc-utils_1.5.20-1_i386.deb) ...
Selecting previously deselected package libacl1.
Unpacking libacl1 (from .../libacl1_2.2.49-3_i386.deb) ...
Selecting previously deselected package libattr1.
Unpacking libattr1 (from .../libattr1_1%3a2.4.44-2_i386.deb) ...
Selecting previously deselected package libblkid1.
Unpacking libblkid1 (from .../libblkid1_2.17.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libbz2-1.0.
Unpacking libbz2-1.0 (from .../libbz2-1.0_1.0.5-4ubuntu1_i386.deb) ...
Selecting previously deselected package libc-bin.
Unpacking libc-bin (from .../libc-bin_2.12.1-0ubuntu6_i386.deb) ...
Preparing to replace libc6 2.12.1-0ubuntu6 (using .../libc6_2.12.1-0ubuntu6_i386.deb) ...
Unpacking replacement libc6 ...
Selecting previously deselected package libcomerr2.
Unpacking libcomerr2 (from .../libcomerr2_1.41.12-1ubuntu2_i386.deb) ...
Selecting previously deselected package libdb4.8.
Unpacking libdb4.8 (from .../libdb4.8_4.8.30-1_i386.deb) ...
Selecting previously deselected package libdbus-1-3.
Unpacking libdbus-1-3 (from .../libdbus-1-3_1.4.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libdrm-intel1.
Unpacking libdrm-intel1 (from .../libdrm-intel1_2.4.21-1ubuntu2_i386.deb) ...
Selecting previously deselected package libdrm-nouveau1.
Unpacking libdrm-nouveau1 (from .../libdrm-nouveau1_2.4.21-1ubuntu2_i386.deb) ...
Selecting previously deselected package libdrm-radeon1.
Unpacking libdrm-radeon1 (from .../libdrm-radeon1_2.4.21-1ubuntu2_i386.deb) ...
Selecting previously deselected package libdrm2.
Unpacking libdrm2 (from .../libdrm2_2.4.21-1ubuntu2_i386.deb) ...
Selecting previously deselected package libgcc1.
Unpacking libgcc1 (from .../libgcc1_1%3a4.5.1-7ubuntu2_i386.deb) ...
Selecting previously deselected package libglib2.0-0.
Unpacking libglib2.0-0 (from .../libglib2.0-0_2.26.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libklibc.
Unpacking libklibc (from .../libklibc_1.5.20-1_i386.deb) ...
Selecting previously deselected package liblocale-gettext-perl.
Unpacking liblocale-gettext-perl (from .../liblocale-gettext-perl_1.05-6_i386.deb) ...
Selecting previously deselected package liblzma2.
Unpacking liblzma2 (from .../liblzma2_4.999.9beta+20100527-1_i386.deb) ...
Selecting previously deselected package libncurses5.
Unpacking libncurses5 (from .../libncurses5_5.7+20100626-0ubuntu1_i386.deb) ...
Selecting previously deselected package libncursesw5.
Unpacking libncursesw5 (from .../libncursesw5_5.7+20100626-0ubuntu1_i386.deb) ...
Selecting previously deselected package libnih-dbus1.
Unpacking libnih-dbus1 (from .../libnih-dbus1_1.0.2-1ubuntu2_i386.deb) ...
Selecting previously deselected package libnih1.
Unpacking libnih1 (from .../libnih1_1.0.2-1ubuntu2_i386.deb) ...
Selecting previously deselected package libpam-modules.
dpkg: regarding .../libpam-modules_1.1.1-4ubuntu1_i386.deb containing libpam-modules, pre-dependency problem:
 libpam-modules pre-depends on libdb4.8
  libdb4.8 is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../libpam-modules_1.1.1-4ubuntu1_i386.deb containing libpam-modules, pre-dependency problem:
 libpam-modules pre-depends on libpam0g (>= 1.1.0)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../libpam-modules_1.1.1-4ubuntu1_i386.deb containing libpam-modules, pre-dependency problem:
 libpam-modules pre-depends on libselinux1 (>= 2.0.85)
dpkg: warning: ignoring pre-dependency problem!
Unpacking libpam-modules (from .../libpam-modules_1.1.1-4ubuntu1_i386.deb) ...
Selecting previously deselected package libpam-runtime.
Unpacking libpam-runtime (from .../libpam-runtime_1.1.1-4ubuntu1_all.deb) ...
Selecting previously deselected package libpam0g.
Unpacking libpam0g (from .../libpam0g_1.1.1-4ubuntu1_i386.deb) ...
Selecting previously deselected package libpcre3.
Unpacking libpcre3 (from .../libpcre3_8.02-1_i386.deb) ...
Selecting previously deselected package libplymouth2.
Unpacking libplymouth2 (from .../libplymouth2_0.8.2-2ubuntu5_i386.deb) ...
Selecting previously deselected package libpng12-0.
Unpacking libpng12-0 (from .../libpng12-0_1.2.44-1_i386.deb) ...
Selecting previously deselected package libselinux1.
Unpacking libselinux1 (from .../libselinux1_2.0.94-1_i386.deb) ...
Selecting previously deselected package libsepol1.
Unpacking libsepol1 (from .../libsepol1_2.0.41-1_i386.deb) ...
Selecting previously deselected package libslang2.
Unpacking libslang2 (from .../libslang2_2.2.2-4ubuntu1_i386.deb) ...
Selecting previously deselected package libss2.
Unpacking libss2 (from .../libss2_1.41.12-1ubuntu2_i386.deb) ...
Selecting previously deselected package libssl0.9.8.
Unpacking libssl0.9.8 (from .../libssl0.9.8_0.9.8o-1ubuntu4_i386.deb) ...
Selecting previously deselected package libtext-charwidth-perl.
Unpacking libtext-charwidth-perl (from .../libtext-charwidth-perl_0.04-6_i386.deb) ...
Selecting previously deselected package libtext-iconv-perl.
Unpacking libtext-iconv-perl (from .../libtext-iconv-perl_1.7-2_i386.deb) ...
Selecting previously deselected package libtext-wrapi18n-perl.
Unpacking libtext-wrapi18n-perl (from .../libtext-wrapi18n-perl_0.06-7_all.deb) ...
Selecting previously deselected package libudev0.
Unpacking libudev0 (from .../libudev0_162-2_i386.deb) ...
Selecting previously deselected package libusb-0.1-4.
Unpacking libusb-0.1-4 (from .../libusb-0.1-4_2%3a0.1.12-15ubuntu2_i386.deb) ...
Selecting previously deselected package libuuid1.
Unpacking libuuid1 (from .../libuuid1_2.17.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package locales.
Unpacking locales (from .../locales_2.13+git20100825-1_all.deb) ...
Selecting previously deselected package login.
dpkg: regarding .../login_1%3a4.1.4.2-1ubuntu3_i386.deb containing login, pre-dependency problem:
 login pre-depends on libpam0g (>= 0.99.7.1)
  libpam0g is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../login_1%3a4.1.4.2-1ubuntu3_i386.deb containing login, pre-dependency problem:
 login pre-depends on libpam-runtime
  libpam-runtime is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../login_1%3a4.1.4.2-1ubuntu3_i386.deb containing login, pre-dependency problem:
 login pre-depends on libpam-modules
  libpam-modules is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
Unpacking login (from .../login_1%3a4.1.4.2-1ubuntu3_i386.deb) ...
Selecting previously deselected package lsb-base.
Unpacking lsb-base (from .../lsb-base_4.0-0ubuntu8_all.deb) ...
Selecting previously deselected package makedev.
Unpacking makedev (from .../makedev_2.3.1-89ubuntu1_all.deb) ...
update-rc.d: using dependency based boot sequencing
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth-splash'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth-splash'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth-log'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth-log'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'plymouth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth-stop'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth-stop'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
Preparing to replace mawk 1.3.3-15ubuntu2 (using .../mawk_1.3.3-15ubuntu2_i386.deb) ...
Unpacking replacement mawk ...
Selecting previously deselected package module-init-tools.
Unpacking module-init-tools (from .../module-init-tools_3.12-1ubuntu2_i386.deb) ...
Selecting previously deselected package mount.
dpkg: regarding .../mount_2.17.2-0ubuntu1_i386.deb containing mount, pre-dependency problem:
 mount pre-depends on libblkid1 (>= 2.17)
  libblkid1 is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../mount_2.17.2-0ubuntu1_i386.deb containing mount, pre-dependency problem:
 mount pre-depends on libselinux1 (>= 2.0.15)
  libselinux1 is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../mount_2.17.2-0ubuntu1_i386.deb containing mount, pre-dependency problem:
 mount pre-depends on libsepol1 (>= 1.14)
  libsepol1 is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../mount_2.17.2-0ubuntu1_i386.deb containing mount, pre-dependency problem:
 mount pre-depends on libuuid1 (>= 2.16)
  libuuid1 is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
Unpacking mount (from .../mount_2.17.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package mountall.
Unpacking mountall (from .../mountall_2.19_i386.deb) ...
Selecting previously deselected package ncurses-base.
Unpacking ncurses-base (from .../ncurses-base_5.7+20100626-0ubuntu1_all.deb) ...
Selecting previously deselected package ncurses-bin.
dpkg: regarding .../ncurses-bin_5.7+20100626-0ubuntu1_i386.deb containing ncurses-bin, pre-dependency problem:
 ncurses-bin pre-depends on libncurses5 (>= 5.7+20100313)
  libncurses5 is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
Unpacking ncurses-bin (from .../ncurses-bin_5.7+20100626-0ubuntu1_i386.deb) ...
Selecting previously deselected package net-tools.
Unpacking net-tools (from .../net-tools_1.60-23ubuntu3_i386.deb) ...
Selecting previously deselected package passwd.
Unpacking passwd (from .../passwd_1%3a4.1.4.2-1ubuntu3_i386.deb) ...
Preparing to replace perl-base 5.10.1-12ubuntu2 (using .../perl-base_5.10.1-12ubuntu2_i386.deb) ...
Unpacking replacement perl-base ...
Selecting previously deselected package plymouth.
Unpacking plymouth (from .../plymouth_0.8.2-2ubuntu5_i386.deb) ...
Selecting previously deselected package procps.
Unpacking procps (from .../procps_1%3a3.2.8-9ubuntu3_i386.deb) ...
Selecting previously deselected package python-minimal.
Unpacking python-minimal (from .../python-minimal_2.6.6-2ubuntu1_all.deb) ...
Selecting previously deselected package python2.6-minimal.
Unpacking python2.6-minimal (from .../python2.6-minimal_2.6.6-5ubuntu1_i386.deb) ...
Selecting previously deselected package sed.
dpkg: regarding .../archives/sed_4.2.1-7_i386.deb containing sed, pre-dependency problem:
 sed pre-depends on libselinux1 (>= 1.32)
  libselinux1 is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
Unpacking sed (from .../archives/sed_4.2.1-7_i386.deb) ...
Selecting previously deselected package sensible-utils.
Unpacking sensible-utils (from .../sensible-utils_0.0.4ubuntu1_all.deb) ...
Selecting previously deselected package sysv-rc.
Unpacking sysv-rc (from .../sysv-rc_2.87dsf-4ubuntu18_all.deb) ...
Selecting previously deselected package sysvinit-utils.
Unpacking sysvinit-utils (from .../sysvinit-utils_2.87dsf-4ubuntu18_i386.deb) ...
Selecting previously deselected package tar.
Unpacking tar (from .../archives/tar_1.23-2_i386.deb) ...
Selecting previously deselected package tzdata.
Unpacking tzdata (from .../tzdata_2010l-1_all.deb) ...
Selecting previously deselected package udev.
Unpacking udev (from .../archives/udev_162-2_i386.deb) ...
Adding 'local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
Selecting previously deselected package upstart.
Unpacking upstart (from .../upstart_0.6.6-3_i386.deb) ...
Selecting previously deselected package util-linux.
dpkg: regarding .../util-linux_2.17.2-0ubuntu1_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libblkid1 (>= 2.17)
  libblkid1 is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../util-linux_2.17.2-0ubuntu1_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libncurses5 (>= 5.6+20071006-3)
  libncurses5 is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../util-linux_2.17.2-0ubuntu1_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libselinux1 (>= 1.32)
  libselinux1 is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../util-linux_2.17.2-0ubuntu1_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libslang2 (>= 2.0.7-1)
  libslang2 is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../util-linux_2.17.2-0ubuntu1_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libuuid1 (>= 2.16)
  libuuid1 is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../util-linux_2.17.2-0ubuntu1_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on zlib1g (>= 1:1.1.4)
dpkg: warning: ignoring pre-dependency problem!
Unpacking util-linux (from .../util-linux_2.17.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package xz-utils.
Unpacking xz-utils (from .../xz-utils_4.999.9beta+20100527-1_i386.deb) ...
Selecting previously deselected package zlib1g.
Unpacking zlib1g (from .../zlib1g_1%3a1.2.3.4.dfsg-3ubuntu1_i386.deb) ...
Setting up ncurses-base (5.7+20100626-0ubuntu1) ...
Setting up sensible-utils (0.0.4ubuntu1) ...
Setting up libklibc (1.5.20-1) ...
Setting up klibc-utils (1.5.20-1) ...
Setting up libc-bin (2.12.1-0ubuntu6) ...
Setting up gcc-4.5-base (4.5.1-7ubuntu2) ...
Setting up perl-base (5.10.1-12ubuntu2) ...
Setting up libtext-iconv-perl (1.7-2) ...
Setting up liblocale-gettext-perl (1.05-6) ...
Setting up libtext-charwidth-perl (0.04-6) ...
Setting up libtext-wrapi18n-perl (0.06-7) ...
Setting up debconf-i18n (1.5.32ubuntu3) ...
Setting up debconf (1.5.32ubuntu3) ...
Setting up tzdata (2010l-1) ...

Current default time zone: 'Etc/UTC'
Local time is now:      Thu Oct  7 15:57:45 UTC 2010.
Universal Time is now:  Thu Oct  7 15:57:45 UTC 2010.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

Setting up libc6 (2.12.1-0ubuntu6) ...
Setting up debianutils (3.2.3) ...
Setting up libdbus-1-3 (1.4.0-0ubuntu1) ...
Setting up libpam0g (1.1.1-4ubuntu1) ...
Setting up libusb-0.1-4 (2:0.1.12-15ubuntu2) ...
Setting up bsdutils (1:2.17.2-0ubuntu1) ...
Setting up libdrm2 (2.4.21-1ubuntu2) ...
Setting up libsepol1 (2.0.41-1) ...
Setting up libudev0 (162-2) ...
Setting up diffutils (1:3.0-1) ...
Setting up tar (1.23-2) ...
update-alternatives: using /usr/sbin/rmt-tar to provide /usr/sbin/rmt (rmt) in auto mode.
Setting up libdrm-radeon1 (2.4.21-1ubuntu2) ...
Setting up zlib1g (1:1.2.3.4.dfsg-3ubuntu1) ...
Setting up locales (2.13+git20100825-1) ...
Setting up libgcc1 (1:4.5.1-7ubuntu2) ...
Setting up libncurses5 (5.7+20100626-0ubuntu1) ...
Setting up initramfs-tools-bin (0.98.1ubuntu6) ...
Setting up libattr1 (1:2.4.44-2) ...
Setting up e2fslibs (1.41.12-1ubuntu2) ...
Setting up base-passwd (3.5.22) ...
Setting up libcomerr2 (1.41.12-1ubuntu2) ...
Setting up mawk (1.3.3-15ubuntu2) ...
Setting up libdb4.8 (4.8.30-1) ...
Setting up net-tools (1.60-23ubuntu3) ...
Setting up libdrm-nouveau1 (2.4.21-1ubuntu2) ...
Setting up libacl1 (2.2.49-3) ...
Setting up libslang2 (2.2.2-4ubuntu1) ...
Setting up libss2 (1.41.12-1ubuntu2) ...
Setting up findutils (4.4.2-1ubuntu1) ...
Setting up liblzma2 (4.999.9beta+20100527-1) ...
Setting up libnih1 (1.0.2-1ubuntu2) ...
Setting up insserv (1.14.0-2) ...
Setting up gzip (1.3.12-9ubuntu1.1) ...
Setting up libpcre3 (8.02-1) ...
Setting up libncursesw5 (5.7+20100626-0ubuntu1) ...
Setting up busybox-initramfs (1:1.15.3-1ubuntu5) ...
Setting up libbz2-1.0 (1.0.5-4ubuntu1) ...
Setting up libdrm-intel1 (2.4.21-1ubuntu2) ...
Setting up libnih-dbus1 (1.0.2-1ubuntu2) ...
Setting up libselinux1 (2.0.94-1) ...
Setting up libpng12-0 (1.2.44-1) ...
Setting up libglib2.0-0 (2.26.0-0ubuntu1) ...
No schema files found: doing nothing.
Setting up coreutils (8.5-1ubuntu3) ...
Setting up makedev (2.3.1-89ubuntu1) ...
Setting up libssl0.9.8 (0.9.8o-1ubuntu4) ...
Setting up ncurses-bin (5.7+20100626-0ubuntu1) ...
Setting up libpam-modules (1.1.1-4ubuntu1) ...
Setting up base-files (5.0.0ubuntu23) ...
Setting up libplymouth2 (0.8.2-2ubuntu5) ...
Setting up passwd (1:4.1.4.2-1ubuntu3) ...
Shadow passwords are now on.
Setting up python2.6-minimal (2.6.6-5ubuntu1) ...
Setting up libpam-runtime (1.1.1-4ubuntu1) ...
Setting up xz-utils (4.999.9beta+20100527-1) ...
Setting up dpkg (1.15.8.4ubuntu3) ...
Setting up sysvinit-utils (2.87dsf-4ubuntu18) ...
Setting up cpio (2.11-4ubuntu1) ...
update-alternatives: using /bin/mt-gnu to provide /bin/mt (mt) in auto mode.
Setting up dash (0.5.5.1-7ubuntu1) ...
Setting up login (1:4.1.4.2-1ubuntu3) ...
Setting up libuuid1 (2.17.2-0ubuntu1) ...
Setting up python-minimal (2.6.6-2ubuntu1) ...
Setting up sysv-rc (2.87dsf-4ubuntu18) ...
Setting up mountall (2.19) ...
Setting up adduser (3.112ubuntu1) ...
Setting up sed (4.2.1-7) ...
Setting up grep (2.6.3-3) ...
Setting up upstart (0.6.6-3) ...
Setting up hostname (3.04ubuntu1) ...
Setting up libblkid1 (2.17.2-0ubuntu1) ...
Setting up bash (4.1-2ubuntu4) ...
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
Setting up module-init-tools (3.12-1ubuntu2) ...
Setting up lsb-base (4.0-0ubuntu8) ...
Setting up ifupdown (0.6.10ubuntu3) ...
Creating /etc/network/interfaces.

Warning: Fake initctl called, doing nothing
Setting up mount (2.17.2-0ubuntu1) ...
Setting up initscripts (2.87dsf-4ubuntu18) ...
Setting up util-linux (2.17.2-0ubuntu1) ...
update-alternatives: using /bin/more to provide /usr/bin/pager (pager) in auto mode.
Setting up procps (1:3.2.8-9ubuntu3) ...
update-alternatives: using /usr/bin/w.procps to provide /usr/bin/w (w) in auto mode.

Warning: Fake initctl called, doing nothing
Setting up e2fsprogs (1.41.12-1ubuntu2) ...
Setting up udev (162-2) ...

Warning: Fake initctl called, doing nothing
Removing 'local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs: deferring update (trigger activated)
Setting up initramfs-tools (0.98.1ubuntu6) ...
update-initramfs: deferring update (trigger activated)
Setting up plymouth (0.8.2-2ubuntu5) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
(Reading database ... 6719 files and directories currently installed.)
Unpacking apt (from .../apt_0.8.3ubuntu7_i386.deb) ...
Unpacking apt-utils (from .../apt-utils_0.8.3ubuntu7_i386.deb) ...
Unpacking bzip2 (from .../bzip2_1.0.5-4ubuntu1_i386.deb) ...
Unpacking console-setup (from .../console-setup_1.34ubuntu15_all.deb) ...
Unpacking console-terminus (from .../console-terminus_4.30-2_all.deb) ...
Unpacking cron (from .../cron_3.0pl1-114ubuntu1_i386.deb) ...
Unpacking dhcp3-client (from .../dhcp3-client_3.1.3-2ubuntu6_i386.deb) ...
Unpacking dhcp3-common (from .../dhcp3-common_3.1.3-2ubuntu6_i386.deb) ...
Unpacking dmsetup (from .../dmsetup_2%3a1.02.39-1ubuntu6_i386.deb) ...
Unpacking eject (from .../eject_2.1.5+deb1+cvs20081104-7_i386.deb) ...
Unpacking file (from .../file_5.03-5ubuntu1_i386.deb) ...
Unpacking gnupg (from .../gnupg_1.4.10-2ubuntu2_i386.deb) ...
Unpacking gpgv (from .../gpgv_1.4.10-2ubuntu2_i386.deb) ...
Unpacking iproute (from .../iproute_20100519-2_i386.deb) ...
Unpacking iputils-ping (from .../iputils-ping_3%3a20100418-2ubuntu1_i386.deb) ...
Unpacking kbd (from .../kbd_1.15-1ubuntu3_i386.deb) ...
Unpacking less (from .../archives/less_436-1_i386.deb) ...
Unpacking libatm1 (from .../libatm1_1%3a2.5.1-1.2_i386.deb) ...
Unpacking libcap2 (from .../libcap2_1%3a2.19-2_i386.deb) ...
Unpacking libdevmapper1.02.1 (from .../libdevmapper1.02.1_2%3a1.02.39-1ubuntu6_i386.deb) ...
Unpacking libexpat1 (from .../libexpat1_2.0.1-7ubuntu1_i386.deb) ...
Unpacking libfribidi0 (from .../libfribidi0_0.19.2-1_i386.deb) ...
Unpacking liblockfile1 (from .../liblockfile1_1.08-4_i386.deb) ...
Unpacking libmagic1 (from .../libmagic1_5.03-5ubuntu1_i386.deb) ...
Unpacking libnewt0.52 (from .../libnewt0.52_0.52.11-1_i386.deb) ...
Unpacking libpopt0 (from .../libpopt0_1.16-1_i386.deb) ...
Unpacking libreadline6 (from .../libreadline6_6.1-3_i386.deb) ...
Unpacking libsqlite3-0 (from .../libsqlite3-0_3.7.2-1_i386.deb) ...
Unpacking libstdc++6 (from .../libstdc++6_4.5.1-7ubuntu2_i386.deb) ...
Unpacking lockfile-progs (from .../lockfile-progs_0.1.15_i386.deb) ...
Unpacking logrotate (from .../logrotate_3.7.8-6ubuntu1_i386.deb) ...
Unpacking lsb-release (from .../lsb-release_4.0-0ubuntu8_all.deb) ...
Unpacking mime-support (from .../mime-support_3.48-1ubuntu2_all.deb) ...
Unpacking netbase (from .../netbase_4.35ubuntu3_all.deb) ...
Unpacking netcat-openbsd (from .../netcat-openbsd_1.89-3ubuntu2_i386.deb) ...
Unpacking ntpdate (from .../ntpdate_1%3a4.2.4p8+dfsg-1ubuntu6_i386.deb) ...
Unpacking python (from .../python_2.6.6-2ubuntu1_all.deb) ...
Unpacking python-central (from .../python-central_0.6.15ubuntu2_all.deb) ...
Unpacking python2.6 (from .../python2.6_2.6.6-5ubuntu1_i386.deb) ...
Unpacking readline-common (from .../readline-common_6.1-3_all.deb) ...
Unpacking rsyslog (from .../rsyslog_4.2.0-2ubuntu8_i386.deb) ...
Unpacking sudo (from .../sudo_1.7.2p7-1ubuntu2_i386.deb) ...
Unpacking ubuntu-keyring (from .../ubuntu-keyring_2010.+09.30_all.deb) ...
Unpacking ubuntu-minimal (from .../ubuntu-minimal_1.207_i386.deb) ...
Unpacking ucf (from .../archives/ucf_3.0025_all.deb) ...
Moving old data out of the way
Unpacking ureadahead (from .../ureadahead_0.100.0-8_i386.deb) ...
Unpacking vim-common (from .../vim-common_2%3a7.2.330-1ubuntu4_i386.deb) ...
Unpacking vim-tiny (from .../vim-tiny_2%3a7.2.330-1ubuntu4_i386.deb) ...
Unpacking whiptail (from .../whiptail_0.52.11-1_i386.deb) ...
Unpacking xkb-data (from .../xkb-data_1.8-1ubuntu8_all.deb) ...
Setting up sudo (1.7.2p7-1ubuntu2) ...
No /etc/sudoers found... creating one for you.
Setting up libpopt0 (1.16-1) ...
Setting up ucf (3.0025) ...
Setting up bzip2 (1.0.5-4ubuntu1) ...
Setting up vim-common (2:7.2.330-1ubuntu4) ...
Setting up netbase (4.35ubuntu3) ...
Setting up libmagic1 (5.03-5ubuntu1) ...
Setting up file (5.03-5ubuntu1) ...
Setting up netcat-openbsd (1.89-3ubuntu2) ...
update-alternatives: using /bin/nc.openbsd to provide /bin/nc (nc) in auto mode.
Setting up libfribidi0 (0.19.2-1) ...
Setting up libsqlite3-0 (3.7.2-1) ...
Setting up libexpat1 (2.0.1-7ubuntu1) ...
Setting up iproute (20100519-2) ...
Setting up libdevmapper1.02.1 (2:1.02.39-1ubuntu6) ...
Setting up libatm1 (1:2.5.1-1.2) ...
Setting up libnewt0.52 (0.52.11-1) ...
Setting up ureadahead (0.100.0-8) ...
Setting up xkb-data (1.8-1ubuntu8) ...
Setting up ubuntu-keyring (2010.+09.30) ...
gpg: waiting for lock (held by 9363) ...
gpg: /etc/apt/trustdb.gpg: trustdb created
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: key FBB75451: public key "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" imported
gpg: Total number processed: 2
gpg:               imported: 2
gpg: no ultimately trusted keys found
Setting up dmsetup (2:1.02.39-1ubuntu6) ...
update-initramfs: deferring update (trigger activated)
Setting up eject (2.1.5+deb1+cvs20081104-7) ...
Setting up iputils-ping (3:20100418-2ubuntu1) ...
Setting up console-terminus (4.30-2) ...
Setting up mime-support (3.48-1ubuntu2) ...
update-alternatives: using /usr/bin/see to provide /usr/bin/view (view) in auto mode.
Setting up cron (3.0pl1-114ubuntu1) ...
Adding group `crontab' (GID 102) ...
Done.

Warning: Fake initctl called, doing nothing
Setting up dhcp3-common (3.1.3-2ubuntu6) ...
Setting up rsyslog (4.2.0-2ubuntu8) ...

Creating config file /etc/rsyslog.d/50-default.conf with new version

Warning: Fake initctl called, doing nothing
Setting up libstdc++6 (4.5.1-7ubuntu2) ...
Setting up vim-tiny (2:7.2.330-1ubuntu4) ...
update-alternatives: using /usr/bin/vim.tiny to provide /usr/bin/rview (rview) in auto mode.
update-alternatives: using /usr/bin/vim.tiny to provide /usr/bin/vi (vi) in auto mode.
update-alternatives: using /usr/bin/vim.tiny to provide /usr/bin/view (view) in auto mode.
update-alternatives: using /usr/bin/vim.tiny to provide /usr/bin/ex (ex) in auto mode.
update-alternatives: using /usr/bin/vim.tiny to provide /usr/bin/editor (editor) in auto mode.
Setting up less (436-1) ...
Setting up readline-common (6.1-3) ...
Setting up libcap2 (1:2.19-2) ...
Setting up liblockfile1 (1.08-4) ...
Setting up apt (0.8.3ubuntu7) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
Setting up whiptail (0.52.11-1) ...
Setting up dhcp3-client (3.1.3-2ubuntu6) ...
Setting up libreadline6 (6.1-3) ...
Setting up lockfile-progs (0.1.15) ...
Setting up logrotate (3.7.8-6ubuntu1) ...
Setting up ntpdate (1:4.2.4p8+dfsg-1ubuntu6) ...
Setting up apt-utils (0.8.3ubuntu7) ...
Setting up gpgv (1.4.10-2ubuntu2) ...
Setting up python2.6 (2.6.6-5ubuntu1) ...
Setting up gnupg (1.4.10-2ubuntu2) ...
Setting up python (2.6.6-2ubuntu1) ...
Setting up python-central (0.6.15ubuntu2) ...
Setting up lsb-release (4.0-0ubuntu8) ...
Setting up kbd (1.15-1ubuntu3) ...
 Removing any system startup links for /etc/init.d/console-screen.kbd.sh ...
update-initramfs: deferring update (trigger activated)
Setting up console-setup (1.34ubuntu15) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for python-central ...
Setting up ubuntu-minimal (1.207) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
[/PHP]

---

### Post by Byb on 2011-01-09
some more ? :popcorn::popcorn:
**[COLOR=Red]daemon.log[/COLOR]**[PHP]Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> sleep requested (sleeping: no  enabled: yes)
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> sleeping or disabling...
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth1): now unmanaged
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth1): device state change: 8 -> 1 (reason 37)
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth1): deactivating device (reason: 37).
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth1): canceled DHCP transaction, DHCP client pid 916
Jan  9 12:20:03 Amilo-M7405 avahi-daemon[733]: Withdrawing address record for 192.168.1.16 on eth1.
Jan  9 12:20:03 Amilo-M7405 avahi-daemon[733]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.16.
Jan  9 12:20:03 Amilo-M7405 avahi-daemon[733]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth1): cleaning up...
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth1): taking down device.
Jan  9 12:20:03 Amilo-M7405 wpa_supplicant[854]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  9 12:20:03 Amilo-M7405 avahi-daemon[733]: Interface eth1.IPv6 no longer relevant for mDNS.
Jan   9 12:20:03 Amilo-M7405 avahi-daemon[733]: Leaving mDNS multicast group  on interface eth1.IPv6 with address fe80::20e:35ff:fe89:579e.
Jan  9 12:20:03 Amilo-M7405 avahi-daemon[733]: Withdrawing address record for IPv6addressHere on eth1.
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth0): now unmanaged
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth0): device state change: 2 -> 1 (reason 37)
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth0): cleaning up...
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth0): taking down device.
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: Successfully dropped root privileges.
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: avahi-daemon 0.6.27 starting up.
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: Successfully called chroot().
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: Successfully dropped remaining capabilities.
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: No service file found in /etc/avahi/services.
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: Network interface enumeration completed.
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: Registering HINFO record with values 'I686'/'LINUX'.
Jan   9 13:16:25 Amilo-M7405 avahi-daemon[625]: Server startup complete. Host  name is Amilo-M7405.local. Local service cookie is 3809600776.
Jan  9  13:16:26 Amilo-M7405 gdm-binary[596]: WARNING: Unable to load file  '/etc/gdm/custom.conf': Aucun fichier ou dossier de ce type
Jan  9 13:16:26 Amilo-M7405 NetworkManager[673]: <info> NetworkManager (version 0.8.1) is starting...
Jan  9 13:16:26 Amilo-M7405 NetworkManager[673]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Jan  9 13:16:26 Amilo-M7405 NetworkManager[673]: <info> trying to start the modem manager...
Jan  9 13:16:27 Amilo-M7405 modem-manager: ModemManager (version 0.4) starting...
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Huawei
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin ZTE
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Longcheer
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin SimTech
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Ericsson MBM
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Generic
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Nokia
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Option
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Gobi
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: init!
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: update_system_hostname
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPluginIfupdown: management mode: unmanaged
Jan   9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown:  devices added (path:  /sys/devices/pci0000:00/0000:00:1e.0/0000:01:07.0/net/eth1, iface: eth1)
Jan   9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown:  device added (path:  /sys/devices/pci0000:00/0000:00:1e.0/0000:01:07.0/net/eth1, iface:  eth1): no ifupdown configuration found.
Jan  9 13:16:27 Amilo-M7405  NetworkManager[673]:    SCPlugin-Ifupdown: devices added (path:  /sys/devices/pci0000:00/0000:00:1e.0/0000:01:0c.0/net/eth0, iface: eth0)
Jan   9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown:  device added (path:  /sys/devices/pci0000:00/0000:00:1e.0/0000:01:0c.0/net/eth0, iface:  eth0): no ifupdown configuration found.
Jan  9 13:16:27 Amilo-M7405  NetworkManager[673]:    SCPlugin-Ifupdown: devices added (path:  /sys/devices/virtual/net/lo, iface: lo)
Jan  9 13:16:27 Amilo-M7405  NetworkManager[673]:    SCPlugin-Ifupdown: device added (path:  /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration  found.
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: end _init.
Jan   9 13:16:27 Amilo-M7405 NetworkManager[673]: <info> Loaded plugin  ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the  NetworkManager mailing list.
Jan  9 13:16:27 Amilo-M7405  NetworkManager[673]: <info> Loaded plugin keyfile: (c) 2007 - 2008  Red Hat, Inc.  To report bugs please use the NetworkManager mailing  list.
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    Ifupdown: get unmanaged devices count: 0
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: (154668368) ... get_connections.
Jan   9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown:  (154668368) ... get_connections (managed=false): return empty list.
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]:    Ifupdown: get unmanaged devices count: 0
Jan   9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> found WiFi  radio killswitch rfkill0 (at  /sys/devices/pci0000:00/0000:00:1e.0/0000:01:07.0/ieee80211/phy0/rfkill0)  (driver <unknown>)
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> Networking is enabled by state file
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): driver supports SSID scans (scan_capa 0x21).
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): now managed
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): bringing up device.
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): preparing device.
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): deactivating device (reason: 2).
Jan   9 13:16:28 Amilo-M7405 NetworkManager[673]:  supplicant_interface_acquire: assertion `mgr_state ==  NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): carrier is OFF
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): new Ethernet device (driver: '8139too' ifindex: 2)
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): now managed
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): bringing up device.
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): preparing device.
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): deactivating device (reason: 2).
Jan   9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> Added default  wired connection 'Auto eth0' for  /sys/devices/pci0000:00/0000:00:1e.0/0000:01:0c.0/net/eth0
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> modem-manager is now available
Jan   9 13:16:28 Amilo-M7405 NetworkManager[673]: <warn> bluez error  getting default adapter: The name org.bluez was not provided by any  .service files
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> Trying to start the supplicant...
Jan  9 13:16:28 Amilo-M7405 modem-manager: Loaded plugin Sierra
Jan  9 13:16:28 Amilo-M7405 modem-manager: Loaded plugin Novatel
Jan  9 13:16:28 Amilo-M7405 modem-manager: Loaded plugin Option High-Speed
Jan  9 13:16:28 Amilo-M7405 modem-manager: Loaded plugin AnyData
Jan  9 13:16:28 Amilo-M7405 modem-manager: Loaded plugin MotoC
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS0): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS10): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS11): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS12): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS13): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS14): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS15): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS16): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS17): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS18): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS19): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS20): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS21): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS22): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS23): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS24): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS25): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS26): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS27): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS28): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS29): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS30): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS31): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS4): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS5): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS6): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS7): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS8): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS9): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant manager state:  down -> idle
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): device state change: 2 -> 3 (reason 0)
Jan  9 13:16:28 Amilo-M7405 gdm-binary[596]: WARNING: Unable to find users: no seat-id found
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant interface state:  starting -> ready
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) starting connection 'Auto DWL'
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> (eth1): device state change: 3 -> 4 (reason 0)
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Jan   9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation  (eth1/wireless): connection 'Auto MySSID' has security, and secrets exist.   No new secrets needed.
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Config: added 'ssid' value 'MySSID'
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Config: added 'scan_ssid' value '1'
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Config: added 'psk' value '<omitted>'
Jan   9 13:16:29 Amilo-M7405 NetworkManager[673]:  nm_setting_802_1x_get_pkcs11_engine_path: assertion  `NM_IS_SETTING_802_1X (setting)' failed
Jan  9 13:16:29 Amilo-M7405  NetworkManager[673]: nm_setting_802_1x_get_pkcs11_module_path: assertion  `NM_IS_SETTING_802_1X (setting)' failed
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Config: set interface ap_scan to 1
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  scanning -> disconnected
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jan   9 13:16:29 Amilo-M7405 avahi-daemon[625]: Joining mDNS multicast group  on interface eth1.IPv6 with address IPv6addressHere.
Jan  9 13:16:29 Amilo-M7405 avahi-daemon[625]: New relevant interface eth1.IPv6 for mDNS.
Jan  9 13:16:29 Amilo-M7405 avahi-daemon[625]: Registering new address record for IPv6addressHere on eth1.*.
Jan   9 13:16:29 Amilo-M7405 gdm-simple-slave[808]: WARNING: Unable to load  file '/etc/gdm/custom.conf': Aucun fichier ou dossier de ce type
Jan  9 13:16:30 Amilo-M7405 wpa_supplicant[805]: Trying to associate with 00:xx:xx:xx:xx:xx (SSID='MySSID' freq=2412 MHz)
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  scanning -> associating
Jan  9 13:16:30 Amilo-M7405 wpa_supplicant[805]: Associated with 00:xx:xx:xx:xx:xx
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  associating -> associated
Jan   9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> (eth1):  supplicant connection state:  associated -> 4-way handshake
Jan  9  13:16:30 Amilo-M7405 modprobe: FATAL: Error inserting padlock_sha  (/lib/modules/2.6.37-020637-generic/kernel/drivers/crypto/padlock-sha.ko):  No such device
Jan  9 13:16:30 Amilo-M7405 wpa_supplicant[805]: WPA: Key negotiation completed with 00:xx:xx:xx:xx:xx [PTK=CCMP GTK=CCMP]
Jan   9 13:16:30 Amilo-M7405 wpa_supplicant[805]: CTRL-EVENT-CONNECTED -  Connection to 00:xx:xx:xx:xx:xx completed (auth) [id=0 id_str=]
Jan  9  13:16:30 Amilo-M7405 NetworkManager[673]: <info> (eth1):  supplicant connection state:  4-way handshake -> group handshake
Jan   9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> (eth1):  supplicant connection state:  group handshake -> completed
Jan  9  13:16:30 Amilo-M7405 NetworkManager[673]: <info> Activation  (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected  to wireless network 'DWL'.
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> (eth1): device state change: 5 -> 7 (reason 0)
Jan   9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> Activation  (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  9 13:16:31 Amilo-M7405 NetworkManager[673]: <info> dhclient started with pid 905
Jan  9 13:16:31 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jan  9 13:16:31 Amilo-M7405 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  9 13:16:31 Amilo-M7405 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jan  9 13:16:31 Amilo-M7405 dhclient: All rights reserved.
Jan  9 13:16:31 Amilo-M7405 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  9 13:16:31 Amilo-M7405 dhclient: 
Jan  9 13:16:31 Amilo-M7405 NetworkManager[673]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Jan  9 13:16:31 Amilo-M7405 dhclient: Listening on LPF/eth1/00:yy:yy:yy:yy:yy
Jan  9 13:16:31 Amilo-M7405 dhclient: Sending on   LPF/eth1/00:yy:yy:yy:yy:yy
Jan  9 13:16:31 Amilo-M7405 dhclient: Sending on   Socket/fallback
Jan  9 13:16:31 Amilo-M7405 dhclient: DHCPREQUEST of 192.168.1.16 on eth1 to 255.255.255.255 port 67
Jan  9 13:16:31 Amilo-M7405 wpa_supplicant[805]: WPA: Group rekeying completed with 00:17:9a:75:73:ce [GTK=CCMP]
Jan   9 13:16:31 Amilo-M7405 NetworkManager[673]: <info> (eth1):  supplicant connection state:  completed -> group handshake
Jan  9  13:16:31 Amilo-M7405 NetworkManager[673]: <info> (eth1):  supplicant connection state:  group handshake -> completed
Jan  9 13:16:34 Amilo-M7405 dhclient: DHCPREQUEST of 192.168.1.16 on eth1 to 255.255.255.255 port 67
Jan  9 13:16:34 Amilo-M7405 dhclient: DHCPACK of 192.168.1.16 from 192.168.1.1
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info>   address 192.168.1.16
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info>   prefix 24 (255.255.255.0)
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info>   gateway 192.168.1.1
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info>   nameserver '212.27.40.240'
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info>   nameserver '212.27.40.241'
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Jan  9 13:16:34 Amilo-M7405 avahi-daemon[625]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.16.
Jan  9 13:16:34 Amilo-M7405 avahi-daemon[625]: New relevant interface eth1.IPv4 for mDNS.
Jan  9 13:16:34 Amilo-M7405 avahi-daemon[625]: Registering new address record for 192.168.1.16 on eth1.IPv4.
Jan  9 13:16:34 Amilo-M7405 dhclient: bound to 192.168.1.16 -- renewal in 324003 seconds.
Jan  9 13:16:35 Amilo-M7405 NetworkManager[673]: <info> (eth1): device state change: 7 -> 8 (reason 0)
Jan  9 13:16:35 Amilo-M7405 NetworkManager[673]: <info> Policy set 'Auto MySSID' (eth1) as default for IPv4 routing and DNS.
Jan  9 13:16:35 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) successful, device activated.
Jan  9 13:16:35 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Jan  9 13:16:36 Amilo-M7405 ntpdate[1003]: adjust time server 91.189.94.4 offset -0.354241 sec
Jan   9 13:16:39 Amilo-M7405 gdm-session-worker[1047]: WARNING: Unable to  load file '/etc/gdm/custom.conf': Aucun fichier ou dossier de ce type
Jan  9 13:16:39 Amilo-M7405 acpid: starting up with proc fs
Jan  9 13:16:39 Amilo-M7405 init: apport pre-start process (1052) terminated with status 1
Jan  9 13:16:39 Amilo-M7405 init: apport post-stop process (1077) terminated with status 1
Jan  9 13:16:41 Amilo-M7405 acpid: 36 rules loaded
Jan  9 13:16:41 Amilo-M7405 acpid: waiting for events: event logging is off
Jan  9 13:16:41 Amilo-M7405 polkitd[1128]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jan  9 13:16:43 Amilo-M7405 init: plymouth-stop pre-start process (1245) terminated with status 1
Jan   9 13:16:43 Amilo-M7405 gdm-simple-greeter[1036]: Gtk-WARNING:  /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a  GtkWindow
Jan  9 13:16:44 Amilo-M7405 gdm-session-worker[1047]:  GLib-GObject-CRITICAL: g_value_get_boolean: assertion  `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  9 13:18:35 Amilo-M7405 gdm-session-worker[1047]: pam_sm_authenticate: Called
Jan  9 13:18:35 Amilo-M7405 gdm-session-worker[1047]: pam_sm_authenticate: username = [fab]
Jan  9 13:18:35 Amilo-M7405 gdm-session-worker[1268]: Passphrase file wrapped
Jan   9 13:18:38 Amilo-M7405 NetworkManager[673]: <error>  [1294575518.941011] [nm-manager.c:1317] user_proxy_init(): could not  init user settings proxy: (3) Could not get owner of name  'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  9  13:18:39 Amilo-M7405 NetworkManager[673]: <error>  [1294575519.83528] [nm-manager.c:1317] user_proxy_init(): could not init  user settings proxy: (3) Could not get owner of name  'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Successfully called chroot.
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Successfully dropped privileges.
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Successfully limited resources.
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Running.
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Watchdog thread running.
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Canary thread running.
Jan   9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Successfully made thread  1390 of process 1390 (n/a) owned by '1000' high priority at nice level  -11.
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Supervising 1 threads of 1 processes of 1 users.
Jan   9 13:18:46 Amilo-M7405 rtkit-daemon[1392]: Successfully made thread  1406 of process 1390 (n/a) owned by '1000' RT at priority 5.
Jan  9 13:18:46 Amilo-M7405 rtkit-daemon[1392]: Supervising 2 threads of 1 processes of 1 users.
Jan   9 13:18:46 Amilo-M7405 rtkit-daemon[1392]: Successfully made thread  1407 of process 1390 (n/a) owned by '1000' RT at priority 5.
Jan  9 13:18:46 Amilo-M7405 rtkit-daemon[1392]: Supervising 3 threads of 1 processes of 1 users.[/PHP]

---

### Post by Byb on 2011-01-09
Still hungry? :popcorn::popcorn::popcorn:
**[COLOR=Red][/COLOR]**

---

### Post by Byb on 2011-01-09
Not fed up? :popcorn::popcorn::popcorn::popcorn:
**[COLOR=Red]dmesg[/COLOR]**[PHP][    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[     0.000000] Linux version 2.6.37-020637-generic (root@zinc) (gcc version  4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #201101050908 SMP Wed Jan 5 10:17:13 UTC  2011
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003efd0000 (usable)
[    0.000000]  BIOS-e820: 000000003efd0000 - 000000003efdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003efdf000 - 000000003f000000 (ACPI NVS)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU or disabled in BIOS!
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: 255/259 Series                  /Amilo M7405 , BIOS 1.03C   01/25/2005
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3efd0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 038000000 mask FFC000000 write-back
[    0.000000]   4 base 03C000000 mask FFE000000 write-back
[    0.000000]   5 base 03E000000 mask FFF000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] initial memory mapped : 0 - 01000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ ffb000-1000000
[    0.000000] RAMDISK: 2e412000 - 2f41c000
[    0.000000] ACPI: RSDP 000f6790 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3efd0000 00034 (v01 A M I  OEMRSDT  01000525 MSFT 00000097)
[    0.000000] ACPI: FACP 3efd0200 00081 (v02 A M I  OEMFACP  01000525 MSFT 00000097)
[    0.000000] ACPI: DSDT 3efd03f0 03714 (v01 UW     F07_____ 00000001 INTL 02002026)
[    0.000000] ACPI: FACS 3efdf000 00040
[    0.000000] ACPI: APIC 3efd0390 00054 (v01 A M I  OEMAPIC  01000525 MSFT 00000097)
[    0.000000] ACPI: OEMB 3efdf040 00040 (v01 A M I  AMI_OEM  01000525 MSFT 00000097)
[    0.000000] ACPI: SSDT 3efd3b10 00394 (v01    AMI   CPU1PM 00000001 INTL 02002026)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003efd0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003efd0
[    0.000000] On node 0 totalpages: 257887
[    0.000000] free_area_init_node: node 0, pgdat c0850d00, node_mem_map f701d200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 240 pages used for memmap
[    0.000000]   HighMem zone: 30434 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f000000 (gap: 3f000000:c1000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f6c00000 s28544 r0 d20608 u4194304
[    0.000000] pcpu-alloc: s28544 r0 d20608 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 255871
[     0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637-generic  root=UUID=53f4ad58-f05f-4972-b816-4105751cba54 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5159680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003efd0)
[    0.000000] Memory: 991900k/1032000k available (5128k kernel code, 39648k reserved, 2467k data, 740k init, 122696k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc086c000 - 0xc0925000   ( 740 kB)
[    0.000000]       .data : 0xc060234f - 0xc086b108   (2467 kB)
[    0.000000]       .text : 0xc0100000 - 0xc060234f   (5128 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f6008000 soft=f600a000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1400.005 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 2800.01 BogoMIPS (lpj=5600020)
[    0.004013] pid_max: default: 32768 minimum: 301
[    0.004046] Security Framework initialized
[    0.004069] AppArmor: AppArmor initialized
[    0.004151] Mount-cache hash table entries: 512
[    0.008127] Initializing cgroup subsys ns
[    0.008133] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.008138] Initializing cgroup subsys cpuacct
[    0.008145] Initializing cgroup subsys memory
[    0.008162] Initializing cgroup subsys devices
[    0.008165] Initializing cgroup subsys freezer
[    0.008169] Initializing cgroup subsys net_cls
[    0.008218] mce: CPU supports 5 MCE banks
[    0.008232] CPU0: Thermal monitoring enabled (TM2)
[    0.008243] Performance Events: p6 PMU driver.
[    0.008254] ... version:                0
[    0.008257] ... bit width:              32
[    0.008260] ... generic registers:      2
[    0.008263] ... value mask:             00000000ffffffff
[    0.008267] ... max period:             000000007fffffff
[    0.008270] ... fixed-purpose events:   0
[    0.008273] ... event mask:             0000000000000003
[    0.009452] SMP alternatives: switching to UP code
[    0.018985] Freeing SMP alternatives: 20k freed
[    0.018998] ACPI: Core revision 20101013
[    0.028014] ftrace: allocating 26658 entries in 53 pages
[    0.032093] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032397] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072731] CPU0: Intel(R) Pentium(R) M processor 1.40GHz stepping 06
[    0.076000] Brought up 1 CPUs
[    0.076000] Total of 1 processors activated (2800.01 BogoMIPS).
[    0.076000] devtmpfs: initialized
[    0.076000] regulator: core version 0.5
[    0.076000] regulator: dummy: 
[    0.076000] Time: 12:16:04  Date: 01/09/11
[    0.076000] NET: Registered protocol family 16
[    0.076000] EISA bus registered
[    0.076000] ACPI: bus type pci registered
[    0.076000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.076000] PCI: Using configuration type 1 for base access
[    0.077452] bio: create slab <bio-0> at 0
[    0.078669] ACPI: EC: Look up EC in DSDT
[    0.079932] ACPI: Executed 2 blocks of module-level executable AML code
[    0.084045] ACPI: Interpreter enabled
[    0.084054] ACPI: (supports S0 S3 S4 S5)
[    0.084087] ACPI: Using IOAPIC for interrupt routing
[    0.092517] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.092695] ACPI: No dock devices found.
[    0.092702] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.092803] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.093024] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.093029] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.093034] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.093038] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.093043] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d6fff] (ignored)
[    0.093048] pci_root PNP0A03:00: host bridge window [mem 0x000d7000-0x000d7fff] (ignored)
[    0.093052] pci_root PNP0A03:00: host bridge window [mem 0x000de000-0x000dffff] (ignored)
[    0.093057] pci_root PNP0A03:00: host bridge window [mem 0x3f000000-0xffffffff] (ignored)
[    0.093074] pci 0000:00:00.0: [8086:3580] type 0 class 0x000600
[    0.093121] pci 0000:00:00.1: [8086:3584] type 0 class 0x000880
[    0.093167] pci 0000:00:00.3: [8086:3585] type 0 class 0x000880
[    0.093219] pci 0000:00:02.0: [8086:3582] type 0 class 0x000300
[    0.093232] pci 0000:00:02.0: reg 10: [mem 0xd8000000-0xdfffffff pref]
[    0.093241] pci 0000:00:02.0: reg 14: [mem 0xe0380000-0xe03fffff]
[    0.093249] pci 0000:00:02.0: reg 18: [io  0xec00-0xec07]
[    0.093279] pci 0000:00:02.0: supports D1
[    0.093292] pci 0000:00:02.1: [8086:3582] type 0 class 0x000380
[    0.093304] pci 0000:00:02.1: reg 10: [mem 0xd0000000-0xd7ffffff pref]
[    0.093313] pci 0000:00:02.1: reg 14: [mem 0xe0300000-0xe037ffff]
[    0.093346] pci 0000:00:02.1: supports D1
[    0.093396] pci 0000:00:1d.0: [8086:24c2] type 0 class 0x000c03
[    0.093441] pci 0000:00:1d.0: reg 20: [io  0xe480-0xe49f]
[    0.093475] pci 0000:00:1d.1: [8086:24c4] type 0 class 0x000c03
[    0.093520] pci 0000:00:1d.1: reg 20: [io  0xe800-0xe81f]
[    0.093553] pci 0000:00:1d.2: [8086:24c7] type 0 class 0x000c03
[    0.093598] pci 0000:00:1d.2: reg 20: [io  0xe880-0xe89f]
[    0.093642] pci 0000:00:1d.7: [8086:24cd] type 0 class 0x000c03
[    0.093665] pci 0000:00:1d.7: reg 10: [mem 0xe02ffc00-0xe02fffff]
[    0.093743] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.093750] pci 0000:00:1d.7: PME# disabled
[    0.093768] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.093811] pci 0000:00:1f.0: [8086:24cc] type 0 class 0x000601
[    0.093876] pci 0000:00:1f.0: quirk: [io  0x0400-0x047f] claimed by ICH4 ACPI/GPIO/TCO
[    0.093882] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH4 GPIO
[    0.093898] pci 0000:00:1f.1: [8086:24ca] type 0 class 0x000101
[    0.093913] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.093924] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.093936] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.093947] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.093958] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.093969] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.093998] pci 0000:00:1f.3: [8086:24c3] type 0 class 0x000c05
[    0.094043] pci 0000:00:1f.3: reg 20: [io  0xd480-0xd49f]
[    0.094081] pci 0000:00:1f.5: [8086:24c5] type 0 class 0x000401
[    0.094098] pci 0000:00:1f.5: reg 10: [io  0xd800-0xd8ff]
[    0.094108] pci 0000:00:1f.5: reg 14: [io  0xdc00-0xdc3f]
[    0.094119] pci 0000:00:1f.5: reg 18: [mem 0xe02ff800-0xe02ff9ff]
[    0.094130] pci 0000:00:1f.5: reg 1c: [mem 0xe02ff400-0xe02ff4ff]
[    0.094167] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.094173] pci 0000:00:1f.5: PME# disabled
[    0.094191] pci 0000:00:1f.6: [8086:24c6] type 0 class 0x000703
[    0.094207] pci 0000:00:1f.6: reg 10: [io  0xe000-0xe0ff]
[    0.094218] pci 0000:00:1f.6: reg 14: [io  0xe400-0xe47f]
[    0.094268] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.094274] pci 0000:00:1f.6: PME# disabled
[    0.094308] pci 0000:01:03.0: [1217:7114] type 2 class 0x000607
[    0.094326] pci 0000:01:03.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.094345] pci 0000:01:03.0: supports D1 D2
[    0.094349] pci 0000:01:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.094355] pci 0000:01:03.0: PME# disabled
[    0.094374] pci 0000:01:03.1: [1217:7114] type 2 class 0x000607
[    0.094392] pci 0000:01:03.1: reg 10: [mem 0x00000000-0x00000fff]
[    0.094411] pci 0000:01:03.1: supports D1 D2
[    0.094415] pci 0000:01:03.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.094420] pci 0000:01:03.1: PME# disabled
[    0.094439] pci 0000:01:03.2: [1217:7110] type 0 class 0x000880
[    0.094457] pci 0000:01:03.2: reg 10: [mem 0xe00ff000-0xe00fffff]
[    0.094519] pci 0000:01:03.2: supports D1 D2
[    0.094523] pci 0000:01:03.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.094528] pci 0000:01:03.2: PME# disabled
[    0.094555] pci 0000:01:07.0: [8086:4220] type 0 class 0x000280
[    0.094573] pci 0000:01:07.0: reg 10: [mem 0xe00fe000-0xe00fefff]
[    0.094635] pci 0000:01:07.0: PME# supported from D0 D3hot D3cold
[    0.094640] pci 0000:01:07.0: PME# disabled
[    0.094661] pci 0000:01:0a.0: [104c:8023] type 0 class 0x000c00
[    0.094679] pci 0000:01:0a.0: reg 10: [mem 0xe00fd800-0xe00fdfff]
[    0.094690] pci 0000:01:0a.0: reg 14: [mem 0xe00f8000-0xe00fbfff]
[    0.094744] pci 0000:01:0a.0: supports D1 D2
[    0.094748] pci 0000:01:0a.0: PME# supported from D0 D1 D2 D3hot
[    0.094753] pci 0000:01:0a.0: PME# disabled
[    0.094773] pci 0000:01:0c.0: [10ec:8139] type 0 class 0x000200
[    0.094790] pci 0000:01:0c.0: reg 10: [io  0xc800-0xc8ff]
[    0.094801] pci 0000:01:0c.0: reg 14: [mem 0xe00fd400-0xe00fd4ff]
[    0.094854] pci 0000:01:0c.0: supports D1 D2
[    0.094858] pci 0000:01:0c.0: PME# supported from D1 D2 D3hot D3cold
[    0.094863] pci 0000:01:0c.0: PME# disabled
[    0.094892] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.094898] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.094905] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xe00fffff]
[    0.094911] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.094916] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.094921] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.094963] pci_bus 0000:02: [bus 02-05] partially hidden behind transparent bridge 0000:01 [bus 01-01]
[    0.094995] pci_bus 0000:06: [bus 06-09] partially hidden behind transparent bridge 0000:01 [bus 01-01]
[    0.095007] pci_bus 0000:00: on NUMA node 0
[    0.095013] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.095145] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.176970] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.177091] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.177207] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.177322] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.177438] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.177555] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.177673] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.177791] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.177851] HEST: Table is not found!
[    0.177956] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.177971] vgaarb: loaded
[    0.178296] SCSI subsystem initialized
[    0.178361] libata version 3.00 loaded.
[    0.178440] usbcore: registered new interface driver usbfs
[    0.178460] usbcore: registered new interface driver hub
[    0.178499] usbcore: registered new device driver usb
[    0.178729] wmi: Mapper loaded
[    0.178732] PCI: Using ACPI for IRQ routing
[    0.178737] PCI: pci_cache_line_size set to 64 bytes
[    0.178817] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.178822] reserve RAM buffer: 000000003efd0000 - 000000003fffffff 
[    0.180009] NetLabel: Initializing
[    0.180012] NetLabel:  domain hash size = 128
[    0.180015] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.180034] NetLabel:  unlabeled traffic allowed by default
[    0.180102] Switching to clocksource tsc
[    0.191597] AppArmor: AppArmor Filesystem Enabled
[    0.191630] pnp: PnP ACPI init
[    0.191685] ACPI: bus type pnp registered
[    0.191874] pnp 00:00: [bus 00-ff]
[    0.191880] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.191884] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.191914] pnp 00:00: [io  0x0d00-0xffff window]
[    0.191918] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.191922] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.191927] pnp 00:00: [mem 0x000d4000-0x000d6fff window]
[    0.191931] pnp 00:00: [mem 0x000d7000-0x000d7fff window]
[    0.191935] pnp 00:00: [mem 0x000de000-0x000dffff window]
[    0.191939] pnp 00:00: [mem 0x3f000000-0xffffffff window]
[    0.192040] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.192126] pnp 00:01: [dma 4]
[    0.192130] pnp 00:01: [io  0x0000-0x000f]
[    0.192133] pnp 00:01: [io  0x0081-0x0083]
[    0.192137] pnp 00:01: [io  0x0087]
[    0.192140] pnp 00:01: [io  0x0089-0x008b]
[    0.192144] pnp 00:01: [io  0x008f]
[    0.192147] pnp 00:01: [io  0x00c0-0x00df]
[    0.192199] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.192224] pnp 00:02: [io  0x0070-0x0071]
[    0.192246] pnp 00:02: [irq 8]
[    0.192300] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.192364] pnp 00:03: [io  0x0060]
[    0.192368] pnp 00:03: [io  0x0064]
[    0.192376] pnp 00:03: [irq 1]
[    0.192429] pnp 00:03: Plug and Play ACPI device, IDs PNP030b PNP0303 (active)
[    0.192521] pnp 00:04: [irq 12]
[    0.192575] pnp 00:04: Plug and Play ACPI device, IDs SYN0801 SYN0800 PNP0f13 (active)
[    0.192591] pnp 00:05: [io  0x0061]
[    0.192641] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.192657] pnp 00:06: [io  0x00f0-0x00ff]
[    0.192663] pnp 00:06: [irq 13]
[    0.192728] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.192931] pnp 00:07: [io  0x0010-0x001f]
[    0.192935] pnp 00:07: [io  0x0022-0x003f]
[    0.192938] pnp 00:07: [io  0x0044-0x005f]
[    0.192942] pnp 00:07: [io  0x0063]
[    0.192945] pnp 00:07: [io  0x0065]
[    0.192949] pnp 00:07: [io  0x0067-0x006f]
[    0.192952] pnp 00:07: [io  0x0072-0x007f]
[    0.192956] pnp 00:07: [io  0x0080]
[    0.192959] pnp 00:07: [io  0x0084-0x0086]
[    0.192962] pnp 00:07: [io  0x0088]
[    0.192966] pnp 00:07: [io  0x008c-0x008e]
[    0.192969] pnp 00:07: [io  0x0090-0x009f]
[    0.192973] pnp 00:07: [io  0x00a2-0x00bf]
[    0.192977] pnp 00:07: [io  0x00e0-0x00ef]
[    0.192980] pnp 00:07: [io  0x04d0-0x04d1]
[    0.192984] pnp 00:07: [io  0x0400-0x047f]
[    0.192987] pnp 00:07: [io  0x0500-0x053f]
[    0.193111] pnp 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.193271] pnp 00:08: [io  0x1100-0x113f]
[    0.193275] pnp 00:08: [io  0x1254]
[    0.193278] pnp 00:08: [io  0x12d4]
[    0.193282] pnp 00:08: [io  0x1300-0x1375]
[    0.193286] pnp 00:08: [io  0x1377-0x137f]
[    0.193290] pnp 00:08: [io  0x0000-0xffffffff disabled]
[    0.193293] pnp 00:08: [io  0x0200-0x020f]
[    0.193297] pnp 00:08: [io  0x0860-0x086f]
[    0.193301] pnp 00:08: [mem 0xfec00000-0xfec00fff]
[    0.193305] pnp 00:08: [mem 0xfee00000-0xfee00fff]
[    0.193308] pnp 00:08: [mem 0xfec10000-0xfec1ffff]
[    0.193312] pnp 00:08: [mem 0xffe80000-0xffefffff]
[    0.193316] pnp 00:08: [mem 0xfff80000-0xffffffff]
[    0.193320] pnp 00:08: [mem 0xfee00400-0xffbfffff]
[    0.193324] pnp 00:08: [mem 0xfff00000-0xfff7ffff]
[    0.193424] pnp 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.193990] pnp 00:09: [mem 0x00000000-0x0009ffff]
[    0.193994] pnp 00:09: [mem 0x00000000-0xffffffff disabled]
[    0.193998] pnp 00:09: [mem 0x000e0000-0x000fffff]
[    0.194002] pnp 00:09: [mem 0x00100000-0x3effffff]
[    0.194006] pnp 00:09: [mem 0x00000000-0xffffffff disabled]
[    0.194087] pnp 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.194424] pnp: PnP ACPI: found 10 devices
[    0.194428] ACPI: ACPI bus type pnp unregistered
[    0.194434] PnPBIOS: Disabled by ACPI PNP
[    0.194457] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.194462] system 00:07: [io  0x0400-0x047f] has been reserved
[    0.194467] system 00:07: [io  0x0500-0x053f] has been reserved
[    0.194475] system 00:08: [io  0x1100-0x113f] has been reserved
[    0.194480] system 00:08: [io  0x1254] has been reserved
[    0.194484] system 00:08: [io  0x12d4] has been reserved
[    0.194489] system 00:08: [io  0x1300-0x1375] has been reserved
[    0.194493] system 00:08: [io  0x1377-0x137f] has been reserved
[    0.194498] system 00:08: [io  0x0200-0x020f] has been reserved
[    0.194503] system 00:08: [io  0x0860-0x086f] has been reserved
[    0.194509] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.194514] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.194519] system 00:08: [mem 0xfec10000-0xfec1ffff] has been reserved
[    0.194524] system 00:08: [mem 0xffe80000-0xffefffff] has been reserved
[    0.194529] system 00:08: [mem 0xfff80000-0xffffffff] has been reserved
[    0.194534] system 00:08: [mem 0xfee00400-0xffbfffff] could not be reserved
[    0.194539] system 00:08: [mem 0xfff00000-0xfff7ffff] has been reserved
[    0.194548] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.194553] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.194558] system 00:09: [mem 0x00100000-0x3effffff] could not be reserved
[    0.232089] pci 0000:00:1e.0: BAR 15: assigned [mem 0x40000000-0x47ffffff pref]
[    0.232097] pci 0000:00:1f.1: BAR 5: assigned [mem 0x48000000-0x480003ff]
[    0.232106] pci 0000:00:1f.1: BAR 5: set to [mem 0x48000000-0x480003ff] (PCI address [0x48000000-0x480003ff])
[    0.232114] pci 0000:01:03.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.232123] pci 0000:01:03.0: BAR 16: assigned [mem 0x4c000000-0x4fffffff]
[    0.232128] pci 0000:01:03.1: BAR 15: assigned [mem 0x44000000-0x47ffffff pref]
[    0.232136] pci 0000:01:03.1: BAR 16: assigned [mem 0x50000000-0x53ffffff]
[    0.232140] pci 0000:01:03.0: BAR 0: assigned [mem 0xe0000000-0xe0000fff]
[    0.232147] pci 0000:01:03.0: BAR 0: set to [mem 0xe0000000-0xe0000fff] (PCI address [0xe0000000-0xe0000fff])
[    0.232153] pci 0000:01:03.1: BAR 0: assigned [mem 0xe0001000-0xe0001fff]
[    0.232160] pci 0000:01:03.1: BAR 0: set to [mem 0xe0001000-0xe0001fff] (PCI address [0xe0001000-0xe0001fff])
[    0.232165] pci 0000:01:03.0: BAR 13: assigned [io  0xc000-0xc0ff]
[    0.232170] pci 0000:01:03.0: BAR 14: assigned [io  0xc400-0xc4ff]
[    0.232174] pci 0000:01:03.1: BAR 13: assigned [io  0xcc00-0xccff]
[    0.232180] pci 0000:01:03.1: BAR 14: assigned [io  0x1000-0x10ff]
[    0.232185] pci 0000:01:03.0: CardBus bridge to [bus 02-05]
[    0.232189] pci 0000:01:03.0:   bridge window [io  0xc000-0xc0ff]
[    0.232195] pci 0000:01:03.0:   bridge window [io  0xc400-0xc4ff]
[    0.232201] pci 0000:01:03.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.232207] pci 0000:01:03.0:   bridge window [mem 0x4c000000-0x4fffffff]
[    0.232213] pci 0000:01:03.1: CardBus bridge to [bus 06-09]
[    0.232217] pci 0000:01:03.1:   bridge window [io  0xcc00-0xccff]
[    0.232223] pci 0000:01:03.1:   bridge window [io  0x1000-0x10ff]
[    0.232229] pci 0000:01:03.1:   bridge window [mem 0x44000000-0x47ffffff pref]
[    0.232235] pci 0000:01:03.1:   bridge window [mem 0x50000000-0x53ffffff]
[    0.232241] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.232247] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.232254] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xe00fffff]
[    0.232260] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x47ffffff pref]
[    0.232279] pci 0000:00:1e.0: setting latency timer to 64
[    0.232300] pci 0000:01:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.232309] pci 0000:01:03.1: enabling device (0000 -> 0003)
[    0.232315] pci 0000:01:03.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.232324] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.232328] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.232332] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.232337] pci_bus 0000:01: resource 1 [mem 0xe0000000-0xe00fffff]
[    0.232341] pci_bus 0000:01: resource 2 [mem 0x40000000-0x47ffffff pref]
[    0.232345] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.232349] pci_bus 0000:01: resource 5 [mem 0x00000000-0xffffffff]
[    0.232354] pci_bus 0000:02: resource 0 [io  0xc000-0xc0ff]
[    0.232358] pci_bus 0000:02: resource 1 [io  0xc400-0xc4ff]
[    0.232362] pci_bus 0000:02: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.232366] pci_bus 0000:02: resource 3 [mem 0x4c000000-0x4fffffff]
[    0.232371] pci_bus 0000:06: resource 0 [io  0xcc00-0xccff]
[    0.232375] pci_bus 0000:06: resource 1 [io  0x1000-0x10ff]
[    0.232379] pci_bus 0000:06: resource 2 [mem 0x44000000-0x47ffffff pref]
[    0.232383] pci_bus 0000:06: resource 3 [mem 0x50000000-0x53ffffff]
[    0.232442] NET: Registered protocol family 2
[    0.232552] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.232937] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.234419] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.235330] TCP: Hash tables configured (established 131072 bind 65536)
[    0.235335] TCP reno registered
[    0.235343] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.235377] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.235579] NET: Registered protocol family 1
[    0.235631] pci 0000:00:02.0: Boot video device
[    0.235745] PCI: CLS 64 bytes, default 64
[    0.235839] Trying to unpack rootfs image as initramfs...
[    0.958669] Freeing initrd memory: 16424k freed
[    0.975881] cpufreq-nforce2: No nForce2 chipset.
[    0.975944] Scanning for low memory corruption every 60 seconds
[    0.976297] audit: initializing netlink socket (disabled)
[    0.976318] type=2000 audit(1294575363.972:1): initialized
[    0.993288] highmem bounce pool size: 64 pages
[    0.993297] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.996341] VFS: Disk quotas dquot_6.5.2
[    0.996435] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.997545] fuse init (API version 7.15)
[    0.997704] msgmni has been set to 1729
[    0.998071] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.998076] io scheduler noop registered
[    0.998079] io scheduler deadline registered
[    0.998103] io scheduler cfq registered (default)
[    0.998333] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.998371] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.008913] ACPI: AC Adapter [AC0] (on-line)
[    1.009030] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.009067] ACPI: Lid Switch [LID]
[    1.009150] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.009157] ACPI: Sleep Button [SLPB]
[    1.009237] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.009242] ACPI: Power Button [PWRB]
[    1.009318] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.009324] ACPI: Power Button [PWRF]
[    1.009507] ACPI: acpi_idle registered with cpuidle
[    1.009549] Marking TSC unstable due to TSC halts in idle
[    1.010416] Switching to clocksource acpi_pm
[    1.011488] thermal LNXTHERM:00: registered as thermal_zone0
[    1.011492] ACPI: Thermal Zone [THRM] (11 C)
[    1.011551] ERST: Table is not found!
[    1.011579] isapnp: Scanning for PnP cards...
[    1.365551] isapnp: No Plug & Play device found
[    1.365766] Linux agpgart interface v0.103
[    1.365877] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[    1.365903] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    1.366726] agpgart-intel 0000:00:00.0: detected 16384K stolen memory
[    1.368534] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
[    1.368616] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.370419] serial 0000:00:1f.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.370428] serial 0000:00:1f.6: PCI INT B disabled
[    1.372480] brd: module loaded
[    1.373428] loop: module loaded
[    1.373719] ata_piix 0000:00:1f.1: version 2.13
[    1.373731] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    1.373749] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.373800] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.374333] scsi0 : ata_piix
[    1.374466] scsi1 : ata_piix
[    1.377403] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.377408] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.378013] Fixed MDIO Bus: probed
[    1.378066] PPP generic driver version 2.4.2
[    1.378131] tun: Universal TUN/TAP device driver, 1.6
[    1.378134] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.378259] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.378283] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.378301] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.378307] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.378366] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.378405] ehci_hcd 0000:00:1d.7: debug port 1
[    1.382279] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.382548] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe02ffc00
[    1.396017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.396208] hub 1-0:1.0: USB hub found
[    1.396216] hub 1-0:1.0: 6 ports detected
[    1.396336] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.396358] uhci_hcd: USB Universal Host Controller Interface driver
[    1.396396] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.396404] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.396409] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.396485] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.396525] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e480
[    1.396721] hub 2-0:1.0: USB hub found
[    1.396728] hub 2-0:1.0: 2 ports detected
[    1.396825] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.396834] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.396838] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.396894] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.396930] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e800
[    1.397129] hub 3-0:1.0: USB hub found
[    1.397135] hub 3-0:1.0: 2 ports detected
[    1.397239] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.397247] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.397252] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.397306] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.397342] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e880
[    1.397555] hub 4-0:1.0: USB hub found
[    1.397562] hub 4-0:1.0: 2 ports detected
[    1.397748] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.403859] i8042.c: Detected active multiplexing controller, rev 1.0.
[    1.404748] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.404757] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.404919] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.404963] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.405006] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.405183] mice: PS/2 mouse device common for all mice
[    1.405936] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.405960] rtc0: alarms up to one month, 114 bytes nvram
[    1.406142] device-mapper: uevent: version 1.0.3
[    1.406453] device-mapper: ioctl: 4.18.0-ioctl (2010-06-29) initialised: dm-devel@redhat.com
[    1.406708] device-mapper: multipath: version 1.1.1 loaded
[    1.406713] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.406933] EISA: Probing bus 0 at eisa.0
[    1.406941] Cannot allocate resource for EISA slot 1
[    1.406973] EISA: Detected 0 cards.
[    1.407168] cpuidle: using governor ladder
[    1.407253] cpuidle: using governor menu
[    1.407696] TCP cubic registered
[    1.407918] NET: Registered protocol family 10
[    1.408486] lo: Disabled Privacy Extensions
[    1.408860] NET: Registered protocol family 17
[    1.408882] Registering the dns_resolver key type
[    1.409530] Using IPI No-Shortcut mode
[    1.410010] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.411983] PM: Hibernation image not present or could not be loaded.
[    1.412174] registered taskstats version 1
[    1.414807]   Magic number: 11:634:278
[    1.414837] tty tty15: hash matches
[    1.414893] rtc_cmos 00:02: setting system clock to 2011-01-09 12:16:05 UTC (1294575365)
[    1.414898] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.414901] EDD information not available.
[    1.417686] ACPI: Battery Slot [BAT0] (battery present)
[    1.544539] ata1.00: ATA-7: FUJITSU MHV2080AH, 000000A0, max UDMA/100
[    1.544544] ata1.00: 156301488 sectors, multi 16: LBA 
[    1.560414] ata2.00: ATAPI: _NEC DVD+/-RW ND-6500A, 2.40, max UDMA/33
[    1.560646] ata1.00: configured for UDMA/100
[    1.560811] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080A 0000 PQ: 0 ANSI: 5
[    1.561049] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.561165] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.561251] sd 0:0:0:0: [sda] Write Protect is off
[    1.561255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.561292] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.608173] ata2.00: configured for UDMA/33
[    1.614393]  sda: sda1 sda2 < sda5 >
[    1.614769] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.695361] scsi 1:0:0:0: CD-ROM            _NEC     DVD+-RW ND-6500A 2.40 PQ: 0 ANSI: 5
[    1.817448] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.817453] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.817597] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.817684] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.817756] Freeing unused kernel memory: 740k freed
[    1.818262] Write protecting the kernel text: 5132k
[    1.818328] Write protecting the kernel read-only data: 2104k
[    1.842298] udev[69]: starting version 163
[    2.083270] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.083310] 8139cp 0000:01:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.094492] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input5
[    2.094580] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[    2.124099] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.124158] 8139too 0000:01:0c.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.125469] 8139too 0000:01:0c.0: eth0: RealTek RTL8139 at 0xc800, 00:03:0d:1f:8e:81, IRQ 19
[    2.126295] firewire_ohci 0000:01:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.182033] firewire_ohci: Added fw-ohci device 0000:01:0a.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    2.211224] [drm] Initialized drm 1.1.0 20060810
[    2.268821] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.268830] i915 0000:00:02.0: setting latency timer to 64
[    2.334212] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.334787] [drm] initialized overlay support
[    2.680357] firewire_core: created device fw0: GUID 00030d4925503c19, S400
[    3.316074] [drm:intel_panel_get_max_backlight] *ERROR* fixme: max PWM is zero.
[    3.325532] Console: switching to colour frame buffer device 128x48
[    3.333805] fb0: inteldrmfb frame buffer device
[    3.333808] drm: registered panic notifier
[    3.334005] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.968935] Btrfs loaded
[    9.342109] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    9.342117] EXT4-fs (sda1): write access will be enabled during recovery
[   11.903055] EXT4-fs (sda1): orphan cleanup on readonly fs
[   11.903070] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1311021
[   11.903178] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1310867
[   11.903198] EXT4-fs (sda1): 2 orphan inodes deleted
[   11.903202] EXT4-fs (sda1): recovery complete
[   12.176272] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.217653] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.319546] udev[304]: starting version 163
[   16.886266] intel_rng: FWH not detected
[   17.042969] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.083808] lib80211: common routines for IEEE802.11 drivers
[   17.083815] lib80211_crypt: registered algorithm 'NULL'
[   17.120294] cfg80211: Calling CRDA to update world regulatory domain
[   17.409575] libipw: 802.11 data/management/control stack, git-1.1.13
[   17.409581] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.476390] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   17.476397] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   17.476555] ipw2200 0000:01:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   17.480029] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   17.878686] lp: driver loaded but no devices found
[   17.975508] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[    18.037103] type=1400 audit(1294575382.119:2): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient3" pid=445  comm="apparmor_parser"
[   18.037213] type=1400  audit(1294575382.119:3): apparmor="STATUS" operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=445  comm="apparmor_parser"
[   18.037302] type=1400  audit(1294575382.119:4): apparmor="STATUS" operation="profile_load"  name="/usr/lib/connman/scripts/dhclient-script" pid=445  comm="apparmor_parser"
[   18.134196] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x6eb1, caps: 0xa04711/0x40a/0x0
[   18.173741] yenta_cardbus 0000:01:03.0: CardBus bridge found [1734:106a]
[    18.173771] yenta_cardbus 0000:01:03.0: O2: enabling read prefetch/write  burst. If you experience problems or performance issues, use the  yenta_socket parameter 'o2_speedup=off'
[   18.185009] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input6
[    18.254552] type=1400 audit(1294575382.335:5): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient3" pid=529  comm="apparmor_parser"
[   18.254663] type=1400  audit(1294575382.335:6): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=529  comm="apparmor_parser"
[   18.254754] type=1400  audit(1294575382.335:7): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=529  comm="apparmor_parser"
[   18.300919] yenta_cardbus 0000:01:03.0: ISA IRQ mask 0x0cb8, PCI irq 17
[   18.300926] yenta_cardbus 0000:01:03.0: Socket status: 30000006
[   18.300933] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #01 to #05
[   18.300948] yenta_cardbus 0000:01:03.0: pcmcia: parent PCI bridge window: [io  0xc000-0xcfff]
[    18.300954] pcmcia_socket pcmcia_socket0: cs: IO port probe  0xc000-0xcfff: excluding 0xc000-0xc0ff 0xc400-0xc4ff 0xc800-0xc8ff  0xcc00-0xccff
[   18.306023] yenta_cardbus 0000:01:03.0: pcmcia: parent PCI bridge window: [mem 0xe0000000-0xe00fffff]
[    18.306029] pcmcia_socket pcmcia_socket0: cs: memory probe  0xe0000000-0xe00fffff: excluding 0xe0000000-0xe000ffff  0xe00f0000-0xe00fffff
[   18.306050] yenta_cardbus 0000:01:03.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x47ffffff pref]
[   18.306055] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x47ffffff: excluding 0x40000000-0x47ffffff
[   18.306860] yenta_cardbus 0000:01:03.1: CardBus bridge found [1734:106a]
[   18.432955] yenta_cardbus 0000:01:03.1: ISA IRQ mask 0x0cb8, PCI irq 17
[   18.432961] yenta_cardbus 0000:01:03.1: Socket status: 30000006
[   18.432967] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #05 to #09
[   18.432979] yenta_cardbus 0000:01:03.1: pcmcia: parent PCI bridge window: [io  0xc000-0xcfff]
[    18.432985] pcmcia_socket pcmcia_socket1: cs: IO port probe  0xc000-0xcfff: excluding 0xc000-0xc0ff 0xc400-0xc4ff 0xc800-0xc8ff  0xcc00-0xccff
[   18.438007] yenta_cardbus 0000:01:03.1: pcmcia: parent PCI bridge window: [mem 0xe0000000-0xe00fffff]
[    18.438013] pcmcia_socket pcmcia_socket1: cs: memory probe  0xe0000000-0xe00fffff: excluding 0xe0000000-0xe000ffff  0xe00f0000-0xe00fffff
[   18.438034] yenta_cardbus 0000:01:03.1: pcmcia: parent PCI bridge window: [mem 0x40000000-0x47ffffff pref]
[   18.438039] pcmcia_socket pcmcia_socket1: cs: memory probe 0x40000000-0x47ffffff: excluding 0x40000000-0x47ffffff
[   19.410465] cfg80211: World regulatory domain updated:
[   19.410473]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.410477]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.410482]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.410486]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.410491]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.410495]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    19.705098] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af:  excluding 0x170-0x177 0x1f0-0x1f7 0x200-0x20f 0x370-0x377
[   19.706775] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x400-0x47f 0x4d0-0x4d7
[   19.707220] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: excluding 0x860-0x86f
[   19.707804] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7:
[    19.708189] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:  excluding 0x170-0x177 0x1f0-0x1f7 0x200-0x20f 0x370-0x377
[   19.709847] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x400-0x47f 0x4d0-0x4d7
[   19.710288] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding 0x860-0x86f
[   19.710871] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[    19.711551] pcmcia_socket pcmcia_socket0: cs: memory probe  0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff  0xe0000-0xfffff
[   19.711636] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   19.711719] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   19.711807] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[    19.712822] pcmcia_socket pcmcia_socket1: cs: memory probe  0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff  0xe0000-0xfffff
[   19.712907] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   19.712990] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: clean.
[   19.713080] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   19.714581]  clean.
[   20.861717] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   20.861760] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   21.688035] intel8x0_measure_ac97_clock: measured 55422 usecs (2671 samples)
[   21.688041] intel8x0: clocking to 48000
[    22.811478] type=1400 audit(1294575386.891:8): apparmor="STATUS"  operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=660  comm="apparmor_parser"
[   22.811756] type=1400  audit(1294575386.891:9): apparmor="STATUS" operation="profile_load"  name="/usr/sbin/cupsd" pid=660 comm="apparmor_parser"
[   23.596222] ppdev: user-space parallel port driver
[    23.771974] type=1400 audit(1294575387.851:10): apparmor="STATUS"  operation="profile_load" name="/usr/share/gdm/guest-session/Xsession"  pid=722 comm="apparmor_parser"
[   24.035239] type=1400  audit(1294575388.115:11): apparmor="STATUS" operation="profile_replace"  name="/sbin/dhclient3" pid=732 comm="apparmor_parser"
[   24.035353]  type=1400 audit(1294575388.115:12): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=732  comm="apparmor_parser"
[   24.035449] type=1400  audit(1294575388.115:13): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=732  comm="apparmor_parser"
[   24.303836] eth0: link down
[   24.304516] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.058750] padlock: VIA PadLock not detected.
[   26.528174] padlock: VIA PadLock Hash Engine not detected.
[   26.668537] lib80211_crypt: registered algorithm 'CCMP'
[   27.848360] Adding 93180k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:93180k 
[    32.878171] type=1400 audit(1294575396.959:14): apparmor="STATUS"  operation="profile_load" name="/usr/bin/evince" pid=738  comm="apparmor_parser"
[   32.879489] type=1400  audit(1294575396.959:15): apparmor="STATUS" operation="profile_load"  name="/usr/bin/evince-previewer" pid=738 comm="apparmor_parser"
[    32.881040] type=1400 audit(1294575396.963:16): apparmor="STATUS"  operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=738  comm="apparmor_parser"
[   33.355274] type=1400  audit(1294575397.435:17): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/cups/backend/cups-pdf" pid=1007 comm="apparmor_parser"
[    33.355571] type=1400 audit(1294575397.435:18): apparmor="STATUS"  operation="profile_replace" name="/usr/sbin/cupsd" pid=1007  comm="apparmor_parser"
[   33.533160] type=1400  audit(1294575397.615:19): apparmor="STATUS" operation="profile_load"  name="/usr/sbin/tcpdump" pid=1008 comm="apparmor_parser"
[   34.448021] eth1: no IPv6 routers present
[/PHP]

---

### Post by Byb on 2011-01-09
Don't forget your friends :popcorn::popcorn::popcorn::popcorn::popcorn:
[COLOR=Red]**dpkg.log**[/COLOR][PHP]nothing today[/PHP][COLOR=Red]**jockey.log**[/COLOR][PHP]nothing today[/PHP][COLOR=Red]**kern.log**[/COLOR][PHP]Jan  9 10:29:51 Amilo-M7405 kernel: [   39.154327] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan  9 12:20:01 Amilo-M7405 kernel: [ 6649.301918] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan  9 13:16:23 Amilo-M7405 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Initializing cgroup subsys cpu
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.000000] Linux version  2.6.37-020637-generic (root@zinc) (gcc version 4.2.3 (Ubuntu  4.2.3-2ubuntu7)) #201101050908 SMP Wed Jan 5 10:17:13 UTC 2011
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] BIOS-provided physical RAM map:
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003efd0000 (usable)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 000000003efd0000 - 000000003efdf000 (ACPI data)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 000000003efdf000 - 000000003f000000 (ACPI NVS)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Notice: NX (Execute Disable) protection missing in CPU or disabled in BIOS!
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] DMI 2.3 present.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] DMI: 255/259 Series                  /Amilo M7405 , BIOS 1.03C   01/25/2005
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.000000] e820 update range:  0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] last_pfn = 0x3efd0 max_arch_pfn = 0x100000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] MTRR default type: uncachable
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] MTRR fixed ranges enabled:
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   00000-9FFFF write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   A0000-EFFFF uncachable
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   F0000-FFFFF write-protect
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] MTRR variable ranges enabled:
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   0 base 000000000 mask FE0000000 write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   1 base 020000000 mask FF0000000 write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   2 base 030000000 mask FF8000000 write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   3 base 038000000 mask FFC000000 write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   4 base 03C000000 mask FFE000000 write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   5 base 03E000000 mask FFF000000 write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   6 disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   7 disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PAT not supported by CPU.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] initial memory mapped : 0 - 01000000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ ffb000-1000000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] RAMDISK: 2e412000 - 2f41c000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: RSDP 000f6790 00014 (v00 ACPIAM)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: RSDT 3efd0000 00034 (v01 A M I  OEMRSDT  01000525 MSFT 00000097)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: FACP 3efd0200 00081 (v02 A M I  OEMFACP  01000525 MSFT 00000097)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: DSDT 3efd03f0 03714 (v01 UW     F07_____ 00000001 INTL 02002026)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: FACS 3efdf000 00040
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: APIC 3efd0390 00054 (v01 A M I  OEMAPIC  01000525 MSFT 00000097)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: OEMB 3efdf040 00040 (v01 A M I  AMI_OEM  01000525 MSFT 00000097)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: SSDT 3efd3b10 00394 (v01    AMI   CPU1PM 00000001 INTL 02002026)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] 119MB HIGHMEM available.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] 887MB LOWMEM available.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   low ram: 0 - 377fe000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Zone PFN ranges:
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003efd0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Movable zone start PFN for each node
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] early_node_map[2] active PFN ranges
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     0: 0x00000100 -> 0x0003efd0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] On node 0 totalpages: 257887
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] free_area_init_node: node 0, pgdat c0850d00, node_mem_map f701d200
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   DMA zone: 0 pages reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   HighMem zone: 240 pages used for memmap
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   HighMem zone: 30434 pages, LIFO batch:7
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Using APIC driver default
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] nr_irqs_gsi: 40
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Allocating PCI resources starting at 3f000000 (gap: 3f000000:c1000000)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PERCPU: Embedded 12 pages/cpu @f6c00000 s28544 r0 d20608 u4194304
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] pcpu-alloc: s28544 r0 d20608 u4194304 alloc=1*4194304
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] pcpu-alloc: [0] 0 
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 255871
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637-generic  root=UUID=53f4ad58-f05f-4972-b816-4105751cba54 ro quiet splash
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Initializing CPU#0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] allocated 5159680 bytes of page_cgroup
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003efd0)
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.000000] Memory: 991900k/1032000k  available (5128k kernel code, 39648k reserved, 2467k data, 740k init,  122696k highmem)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] virtual kernel memory layout:
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]       .init : 0xc086c000 - 0xc0925000   ( 740 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]       .data : 0xc060234f - 0xc086b108   (2467 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]       .text : 0xc0100000 - 0xc060234f   (5128 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Hierarchical RCU implementation.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256 16
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] CPU 0 irqstacks, hard=f6008000 soft=f600a000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Console: colour VGA+ 80x25
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] console [tty0] enabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Fast TSC calibration using PIT
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Detected 1400.005 MHz processor.
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.004006] Calibrating delay loop  (skipped), value calculated using timer frequency.. 2800.01 BogoMIPS  (lpj=5600020)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.004013] pid_max: default: 32768 minimum: 301
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.004046] Security Framework initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.004069] AppArmor: AppArmor initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.004151] Mount-cache hash table entries: 512
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008127] Initializing cgroup subsys ns
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.008133] ns_cgroup deprecated:  consider using the 'clone_children' flag without the ns_cgroup.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008138] Initializing cgroup subsys cpuacct
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008145] Initializing cgroup subsys memory
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008162] Initializing cgroup subsys devices
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008165] Initializing cgroup subsys freezer
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008169] Initializing cgroup subsys net_cls
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008218] mce: CPU supports 5 MCE banks
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008232] CPU0: Thermal monitoring enabled (TM2)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008243] Performance Events: p6 PMU driver.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008254] ... version:                0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008257] ... bit width:              32
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008260] ... generic registers:      2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008263] ... value mask:             00000000ffffffff
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008267] ... max period:             000000007fffffff
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008270] ... fixed-purpose events:   0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008273] ... event mask:             0000000000000003
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.009452] SMP alternatives: switching to UP code
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.018985] Freeing SMP alternatives: 20k freed
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.018998] ACPI: Core revision 20101013
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.028014] ftrace: allocating 26658 entries in 53 pages
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.032093] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.032397] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.072731] CPU0: Intel(R) Pentium(R) M processor 1.40GHz stepping 06
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] Brought up 1 CPUs
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] Total of 1 processors activated (2800.01 BogoMIPS).
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] devtmpfs: initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] regulator: core version 0.5
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] regulator: dummy: 
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] Time: 12:16:04  Date: 01/09/11
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] NET: Registered protocol family 16
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] EISA bus registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] ACPI: bus type pci registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] PCI: Using configuration type 1 for base access
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.077452] bio: create slab <bio-0> at 0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.078669] ACPI: EC: Look up EC in DSDT
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.079932] ACPI: Executed 2 blocks of module-level executable AML code
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.084045] ACPI: Interpreter enabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.084054] ACPI: (supports S0 S3 S4 S5)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.084087] ACPI: Using IOAPIC for interrupt routing
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.092517] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.092695] ACPI: No dock devices found.
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.092702] PCI: Ignoring host bridge  windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.092803] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093024] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093029] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093034] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093038] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093043] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d6fff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093048] pci_root PNP0A03:00: host bridge window [mem 0x000d7000-0x000d7fff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093052] pci_root PNP0A03:00: host bridge window [mem 0x000de000-0x000dffff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093057] pci_root PNP0A03:00: host bridge window [mem 0x3f000000-0xffffffff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093074] pci 0000:00:00.0: [8086:3580] type 0 class 0x000600
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093121] pci 0000:00:00.1: [8086:3584] type 0 class 0x000880
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093167] pci 0000:00:00.3: [8086:3585] type 0 class 0x000880
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093219] pci 0000:00:02.0: [8086:3582] type 0 class 0x000300
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093232] pci 0000:00:02.0: reg 10: [mem 0xd8000000-0xdfffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093241] pci 0000:00:02.0: reg 14: [mem 0xe0380000-0xe03fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093249] pci 0000:00:02.0: reg 18: [io  0xec00-0xec07]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093279] pci 0000:00:02.0: supports D1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093292] pci 0000:00:02.1: [8086:3582] type 0 class 0x000380
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093304] pci 0000:00:02.1: reg 10: [mem 0xd0000000-0xd7ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093313] pci 0000:00:02.1: reg 14: [mem 0xe0300000-0xe037ffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093346] pci 0000:00:02.1: supports D1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093396] pci 0000:00:1d.0: [8086:24c2] type 0 class 0x000c03
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093441] pci 0000:00:1d.0: reg 20: [io  0xe480-0xe49f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093475] pci 0000:00:1d.1: [8086:24c4] type 0 class 0x000c03
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093520] pci 0000:00:1d.1: reg 20: [io  0xe800-0xe81f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093553] pci 0000:00:1d.2: [8086:24c7] type 0 class 0x000c03
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093598] pci 0000:00:1d.2: reg 20: [io  0xe880-0xe89f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093642] pci 0000:00:1d.7: [8086:24cd] type 0 class 0x000c03
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093665] pci 0000:00:1d.7: reg 10: [mem 0xe02ffc00-0xe02fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093743] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093750] pci 0000:00:1d.7: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093768] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093811] pci 0000:00:1f.0: [8086:24cc] type 0 class 0x000601
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093876] pci 0000:00:1f.0: quirk: [io  0x0400-0x047f] claimed by ICH4 ACPI/GPIO/TCO
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093882] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH4 GPIO
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093898] pci 0000:00:1f.1: [8086:24ca] type 0 class 0x000101
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093913] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093924] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093936] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093947] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093958] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093969] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093998] pci 0000:00:1f.3: [8086:24c3] type 0 class 0x000c05
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094043] pci 0000:00:1f.3: reg 20: [io  0xd480-0xd49f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094081] pci 0000:00:1f.5: [8086:24c5] type 0 class 0x000401
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094098] pci 0000:00:1f.5: reg 10: [io  0xd800-0xd8ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094108] pci 0000:00:1f.5: reg 14: [io  0xdc00-0xdc3f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094119] pci 0000:00:1f.5: reg 18: [mem 0xe02ff800-0xe02ff9ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094130] pci 0000:00:1f.5: reg 1c: [mem 0xe02ff400-0xe02ff4ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094167] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094173] pci 0000:00:1f.5: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094191] pci 0000:00:1f.6: [8086:24c6] type 0 class 0x000703
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094207] pci 0000:00:1f.6: reg 10: [io  0xe000-0xe0ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094218] pci 0000:00:1f.6: reg 14: [io  0xe400-0xe47f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094268] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094274] pci 0000:00:1f.6: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094308] pci 0000:01:03.0: [1217:7114] type 2 class 0x000607
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094326] pci 0000:01:03.0: reg 10: [mem 0x00000000-0x00000fff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094345] pci 0000:01:03.0: supports D1 D2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094349] pci 0000:01:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094355] pci 0000:01:03.0: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094374] pci 0000:01:03.1: [1217:7114] type 2 class 0x000607
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094392] pci 0000:01:03.1: reg 10: [mem 0x00000000-0x00000fff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094411] pci 0000:01:03.1: supports D1 D2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094415] pci 0000:01:03.1: PME# supported from D0 D1 D2 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094420] pci 0000:01:03.1: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094439] pci 0000:01:03.2: [1217:7110] type 0 class 0x000880
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094457] pci 0000:01:03.2: reg 10: [mem 0xe00ff000-0xe00fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094519] pci 0000:01:03.2: supports D1 D2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094523] pci 0000:01:03.2: PME# supported from D0 D1 D2 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094528] pci 0000:01:03.2: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094555] pci 0000:01:07.0: [8086:4220] type 0 class 0x000280
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094573] pci 0000:01:07.0: reg 10: [mem 0xe00fe000-0xe00fefff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094635] pci 0000:01:07.0: PME# supported from D0 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094640] pci 0000:01:07.0: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094661] pci 0000:01:0a.0: [104c:8023] type 0 class 0x000c00
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094679] pci 0000:01:0a.0: reg 10: [mem 0xe00fd800-0xe00fdfff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094690] pci 0000:01:0a.0: reg 14: [mem 0xe00f8000-0xe00fbfff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094744] pci 0000:01:0a.0: supports D1 D2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094748] pci 0000:01:0a.0: PME# supported from D0 D1 D2 D3hot
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094753] pci 0000:01:0a.0: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094773] pci 0000:01:0c.0: [10ec:8139] type 0 class 0x000200
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094790] pci 0000:01:0c.0: reg 10: [io  0xc800-0xc8ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094801] pci 0000:01:0c.0: reg 14: [mem 0xe00fd400-0xe00fd4ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094854] pci 0000:01:0c.0: supports D1 D2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094858] pci 0000:01:0c.0: PME# supported from D1 D2 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094863] pci 0000:01:0c.0: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094892] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094898] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094905] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xe00fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094911] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094916] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.094921] pci 0000:00:1e.0:    bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
Jan  9  13:16:23 Amilo-M7405 kernel: [    0.094963] pci_bus 0000:02: [bus  02-05] partially hidden behind transparent bridge 0000:01 [bus 01-01]
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.094995] pci_bus 0000:06: [bus  06-09] partially hidden behind transparent bridge 0000:01 [bus 01-01]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.095007] pci_bus 0000:00: on NUMA node 0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.095013] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.095145] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.176970] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177091] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177207] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177322] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.177438] ACPI: PCI Interrupt Link  [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jan  9  13:16:23 Amilo-M7405 kernel: [    0.177555] ACPI: PCI Interrupt Link  [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jan  9  13:16:23 Amilo-M7405 kernel: [    0.177673] ACPI: PCI Interrupt Link  [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177791] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177851] HEST: Table is not found!
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177956] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177971] vgaarb: loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178296] SCSI subsystem initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178361] libata version 3.00 loaded.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178440] usbcore: registered new interface driver usbfs
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178460] usbcore: registered new interface driver hub
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178499] usbcore: registered new device driver usb
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178729] wmi: Mapper loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178732] PCI: Using ACPI for IRQ routing
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178737] PCI: pci_cache_line_size set to 64 bytes
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178817] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178822] reserve RAM buffer: 000000003efd0000 - 000000003fffffff 
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180009] NetLabel: Initializing
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180012] NetLabel:  domain hash size = 128
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180015] NetLabel:  protocols = UNLABELED CIPSOv4
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180034] NetLabel:  unlabeled traffic allowed by default
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180102] Switching to clocksource tsc
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191597] AppArmor: AppArmor Filesystem Enabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191630] pnp: PnP ACPI init
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191685] ACPI: bus type pnp registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191874] pnp 00:00: [bus 00-ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191880] pnp 00:00: [io  0x0cf8-0x0cff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191884] pnp 00:00: [io  0x0000-0x0cf7 window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191914] pnp 00:00: [io  0x0d00-0xffff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191918] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191922] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191927] pnp 00:00: [mem 0x000d4000-0x000d6fff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191931] pnp 00:00: [mem 0x000d7000-0x000d7fff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191935] pnp 00:00: [mem 0x000de000-0x000dffff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191939] pnp 00:00: [mem 0x3f000000-0xffffffff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192040] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192126] pnp 00:01: [dma 4]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192130] pnp 00:01: [io  0x0000-0x000f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192133] pnp 00:01: [io  0x0081-0x0083]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192137] pnp 00:01: [io  0x0087]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192140] pnp 00:01: [io  0x0089-0x008b]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192144] pnp 00:01: [io  0x008f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192147] pnp 00:01: [io  0x00c0-0x00df]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192199] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192224] pnp 00:02: [io  0x0070-0x0071]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192246] pnp 00:02: [irq 8]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192300] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192364] pnp 00:03: [io  0x0060]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192368] pnp 00:03: [io  0x0064]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192376] pnp 00:03: [irq 1]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192429] pnp 00:03: Plug and Play ACPI device, IDs PNP030b PNP0303 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192521] pnp 00:04: [irq 12]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192575] pnp 00:04: Plug and Play ACPI device, IDs SYN0801 SYN0800 PNP0f13 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192591] pnp 00:05: [io  0x0061]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192641] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192657] pnp 00:06: [io  0x00f0-0x00ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192663] pnp 00:06: [irq 13]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192728] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192931] pnp 00:07: [io  0x0010-0x001f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192935] pnp 00:07: [io  0x0022-0x003f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192938] pnp 00:07: [io  0x0044-0x005f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192942] pnp 00:07: [io  0x0063]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192945] pnp 00:07: [io  0x0065]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192949] pnp 00:07: [io  0x0067-0x006f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192952] pnp 00:07: [io  0x0072-0x007f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192956] pnp 00:07: [io  0x0080]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192959] pnp 00:07: [io  0x0084-0x0086]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192962] pnp 00:07: [io  0x0088]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192966] pnp 00:07: [io  0x008c-0x008e]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192969] pnp 00:07: [io  0x0090-0x009f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192973] pnp 00:07: [io  0x00a2-0x00bf]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192977] pnp 00:07: [io  0x00e0-0x00ef]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192980] pnp 00:07: [io  0x04d0-0x04d1]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192984] pnp 00:07: [io  0x0400-0x047f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192987] pnp 00:07: [io  0x0500-0x053f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193111] pnp 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193271] pnp 00:08: [io  0x1100-0x113f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193275] pnp 00:08: [io  0x1254]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193278] pnp 00:08: [io  0x12d4]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193282] pnp 00:08: [io  0x1300-0x1375]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193286] pnp 00:08: [io  0x1377-0x137f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193290] pnp 00:08: [io  0x0000-0xffffffff disabled]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193293] pnp 00:08: [io  0x0200-0x020f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193297] pnp 00:08: [io  0x0860-0x086f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193301] pnp 00:08: [mem 0xfec00000-0xfec00fff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193305] pnp 00:08: [mem 0xfee00000-0xfee00fff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193308] pnp 00:08: [mem 0xfec10000-0xfec1ffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193312] pnp 00:08: [mem 0xffe80000-0xffefffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193316] pnp 00:08: [mem 0xfff80000-0xffffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193320] pnp 00:08: [mem 0xfee00400-0xffbfffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193324] pnp 00:08: [mem 0xfff00000-0xfff7ffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193424] pnp 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193990] pnp 00:09: [mem 0x00000000-0x0009ffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193994] pnp 00:09: [mem 0x00000000-0xffffffff disabled]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193998] pnp 00:09: [mem 0x000e0000-0x000fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194002] pnp 00:09: [mem 0x00100000-0x3effffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194006] pnp 00:09: [mem 0x00000000-0xffffffff disabled]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194087] pnp 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194424] pnp: PnP ACPI: found 10 devices
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194428] ACPI: ACPI bus type pnp unregistered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194434] PnPBIOS: Disabled by ACPI PNP
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194457] system 00:07: [io  0x04d0-0x04d1] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194462] system 00:07: [io  0x0400-0x047f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194467] system 00:07: [io  0x0500-0x053f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194475] system 00:08: [io  0x1100-0x113f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194480] system 00:08: [io  0x1254] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194484] system 00:08: [io  0x12d4] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194489] system 00:08: [io  0x1300-0x1375] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194493] system 00:08: [io  0x1377-0x137f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194498] system 00:08: [io  0x0200-0x020f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194503] system 00:08: [io  0x0860-0x086f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194509] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194514] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194519] system 00:08: [mem 0xfec10000-0xfec1ffff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194524] system 00:08: [mem 0xffe80000-0xffefffff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194529] system 00:08: [mem 0xfff80000-0xffffffff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194534] system 00:08: [mem 0xfee00400-0xffbfffff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194539] system 00:08: [mem 0xfff00000-0xfff7ffff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194548] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194553] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194558] system 00:09: [mem 0x00100000-0x3effffff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232089] pci 0000:00:1e.0: BAR 15: assigned [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232097] pci 0000:00:1f.1: BAR 5: assigned [mem 0x48000000-0x480003ff]
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.232106] pci 0000:00:1f.1: BAR 5:  set to [mem 0x48000000-0x480003ff] (PCI address [0x48000000-0x480003ff])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232114] pci 0000:01:03.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232123] pci 0000:01:03.0: BAR 16: assigned [mem 0x4c000000-0x4fffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232128] pci 0000:01:03.1: BAR 15: assigned [mem 0x44000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232136] pci 0000:01:03.1: BAR 16: assigned [mem 0x50000000-0x53ffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232140] pci 0000:01:03.0: BAR 0: assigned [mem 0xe0000000-0xe0000fff]
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.232147] pci 0000:01:03.0: BAR 0:  set to [mem 0xe0000000-0xe0000fff] (PCI address [0xe0000000-0xe0000fff])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232153] pci 0000:01:03.1: BAR 0: assigned [mem 0xe0001000-0xe0001fff]
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.232160] pci 0000:01:03.1: BAR 0:  set to [mem 0xe0001000-0xe0001fff] (PCI address [0xe0001000-0xe0001fff])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232165] pci 0000:01:03.0: BAR 13: assigned [io  0xc000-0xc0ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232170] pci 0000:01:03.0: BAR 14: assigned [io  0xc400-0xc4ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232174] pci 0000:01:03.1: BAR 13: assigned [io  0xcc00-0xccff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232180] pci 0000:01:03.1: BAR 14: assigned [io  0x1000-0x10ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232185] pci 0000:01:03.0: CardBus bridge to [bus 02-05]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232189] pci 0000:01:03.0:   bridge window [io  0xc000-0xc0ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232195] pci 0000:01:03.0:   bridge window [io  0xc400-0xc4ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232201] pci 0000:01:03.0:   bridge window [mem 0x40000000-0x43ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232207] pci 0000:01:03.0:   bridge window [mem 0x4c000000-0x4fffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232213] pci 0000:01:03.1: CardBus bridge to [bus 06-09]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232217] pci 0000:01:03.1:   bridge window [io  0xcc00-0xccff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232223] pci 0000:01:03.1:   bridge window [io  0x1000-0x10ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232229] pci 0000:01:03.1:   bridge window [mem 0x44000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232235] pci 0000:01:03.1:   bridge window [mem 0x50000000-0x53ffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232241] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232247] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232254] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xe00fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232260] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232279] pci 0000:00:1e.0: setting latency timer to 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232300] pci 0000:01:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232309] pci 0000:01:03.1: enabling device (0000 -> 0003)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232315] pci 0000:01:03.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232324] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232328] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232332] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232337] pci_bus 0000:01: resource 1 [mem 0xe0000000-0xe00fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232341] pci_bus 0000:01: resource 2 [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232345] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232349] pci_bus 0000:01: resource 5 [mem 0x00000000-0xffffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232354] pci_bus 0000:02: resource 0 [io  0xc000-0xc0ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232358] pci_bus 0000:02: resource 1 [io  0xc400-0xc4ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232362] pci_bus 0000:02: resource 2 [mem 0x40000000-0x43ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232366] pci_bus 0000:02: resource 3 [mem 0x4c000000-0x4fffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232371] pci_bus 0000:06: resource 0 [io  0xcc00-0xccff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232375] pci_bus 0000:06: resource 1 [io  0x1000-0x10ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232379] pci_bus 0000:06: resource 2 [mem 0x44000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232383] pci_bus 0000:06: resource 3 [mem 0x50000000-0x53ffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232442] NET: Registered protocol family 2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232552] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232937] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.234419] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235330] TCP: Hash tables configured (established 131072 bind 65536)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235335] TCP reno registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235343] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235377] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235579] NET: Registered protocol family 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235631] pci 0000:00:02.0: Boot video device
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235745] PCI: CLS 64 bytes, default 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235839] Trying to unpack rootfs image as initramfs...
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.958669] Freeing initrd memory: 16424k freed
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.975881] cpufreq-nforce2: No nForce2 chipset.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.975944] Scanning for low memory corruption every 60 seconds
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.976297] audit: initializing netlink socket (disabled)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.976318] type=2000 audit(1294575363.972:1): initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.993288] highmem bounce pool size: 64 pages
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.993297] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.996341] VFS: Disk quotas dquot_6.5.2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.996435] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.997545] fuse init (API version 7.15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.997704] msgmni has been set to 1729
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998071] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998076] io scheduler noop registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998079] io scheduler deadline registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998103] io scheduler cfq registered (default)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998333] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998371] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.008913] ACPI: AC Adapter [AC0] (on-line)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009030] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009067] ACPI: Lid Switch [LID]
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009150] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009157] ACPI: Sleep Button [SLPB]
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009237] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009242] ACPI: Power Button [PWRB]
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009318] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009324] ACPI: Power Button [PWRF]
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009507] ACPI: acpi_idle registered with cpuidle
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009549] Marking TSC unstable due to TSC halts in idle
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.010416] Switching to clocksource acpi_pm
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.011488] thermal LNXTHERM:00: registered as thermal_zone0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.011492] ACPI: Thermal Zone [THRM] (11 C)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.011551] ERST: Table is not found!
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.011579] isapnp: Scanning for PnP cards...
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.365551] isapnp: No Plug & Play device found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.365766] Linux agpgart interface v0.103
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.365877] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
Jan   9 13:16:23 Amilo-M7405 kernel: [    1.365903] agpgart-intel  0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.366726] agpgart-intel 0000:00:00.0: detected 16384K stolen memory
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.368534] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.368616] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.370419] serial 0000:00:1f.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.370428] serial 0000:00:1f.6: PCI INT B disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.372480] brd: module loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.373428] loop: module loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.373719] ata_piix 0000:00:1f.1: version 2.13
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.373731] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.373749] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.373800] ata_piix 0000:00:1f.1: setting latency timer to 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.374333] scsi0 : ata_piix
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.374466] scsi1 : ata_piix
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.377403] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.377408] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378013] Fixed MDIO Bus: probed
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378066] PPP generic driver version 2.4.2
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378131] tun: Universal TUN/TAP device driver, 1.6
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378134] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378259] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378283] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378301] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378307] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378366] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378405] ehci_hcd 0000:00:1d.7: debug port 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.382279] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.382548] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe02ffc00
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396208] hub 1-0:1.0: USB hub found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396216] hub 1-0:1.0: 6 ports detected
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396336] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396358] uhci_hcd: USB Universal Host Controller Interface driver
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396396] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396404] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396409] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396485] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396525] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e480
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396721] hub 2-0:1.0: USB hub found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396728] hub 2-0:1.0: 2 ports detected
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396825] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396834] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396838] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396894] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396930] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e800
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397129] hub 3-0:1.0: USB hub found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397135] hub 3-0:1.0: 2 ports detected
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397239] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397247] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397252] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397306] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397342] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e880
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397555] hub 4-0:1.0: USB hub found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397562] hub 4-0:1.0: 2 ports detected
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397748] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.403859] i8042.c: Detected active multiplexing controller, rev 1.0.
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.404748] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.404757] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.404919] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.404963] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.405006] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.405183] mice: PS/2 mouse device common for all mice
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.405936] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.405960] rtc0: alarms up to one month, 114 bytes nvram
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406142] device-mapper: uevent: version 1.0.3
Jan   9 13:16:23 Amilo-M7405 kernel: [    1.406453] device-mapper: ioctl:  4.18.0-ioctl (2010-06-29) initialised: dm-devel@redhat.com
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406708] device-mapper: multipath: version 1.1.1 loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406713] device-mapper: multipath round-robin: version 1.0.0 loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406933] EISA: Probing bus 0 at eisa.0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406941] Cannot allocate resource for EISA slot 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406973] EISA: Detected 0 cards.
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.407168] cpuidle: using governor ladder
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.407253] cpuidle: using governor menu
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.407696] TCP cubic registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.407918] NET: Registered protocol family 10
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.408486] lo: Disabled Privacy Extensions
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.408860] NET: Registered protocol family 17
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.408882] Registering the dns_resolver key type
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.409530] Using IPI No-Shortcut mode
Jan   9 13:16:23 Amilo-M7405 kernel: [    1.410010] input: AT Translated Set 2  keyboard as /devices/platform/i8042/serio0/input/input4
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.411983] PM: Hibernation image not present or could not be loaded.
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.412174] registered taskstats version 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414807]   Magic number: 11:634:278
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414837] tty tty15: hash matches
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414893] rtc_cmos 00:02: setting system clock to 2011-01-09 12:16:05 UTC (1294575365)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414898] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414901] EDD information not available.
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.417686] ACPI: Battery Slot [BAT0] (battery present)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.544539] ata1.00: ATA-7: FUJITSU MHV2080AH, 000000A0, max UDMA/100
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.544544] ata1.00: 156301488 sectors, multi 16: LBA 
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.560414] ata2.00: ATAPI: _NEC DVD+/-RW ND-6500A, 2.40, max UDMA/33
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.560646] ata1.00: configured for UDMA/100
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.560811] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080A 0000 PQ: 0 ANSI: 5
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.561049] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.561165] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.561251] sd 0:0:0:0: [sda] Write Protect is off
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.561255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan   9 13:16:23 Amilo-M7405 kernel: [    1.561292] sd 0:0:0:0: [sda] Write  cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.608173] ata2.00: configured for UDMA/33
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.614393]  sda: sda1 sda2 < sda5 >
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.614769] sd 0:0:0:0: [sda] Attached SCSI disk
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.695361] scsi 1:0:0:0: CD-ROM            _NEC     DVD+-RW ND-6500A 2.40 PQ: 0 ANSI: 5
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817448] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817453] cdrom: Uniform CD-ROM driver Revision: 3.20
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817597] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817684] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817756] Freeing unused kernel memory: 740k freed
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.818262] Write protecting the kernel text: 5132k
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.818328] Write protecting the kernel read-only data: 2104k
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.842298] udev[69]: starting version 163
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.083270] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jan   9 13:16:23 Amilo-M7405 kernel: [    2.083310] 8139cp 0000:01:0c.0: This  (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Jan   9 13:16:23 Amilo-M7405 kernel: [    2.094492] input: Video Bus as  /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input5
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.094580] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.124099] 8139too: 8139too Fast Ethernet driver 0.9.28
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.124158] 8139too 0000:01:0c.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jan   9 13:16:23 Amilo-M7405 kernel: [    2.125469] 8139too 0000:01:0c.0:  eth0: RealTek RTL8139 at 0xc800, 00:03:0d:1f:8e:81, IRQ 19
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.126295] firewire_ohci 0000:01:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan   9 13:16:23 Amilo-M7405 kernel: [    2.182033] firewire_ohci: Added  fw-ohci device 0000:01:0a.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks  0x2
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.211224] [drm] Initialized drm 1.1.0 20060810
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.268821] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.268830] i915 0000:00:02.0: setting latency timer to 64
Jan   9 13:16:23 Amilo-M7405 kernel: [    2.334212] vgaarb: device changed  decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.334787] [drm] initialized overlay support
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.680357] firewire_core: created device fw0: GUID 00030d4925503c19, S400
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.316074] [drm:intel_panel_get_max_backlight] *ERROR* fixme: max PWM is zero.
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.325532] Console: switching to colour frame buffer device 128x48
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.333805] fb0: inteldrmfb frame buffer device
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.333808] drm: registered panic notifier
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.334005] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.968935] Btrfs loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    9.342109] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Jan  9 13:16:23 Amilo-M7405 kernel: [    9.342117] EXT4-fs (sda1): write access will be enabled during recovery
Jan  9 13:16:23 Amilo-M7405 kernel: [   11.903055] EXT4-fs (sda1): orphan cleanup on readonly fs
Jan  9 13:16:23 Amilo-M7405 kernel: [   11.903070] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1311021
Jan  9 13:16:23 Amilo-M7405 kernel: [   11.903178] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1310867
Jan  9 13:16:23 Amilo-M7405 kernel: [   11.903198] EXT4-fs (sda1): 2 orphan inodes deleted
Jan  9 13:16:23 Amilo-M7405 kernel: [   11.903202] EXT4-fs (sda1): recovery complete
Jan  9 13:16:23 Amilo-M7405 kernel: [   12.176272] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan  9 13:16:23 Amilo-M7405 kernel: [   15.217653] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jan  9 13:16:23 Amilo-M7405 kernel: [   15.319546] udev[304]: starting version 163
Jan  9 13:16:23 Amilo-M7405 kernel: [   16.886266] intel_rng: FWH not detected
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.042969] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.083808] lib80211: common routines for IEEE802.11 drivers
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.083815] lib80211_crypt: registered algorithm 'NULL'
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.120294] cfg80211: Calling CRDA to update world regulatory domain
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.409575] libipw: 802.11 data/management/control stack, git-1.1.13
Jan   9 13:16:23 Amilo-M7405 kernel: [   17.409581] libipw: Copyright (C)  2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.476390] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.476397] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.476555] ipw2200 0000:01:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.480029] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.878686] lp: driver loaded but no devices found
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.975508] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
Jan   9 13:16:23 Amilo-M7405 kernel: [   18.037103] type=1400  audit(1294575382.119:2): apparmor="STATUS" operation="profile_load"  name="/sbin/dhclient3" pid=445 comm="apparmor_parser"
Jan  9 13:16:23  Amilo-M7405 kernel: [   18.037213] type=1400 audit(1294575382.119:3):  apparmor="STATUS" operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=445  comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [    18.037302] type=1400 audit(1294575382.119:4): apparmor="STATUS"  operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script"  pid=445 comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.134196] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x6eb1, caps: 0xa04711/0x40a/0x0
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.173741] yenta_cardbus 0000:01:03.0: CardBus bridge found [1734:106a]
Jan   9 13:16:23 Amilo-M7405 kernel: [   18.173771] yenta_cardbus  0000:01:03.0: O2: enabling read prefetch/write burst. If you experience  problems or performance issues, use the yenta_socket parameter  'o2_speedup=off'
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.185009]  input: SynPS/2 Synaptics TouchPad as  /devices/platform/i8042/serio2/input/input6
Jan  9 13:16:23  Amilo-M7405 kernel: [   18.254552] type=1400 audit(1294575382.335:5):  apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3"  pid=529 comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel:  [   18.254663] type=1400 audit(1294575382.335:6): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=529  comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [    18.254754] type=1400 audit(1294575382.335:7): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=529  comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.300919] yenta_cardbus 0000:01:03.0: ISA IRQ mask 0x0cb8, PCI irq 17
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.300926] yenta_cardbus 0000:01:03.0: Socket status: 30000006
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.300933] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #01 to #05
Jan   9 13:16:23 Amilo-M7405 kernel: [   18.300948] yenta_cardbus  0000:01:03.0: pcmcia: parent PCI bridge window: [io  0xc000-0xcfff]
Jan   9 13:16:23 Amilo-M7405 kernel: [   18.300954] pcmcia_socket  pcmcia_socket0: cs: IO port probe 0xc000-0xcfff: excluding 0xc000-0xc0ff  0xc400-0xc4ff 0xc800-0xc8ff 0xcc00-0xccff
Jan  9 13:16:23  Amilo-M7405 kernel: [   18.306023] yenta_cardbus 0000:01:03.0: pcmcia:  parent PCI bridge window: [mem 0xe0000000-0xe00fffff]
Jan  9 13:16:23  Amilo-M7405 kernel: [   18.306029] pcmcia_socket pcmcia_socket0: cs:  memory probe 0xe0000000-0xe00fffff: excluding 0xe0000000-0xe000ffff  0xe00f0000-0xe00fffff
Jan  9 13:16:23 Amilo-M7405 kernel: [    18.306050] yenta_cardbus 0000:01:03.0: pcmcia: parent PCI bridge window:  [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel:  [   18.306055] pcmcia_socket pcmcia_socket0: cs: memory probe  0x40000000-0x47ffffff: excluding 0x40000000-0x47ffffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.306860] yenta_cardbus 0000:01:03.1: CardBus bridge found [1734:106a]
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.432955] yenta_cardbus 0000:01:03.1: ISA IRQ mask 0x0cb8, PCI irq 17
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.432961] yenta_cardbus 0000:01:03.1: Socket status: 30000006
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.432967] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #05 to #09
Jan   9 13:16:23 Amilo-M7405 kernel: [   18.432979] yenta_cardbus  0000:01:03.1: pcmcia: parent PCI bridge window: [io  0xc000-0xcfff]
Jan   9 13:16:23 Amilo-M7405 kernel: [   18.432985] pcmcia_socket  pcmcia_socket1: cs: IO port probe 0xc000-0xcfff: excluding 0xc000-0xc0ff  0xc400-0xc4ff 0xc800-0xc8ff 0xcc00-0xccff
Jan  9 13:16:23  Amilo-M7405 kernel: [   18.438007] yenta_cardbus 0000:01:03.1: pcmcia:  parent PCI bridge window: [mem 0xe0000000-0xe00fffff]
Jan  9 13:16:23  Amilo-M7405 kernel: [   18.438013] pcmcia_socket pcmcia_socket1: cs:  memory probe 0xe0000000-0xe00fffff: excluding 0xe0000000-0xe000ffff  0xe00f0000-0xe00fffff
Jan  9 13:16:23 Amilo-M7405 kernel: [    18.438034] yenta_cardbus 0000:01:03.1: pcmcia: parent PCI bridge window:  [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel:  [   18.438039] pcmcia_socket pcmcia_socket1: cs: memory probe  0x40000000-0x47ffffff: excluding 0x40000000-0x47ffffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410465] cfg80211: World regulatory domain updated:
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410473]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410477]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410482]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410486]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410491]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410495]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan   9 13:16:23 Amilo-M7405 kernel: [   19.705098] pcmcia_socket  pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177  0x1f0-0x1f7 0x200-0x20f 0x370-0x377
Jan  9 13:16:23 Amilo-M7405  kernel: [   19.706775] pcmcia_socket pcmcia_socket1: cs: IO port probe  0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x400-0x47f 0x4d0-0x4d7
Jan  9  13:16:23 Amilo-M7405 kernel: [   19.707220] pcmcia_socket  pcmcia_socket1: cs: IO port probe 0x820-0x8ff: excluding 0x860-0x86f
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.707804] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7:
Jan   9 13:16:23 Amilo-M7405 kernel: [   19.708189] pcmcia_socket  pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177  0x1f0-0x1f7 0x200-0x20f 0x370-0x377
Jan  9 13:16:23 Amilo-M7405  kernel: [   19.709847] pcmcia_socket pcmcia_socket0: cs: IO port probe  0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x400-0x47f 0x4d0-0x4d7
Jan  9  13:16:23 Amilo-M7405 kernel: [   19.710288] pcmcia_socket  pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding 0x860-0x86f
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.710871] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Jan   9 13:16:23 Amilo-M7405 kernel: [   19.711551] pcmcia_socket  pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding  0xc0000-0xc7fff 0xcc000-0xcffff 0xe0000-0xfffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.711636] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.711719] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.711807] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Jan   9 13:16:23 Amilo-M7405 kernel: [   19.712822] pcmcia_socket  pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding  0xc0000-0xc7fff 0xcc000-0xcffff 0xe0000-0xfffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.712907] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.712990] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.713080] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.714581]  clean.
Jan  9 13:16:24 Amilo-M7405 kernel: [   20.861717] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jan  9 13:16:24 Amilo-M7405 kernel: [   20.861760] Intel ICH 0000:00:1f.5: setting latency timer to 64
Jan  9 13:16:25 Amilo-M7405 kernel: [   21.688035] intel8x0_measure_ac97_clock: measured 55422 usecs (2671 samples)
Jan  9 13:16:25 Amilo-M7405 kernel: [   21.688041] intel8x0: clocking to 48000
Jan   9 13:16:26 Amilo-M7405 kernel: [   22.811478] type=1400  audit(1294575386.891:8): apparmor="STATUS" operation="profile_load"  name="/usr/lib/cups/backend/cups-pdf" pid=660 comm="apparmor_parser"
Jan   9 13:16:26 Amilo-M7405 kernel: [   22.811756] type=1400  audit(1294575386.891:9): apparmor="STATUS" operation="profile_load"  name="/usr/sbin/cupsd" pid=660 comm="apparmor_parser"
Jan  9 13:16:27 Amilo-M7405 kernel: [   23.596222] ppdev: user-space parallel port driver
Jan   9 13:16:27 Amilo-M7405 kernel: [   23.771974] type=1400  audit(1294575387.851:10): apparmor="STATUS" operation="profile_load"  name="/usr/share/gdm/guest-session/Xsession" pid=722  comm="apparmor_parser"
Jan  9 13:16:28 Amilo-M7405 kernel: [    24.035239] type=1400 audit(1294575388.115:11): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient3" pid=732  comm="apparmor_parser"
Jan  9 13:16:28 Amilo-M7405 kernel: [    24.035353] type=1400 audit(1294575388.115:12): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=732  comm="apparmor_parser"
Jan  9 13:16:28 Amilo-M7405 kernel: [    24.035449] type=1400 audit(1294575388.115:13): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=732  comm="apparmor_parser"
Jan  9 13:16:28 Amilo-M7405 kernel: [   24.303836] eth0: link down
Jan  9 13:16:28 Amilo-M7405 kernel: [   24.304516] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  9 13:16:30 Amilo-M7405 kernel: [   26.058750] padlock: VIA PadLock not detected.
Jan  9 13:16:30 Amilo-M7405 kernel: [   26.528174] padlock: VIA PadLock Hash Engine not detected.
Jan  9 13:16:30 Amilo-M7405 kernel: [   26.668537] lib80211_crypt: registered algorithm 'CCMP'
Jan   9 13:16:31 Amilo-M7405 kernel: [   27.848360] Adding 93180k swap on  /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:93180k 
Jan  9  13:16:36 Amilo-M7405 kernel: [   32.878171] type=1400  audit(1294575396.959:14): apparmor="STATUS" operation="profile_load"  name="/usr/bin/evince" pid=738 comm="apparmor_parser"
Jan  9 13:16:36  Amilo-M7405 kernel: [   32.879489] type=1400 audit(1294575396.959:15):  apparmor="STATUS" operation="profile_load"  name="/usr/bin/evince-previewer" pid=738 comm="apparmor_parser"
Jan  9  13:16:36 Amilo-M7405 kernel: [   32.881040] type=1400  audit(1294575396.963:16): apparmor="STATUS" operation="profile_load"  name="/usr/bin/evince-thumbnailer" pid=738 comm="apparmor_parser"
Jan   9 13:16:37 Amilo-M7405 kernel: [   33.355274] type=1400  audit(1294575397.435:17): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/cups/backend/cups-pdf" pid=1007 comm="apparmor_parser"
Jan   9 13:16:37 Amilo-M7405 kernel: [   33.355571] type=1400  audit(1294575397.435:18): apparmor="STATUS" operation="profile_replace"  name="/usr/sbin/cupsd" pid=1007 comm="apparmor_parser"
Jan  9  13:16:37 Amilo-M7405 kernel: [   33.533160] type=1400  audit(1294575397.615:19): apparmor="STATUS" operation="profile_load"  name="/usr/sbin/tcpdump" pid=1008 comm="apparmor_parser"
Jan  9 13:16:38 Amilo-M7405 kernel: [   34.448021] eth1: no IPv6 routers present
Jan  9 13:16:43 Amilo-M7405 kernel: [   39.134148] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[/PHP][COLOR=Red]**lpr.log**[/COLOR][PHP]Jan  9 01:20:49 Amilo-M7405 udev-configure-printer: add /module/lp
Jan  9 01:20:49 Amilo-M7405 udev-configure-printer: Failed to get parent
Jan  9 13:16:23 Amilo-M7405 udev-configure-printer: add /module/lp
Jan  9 13:16:23 Amilo-M7405 udev-configure-printer: Failed to get parent
[/PHP][COLOR=Red]**mail.err/info/log/warn**[/COLOR][PHP]empty[/PHP]**[COLOR=Red]messages[/COLOR]**[PHP]Jan  9 12:18:05 Amilo-M7405 pulseaudio[1381]: ratelimit.c: 1 events suppressed
Jan  9 12:20:01 Amilo-M7405 kernel: [ 6649.301918] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan  9 13:16:23 Amilo-M7405 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jan   9 13:16:23 Amilo-M7405 rsyslogd: [origin software="rsyslogd"  swVersion="4.2.0" x-pid="531" x-info="http://www.rsyslog.com"] (re)start
Jan  9 13:16:23 Amilo-M7405 rsyslogd: rsyslogd's groupid changed to 103
Jan  9 13:16:23 Amilo-M7405 rsyslogd: rsyslogd's userid changed to 101
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Initializing cgroup subsys cpu
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.000000] Linux version  2.6.37-020637-generic (root@zinc) (gcc version 4.2.3 (Ubuntu  4.2.3-2ubuntu7)) #201101050908 SMP Wed Jan 5 10:17:13 UTC 2011
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] BIOS-provided physical RAM map:
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003efd0000 (usable)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 000000003efd0000 - 000000003efdf000 (ACPI data)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 000000003efdf000 - 000000003f000000 (ACPI NVS)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Notice: NX (Execute Disable) protection missing in CPU or disabled in BIOS!
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] DMI 2.3 present.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] last_pfn = 0x3efd0 max_arch_pfn = 0x100000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PAT not supported by CPU.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] RAMDISK: 2e412000 - 2f41c000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: RSDP 000f6790 00014 (v00 ACPIAM)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: RSDT 3efd0000 00034 (v01 A M I  OEMRSDT  01000525 MSFT 00000097)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: FACP 3efd0200 00081 (v02 A M I  OEMFACP  01000525 MSFT 00000097)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: DSDT 3efd03f0 03714 (v01 UW     F07_____ 00000001 INTL 02002026)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: FACS 3efdf000 00040
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: APIC 3efd0390 00054 (v01 A M I  OEMAPIC  01000525 MSFT 00000097)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: OEMB 3efdf040 00040 (v01 A M I  AMI_OEM  01000525 MSFT 00000097)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: SSDT 3efd3b10 00394 (v01    AMI   CPU1PM 00000001 INTL 02002026)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] 119MB HIGHMEM available.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] 887MB LOWMEM available.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   low ram: 0 - 377fe000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Zone PFN ranges:
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003efd0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Movable zone start PFN for each node
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] early_node_map[2] active PFN ranges
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     0: 0x00000100 -> 0x0003efd0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Using APIC driver default
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Allocating PCI resources starting at 3f000000 (gap: 3f000000:c1000000)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PERCPU: Embedded 12 pages/cpu @f6c00000 s28544 r0 d20608 u4194304
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 255871
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637-generic  root=UUID=53f4ad58-f05f-4972-b816-4105751cba54 ro quiet splash
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Initializing CPU#0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] allocated 5159680 bytes of page_cgroup
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003efd0)
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.000000] Memory: 991900k/1032000k  available (5128k kernel code, 39648k reserved, 2467k data, 740k init,  122696k highmem)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] virtual kernel memory layout:
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]       .init : 0xc086c000 - 0xc0925000   ( 740 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]       .data : 0xc060234f - 0xc086b108   (2467 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]       .text : 0xc0100000 - 0xc060234f   (5128 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Hierarchical RCU implementation.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256 16
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Console: colour VGA+ 80x25
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] console [tty0] enabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Fast TSC calibration using PIT
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Detected 1400.005 MHz processor.
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.004006] Calibrating delay loop  (skipped), value calculated using timer frequency.. 2800.01 BogoMIPS  (lpj=5600020)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.004013] pid_max: default: 32768 minimum: 301
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.004046] Security Framework initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.004069] AppArmor: AppArmor initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.004151] Mount-cache hash table entries: 512
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008127] Initializing cgroup subsys ns
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.008133] ns_cgroup deprecated:  consider using the 'clone_children' flag without the ns_cgroup.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008138] Initializing cgroup subsys cpuacct
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008145] Initializing cgroup subsys memory
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008162] Initializing cgroup subsys devices
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008165] Initializing cgroup subsys freezer
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008169] Initializing cgroup subsys net_cls
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008218] mce: CPU supports 5 MCE banks
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008232] CPU0: Thermal monitoring enabled (TM2)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008243] Performance Events: p6 PMU driver.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008254] ... version:                0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008257] ... bit width:              32
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008260] ... generic registers:      2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008263] ... value mask:             00000000ffffffff
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008267] ... max period:             000000007fffffff
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008270] ... fixed-purpose events:   0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008273] ... event mask:             0000000000000003
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.009452] SMP alternatives: switching to UP code
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.018985] Freeing SMP alternatives: 20k freed
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.018998] ACPI: Core revision 20101013
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.028014] ftrace: allocating 26658 entries in 53 pages
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.032093] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.032397] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.072731] CPU0: Intel(R) Pentium(R) M processor 1.40GHz stepping 06
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] Brought up 1 CPUs
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] Total of 1 processors activated (2800.01 BogoMIPS).
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] devtmpfs: initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] regulator: core version 0.5
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] regulator: dummy: 
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] Time: 12:16:04  Date: 01/09/11
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] NET: Registered protocol family 16
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] EISA bus registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] ACPI: bus type pci registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] PCI: Using configuration type 1 for base access
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.077452] bio: create slab <bio-0> at 0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.079932] ACPI: Executed 2 blocks of module-level executable AML code
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.084045] ACPI: Interpreter enabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.084054] ACPI: (supports S0 S3 S4 S5)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.084087] ACPI: Using IOAPIC for interrupt routing
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.092517] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.092695] ACPI: No dock devices found.
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.092702] PCI: Ignoring host bridge  windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.092803] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093876] pci 0000:00:1f.0: quirk: [io  0x0400-0x047f] claimed by ICH4 ACPI/GPIO/TCO
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093882] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH4 GPIO
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094892] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.094963] pci_bus 0000:02: [bus  02-05] partially hidden behind transparent bridge 0000:01 [bus 01-01]
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.094995] pci_bus 0000:06: [bus  06-09] partially hidden behind transparent bridge 0000:01 [bus 01-01]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.176970] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177091] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177207] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177322] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.177438] ACPI: PCI Interrupt Link  [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jan  9  13:16:23 Amilo-M7405 kernel: [    0.177555] ACPI: PCI Interrupt Link  [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jan  9  13:16:23 Amilo-M7405 kernel: [    0.177673] ACPI: PCI Interrupt Link  [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177791] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177851] HEST: Table is not found!
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177956] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177971] vgaarb: loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178296] SCSI subsystem initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178440] usbcore: registered new interface driver usbfs
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178460] usbcore: registered new interface driver hub
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178499] usbcore: registered new device driver usb
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178729] wmi: Mapper loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178732] PCI: Using ACPI for IRQ routing
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180009] NetLabel: Initializing
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180012] NetLabel:  domain hash size = 128
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180015] NetLabel:  protocols = UNLABELED CIPSOv4
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180034] NetLabel:  unlabeled traffic allowed by default
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180102] Switching to clocksource tsc
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191597] AppArmor: AppArmor Filesystem Enabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191630] pnp: PnP ACPI init
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191685] ACPI: bus type pnp registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194424] pnp: PnP ACPI: found 10 devices
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194428] ACPI: ACPI bus type pnp unregistered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194434] PnPBIOS: Disabled by ACPI PNP
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194457] system 00:07: [io  0x04d0-0x04d1] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194462] system 00:07: [io  0x0400-0x047f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194467] system 00:07: [io  0x0500-0x053f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194475] system 00:08: [io  0x1100-0x113f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194480] system 00:08: [io  0x1254] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194484] system 00:08: [io  0x12d4] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194489] system 00:08: [io  0x1300-0x1375] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194493] system 00:08: [io  0x1377-0x137f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194498] system 00:08: [io  0x0200-0x020f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194503] system 00:08: [io  0x0860-0x086f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194509] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194514] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194519] system 00:08: [mem 0xfec10000-0xfec1ffff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194524] system 00:08: [mem 0xffe80000-0xffefffff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194529] system 00:08: [mem 0xfff80000-0xffffffff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194534] system 00:08: [mem 0xfee00400-0xffbfffff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194539] system 00:08: [mem 0xfff00000-0xfff7ffff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194548] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194553] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194558] system 00:09: [mem 0x00100000-0x3effffff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232089] pci 0000:00:1e.0: BAR 15: assigned [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232097] pci 0000:00:1f.1: BAR 5: assigned [mem 0x48000000-0x480003ff]
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.232106] pci 0000:00:1f.1: BAR 5:  set to [mem 0x48000000-0x480003ff] (PCI address [0x48000000-0x480003ff])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232114] pci 0000:01:03.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232123] pci 0000:01:03.0: BAR 16: assigned [mem 0x4c000000-0x4fffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232128] pci 0000:01:03.1: BAR 15: assigned [mem 0x44000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232136] pci 0000:01:03.1: BAR 16: assigned [mem 0x50000000-0x53ffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232140] pci 0000:01:03.0: BAR 0: assigned [mem 0xe0000000-0xe0000fff]
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.232147] pci 0000:01:03.0: BAR 0:  set to [mem 0xe0000000-0xe0000fff] (PCI address [0xe0000000-0xe0000fff])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232153] pci 0000:01:03.1: BAR 0: assigned [mem 0xe0001000-0xe0001fff]
Jan   9 13:16:23 Amilo-M7405 kernel: [    0.232160] pci 0000:01:03.1: BAR 0:  set to [mem 0xe0001000-0xe0001fff] (PCI address [0xe0001000-0xe0001fff])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232165] pci 0000:01:03.0: BAR 13: assigned [io  0xc000-0xc0ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232170] pci 0000:01:03.0: BAR 14: assigned [io  0xc400-0xc4ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232174] pci 0000:01:03.1: BAR 13: assigned [io  0xcc00-0xccff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232180] pci 0000:01:03.1: BAR 14: assigned [io  0x1000-0x10ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232185] pci 0000:01:03.0: CardBus bridge to [bus 02-05]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232189] pci 0000:01:03.0:   bridge window [io  0xc000-0xc0ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232195] pci 0000:01:03.0:   bridge window [io  0xc400-0xc4ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232201] pci 0000:01:03.0:   bridge window [mem 0x40000000-0x43ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232207] pci 0000:01:03.0:   bridge window [mem 0x4c000000-0x4fffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232213] pci 0000:01:03.1: CardBus bridge to [bus 06-09]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232217] pci 0000:01:03.1:   bridge window [io  0xcc00-0xccff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232223] pci 0000:01:03.1:   bridge window [io  0x1000-0x10ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232229] pci 0000:01:03.1:   bridge window [mem 0x44000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232235] pci 0000:01:03.1:   bridge window [mem 0x50000000-0x53ffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232241] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232247] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232254] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xe00fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232260] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232300] pci 0000:01:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232309] pci 0000:01:03.1: enabling device (0000 -> 0003)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232315] pci 0000:01:03.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232442] NET: Registered protocol family 2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232552] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232937] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.234419] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235330] TCP: Hash tables configured (established 131072 bind 65536)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235335] TCP reno registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235343] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235377] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235579] NET: Registered protocol family 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235839] Trying to unpack rootfs image as initramfs...
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.958669] Freeing initrd memory: 16424k freed
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.975881] cpufreq-nforce2: No nForce2 chipset.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.975944] Scanning for low memory corruption every 60 seconds
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.976297] audit: initializing netlink socket (disabled)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.976318] type=2000 audit(1294575363.972:1): initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.993288] highmem bounce pool size: 64 pages
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.993297] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.996341] VFS: Disk quotas dquot_6.5.2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.996435] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.997545] fuse init (API version 7.15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.997704] msgmni has been set to 1729
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998071] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998076] io scheduler noop registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998079] io scheduler deadline registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998103] io scheduler cfq registered (default)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998333] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998371] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.008913] ACPI: AC Adapter [AC0] (on-line)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009030] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009067] ACPI: Lid Switch [LID]
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009150] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009157] ACPI: Sleep Button [SLPB]
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009237] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009242] ACPI: Power Button [PWRB]
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009318] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009324] ACPI: Power Button [PWRF]
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009549] Marking TSC unstable due to TSC halts in idle
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.010416] Switching to clocksource acpi_pm
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.011488] thermal LNXTHERM:00: registered as thermal_zone0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.011492] ACPI: Thermal Zone [THRM] (11 C)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.011551] ERST: Table is not found!
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.011579] isapnp: Scanning for PnP cards...
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.365551] isapnp: No Plug & Play device found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.365766] Linux agpgart interface v0.103
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.365877] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
Jan   9 13:16:23 Amilo-M7405 kernel: [    1.365903] agpgart-intel  0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.366726] agpgart-intel 0000:00:00.0: detected 16384K stolen memory
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.368534] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.368616] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.370419] serial 0000:00:1f.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.370428] serial 0000:00:1f.6: PCI INT B disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.372480] brd: module loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.373428] loop: module loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.373731] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.373749] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.374333] scsi0 : ata_piix
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.374466] scsi1 : ata_piix
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.377403] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.377408] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378013] Fixed MDIO Bus: probed
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378066] PPP generic driver version 2.4.2
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378131] tun: Universal TUN/TAP device driver, 1.6
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378134] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378259] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378283] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378307] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378366] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378405] ehci_hcd 0000:00:1d.7: debug port 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.382548] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe02ffc00
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396208] hub 1-0:1.0: USB hub found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396216] hub 1-0:1.0: 6 ports detected
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396336] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396358] uhci_hcd: USB Universal Host Controller Interface driver
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396396] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396409] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396485] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396525] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e480
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396721] hub 2-0:1.0: USB hub found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396728] hub 2-0:1.0: 2 ports detected
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396825] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396838] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396894] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396930] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e800
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397129] hub 3-0:1.0: USB hub found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397135] hub 3-0:1.0: 2 ports detected
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397239] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397252] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397306] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397342] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e880
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397555] hub 4-0:1.0: USB hub found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397562] hub 4-0:1.0: 2 ports detected
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397748] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.403859] i8042.c: Detected active multiplexing controller, rev 1.0.
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.404748] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.404757] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.404919] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.404963] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.405006] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.405183] mice: PS/2 mouse device common for all mice
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.405936] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.405960] rtc0: alarms up to one month, 114 bytes nvram
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406142] device-mapper: uevent: version 1.0.3
Jan   9 13:16:23 Amilo-M7405 kernel: [    1.406453] device-mapper: ioctl:  4.18.0-ioctl (2010-06-29) initialised: dm-devel@redhat.com
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406708] device-mapper: multipath: version 1.1.1 loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406713] device-mapper: multipath round-robin: version 1.0.0 loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406933] EISA: Probing bus 0 at eisa.0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406941] Cannot allocate resource for EISA slot 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406973] EISA: Detected 0 cards.
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.407168] cpuidle: using governor ladder
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.407253] cpuidle: using governor menu
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.407696] TCP cubic registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.407918] NET: Registered protocol family 10
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.408486] lo: Disabled Privacy Extensions
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.408860] NET: Registered protocol family 17
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.408882] Registering the dns_resolver key type
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.409530] Using IPI No-Shortcut mode
Jan   9 13:16:23 Amilo-M7405 kernel: [    1.410010] input: AT Translated Set 2  keyboard as /devices/platform/i8042/serio0/input/input4
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.412174] registered taskstats version 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414807]   Magic number: 11:634:278
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414837] tty tty15: hash matches
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414893] rtc_cmos 00:02: setting system clock to 2011-01-09 12:16:05 UTC (1294575365)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414898] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414901] EDD information not available.
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.417686] ACPI: Battery Slot [BAT0] (battery present)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.544539] ata1.00: ATA-7: FUJITSU MHV2080AH, 000000A0, max UDMA/100
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.544544] ata1.00: 156301488 sectors, multi 16: LBA 
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.560414] ata2.00: ATAPI: _NEC DVD+/-RW ND-6500A, 2.40, max UDMA/33
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.560646] ata1.00: configured for UDMA/100
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.560811] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080A 0000 PQ: 0 ANSI: 5
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.561049] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.561165] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.561251] sd 0:0:0:0: [sda] Write Protect is off
Jan   9 13:16:23 Amilo-M7405 kernel: [    1.561292] sd 0:0:0:0: [sda] Write  cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.608173] ata2.00: configured for UDMA/33
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.614393]  sda: sda1 sda2 < sda5 >
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.614769] sd 0:0:0:0: [sda] Attached SCSI disk
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.695361] scsi 1:0:0:0: CD-ROM            _NEC     DVD+-RW ND-6500A 2.40 PQ: 0 ANSI: 5
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817448] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817453] cdrom: Uniform CD-ROM driver Revision: 3.20
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817684] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817756] Freeing unused kernel memory: 740k freed
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.818262] Write protecting the kernel text: 5132k
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.818328] Write protecting the kernel read-only data: 2104k
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.842298] udev[69]: starting version 163
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.083270] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jan   9 13:16:23 Amilo-M7405 kernel: [    2.083310] 8139cp 0000:01:0c.0: This  (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Jan   9 13:16:23 Amilo-M7405 kernel: [    2.094492] input: Video Bus as  /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input5
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.094580] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.124099] 8139too: 8139too Fast Ethernet driver 0.9.28
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.124158] 8139too 0000:01:0c.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jan   9 13:16:23 Amilo-M7405 kernel: [    2.125469] 8139too 0000:01:0c.0:  eth0: RealTek RTL8139 at 0xc800, 00:03:0d:1f:8e:81, IRQ 19
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.126295] firewire_ohci 0000:01:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan   9 13:16:23 Amilo-M7405 kernel: [    2.182033] firewire_ohci: Added  fw-ohci device 0000:01:0a.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks  0x2
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.211224] [drm] Initialized drm 1.1.0 20060810
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.268821] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan   9 13:16:23 Amilo-M7405 kernel: [    2.334212] vgaarb: device changed  decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.334787] [drm] initialized overlay support
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.680357] firewire_core: created device fw0: GUID 00030d4925503c19, S400
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.325532] Console: switching to colour frame buffer device 128x48
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.333805] fb0: inteldrmfb frame buffer device
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.333808] drm: registered panic notifier
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.334005] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.968935] Btrfs loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    9.342109] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Jan  9 13:16:23 Amilo-M7405 kernel: [    9.342117] EXT4-fs (sda1): write access will be enabled during recovery
Jan  9 13:16:23 Amilo-M7405 kernel: [   11.903055] EXT4-fs (sda1): orphan cleanup on readonly fs
Jan  9 13:16:23 Amilo-M7405 kernel: [   11.903198] EXT4-fs (sda1): 2 orphan inodes deleted
Jan  9 13:16:23 Amilo-M7405 kernel: [   11.903202] EXT4-fs (sda1): recovery complete
Jan  9 13:16:23 Amilo-M7405 kernel: [   12.176272] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan  9 13:16:23 Amilo-M7405 kernel: [   15.217653] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jan  9 13:16:23 Amilo-M7405 kernel: [   15.319546] udev[304]: starting version 163
Jan  9 13:16:23 Amilo-M7405 kernel: [   16.886266] intel_rng: FWH not detected
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.042969] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.083808] lib80211: common routines for IEEE802.11 drivers
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.120294] cfg80211: Calling CRDA to update world regulatory domain
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.409575] libipw: 802.11 data/management/control stack, git-1.1.13
Jan   9 13:16:23 Amilo-M7405 kernel: [   17.409581] libipw: Copyright (C)  2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.476390] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.476397] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.476555] ipw2200 0000:01:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.480029] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.878686] lp: driver loaded but no devices found
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.975508] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
Jan   9 13:16:23 Amilo-M7405 kernel: [   18.037103] type=1400  audit(1294575382.119:2): apparmor="STATUS" operation="profile_load"  name="/sbin/dhclient3" pid=445 comm="apparmor_parser"
Jan  9 13:16:23  Amilo-M7405 kernel: [   18.037213] type=1400 audit(1294575382.119:3):  apparmor="STATUS" operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=445  comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [    18.037302] type=1400 audit(1294575382.119:4): apparmor="STATUS"  operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script"  pid=445 comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.134196] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x6eb1, caps: 0xa04711/0x40a/0x0
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.173741] yenta_cardbus 0000:01:03.0: CardBus bridge found [1734:106a]
Jan   9 13:16:23 Amilo-M7405 kernel: [   18.173771] yenta_cardbus  0000:01:03.0: O2: enabling read prefetch/write burst. If you experience  problems or performance issues, use the yenta_socket parameter  'o2_speedup=off'
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.185009]  input: SynPS/2 Synaptics TouchPad as  /devices/platform/i8042/serio2/input/input6
Jan  9 13:16:23  Amilo-M7405 kernel: [   18.254552] type=1400 audit(1294575382.335:5):  apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3"  pid=529 comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel:  [   18.254663] type=1400 audit(1294575382.335:6): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=529  comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [    18.254754] type=1400 audit(1294575382.335:7): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=529  comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.300919] yenta_cardbus 0000:01:03.0: ISA IRQ mask 0x0cb8, PCI irq 17
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.300926] yenta_cardbus 0000:01:03.0: Socket status: 30000006
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.300933] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #01 to #05
Jan   9 13:16:23 Amilo-M7405 kernel: [   18.300948] yenta_cardbus  0000:01:03.0: pcmcia: parent PCI bridge window: [io  0xc000-0xcfff]
Jan   9 13:16:23 Amilo-M7405 kernel: [   18.300954] pcmcia_socket  pcmcia_socket0: cs: IO port probe 0xc000-0xcfff: excluding 0xc000-0xc0ff  0xc400-0xc4ff 0xc800-0xc8ff 0xcc00-0xccff
Jan  9 13:16:23  Amilo-M7405 kernel: [   18.306023] yenta_cardbus 0000:01:03.0: pcmcia:  parent PCI bridge window: [mem 0xe0000000-0xe00fffff]
Jan  9 13:16:23  Amilo-M7405 kernel: [   18.306029] pcmcia_socket pcmcia_socket0: cs:  memory probe 0xe0000000-0xe00fffff: excluding 0xe0000000-0xe000ffff  0xe00f0000-0xe00fffff
Jan  9 13:16:23 Amilo-M7405 kernel: [    18.306050] yenta_cardbus 0000:01:03.0: pcmcia: parent PCI bridge window:  [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel:  [   18.306055] pcmcia_socket pcmcia_socket0: cs: memory probe  0x40000000-0x47ffffff: excluding 0x40000000-0x47ffffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.306860] yenta_cardbus 0000:01:03.1: CardBus bridge found [1734:106a]
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.432955] yenta_cardbus 0000:01:03.1: ISA IRQ mask 0x0cb8, PCI irq 17
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.432961] yenta_cardbus 0000:01:03.1: Socket status: 30000006
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.432967] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #05 to #09
Jan   9 13:16:23 Amilo-M7405 kernel: [   18.432979] yenta_cardbus  0000:01:03.1: pcmcia: parent PCI bridge window: [io  0xc000-0xcfff]
Jan   9 13:16:23 Amilo-M7405 kernel: [   18.432985] pcmcia_socket  pcmcia_socket1: cs: IO port probe 0xc000-0xcfff: excluding 0xc000-0xc0ff  0xc400-0xc4ff 0xc800-0xc8ff 0xcc00-0xccff
Jan  9 13:16:23  Amilo-M7405 kernel: [   18.438007] yenta_cardbus 0000:01:03.1: pcmcia:  parent PCI bridge window: [mem 0xe0000000-0xe00fffff]
Jan  9 13:16:23  Amilo-M7405 kernel: [   18.438013] pcmcia_socket pcmcia_socket1: cs:  memory probe 0xe0000000-0xe00fffff: excluding 0xe0000000-0xe000ffff  0xe00f0000-0xe00fffff
Jan  9 13:16:23 Amilo-M7405 kernel: [    18.438034] yenta_cardbus 0000:01:03.1: pcmcia: parent PCI bridge window:  [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel:  [   18.438039] pcmcia_socket pcmcia_socket1: cs: memory probe  0x40000000-0x47ffffff: excluding 0x40000000-0x47ffffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410465] cfg80211: World regulatory domain updated:
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410473]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410477]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410482]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410486]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410491]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410495]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan   9 13:16:23 Amilo-M7405 kernel: [   19.705098] pcmcia_socket  pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177  0x1f0-0x1f7 0x200-0x20f 0x370-0x377
Jan  9 13:16:23 Amilo-M7405  kernel: [   19.706775] pcmcia_socket pcmcia_socket1: cs: IO port probe  0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x400-0x47f 0x4d0-0x4d7
Jan  9  13:16:23 Amilo-M7405 kernel: [   19.707220] pcmcia_socket  pcmcia_socket1: cs: IO port probe 0x820-0x8ff: excluding 0x860-0x86f
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.707804] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7:
Jan   9 13:16:23 Amilo-M7405 kernel: [   19.708189] pcmcia_socket  pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177  0x1f0-0x1f7 0x200-0x20f 0x370-0x377
Jan  9 13:16:23 Amilo-M7405  kernel: [   19.709847] pcmcia_socket pcmcia_socket0: cs: IO port probe  0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x400-0x47f 0x4d0-0x4d7
Jan  9  13:16:23 Amilo-M7405 kernel: [   19.710288] pcmcia_socket  pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding 0x860-0x86f
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.710871] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Jan   9 13:16:23 Amilo-M7405 kernel: [   19.711551] pcmcia_socket  pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding  0xc0000-0xc7fff 0xcc000-0xcffff 0xe0000-0xfffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.711636] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.711719] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.711807] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Jan   9 13:16:23 Amilo-M7405 kernel: [   19.712822] pcmcia_socket  pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding  0xc0000-0xc7fff 0xcc000-0xcffff 0xe0000-0xfffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.712907] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.712990] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.713080] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.714581]  clean.
Jan  9 13:16:24 Amilo-M7405 kernel: [   20.861717] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jan  9 13:16:25 Amilo-M7405 kernel: [   21.688035] intel8x0_measure_ac97_clock: measured 55422 usecs (2671 samples)
Jan  9 13:16:25 Amilo-M7405 kernel: [   21.688041] intel8x0: clocking to 48000
Jan   9 13:16:26 Amilo-M7405 kernel: [   22.811478] type=1400  audit(1294575386.891:8): apparmor="STATUS" operation="profile_load"  name="/usr/lib/cups/backend/cups-pdf" pid=660 comm="apparmor_parser"
Jan   9 13:16:26 Amilo-M7405 kernel: [   22.811756] type=1400  audit(1294575386.891:9): apparmor="STATUS" operation="profile_load"  name="/usr/sbin/cupsd" pid=660 comm="apparmor_parser"
Jan  9 13:16:27 Amilo-M7405 kernel: [   23.596222] ppdev: user-space parallel port driver
Jan   9 13:16:27 Amilo-M7405 kernel: [   23.771974] type=1400  audit(1294575387.851:10): apparmor="STATUS" operation="profile_load"  name="/usr/share/gdm/guest-session/Xsession" pid=722  comm="apparmor_parser"
Jan  9 13:16:28 Amilo-M7405 kernel: [    24.035239] type=1400 audit(1294575388.115:11): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient3" pid=732  comm="apparmor_parser"
Jan  9 13:16:28 Amilo-M7405 kernel: [    24.035353] type=1400 audit(1294575388.115:12): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=732  comm="apparmor_parser"
Jan  9 13:16:28 Amilo-M7405 kernel: [    24.035449] type=1400 audit(1294575388.115:13): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=732  comm="apparmor_parser"
Jan  9 13:16:28 Amilo-M7405 kernel: [   24.303836] eth0: link down
Jan  9 13:16:28 Amilo-M7405 kernel: [   24.304516] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  9 13:16:30 Amilo-M7405 kernel: [   26.058750] padlock: VIA PadLock not detected.
Jan  9 13:16:30 Amilo-M7405 kernel: [   26.528174] padlock: VIA PadLock Hash Engine not detected.
Jan   9 13:16:31 Amilo-M7405 kernel: [   27.848360] Adding 93180k swap on  /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:93180k 
Jan  9  13:16:36 Amilo-M7405 kernel: [   32.878171] type=1400  audit(1294575396.959:14): apparmor="STATUS" operation="profile_load"  name="/usr/bin/evince" pid=738 comm="apparmor_parser"
Jan  9 13:16:36  Amilo-M7405 kernel: [   32.879489] type=1400 audit(1294575396.959:15):  apparmor="STATUS" operation="profile_load"  name="/usr/bin/evince-previewer" pid=738 comm="apparmor_parser"
Jan  9  13:16:36 Amilo-M7405 kernel: [   32.881040] type=1400  audit(1294575396.963:16): apparmor="STATUS" operation="profile_load"  name="/usr/bin/evince-thumbnailer" pid=738 comm="apparmor_parser"
Jan   9 13:16:37 Amilo-M7405 kernel: [   33.355274] type=1400  audit(1294575397.435:17): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/cups/backend/cups-pdf" pid=1007 comm="apparmor_parser"
Jan   9 13:16:37 Amilo-M7405 kernel: [   33.355571] type=1400  audit(1294575397.435:18): apparmor="STATUS" operation="profile_replace"  name="/usr/sbin/cupsd" pid=1007 comm="apparmor_parser"
Jan  9  13:16:37 Amilo-M7405 kernel: [   33.533160] type=1400  audit(1294575397.615:19): apparmor="STATUS" operation="profile_load"  name="/usr/sbin/tcpdump" pid=1008 comm="apparmor_parser"
Jan  9 13:16:43 Amilo-M7405 kernel: [   39.134148] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan  9 13:18:52 Amilo-M7405 pulseaudio[1390]: ratelimit.c: 2 events suppressed
Jan  9 13:20:29 Amilo-M7405 pulseaudio[1390]: ratelimit.c: 1 events suppressed
Jan  9 13:20:55 Amilo-M7405 sudo: pam_sm_authenticate: Called
Jan  9 13:20:55 Amilo-M7405 sudo: pam_sm_authenticate: username = [fab]
Jan  9 13:20:55 Amilo-M7405 sudo: pam_sm_authenticate: /home/fab is already mounted
[/PHP]

---

### Post by Byb on 2011-01-09
... and the tramps outside :popcorn::popcorn::popcorn::popcorn::popcorn: :popcorn:[B][COLOR=Red]

pm-suspend.log[/COLOR][/B][PHP]Initial commandline parameters: 
Sat Jan  1 18:46:53 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637rc7-generic #201012221342 SMP Wed Dec 22 14:58:33 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
iptable_nat             3624  0 
nf_nat                 15727  1 iptable_nat
nf_conntrack_ipv4      11168  3 iptable_nat,nf_nat
nf_conntrack           65711  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1319  1 nf_conntrack_ipv4
iptable_filter          1334  1 
ip_tables              11241  2 iptable_nat,iptable_filter
x_tables               15933  3 iptable_nat,iptable_filter,ip_tables
binfmt_misc             6586  1 
sha256_generic         12003  2 
aes_i586                7280  341 
aes_generic            26907  1 aes_i586
parport_pc             27846  0 
ppdev                   5245  0 
dm_crypt               11892  1 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75543  2 snd_intel8x0,snd_ac97_codec
pcmcia                 37586  0 
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
joydev                  9423  0 
yenta_socket           20749  0 
snd_timer              19824  2 snd_pcm,snd_seq
ipw2200               140899  0 
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_rsrc            10372  1 yenta_socket
libipw                 40474  1 ipw2200
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                58014  0 
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
cfg80211              144857  2 ipw2200,libipw
soundcore                880  1 snd
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
lib80211                5058  2 ipw2200,libipw
serio_raw               4062  0 
lp                      7400  0 
shpchp                 25357  0 
parport                32560  3 parport_pc,ppdev,lp
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  394586  3 
drm_kms_helper         31992  1 i915
drm                   176940  4 i915,drm_kms_helper
firewire_ohci          25399  0 
8139too                18785  0 
8139cp                 16763  0 
firewire_core          52533  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
i2c_algo_bit            4910  1 i915
video                  12975  1 i915
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009092     817060     192032          0     121868     453660
-/+ buffers/cache:     241532     767560
Swap:        93180          4      93176

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.308 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sat Jan  1 18:46:56 CET 2011: performing suspend
Initial commandline parameters: 
Tue Jan  4 12:45:58 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637rc8-generic #201012290905 SMP Wed Dec 29 10:16:26 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3293  0 
nls_cp437               4931  0 
vfat                    9344  0 
fat                    47609  1 vfat
usb_storage            40290  0 
uas                     7466  0 
rtl8150                 9089  0 
iptable_filter          1334  0 
ip_tables              11241  1 iptable_filter
x_tables               15933  2 iptable_filter,ip_tables
lib80211_crypt_ccmp     4573  2 
binfmt_misc             6586  1 
sha256_generic         12003  2 
aes_i586                7280  135 
aes_generic            26907  1 aes_i586
parport_pc             27846  0 
ppdev                   5245  0 
dm_crypt               11892  1 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75575  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4786  0 
joydev                  9423  0 
snd_rawmidi            17763  1 snd_seq_midi
ipw2200               140899  0 
snd_seq_midi_event      5919  1 snd_seq_midi
pcmcia                 37586  0 
libipw                 40474  1 ipw2200
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19824  2 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           20749  0 
pcmcia_rsrc            10372  1 yenta_socket
psmouse                58014  0 
cfg80211              144857  2 ipw2200,libipw
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
soundcore                880  1 snd
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw               4062  0 
shpchp                 25357  0 
lp                      7400  0 
parport                32560  3 parport_pc,ppdev,lp
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  394840  3 
drm_kms_helper         32024  1 i915
drm                   176940  4 i915,drm_kms_helper
8139too                18785  0 
firewire_ohci          25399  0 
firewire_core          52533  1 firewire_ohci
i2c_algo_bit            4910  1 i915
8139cp                 16763  0 
video                  12975  1 i915
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009084     783412     225672          0      42188     460648
-/+ buffers/cache:     280576     728508
Swap:        93180      14892      78288

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.2 -> dest=:1.87 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Tue Jan  4 12:46:04 CET 2011: performing suspend
Initial commandline parameters: 
Tue Jan  4 13:20:09 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637rc8-generic #201012290905 SMP Wed Dec 29 10:16:26 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6586  1 
sha256_generic         12003  2 
aes_i586                7280  369 
aes_generic            26907  1 aes_i586
parport_pc             27846  0 
ppdev                   5245  0 
dm_crypt               11892  1 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75575  2 snd_intel8x0,snd_ac97_codec
pcmcia                 37586  0 
snd_seq_midi            4786  0 
joydev                  9423  0 
ipw2200               140899  0 
yenta_socket           20749  0 
pcmcia_rsrc            10372  1 yenta_socket
snd_rawmidi            17763  1 snd_seq_midi
libipw                 40474  1 ipw2200
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_midi_event      5919  1 snd_seq_midi
cfg80211              144857  2 ipw2200,libipw
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19824  2 snd_pcm,snd_seq
lib80211                5058  2 ipw2200,libipw
psmouse                58014  0 
shpchp                 25357  0 
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               4062  0 
lp                      7400  0 
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
parport                32560  3 parport_pc,ppdev,lp
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  394840  3 
drm_kms_helper         32024  1 i915
drm                   176940  4 i915,drm_kms_helper
firewire_ohci          25399  0 
8139too                18785  0 
8139cp                 16763  0 
i2c_algo_bit            4910  1 i915
video                  12975  1 i915
firewire_core          52533  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009084     630556     378528          0     117440     285472
-/+ buffers/cache:     227644     781440
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.61 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Tue Jan  4 13:20:12 CET 2011: performing suspend
Initial commandline parameters: 
Wed Jan  5 22:48:11 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637rc8-generic #201012290905 SMP Wed Dec 29 10:16:26 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6586  1 
sha256_generic         12003  2 
lib80211_crypt_ccmp     4573  2 
aes_i586                7280  395 
aes_generic            26907  1 aes_i586
dm_crypt               11892  1 
parport_pc             27846  0 
ppdev                   5245  0 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75575  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
joydev                  9423  0 
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19824  2 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               140899  0 
pcmcia                 37586  0 
libipw                 40474  1 ipw2200
cfg80211              144857  2 ipw2200,libipw
psmouse                58014  0 
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
yenta_socket           20749  0 
pcmcia_rsrc            10372  1 yenta_socket
soundcore                880  1 snd
serio_raw               4062  0 
lp                      7400  0 
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
parport                32560  3 parport_pc,ppdev,lp
shpchp                 25357  0 
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  394840  3 
drm_kms_helper         32024  1 i915
drm                   176940  4 i915,drm_kms_helper
i2c_algo_bit            4910  1 i915
firewire_ohci          25399  0 
8139too                18785  0 
firewire_core          52533  1 firewire_ohci
8139cp                 16763  0 
video                  12975  1 i915
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009084     535432     473652          0      31712     337948
-/+ buffers/cache:     165772     843312
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.58 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Wed Jan  5 22:48:13 CET 2011: performing suspend
Initial commandline parameters: 
Fri Jan  7 09:13:08 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637-generic #201101050908 SMP Wed Jan 5 10:17:13 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6586  1 
sha256_generic         12003  2 
aes_i586                7280  146 
aes_generic            26907  1 aes_i586
lib80211_crypt_ccmp     4573  2 
parport_pc             27846  0 
dm_crypt               11892  1 
ppdev                   5245  0 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75575  2 snd_intel8x0,snd_ac97_codec
pcmcia                 37586  0 
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           20749  0 
pcmcia_rsrc            10372  1 yenta_socket
snd_timer              19824  2 snd_pcm,snd_seq
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
ipw2200               140899  0 
libipw                 40474  1 ipw2200
joydev                  9423  0 
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              144857  2 ipw2200,libipw
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
shpchp                 25357  0 
soundcore                880  1 snd
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
lp                      7400  0 
parport                32560  3 parport_pc,ppdev,lp
psmouse                58014  0 
serio_raw               4062  0 
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  395193  3 
drm_kms_helper         32024  1 i915
drm                   176940  4 i915,drm_kms_helper
firewire_ohci          25399  0 
8139too                18785  0 
8139cp                 16763  0 
i2c_algo_bit            4910  1 i915
firewire_core          52533  1 firewire_ohci
video                  12975  1 i915
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009084     957892      51192          0     162788     427988
-/+ buffers/cache:     367116     641968
Swap:        93180       2288      90892

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.2 -> dest=:1.130 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Fri Jan  7 09:13:13 CET 2011: performing suspend
Initial commandline parameters: 
Fri Jan  7 09:17:19 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637rc8-generic #201012290905 SMP Wed Dec 29 10:16:26 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6586  1 
sha256_generic         12003  2 
aes_i586                7280  4 
aes_generic            26907  1 aes_i586
lib80211_crypt_ccmp     4573  2 
parport_pc             27846  0 
ppdev                   5245  0 
dm_crypt               11892  1 
snd_intel8x0           26553  0 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75575  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19824  2 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                  9423  0 
snd                    49949  7 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia                 37586  0 
ipw2200               140899  0 
soundcore                880  1 snd
psmouse                58014  0 
yenta_socket           20749  0 
pcmcia_rsrc            10372  1 yenta_socket
libipw                 40474  1 ipw2200
serio_raw               4062  0 
cfg80211              144857  2 ipw2200,libipw
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
lp                      7400  0 
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
shpchp                 25357  0 
parport                32560  3 parport_pc,ppdev,lp
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  394840  2 
drm_kms_helper         32024  1 i915
drm                   176940  3 i915,drm_kms_helper
8139too                18785  0 
firewire_ohci          25399  0 
i2c_algo_bit            4910  1 i915
8139cp                 16763  0 
firewire_core          52533  1 firewire_ohci
video                  12975  1 i915
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009084     222148     786936          0      74076      93028
-/+ buffers/cache:      55044     954040
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.23 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Fri Jan  7 09:17:19 CET 2011: performing suspend
Initial commandline parameters: 
Fri Jan  7 10:02:51 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637rc8-generic #201012290905 SMP Wed Dec 29 10:16:26 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6586  1 
lib80211_crypt_ccmp     4573  2 
sha256_generic         12003  2 
aes_i586                7280  381 
aes_generic            26907  1 aes_i586
parport_pc             27846  0 
ppdev                   5245  0 
dm_crypt               11892  1 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75575  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
ipw2200               140899  0 
snd_timer              19824  2 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
libipw                 40474  1 ipw2200
joydev                  9423  0 
cfg80211              144857  2 ipw2200,libipw
pcmcia                 37586  0 
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
yenta_socket           20749  0 
pcmcia_rsrc            10372  1 yenta_socket
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
psmouse                58014  0 
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw               4062  0 
lp                      7400  0 
shpchp                 25357  0 
parport                32560  3 parport_pc,ppdev,lp
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  394840  3 
drm_kms_helper         32024  1 i915
drm                   176940  4 i915,drm_kms_helper
8139too                18785  0 
firewire_ohci          25399  0 
8139cp                 16763  0 
i2c_algo_bit            4910  1 i915
firewire_core          52533  1 firewire_ohci
video                  12975  1 i915
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009084     760144     248940          0      33872     437004
-/+ buffers/cache:     289268     719816
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.4 -> dest=:1.56 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Fri Jan  7 10:02:54 CET 2011: performing suspend
Initial commandline parameters: 
Fri Jan  7 22:24:24 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637-generic #201101050908 SMP Wed Jan 5 10:17:13 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6586  1 
sha256_generic         12003  2 
lib80211_crypt_ccmp     4573  2 
aes_i586                7280  4 
aes_generic            26907  1 aes_i586
parport_pc             27846  0 
dm_crypt               11892  1 
ppdev                   5245  0 
snd_intel8x0           26553  0 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75575  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4786  0 
pcmcia                 37586  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
ipw2200               140899  0 
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           20749  0 
joydev                  9423  0 
snd_timer              19824  2 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_rsrc            10372  1 yenta_socket
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
libipw                 40474  1 ipw2200
cfg80211              144857  2 ipw2200,libipw
snd                    49949  7 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
shpchp                 25357  0 
soundcore                880  1 snd
lp                      7400  0 
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
psmouse                58014  0 
serio_raw               4062  0 
parport                32560  3 parport_pc,ppdev,lp
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  395193  2 
drm_kms_helper         32024  1 i915
drm                   176940  3 i915,drm_kms_helper
8139too                18785  0 
firewire_ohci          25399  0 
firewire_core          52533  1 firewire_ohci
8139cp                 16763  0 
i2c_algo_bit            4910  1 i915
video                  12975  1 i915
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009084     166864     842220          0      19900      94480
-/+ buffers/cache:      52484     956600
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.22 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Fri Jan  7 22:24:25 CET 2011: performing suspend
Initial commandline parameters: 
Fri Jan  7 23:17:26 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637-generic #201101050908 SMP Wed Jan 5 10:17:13 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6586  1 
lib80211_crypt_ccmp     4573  2 
sha256_generic         12003  2 
aes_i586                7280  236 
aes_generic            26907  1 aes_i586
parport_pc             27846  0 
ppdev                   5245  0 
dm_crypt               11892  1 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75575  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 37586  0 
joydev                  9423  0 
snd_timer              19824  2 snd_pcm,snd_seq
ipw2200               140899  0 
libipw                 40474  1 ipw2200
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           20749  0 
pcmcia_rsrc            10372  1 yenta_socket
cfg80211              144857  2 ipw2200,libipw
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore                880  1 snd
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
psmouse                58014  0 
shpchp                 25357  0 
serio_raw               4062  0 
lp                      7400  0 
parport                32560  3 parport_pc,ppdev,lp
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  395193  3 
drm_kms_helper         32024  1 i915
drm                   176940  4 i915,drm_kms_helper
firewire_ohci          25399  0 
8139too                18785  0 
i2c_algo_bit            4910  1 i915
firewire_core          52533  1 firewire_ohci
8139cp                 16763  0 
video                  12975  1 i915
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009084     367204     641880          0      28976     185732
-/+ buffers/cache:     152496     856588
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.54 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Fri Jan  7 23:17:28 CET 2011: performing suspend
Initial commandline parameters: 
Fri Jan  7 23:36:02 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637-generic #201101050908 SMP Wed Jan 5 10:17:13 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6586  1 
lib80211_crypt_ccmp     4573  2 
sha256_generic         12003  2 
aes_i586                7280  376 
aes_generic            26907  1 aes_i586
parport_pc             27846  0 
dm_crypt               11892  1 
ppdev                   5245  0 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75575  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
ipw2200               140899  0 
snd_seq_midi_event      5919  1 snd_seq_midi
pcmcia                 37586  0 
libipw                 40474  1 ipw2200
yenta_socket           20749  0 
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
pcmcia_rsrc            10372  1 yenta_socket
snd_timer              19824  2 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                  9423  0 
lp                      7400  0 
cfg80211              144857  2 ipw2200,libipw
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 25357  0 
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
parport                32560  3 parport_pc,ppdev,lp
psmouse                58014  0 
serio_raw               4062  0 
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  395193  3 
drm_kms_helper         32024  1 i915
firewire_ohci          25399  0 
drm                   176940  4 i915,drm_kms_helper
8139too                18785  0 
firewire_core          52533  1 firewire_ohci
8139cp                 16763  0 
i2c_algo_bit            4910  1 i915
video                  12975  1 i915
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009084     624404     384680          0      32688     318064
-/+ buffers/cache:     273652     735432
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.59 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Fri Jan  7 23:36:06 CET 2011: performing suspend
Initial commandline parameters: 
Sat Jan  8 09:36:07 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637-generic #201101050908 SMP Wed Jan 5 10:17:13 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6586  1 
lib80211_crypt_ccmp     4573  2 
sha256_generic         12003  2 
aes_i586                7280  240 
aes_generic            26907  1 aes_i586
parport_pc             27846  0 
ppdev                   5245  0 
dm_crypt               11892  1 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75575  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
pcmcia                 37586  0 
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19824  2 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           20749  0 
pcmcia_rsrc            10372  1 yenta_socket
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ipw2200               140899  0 
joydev                  9423  0 
libipw                 40474  1 ipw2200
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore                880  1 snd
cfg80211              144857  2 ipw2200,libipw
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
shpchp                 25357  0 
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
psmouse                58014  0 
serio_raw               4062  0 
lp                      7400  0 
parport                32560  3 parport_pc,ppdev,lp
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  395193  3 
drm_kms_helper         32024  1 i915
drm                   176940  4 i915,drm_kms_helper
firewire_ohci          25399  0 
8139too                18785  0 
8139cp                 16763  0 
firewire_core          52533  1 firewire_ohci
i2c_algo_bit            4910  1 i915
video                  12975  1 i915
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009084     402888     606196          0      29224     217892
-/+ buffers/cache:     155772     853312
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.55 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module xhci...Done.

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sat Jan  8 09:36:09 CET 2011: performing suspend
Initial commandline parameters: 
Sat Jan  8 10:47:16 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637-generic #201101050908 SMP Wed Jan 5 10:17:13 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6586  1 
sha256_generic         12003  2 
lib80211_crypt_ccmp     4573  2 
aes_i586                7280  391 
parport_pc             27846  0 
aes_generic            26907  1 aes_i586
ppdev                   5245  0 
dm_crypt               11892  1 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75575  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
joydev                  9423  0 
snd_timer              19824  2 snd_pcm,snd_seq
ipw2200               140899  0 
libipw                 40474  1 ipw2200
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 37586  0 
cfg80211              144857  2 ipw2200,libipw
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
soundcore                880  1 snd
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
yenta_socket           20749  0 
pcmcia_rsrc            10372  1 yenta_socket
psmouse                58014  0 
serio_raw               4062  0 
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 25357  0 
lp                      7400  0 
parport                32560  3 parport_pc,ppdev,lp
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  395193  3 
drm_kms_helper         32024  1 i915
drm                   176940  4 i915,drm_kms_helper
firewire_ohci          25399  0 
8139too                18785  0 
firewire_core          52533  1 firewire_ohci
i2c_algo_bit            4910  1 i915
8139cp                 16763  0 
video                  12975  1 i915
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009084     684464     324620          0      34668     379856
-/+ buffers/cache:     269940     739144
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.59 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sat Jan  8 10:47:19 CET 2011: performing suspend
Initial commandline parameters: 
Sun Jan  9 12:20:01 CET 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637-generic #201101050908 SMP Wed Jan 5 10:17:13 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6586  1 
lib80211_crypt_ccmp     4573  2 
sha256_generic         12003  2 
aes_i586                7280  551 
aes_generic            26907  1 aes_i586
parport_pc             27846  0 
ppdev                   5245  0 
dm_crypt               11892  1 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75575  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
ipw2200               140899  0 
pcmcia                 37586  0 
libipw                 40474  1 ipw2200
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           20749  0 
pcmcia_rsrc            10372  1 yenta_socket
joydev                  9423  0 
snd_timer              19824  2 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
cfg80211              144857  2 ipw2200,libipw
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
shpchp                 25357  0 
soundcore                880  1 snd
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
lp                      7400  0 
parport                32560  3 parport_pc,ppdev,lp
psmouse                58014  0 
serio_raw               4062  0 
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  395193  3 
drm_kms_helper         32024  1 i915
drm                   176940  4 i915,drm_kms_helper
firewire_ohci          25399  0 
8139too                18785  0 
i2c_algo_bit            4910  1 i915
firewire_core          52533  1 firewire_ohci
8139cp                 16763  0 
video                  12975  1 i915
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009084     605588     403496          0      37788     399124
-/+ buffers/cache:     168676     840408
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.57 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sun Jan  9 12:20:03 CET 2011: performing suspend
[/PHP]**[COLOR=Red]pm-suspend.log.1[/COLOR]**[PHP]Initial commandline parameters: 
Mon Dec 20 15:55:59 CET 2010: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-997-generic #201012190905 SMP Sun Dec 19 10:23:39 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
lib80211_crypt_ccmp     4573  2 
binfmt_misc             6586  1 
sha256_generic         12003  2 
aes_i586                7280  188 
aes_generic            26907  1 aes_i586
parport_pc             27846  0 
dm_crypt               11892  1 
ppdev                   5245  0 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75543  2 snd_intel8x0,snd_ac97_codec
joydev                  9423  0 
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
ipw2200               140899  0 
pcmcia                 37586  0 
snd_timer              19824  2 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
libipw                 40474  1 ipw2200
yenta_socket           20749  0 
cfg80211              144857  2 ipw2200,libipw
pcmcia_rsrc            10372  1 yenta_socket
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
soundcore                880  1 snd
psmouse                58014  0 
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
lp                      7400  0 
serio_raw               4062  0 
shpchp                 25357  0 
parport                32560  3 parport_pc,ppdev,lp
btrfs                 501909  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  513670  3 
drm_kms_helper         32088  1 i915
drm                   182490  4 i915,drm_kms_helper
8139too                18785  0 
firewire_ohci          25335  0 
i2c_algo_bit            4910  1 i915
8139cp                 16763  0 
firewire_core          52533  1 firewire_ohci
video                  12975  1 i915
crc_itu_t               1383  1 firewire_core
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009088     432620     576468          0      41244     227588
-/+ buffers/cache:     163788     845300
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.1 -> dest=:1.54 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Mon Dec 20 15:56:02 CET 2010: performing suspend
Initial commandline parameters: 
Thu Dec 23 13:28:46 CET 2010: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637rc7-generic #201012221342 SMP Wed Dec 22 14:58:33 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
lib80211_crypt_ccmp     4573  2 
binfmt_misc             6586  1 
sha256_generic         12003  2 
aes_i586                7280  602 
aes_generic            26907  1 aes_i586
parport_pc             27846  0 
dm_crypt               11892  1 
ppdev                   5245  0 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75543  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4786  0 
pcmcia                 37586  0 
snd_rawmidi            17763  1 snd_seq_midi
ipw2200               140899  0 
yenta_socket           20749  0 
snd_seq_midi_event      5919  1 snd_seq_midi
libipw                 40474  1 ipw2200
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
pcmcia_rsrc            10372  1 yenta_socket
cfg80211              144857  2 ipw2200,libipw
snd_timer              19824  2 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                  9423  0 
shpchp                 25357  0 
soundcore                880  1 snd
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
psmouse                58014  0 
serio_raw               4062  0 
lp                      7400  0 
parport                32560  3 parport_pc,ppdev,lp
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  394586  5 
drm_kms_helper         31992  1 i915
firewire_ohci          25399  0 
drm                   176940  6 i915,drm_kms_helper
8139too                18785  0 
firewire_core          52533  1 firewire_ohci
8139cp                 16763  0 
crc_itu_t               1383  1 firewire_core
i2c_algo_bit            4910  1 i915
video                  12975  1 i915
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009092     850960     158132          0      52748     512376
-/+ buffers/cache:     285836     723256
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.61 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Thu Dec 23 13:28:49 CET 2010: performing suspend
Initial commandline parameters: 
Fri Dec 24 19:58:10 CET 2010: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637rc7-generic #201012221342 SMP Wed Dec 22 14:58:33 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6586  1 
sha256_generic         12003  2 
aes_i586                7280  2 
aes_generic            26907  1 aes_i586
parport_pc             27846  0 
ppdev                   5245  0 
dm_crypt               11892  1 
snd_intel8x0           26553  0 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
ipw2200               140899  0 
snd_pcm                75543  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4786  0 
joydev                  9423  0 
libipw                 40474  1 ipw2200
snd_rawmidi            17763  1 snd_seq_midi
cfg80211              144857  2 ipw2200,libipw
pcmcia                 37586  0 
snd_seq_midi_event      5919  1 snd_seq_midi
yenta_socket           20749  0 
pcmcia_rsrc            10372  1 yenta_socket
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
lib80211                5058  2 ipw2200,libipw
snd_timer              19824  2 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
lp                      7400  0 
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                58014  0 
snd                    49949  7 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 25357  0 
parport                32560  3 parport_pc,ppdev,lp
soundcore                880  1 snd
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
serio_raw               4062  0 
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  394586  2 
drm_kms_helper         31992  1 i915
drm                   176940  3 i915,drm_kms_helper
firewire_ohci          25399  0 
8139too                18785  0 
firewire_core          52533  1 firewire_ohci
8139cp                 16763  0 
crc_itu_t               1383  1 firewire_core
i2c_algo_bit            4910  1 i915
video                  12975  1 i915
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009092     167620     841472          0      19080      94684
-/+ buffers/cache:      53856     955236
Swap:        93180          0      93180

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.20 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Fri Dec 24 19:58:10 CET 2010: performing suspend
Initial commandline parameters: 
Wed Dec 29 08:34:32 CET 2010: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Amilo-M7405 2.6.37-020637rc7-generic #201012221342 SMP Wed Dec 22 14:58:33 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3293  0 
nls_cp437               4931  0 
vfat                    9344  0 
fat                    47609  1 vfat
usb_storage            40290  0 
uas                     7466  0 
lib80211_crypt_ccmp     4573  2 
binfmt_misc             6586  1 
parport_pc             27846  0 
ppdev                   5245  0 
sha256_generic         12003  2 
aes_i586                7280  348 
aes_generic            26907  1 aes_i586
dm_crypt               11892  1 
snd_intel8x0           26553  2 
snd_ac97_codec         99881  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75543  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19824  2 snd_pcm,snd_seq
ipw2200               140899  0 
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49949  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
libipw                 40474  1 ipw2200
pcmcia                 37586  0 
soundcore                880  1 snd
cfg80211              144857  2 ipw2200,libipw
snd_page_alloc          7352  2 snd_intel8x0,snd_pcm
lib80211                5058  3 lib80211_crypt_ccmp,ipw2200,libipw
yenta_socket           20749  0 
pcmcia_rsrc            10372  1 yenta_socket
pcmcia_core            13897  3 pcmcia,yenta_socket,pcmcia_rsrc
joydev                  9423  0 
shpchp                 25357  0 
lp                      7400  0 
psmouse                58014  0 
parport                32560  3 parport_pc,ppdev,lp
serio_raw               4062  0 
btrfs                 502612  0 
zlib_deflate           19197  1 btrfs
libcrc32c                887  1 btrfs
i915                  394586  4 
drm_kms_helper         31992  1 i915
drm                   176940  5 i915,drm_kms_helper
8139too                18785  0 
firewire_ohci          25399  0 
8139cp                 16763  0 
firewire_core          52533  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
i2c_algo_bit            4910  1 i915
video                  12975  1 i915
output                  1851  1 video
             total       used       free     shared    buffers     cached
Mem:       1009092     919972      89120          0     123496     509320
-/+ buffers/cache:     287156     721936
Swap:        93180       2260      90920

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.119 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Wed Dec 29 08:34:35 CET 2010: performing suspend
[/PHP]**[COLOR=Red]pycentral.log[/COLOR]**[PHP]empty[/PHP]

---

### Post by Byb on 2011-01-09
[COLOR=Red][COLOR=Black]Pastries now ? :popcorn::popcorn::popcorn::popcorn::popcorn: :popcorn::popcorn: [/COLOR][B]
syslog[/B][/COLOR][PHP]Jan  9 12:17:01 Amilo-M7405 CRON[1763]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  9 12:18:05 Amilo-M7405 pulseaudio[1381]: ratelimit.c: 1 events suppressed
Jan  9 12:20:01 Amilo-M7405 anacron[1852]: Anacron 2.3 started on 2011-01-09
Jan  9 12:20:01 Amilo-M7405 anacron[1852]: Normal exit (0 jobs run)
Jan  9 12:20:01 Amilo-M7405 kernel: [ 6649.301918] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> sleep requested (sleeping: no  enabled: yes)
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> sleeping or disabling...
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth1): now unmanaged
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth1): device state change: 8 -> 1 (reason 37)
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth1): deactivating device (reason: 37).
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth1): canceled DHCP transaction, DHCP client pid 916
Jan  9 12:20:03 Amilo-M7405 avahi-daemon[733]: Withdrawing address record for 192.168.22.106 on eth1.
Jan  9 12:20:03 Amilo-M7405 avahi-daemon[733]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.22.106.
Jan  9 12:20:03 Amilo-M7405 avahi-daemon[733]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth1): cleaning up...
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth1): taking down device.
Jan  9 12:20:03 Amilo-M7405 wpa_supplicant[854]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  9 12:20:03 Amilo-M7405 avahi-daemon[733]: Interface eth1.IPv6 no longer relevant for mDNS.
Jan  9 12:20:03 Amilo-M7405 avahi-daemon[733]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::20e:35ff:fe89:579e.
Jan  9 12:20:03 Amilo-M7405 avahi-daemon[733]: Withdrawing address record for fe80::20e:35ff:fe89:579e on eth1.
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth0): now unmanaged
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth0): device state change: 2 -> 1 (reason 37)
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth0): cleaning up...
Jan  9 12:20:03 Amilo-M7405 NetworkManager[746]: <info> (eth0): taking down device.
Jan  9 13:16:23 Amilo-M7405 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jan  9 13:16:23 Amilo-M7405 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="531" x-info="http://www.rsyslog.com"] (re)start
Jan  9 13:16:23 Amilo-M7405 rsyslogd: rsyslogd's groupid changed to 103
Jan  9 13:16:23 Amilo-M7405 rsyslogd: rsyslogd's userid changed to 101
Jan  9 13:16:23 Amilo-M7405 rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Linux version 2.6.37-020637-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #201101050908 SMP Wed Jan 5 10:17:13 UTC 2011
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] BIOS-provided physical RAM map:
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003efd0000 (usable)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 000000003efd0000 - 000000003efdf000 (ACPI data)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  BIOS-e820: 000000003efdf000 - 000000003f000000 (ACPI NVS)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Notice: NX (Execute Disable) protection missing in CPU or disabled in BIOS!
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] DMI 2.3 present.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] DMI: 255/259 Series                  /Amilo M7405 , BIOS 1.03C   01/25/2005
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] last_pfn = 0x3efd0 max_arch_pfn = 0x100000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] MTRR default type: uncachable
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] MTRR fixed ranges enabled:
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   00000-9FFFF write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   A0000-EFFFF uncachable
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   F0000-FFFFF write-protect
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] MTRR variable ranges enabled:
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   0 base 000000000 mask FE0000000 write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   1 base 020000000 mask FF0000000 write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   2 base 030000000 mask FF8000000 write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   3 base 038000000 mask FFC000000 write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   4 base 03C000000 mask FFE000000 write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   5 base 03E000000 mask FFF000000 write-back
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   6 disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   7 disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PAT not supported by CPU.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] initial memory mapped : 0 - 01000000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ ffb000-1000000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] RAMDISK: 2e412000 - 2f41c000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: RSDP 000f6790 00014 (v00 ACPIAM)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: RSDT 3efd0000 00034 (v01 A M I  OEMRSDT  01000525 MSFT 00000097)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: FACP 3efd0200 00081 (v02 A M I  OEMFACP  01000525 MSFT 00000097)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: DSDT 3efd03f0 03714 (v01 UW     F07_____ 00000001 INTL 02002026)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: FACS 3efdf000 00040
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: APIC 3efd0390 00054 (v01 A M I  OEMAPIC  01000525 MSFT 00000097)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: OEMB 3efdf040 00040 (v01 A M I  AMI_OEM  01000525 MSFT 00000097)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: SSDT 3efd3b10 00394 (v01    AMI   CPU1PM 00000001 INTL 02002026)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] 119MB HIGHMEM available.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] 887MB LOWMEM available.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   low ram: 0 - 377fe000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Zone PFN ranges:
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003efd0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Movable zone start PFN for each node
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] early_node_map[2] active PFN ranges
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     0: 0x00000100 -> 0x0003efd0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] On node 0 totalpages: 257887
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] free_area_init_node: node 0, pgdat c0850d00, node_mem_map f701d200
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   DMA zone: 0 pages reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   HighMem zone: 240 pages used for memmap
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]   HighMem zone: 30434 pages, LIFO batch:7
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Using APIC driver default
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] nr_irqs_gsi: 40
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Allocating PCI resources starting at 3f000000 (gap: 3f000000:c1000000)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PERCPU: Embedded 12 pages/cpu @f6c00000 s28544 r0 d20608 u4194304
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] pcpu-alloc: s28544 r0 d20608 u4194304 alloc=1*4194304
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] pcpu-alloc: [0] 0 
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 255871
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637-generic root=UUID=53f4ad58-f05f-4972-b816-4105751cba54 ro quiet splash
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Initializing CPU#0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] allocated 5159680 bytes of page_cgroup
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003efd0)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Memory: 991900k/1032000k available (5128k kernel code, 39648k reserved, 2467k data, 740k init, 122696k highmem)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] virtual kernel memory layout:
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]       .init : 0xc086c000 - 0xc0925000   ( 740 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]       .data : 0xc060234f - 0xc086b108   (2467 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]       .text : 0xc0100000 - 0xc060234f   (5128 kB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Hierarchical RCU implementation.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256 16
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] CPU 0 irqstacks, hard=f6008000 soft=f600a000
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Console: colour VGA+ 80x25
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] console [tty0] enabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Fast TSC calibration using PIT
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.000000] Detected 1400.005 MHz processor.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 2800.01 BogoMIPS (lpj=5600020)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.004013] pid_max: default: 32768 minimum: 301
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.004046] Security Framework initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.004069] AppArmor: AppArmor initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.004151] Mount-cache hash table entries: 512
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008127] Initializing cgroup subsys ns
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008133] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008138] Initializing cgroup subsys cpuacct
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008145] Initializing cgroup subsys memory
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008162] Initializing cgroup subsys devices
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008165] Initializing cgroup subsys freezer
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008169] Initializing cgroup subsys net_cls
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008218] mce: CPU supports 5 MCE banks
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008232] CPU0: Thermal monitoring enabled (TM2)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008243] Performance Events: p6 PMU driver.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008254] ... version:                0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008257] ... bit width:              32
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008260] ... generic registers:      2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008263] ... value mask:             00000000ffffffff
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008267] ... max period:             000000007fffffff
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008270] ... fixed-purpose events:   0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.008273] ... event mask:             0000000000000003
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.009452] SMP alternatives: switching to UP code
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.018985] Freeing SMP alternatives: 20k freed
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.018998] ACPI: Core revision 20101013
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.028014] ftrace: allocating 26658 entries in 53 pages
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.032093] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.032397] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.072731] CPU0: Intel(R) Pentium(R) M processor 1.40GHz stepping 06
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] Brought up 1 CPUs
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] Total of 1 processors activated (2800.01 BogoMIPS).
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] devtmpfs: initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] regulator: core version 0.5
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] regulator: dummy: 
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] Time: 12:16:04  Date: 01/09/11
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] NET: Registered protocol family 16
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] EISA bus registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] ACPI: bus type pci registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.076000] PCI: Using configuration type 1 for base access
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.077452] bio: create slab <bio-0> at 0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.078669] ACPI: EC: Look up EC in DSDT
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.079932] ACPI: Executed 2 blocks of module-level executable AML code
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.084045] ACPI: Interpreter enabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.084054] ACPI: (supports S0 S3 S4 S5)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.084087] ACPI: Using IOAPIC for interrupt routing
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.092517] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.092695] ACPI: No dock devices found.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.092702] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.092803] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093024] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093029] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093034] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093038] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093043] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d6fff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093048] pci_root PNP0A03:00: host bridge window [mem 0x000d7000-0x000d7fff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093052] pci_root PNP0A03:00: host bridge window [mem 0x000de000-0x000dffff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093057] pci_root PNP0A03:00: host bridge window [mem 0x3f000000-0xffffffff] (ignored)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093074] pci 0000:00:00.0: [8086:3580] type 0 class 0x000600
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093121] pci 0000:00:00.1: [8086:3584] type 0 class 0x000880
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093167] pci 0000:00:00.3: [8086:3585] type 0 class 0x000880
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093219] pci 0000:00:02.0: [8086:3582] type 0 class 0x000300
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093232] pci 0000:00:02.0: reg 10: [mem 0xd8000000-0xdfffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093241] pci 0000:00:02.0: reg 14: [mem 0xe0380000-0xe03fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093249] pci 0000:00:02.0: reg 18: [io  0xec00-0xec07]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093279] pci 0000:00:02.0: supports D1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093292] pci 0000:00:02.1: [8086:3582] type 0 class 0x000380
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093304] pci 0000:00:02.1: reg 10: [mem 0xd0000000-0xd7ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093313] pci 0000:00:02.1: reg 14: [mem 0xe0300000-0xe037ffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093346] pci 0000:00:02.1: supports D1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093396] pci 0000:00:1d.0: [8086:24c2] type 0 class 0x000c03
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093441] pci 0000:00:1d.0: reg 20: [io  0xe480-0xe49f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093475] pci 0000:00:1d.1: [8086:24c4] type 0 class 0x000c03
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093520] pci 0000:00:1d.1: reg 20: [io  0xe800-0xe81f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093553] pci 0000:00:1d.2: [8086:24c7] type 0 class 0x000c03
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093598] pci 0000:00:1d.2: reg 20: [io  0xe880-0xe89f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093642] pci 0000:00:1d.7: [8086:24cd] type 0 class 0x000c03
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093665] pci 0000:00:1d.7: reg 10: [mem 0xe02ffc00-0xe02fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093743] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093750] pci 0000:00:1d.7: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093768] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093811] pci 0000:00:1f.0: [8086:24cc] type 0 class 0x000601
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093876] pci 0000:00:1f.0: quirk: [io  0x0400-0x047f] claimed by ICH4 ACPI/GPIO/TCO
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093882] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH4 GPIO
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093898] pci 0000:00:1f.1: [8086:24ca] type 0 class 0x000101
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093913] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093924] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093936] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093947] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093958] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093969] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.093998] pci 0000:00:1f.3: [8086:24c3] type 0 class 0x000c05
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094043] pci 0000:00:1f.3: reg 20: [io  0xd480-0xd49f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094081] pci 0000:00:1f.5: [8086:24c5] type 0 class 0x000401
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094098] pci 0000:00:1f.5: reg 10: [io  0xd800-0xd8ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094108] pci 0000:00:1f.5: reg 14: [io  0xdc00-0xdc3f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094119] pci 0000:00:1f.5: reg 18: [mem 0xe02ff800-0xe02ff9ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094130] pci 0000:00:1f.5: reg 1c: [mem 0xe02ff400-0xe02ff4ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094167] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094173] pci 0000:00:1f.5: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094191] pci 0000:00:1f.6: [8086:24c6] type 0 class 0x000703
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094207] pci 0000:00:1f.6: reg 10: [io  0xe000-0xe0ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094218] pci 0000:00:1f.6: reg 14: [io  0xe400-0xe47f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094268] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094274] pci 0000:00:1f.6: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094308] pci 0000:01:03.0: [1217:7114] type 2 class 0x000607
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094326] pci 0000:01:03.0: reg 10: [mem 0x00000000-0x00000fff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094345] pci 0000:01:03.0: supports D1 D2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094349] pci 0000:01:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094355] pci 0000:01:03.0: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094374] pci 0000:01:03.1: [1217:7114] type 2 class 0x000607
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094392] pci 0000:01:03.1: reg 10: [mem 0x00000000-0x00000fff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094411] pci 0000:01:03.1: supports D1 D2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094415] pci 0000:01:03.1: PME# supported from D0 D1 D2 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094420] pci 0000:01:03.1: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094439] pci 0000:01:03.2: [1217:7110] type 0 class 0x000880
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094457] pci 0000:01:03.2: reg 10: [mem 0xe00ff000-0xe00fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094519] pci 0000:01:03.2: supports D1 D2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094523] pci 0000:01:03.2: PME# supported from D0 D1 D2 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094528] pci 0000:01:03.2: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094555] pci 0000:01:07.0: [8086:4220] type 0 class 0x000280
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094573] pci 0000:01:07.0: reg 10: [mem 0xe00fe000-0xe00fefff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094635] pci 0000:01:07.0: PME# supported from D0 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094640] pci 0000:01:07.0: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094661] pci 0000:01:0a.0: [104c:8023] type 0 class 0x000c00
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094679] pci 0000:01:0a.0: reg 10: [mem 0xe00fd800-0xe00fdfff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094690] pci 0000:01:0a.0: reg 14: [mem 0xe00f8000-0xe00fbfff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094744] pci 0000:01:0a.0: supports D1 D2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094748] pci 0000:01:0a.0: PME# supported from D0 D1 D2 D3hot
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094753] pci 0000:01:0a.0: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094773] pci 0000:01:0c.0: [10ec:8139] type 0 class 0x000200
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094790] pci 0000:01:0c.0: reg 10: [io  0xc800-0xc8ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094801] pci 0000:01:0c.0: reg 14: [mem 0xe00fd400-0xe00fd4ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094854] pci 0000:01:0c.0: supports D1 D2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094858] pci 0000:01:0c.0: PME# supported from D1 D2 D3hot D3cold
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094863] pci 0000:01:0c.0: PME# disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094892] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094898] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094905] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xe00fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094911] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094916] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094921] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094963] pci_bus 0000:02: [bus 02-05] partially hidden behind transparent bridge 0000:01 [bus 01-01]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.094995] pci_bus 0000:06: [bus 06-09] partially hidden behind transparent bridge 0000:01 [bus 01-01]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.095007] pci_bus 0000:00: on NUMA node 0
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.095013] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.095145] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.176970] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177091] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177207] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177322] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177438] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177555] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177673] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177791] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177851] HEST: Table is not found!
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177956] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.177971] vgaarb: loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178296] SCSI subsystem initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178361] libata version 3.00 loaded.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178440] usbcore: registered new interface driver usbfs
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178460] usbcore: registered new interface driver hub
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178499] usbcore: registered new device driver usb
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178729] wmi: Mapper loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178732] PCI: Using ACPI for IRQ routing
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178737] PCI: pci_cache_line_size set to 64 bytes
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178817] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.178822] reserve RAM buffer: 000000003efd0000 - 000000003fffffff 
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180009] NetLabel: Initializing
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180012] NetLabel:  domain hash size = 128
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180015] NetLabel:  protocols = UNLABELED CIPSOv4
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180034] NetLabel:  unlabeled traffic allowed by default
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.180102] Switching to clocksource tsc
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191597] AppArmor: AppArmor Filesystem Enabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191630] pnp: PnP ACPI init
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191685] ACPI: bus type pnp registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191874] pnp 00:00: [bus 00-ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191880] pnp 00:00: [io  0x0cf8-0x0cff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191884] pnp 00:00: [io  0x0000-0x0cf7 window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191914] pnp 00:00: [io  0x0d00-0xffff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191918] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191922] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191927] pnp 00:00: [mem 0x000d4000-0x000d6fff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191931] pnp 00:00: [mem 0x000d7000-0x000d7fff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191935] pnp 00:00: [mem 0x000de000-0x000dffff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.191939] pnp 00:00: [mem 0x3f000000-0xffffffff window]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192040] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192126] pnp 00:01: [dma 4]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192130] pnp 00:01: [io  0x0000-0x000f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192133] pnp 00:01: [io  0x0081-0x0083]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192137] pnp 00:01: [io  0x0087]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192140] pnp 00:01: [io  0x0089-0x008b]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192144] pnp 00:01: [io  0x008f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192147] pnp 00:01: [io  0x00c0-0x00df]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192199] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192224] pnp 00:02: [io  0x0070-0x0071]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192246] pnp 00:02: [irq 8]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192300] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192364] pnp 00:03: [io  0x0060]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192368] pnp 00:03: [io  0x0064]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192376] pnp 00:03: [irq 1]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192429] pnp 00:03: Plug and Play ACPI device, IDs PNP030b PNP0303 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192521] pnp 00:04: [irq 12]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192575] pnp 00:04: Plug and Play ACPI device, IDs SYN0801 SYN0800 PNP0f13 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192591] pnp 00:05: [io  0x0061]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192641] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192657] pnp 00:06: [io  0x00f0-0x00ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192663] pnp 00:06: [irq 13]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192728] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192931] pnp 00:07: [io  0x0010-0x001f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192935] pnp 00:07: [io  0x0022-0x003f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192938] pnp 00:07: [io  0x0044-0x005f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192942] pnp 00:07: [io  0x0063]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192945] pnp 00:07: [io  0x0065]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192949] pnp 00:07: [io  0x0067-0x006f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192952] pnp 00:07: [io  0x0072-0x007f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192956] pnp 00:07: [io  0x0080]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192959] pnp 00:07: [io  0x0084-0x0086]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192962] pnp 00:07: [io  0x0088]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192966] pnp 00:07: [io  0x008c-0x008e]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192969] pnp 00:07: [io  0x0090-0x009f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192973] pnp 00:07: [io  0x00a2-0x00bf]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192977] pnp 00:07: [io  0x00e0-0x00ef]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192980] pnp 00:07: [io  0x04d0-0x04d1]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192984] pnp 00:07: [io  0x0400-0x047f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.192987] pnp 00:07: [io  0x0500-0x053f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193111] pnp 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193271] pnp 00:08: [io  0x1100-0x113f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193275] pnp 00:08: [io  0x1254]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193278] pnp 00:08: [io  0x12d4]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193282] pnp 00:08: [io  0x1300-0x1375]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193286] pnp 00:08: [io  0x1377-0x137f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193290] pnp 00:08: [io  0x0000-0xffffffff disabled]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193293] pnp 00:08: [io  0x0200-0x020f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193297] pnp 00:08: [io  0x0860-0x086f]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193301] pnp 00:08: [mem 0xfec00000-0xfec00fff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193305] pnp 00:08: [mem 0xfee00000-0xfee00fff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193308] pnp 00:08: [mem 0xfec10000-0xfec1ffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193312] pnp 00:08: [mem 0xffe80000-0xffefffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193316] pnp 00:08: [mem 0xfff80000-0xffffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193320] pnp 00:08: [mem 0xfee00400-0xffbfffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193324] pnp 00:08: [mem 0xfff00000-0xfff7ffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193424] pnp 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193990] pnp 00:09: [mem 0x00000000-0x0009ffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193994] pnp 00:09: [mem 0x00000000-0xffffffff disabled]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.193998] pnp 00:09: [mem 0x000e0000-0x000fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194002] pnp 00:09: [mem 0x00100000-0x3effffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194006] pnp 00:09: [mem 0x00000000-0xffffffff disabled]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194087] pnp 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194424] pnp: PnP ACPI: found 10 devices
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194428] ACPI: ACPI bus type pnp unregistered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194434] PnPBIOS: Disabled by ACPI PNP
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194457] system 00:07: [io  0x04d0-0x04d1] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194462] system 00:07: [io  0x0400-0x047f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194467] system 00:07: [io  0x0500-0x053f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194475] system 00:08: [io  0x1100-0x113f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194480] system 00:08: [io  0x1254] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194484] system 00:08: [io  0x12d4] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194489] system 00:08: [io  0x1300-0x1375] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194493] system 00:08: [io  0x1377-0x137f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194498] system 00:08: [io  0x0200-0x020f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194503] system 00:08: [io  0x0860-0x086f] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194509] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194514] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194519] system 00:08: [mem 0xfec10000-0xfec1ffff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194524] system 00:08: [mem 0xffe80000-0xffefffff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194529] system 00:08: [mem 0xfff80000-0xffffffff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194534] system 00:08: [mem 0xfee00400-0xffbfffff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194539] system 00:08: [mem 0xfff00000-0xfff7ffff] has been reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194548] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194553] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.194558] system 00:09: [mem 0x00100000-0x3effffff] could not be reserved
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232089] pci 0000:00:1e.0: BAR 15: assigned [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232097] pci 0000:00:1f.1: BAR 5: assigned [mem 0x48000000-0x480003ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232106] pci 0000:00:1f.1: BAR 5: set to [mem 0x48000000-0x480003ff] (PCI address [0x48000000-0x480003ff])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232114] pci 0000:01:03.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232123] pci 0000:01:03.0: BAR 16: assigned [mem 0x4c000000-0x4fffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232128] pci 0000:01:03.1: BAR 15: assigned [mem 0x44000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232136] pci 0000:01:03.1: BAR 16: assigned [mem 0x50000000-0x53ffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232140] pci 0000:01:03.0: BAR 0: assigned [mem 0xe0000000-0xe0000fff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232147] pci 0000:01:03.0: BAR 0: set to [mem 0xe0000000-0xe0000fff] (PCI address [0xe0000000-0xe0000fff])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232153] pci 0000:01:03.1: BAR 0: assigned [mem 0xe0001000-0xe0001fff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232160] pci 0000:01:03.1: BAR 0: set to [mem 0xe0001000-0xe0001fff] (PCI address [0xe0001000-0xe0001fff])
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232165] pci 0000:01:03.0: BAR 13: assigned [io  0xc000-0xc0ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232170] pci 0000:01:03.0: BAR 14: assigned [io  0xc400-0xc4ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232174] pci 0000:01:03.1: BAR 13: assigned [io  0xcc00-0xccff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232180] pci 0000:01:03.1: BAR 14: assigned [io  0x1000-0x10ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232185] pci 0000:01:03.0: CardBus bridge to [bus 02-05]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232189] pci 0000:01:03.0:   bridge window [io  0xc000-0xc0ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232195] pci 0000:01:03.0:   bridge window [io  0xc400-0xc4ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232201] pci 0000:01:03.0:   bridge window [mem 0x40000000-0x43ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232207] pci 0000:01:03.0:   bridge window [mem 0x4c000000-0x4fffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232213] pci 0000:01:03.1: CardBus bridge to [bus 06-09]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232217] pci 0000:01:03.1:   bridge window [io  0xcc00-0xccff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232223] pci 0000:01:03.1:   bridge window [io  0x1000-0x10ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232229] pci 0000:01:03.1:   bridge window [mem 0x44000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232235] pci 0000:01:03.1:   bridge window [mem 0x50000000-0x53ffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232241] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232247] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232254] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xe00fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232260] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232279] pci 0000:00:1e.0: setting latency timer to 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232300] pci 0000:01:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232309] pci 0000:01:03.1: enabling device (0000 -> 0003)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232315] pci 0000:01:03.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232324] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232328] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232332] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232337] pci_bus 0000:01: resource 1 [mem 0xe0000000-0xe00fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232341] pci_bus 0000:01: resource 2 [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232345] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232349] pci_bus 0000:01: resource 5 [mem 0x00000000-0xffffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232354] pci_bus 0000:02: resource 0 [io  0xc000-0xc0ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232358] pci_bus 0000:02: resource 1 [io  0xc400-0xc4ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232362] pci_bus 0000:02: resource 2 [mem 0x40000000-0x43ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232366] pci_bus 0000:02: resource 3 [mem 0x4c000000-0x4fffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232371] pci_bus 0000:06: resource 0 [io  0xcc00-0xccff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232375] pci_bus 0000:06: resource 1 [io  0x1000-0x10ff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232379] pci_bus 0000:06: resource 2 [mem 0x44000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232383] pci_bus 0000:06: resource 3 [mem 0x50000000-0x53ffffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232442] NET: Registered protocol family 2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232552] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.232937] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.234419] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235330] TCP: Hash tables configured (established 131072 bind 65536)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235335] TCP reno registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235343] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235377] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235579] NET: Registered protocol family 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235631] pci 0000:00:02.0: Boot video device
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235745] PCI: CLS 64 bytes, default 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.235839] Trying to unpack rootfs image as initramfs...
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.958669] Freeing initrd memory: 16424k freed
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.975881] cpufreq-nforce2: No nForce2 chipset.
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.975944] Scanning for low memory corruption every 60 seconds
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.976297] audit: initializing netlink socket (disabled)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.976318] type=2000 audit(1294575363.972:1): initialized
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.993288] highmem bounce pool size: 64 pages
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.993297] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.996341] VFS: Disk quotas dquot_6.5.2
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.996435] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.997545] fuse init (API version 7.15)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.997704] msgmni has been set to 1729
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998071] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998076] io scheduler noop registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998079] io scheduler deadline registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998103] io scheduler cfq registered (default)
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998333] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  9 13:16:23 Amilo-M7405 kernel: [    0.998371] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.008913] ACPI: AC Adapter [AC0] (on-line)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009030] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009067] ACPI: Lid Switch [LID]
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009150] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009157] ACPI: Sleep Button [SLPB]
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009237] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009242] ACPI: Power Button [PWRB]
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009318] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009324] ACPI: Power Button [PWRF]
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009507] ACPI: acpi_idle registered with cpuidle
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.009549] Marking TSC unstable due to TSC halts in idle
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.010416] Switching to clocksource acpi_pm
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.011488] thermal LNXTHERM:00: registered as thermal_zone0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.011492] ACPI: Thermal Zone [THRM] (11 C)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.011551] ERST: Table is not found!
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.011579] isapnp: Scanning for PnP cards...
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.365551] isapnp: No Plug & Play device found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.365766] Linux agpgart interface v0.103
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.365877] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.365903] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.366726] agpgart-intel 0000:00:00.0: detected 16384K stolen memory
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.368534] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.368616] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.370419] serial 0000:00:1f.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.370428] serial 0000:00:1f.6: PCI INT B disabled
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.372480] brd: module loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.373428] loop: module loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.373719] ata_piix 0000:00:1f.1: version 2.13
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.373731] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.373749] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.373800] ata_piix 0000:00:1f.1: setting latency timer to 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.374333] scsi0 : ata_piix
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.374466] scsi1 : ata_piix
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.377403] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.377408] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378013] Fixed MDIO Bus: probed
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378066] PPP generic driver version 2.4.2
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378131] tun: Universal TUN/TAP device driver, 1.6
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378134] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378259] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378283] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378301] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378307] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378366] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.378405] ehci_hcd 0000:00:1d.7: debug port 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.382279] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.382548] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe02ffc00
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396208] hub 1-0:1.0: USB hub found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396216] hub 1-0:1.0: 6 ports detected
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396336] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396358] uhci_hcd: USB Universal Host Controller Interface driver
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396396] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396404] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396409] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396485] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396525] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e480
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396721] hub 2-0:1.0: USB hub found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396728] hub 2-0:1.0: 2 ports detected
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396825] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396834] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396838] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396894] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.396930] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e800
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397129] hub 3-0:1.0: USB hub found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397135] hub 3-0:1.0: 2 ports detected
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397239] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397247] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397252] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397306] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397342] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e880
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397555] hub 4-0:1.0: USB hub found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397562] hub 4-0:1.0: 2 ports detected
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.397748] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.403859] i8042.c: Detected active multiplexing controller, rev 1.0.
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.404748] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.404757] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.404919] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.404963] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.405006] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.405183] mice: PS/2 mouse device common for all mice
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.405936] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.405960] rtc0: alarms up to one month, 114 bytes nvram
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406142] device-mapper: uevent: version 1.0.3
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406453] device-mapper: ioctl: 4.18.0-ioctl (2010-06-29) initialised: dm-devel@redhat.com
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406708] device-mapper: multipath: version 1.1.1 loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406713] device-mapper: multipath round-robin: version 1.0.0 loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406933] EISA: Probing bus 0 at eisa.0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406941] Cannot allocate resource for EISA slot 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.406973] EISA: Detected 0 cards.
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.407168] cpuidle: using governor ladder
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.407253] cpuidle: using governor menu
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.407696] TCP cubic registered
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.407918] NET: Registered protocol family 10
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.408486] lo: Disabled Privacy Extensions
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.408860] NET: Registered protocol family 17
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.408882] Registering the dns_resolver key type
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.409530] Using IPI No-Shortcut mode
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.410010] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.411983] PM: Hibernation image not present or could not be loaded.
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.412174] registered taskstats version 1
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414807]   Magic number: 11:634:278
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414837] tty tty15: hash matches
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414893] rtc_cmos 00:02: setting system clock to 2011-01-09 12:16:05 UTC (1294575365)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414898] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.414901] EDD information not available.
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.417686] ACPI: Battery Slot [BAT0] (battery present)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.544539] ata1.00: ATA-7: FUJITSU MHV2080AH, 000000A0, max UDMA/100
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.544544] ata1.00: 156301488 sectors, multi 16: LBA 
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.560414] ata2.00: ATAPI: _NEC DVD+/-RW ND-6500A, 2.40, max UDMA/33
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.560646] ata1.00: configured for UDMA/100
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.560811] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080A 0000 PQ: 0 ANSI: 5
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.561049] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.561165] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.561251] sd 0:0:0:0: [sda] Write Protect is off
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.561255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.561292] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.608173] ata2.00: configured for UDMA/33
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.614393]  sda: sda1 sda2 < sda5 >
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.614769] sd 0:0:0:0: [sda] Attached SCSI disk
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.695361] scsi 1:0:0:0: CD-ROM            _NEC     DVD+-RW ND-6500A 2.40 PQ: 0 ANSI: 5
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817448] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817453] cdrom: Uniform CD-ROM driver Revision: 3.20
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817597] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817684] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.817756] Freeing unused kernel memory: 740k freed
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.818262] Write protecting the kernel text: 5132k
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.818328] Write protecting the kernel read-only data: 2104k
Jan  9 13:16:23 Amilo-M7405 kernel: [    1.842298] udev[69]: starting version 163
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.083270] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.083310] 8139cp 0000:01:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.094492] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input5
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.094580] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.124099] 8139too: 8139too Fast Ethernet driver 0.9.28
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.124158] 8139too 0000:01:0c.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.125469] 8139too 0000:01:0c.0: eth0: RealTek RTL8139 at 0xc800, 00:03:0d:1f:8e:81, IRQ 19
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.126295] firewire_ohci 0000:01:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.182033] firewire_ohci: Added fw-ohci device 0000:01:0a.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.211224] [drm] Initialized drm 1.1.0 20060810
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.268821] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.268830] i915 0000:00:02.0: setting latency timer to 64
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.334212] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.334787] [drm] initialized overlay support
Jan  9 13:16:23 Amilo-M7405 kernel: [    2.680357] firewire_core: created device fw0: GUID 00030d4925503c19, S400
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.316074] [drm:intel_panel_get_max_backlight] *ERROR* fixme: max PWM is zero.
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.325532] Console: switching to colour frame buffer device 128x48
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.333805] fb0: inteldrmfb frame buffer device
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.333808] drm: registered panic notifier
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.334005] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jan  9 13:16:23 Amilo-M7405 kernel: [    3.968935] Btrfs loaded
Jan  9 13:16:23 Amilo-M7405 kernel: [    9.342109] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Jan  9 13:16:23 Amilo-M7405 kernel: [    9.342117] EXT4-fs (sda1): write access will be enabled during recovery
Jan  9 13:16:23 Amilo-M7405 kernel: [   11.903055] EXT4-fs (sda1): orphan cleanup on readonly fs
Jan  9 13:16:23 Amilo-M7405 kernel: [   11.903070] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1311021
Jan  9 13:16:23 Amilo-M7405 kernel: [   11.903178] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1310867
Jan  9 13:16:23 Amilo-M7405 kernel: [   11.903198] EXT4-fs (sda1): 2 orphan inodes deleted
Jan  9 13:16:23 Amilo-M7405 kernel: [   11.903202] EXT4-fs (sda1): recovery complete
Jan  9 13:16:23 Amilo-M7405 kernel: [   12.176272] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan  9 13:16:23 Amilo-M7405 kernel: [   15.217653] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jan  9 13:16:23 Amilo-M7405 kernel: [   15.319546] udev[304]: starting version 163
Jan  9 13:16:23 Amilo-M7405 kernel: [   16.886266] intel_rng: FWH not detected
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.042969] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.083808] lib80211: common routines for IEEE802.11 drivers
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.083815] lib80211_crypt: registered algorithm 'NULL'
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.120294] cfg80211: Calling CRDA to update world regulatory domain
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.409575] libipw: 802.11 data/management/control stack, git-1.1.13
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.409581] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.476390] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.476397] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.476555] ipw2200 0000:01:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.480029] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.878686] lp: driver loaded but no devices found
Jan  9 13:16:23 Amilo-M7405 kernel: [   17.975508] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.037103] type=1400 audit(1294575382.119:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=445 comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.037213] type=1400 audit(1294575382.119:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=445 comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.037302] type=1400 audit(1294575382.119:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=445 comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.134196] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x6eb1, caps: 0xa04711/0x40a/0x0
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.173741] yenta_cardbus 0000:01:03.0: CardBus bridge found [1734:106a]
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.173771] yenta_cardbus 0000:01:03.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.185009] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input6
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.254552] type=1400 audit(1294575382.335:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=529 comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.254663] type=1400 audit(1294575382.335:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=529 comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.254754] type=1400 audit(1294575382.335:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=529 comm="apparmor_parser"
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.300919] yenta_cardbus 0000:01:03.0: ISA IRQ mask 0x0cb8, PCI irq 17
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.300926] yenta_cardbus 0000:01:03.0: Socket status: 30000006
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.300933] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #01 to #05
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.300948] yenta_cardbus 0000:01:03.0: pcmcia: parent PCI bridge window: [io  0xc000-0xcfff]
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.300954] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc000-0xcfff: excluding 0xc000-0xc0ff 0xc400-0xc4ff 0xc800-0xc8ff 0xcc00-0xccff
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.306023] yenta_cardbus 0000:01:03.0: pcmcia: parent PCI bridge window: [mem 0xe0000000-0xe00fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.306029] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0000000-0xe00fffff: excluding 0xe0000000-0xe000ffff 0xe00f0000-0xe00fffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.306050] yenta_cardbus 0000:01:03.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.306055] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x47ffffff: excluding 0x40000000-0x47ffffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.306860] yenta_cardbus 0000:01:03.1: CardBus bridge found [1734:106a]
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.432955] yenta_cardbus 0000:01:03.1: ISA IRQ mask 0x0cb8, PCI irq 17
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.432961] yenta_cardbus 0000:01:03.1: Socket status: 30000006
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.432967] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #05 to #09
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.432979] yenta_cardbus 0000:01:03.1: pcmcia: parent PCI bridge window: [io  0xc000-0xcfff]
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.432985] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc000-0xcfff: excluding 0xc000-0xc0ff 0xc400-0xc4ff 0xc800-0xc8ff 0xcc00-0xccff
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.438007] yenta_cardbus 0000:01:03.1: pcmcia: parent PCI bridge window: [mem 0xe0000000-0xe00fffff]
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.438013] pcmcia_socket pcmcia_socket1: cs: memory probe 0xe0000000-0xe00fffff: excluding 0xe0000000-0xe000ffff 0xe00f0000-0xe00fffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.438034] yenta_cardbus 0000:01:03.1: pcmcia: parent PCI bridge window: [mem 0x40000000-0x47ffffff pref]
Jan  9 13:16:23 Amilo-M7405 kernel: [   18.438039] pcmcia_socket pcmcia_socket1: cs: memory probe 0x40000000-0x47ffffff: excluding 0x40000000-0x47ffffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410465] cfg80211: World regulatory domain updated:
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410473]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410477]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410482]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410486]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410491]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.410495]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  9 13:16:23 Amilo-M7405 udev-configure-printer: add /module/lp
Jan  9 13:16:23 Amilo-M7405 udev-configure-printer: Failed to get parent
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.705098] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x200-0x20f 0x370-0x377
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.706775] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x400-0x47f 0x4d0-0x4d7
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.707220] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: excluding 0x860-0x86f
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.707804] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7:
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.708189] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x200-0x20f 0x370-0x377
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.709847] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x400-0x47f 0x4d0-0x4d7
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.710288] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding 0x860-0x86f
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.710871] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.711551] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xe0000-0xfffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.711636] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.711719] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.711807] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.712822] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xe0000-0xfffff
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.712907] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.712990] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.713080] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
Jan  9 13:16:23 Amilo-M7405 kernel: [   19.714581]  clean.
Jan  9 13:16:24 Amilo-M7405 kernel: [   20.861717] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jan  9 13:16:24 Amilo-M7405 kernel: [   20.861760] Intel ICH 0000:00:1f.5: setting latency timer to 64
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: Successfully dropped root privileges.
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: avahi-daemon 0.6.27 starting up.
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: Successfully called chroot().
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: Successfully dropped remaining capabilities.
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: No service file found in /etc/avahi/services.
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: Network interface enumeration completed.
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: Registering HINFO record with values 'I686'/'LINUX'.
Jan  9 13:16:25 Amilo-M7405 avahi-daemon[625]: Server startup complete. Host name is Amilo-M7405.local. Local service cookie is 3809600776.
Jan  9 13:16:25 Amilo-M7405 kernel: [   21.688035] intel8x0_measure_ac97_clock: measured 55422 usecs (2671 samples)
Jan  9 13:16:25 Amilo-M7405 kernel: [   21.688041] intel8x0: clocking to 48000
Jan  9 13:16:26 Amilo-M7405 gdm-binary[596]: WARNING: Unable to load file '/etc/gdm/custom.conf': Aucun fichier ou dossier de ce type
Jan  9 13:16:26 Amilo-M7405 NetworkManager[673]: <info> NetworkManager (version 0.8.1) is starting...
Jan  9 13:16:26 Amilo-M7405 NetworkManager[673]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Jan  9 13:16:26 Amilo-M7405 NetworkManager[673]: <info> trying to start the modem manager...
Jan  9 13:16:26 Amilo-M7405 kernel: [   22.811478] type=1400 audit(1294575386.891:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=660 comm="apparmor_parser"
Jan  9 13:16:26 Amilo-M7405 kernel: [   22.811756] type=1400 audit(1294575386.891:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=660 comm="apparmor_parser"
Jan  9 13:16:27 Amilo-M7405 modem-manager: ModemManager (version 0.4) starting...
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Huawei
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin ZTE
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Longcheer
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin SimTech
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Ericsson MBM
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Generic
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Nokia
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Option
Jan  9 13:16:27 Amilo-M7405 modem-manager: Loaded plugin Gobi
Jan  9 13:16:27 Amilo-M7405 kernel: [   23.596222] ppdev: user-space parallel port driver
Jan  9 13:16:27 Amilo-M7405 kernel: [   23.771974] type=1400 audit(1294575387.851:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=722 comm="apparmor_parser"
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: init!
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: update_system_hostname
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPluginIfupdown: management mode: unmanaged
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:07.0/net/eth1, iface: eth1)
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:07.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:0c.0/net/eth0, iface: eth0)
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:0c.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: end _init.
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    Ifupdown: get unmanaged devices count: 0
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: (154668368) ... get_connections.
Jan  9 13:16:27 Amilo-M7405 NetworkManager[673]:    SCPlugin-Ifupdown: (154668368) ... get_connections (managed=false): return empty list.
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]:    Ifupdown: get unmanaged devices count: 0
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:01:07.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Jan  9 13:16:28 Amilo-M7405 kernel: [   24.035239] type=1400 audit(1294575388.115:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=732 comm="apparmor_parser"
Jan  9 13:16:28 Amilo-M7405 kernel: [   24.035353] type=1400 audit(1294575388.115:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=732 comm="apparmor_parser"
Jan  9 13:16:28 Amilo-M7405 kernel: [   24.035449] type=1400 audit(1294575388.115:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=732 comm="apparmor_parser"
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> Networking is enabled by state file
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): driver supports SSID scans (scan_capa 0x21).
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): now managed
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): bringing up device.
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): preparing device.
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): deactivating device (reason: 2).
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): carrier is OFF
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): new Ethernet device (driver: '8139too' ifindex: 2)
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): now managed
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): bringing up device.
Jan  9 13:16:28 Amilo-M7405 kernel: [   24.303836] eth0: link down
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): preparing device.
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth0): deactivating device (reason: 2).
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:01:0c.0/net/eth0
Jan  9 13:16:28 Amilo-M7405 kernel: [   24.304516] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> modem-manager is now available
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> Trying to start the supplicant...
Jan  9 13:16:28 Amilo-M7405 modem-manager: Loaded plugin Sierra
Jan  9 13:16:28 Amilo-M7405 modem-manager: Loaded plugin Novatel
Jan  9 13:16:28 Amilo-M7405 modem-manager: Loaded plugin Option High-Speed
Jan  9 13:16:28 Amilo-M7405 modem-manager: Loaded plugin AnyData
Jan  9 13:16:28 Amilo-M7405 modem-manager: Loaded plugin MotoC
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS0): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS10): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS11): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS12): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS13): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS14): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS15): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS16): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS17): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS18): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS19): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS20): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS21): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS22): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS23): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS24): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS25): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS26): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS27): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS28): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS29): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS30): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS31): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS4): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS5): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS6): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS7): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS8): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 modem-manager: (tty/ttyS9): port's parent platform driver is not whitelisted
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant manager state:  down -> idle
Jan  9 13:16:28 Amilo-M7405 NetworkManager[673]: <info> (eth1): device state change: 2 -> 3 (reason 0)
Jan  9 13:16:28 Amilo-M7405 gdm-binary[596]: WARNING: Unable to find users: no seat-id found
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant interface state:  starting -> ready
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) starting connection 'Auto DWL'
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> (eth1): device state change: 3 -> 4 (reason 0)
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1/wireless): connection 'Auto DWL' has security, and secrets exist.  No new secrets needed.
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Config: added 'ssid' value 'DWL'
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Config: added 'scan_ssid' value '1'
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Config: added 'psk' value '<omitted>'
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> Config: set interface ap_scan to 1
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  scanning -> disconnected
Jan  9 13:16:29 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jan  9 13:16:29 Amilo-M7405 avahi-daemon[625]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::20e:35ff:fe89:579e.
Jan  9 13:16:29 Amilo-M7405 avahi-daemon[625]: New relevant interface eth1.IPv6 for mDNS.
Jan  9 13:16:29 Amilo-M7405 avahi-daemon[625]: Registering new address record for fe80::20e:35ff:fe89:579e on eth1.*.
Jan  9 13:16:29 Amilo-M7405 gdm-simple-slave[808]: WARNING: Unable to load file '/etc/gdm/custom.conf': Aucun fichier ou dossier de ce type
Jan  9 13:16:30 Amilo-M7405 wpa_supplicant[805]: Trying to associate with 00:xx:xx:xx:xx:xx (SSID='MySSID' freq=2412 MHz)
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  scanning -> associating
Jan  9 13:16:30 Amilo-M7405 kernel: [   26.058750] padlock: VIA PadLock not detected.
Jan  9 13:16:30 Amilo-M7405 wpa_supplicant[805]: Associated with 00:xx:xx:xx:xx:xx
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  associating -> associated
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Jan  9 13:16:30 Amilo-M7405 modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.37-020637-generic/kernel/drivers/crypto/padlock-sha.ko): No such device
Jan  9 13:16:30 Amilo-M7405 kernel: [   26.528174] padlock: VIA PadLock Hash Engine not detected.
Jan  9 13:16:30 Amilo-M7405 wpa_supplicant[805]: WPA: Key negotiation completed with 00:xx:xx:xx:xx:xx [PTK=CCMP GTK=CCMP]
Jan  9 13:16:30 Amilo-M7405 wpa_supplicant[805]: CTRL-EVENT-CONNECTED - Connection to 00:xx:xx:xx:xx:xx completed (auth) [id=0 id_str=]
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  4-way handshake -> group handshake
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  group handshake -> completed
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'MySSID'.
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> (eth1): device state change: 5 -> 7 (reason 0)
Jan  9 13:16:30 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  9 13:16:30 Amilo-M7405 kernel: [   26.668537] lib80211_crypt: registered algorithm 'CCMP'
Jan  9 13:16:31 Amilo-M7405 NetworkManager[673]: <info> dhclient started with pid 905
Jan  9 13:16:31 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jan  9 13:16:31 Amilo-M7405 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  9 13:16:31 Amilo-M7405 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jan  9 13:16:31 Amilo-M7405 dhclient: All rights reserved.
Jan  9 13:16:31 Amilo-M7405 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  9 13:16:31 Amilo-M7405 dhclient: 
Jan  9 13:16:31 Amilo-M7405 NetworkManager[673]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Jan  9 13:16:31 Amilo-M7405 dhclient: Listening on LPF/eth1/00:yy:yy:yy:yy:yy
Jan  9 13:16:31 Amilo-M7405 dhclient: Sending on   LPF/eth1/00:yy:yy:yy:yy:yy
Jan  9 13:16:31 Amilo-M7405 dhclient: Sending on   Socket/fallback
Jan  9 13:16:31 Amilo-M7405 dhclient: DHCPREQUEST of 192.168.1.16 on eth1 to 255.255.255.255 port 67
Jan  9 13:16:31 Amilo-M7405 wpa_supplicant[805]: WPA: Group rekeying completed with 00:xx:xx:xx:xx:xx [GTK=CCMP]
Jan  9 13:16:31 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  completed -> group handshake
Jan  9 13:16:31 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  group handshake -> completed
Jan  9 13:16:31 Amilo-M7405 kernel: [   27.848360] Adding 93180k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:93180k 
Jan  9 13:16:34 Amilo-M7405 dhclient: DHCPREQUEST of 192.168.1.16 on eth1 to 255.255.255.255 port 67
Jan  9 13:16:34 Amilo-M7405 dhclient: DHCPACK of 192.168.1.16 from 192.168.1.1
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info>   address 192.168.1.16
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info>   prefix 24 (255.255.255.0)
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info>   gateway 192.168.1.1
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info>   nameserver '212.27.40.240'
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info>   nameserver '212.27.40.241'
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Jan  9 13:16:34 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Jan  9 13:16:34 Amilo-M7405 avahi-daemon[625]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.22.106.
Jan  9 13:16:34 Amilo-M7405 avahi-daemon[625]: New relevant interface eth1.IPv4 for mDNS.
Jan  9 13:16:34 Amilo-M7405 avahi-daemon[625]: Registering new address record for 192.168.1.16 on eth1.IPv4.
Jan  9 13:16:34 Amilo-M7405 dhclient: bound to 192.168.1.16 -- renewal in 324003 seconds.
Jan  9 13:16:35 Amilo-M7405 NetworkManager[673]: <info> (eth1): device state change: 7 -> 8 (reason 0)
Jan  9 13:16:35 Amilo-M7405 NetworkManager[673]: <info> Policy set 'Auto DWL' (eth1) as default for IPv4 routing and DNS.
Jan  9 13:16:35 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) successful, device activated.
Jan  9 13:16:35 Amilo-M7405 NetworkManager[673]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Jan  9 13:16:36 Amilo-M7405 ntpdate[1003]: adjust time server 91.189.94.4 offset -0.354241 sec
Jan  9 13:16:36 Amilo-M7405 kernel: [   32.878171] type=1400 audit(1294575396.959:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=738 comm="apparmor_parser"
Jan  9 13:16:36 Amilo-M7405 kernel: [   32.879489] type=1400 audit(1294575396.959:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=738 comm="apparmor_parser"
Jan  9 13:16:36 Amilo-M7405 kernel: [   32.881040] type=1400 audit(1294575396.963:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=738 comm="apparmor_parser"
Jan  9 13:16:37 Amilo-M7405 kernel: [   33.355274] type=1400 audit(1294575397.435:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1007 comm="apparmor_parser"
Jan  9 13:16:37 Amilo-M7405 kernel: [   33.355571] type=1400 audit(1294575397.435:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1007 comm="apparmor_parser"
Jan  9 13:16:37 Amilo-M7405 kernel: [   33.533160] type=1400 audit(1294575397.615:19): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1008 comm="apparmor_parser"
Jan  9 13:16:38 Amilo-M7405 kernel: [   34.448021] eth1: no IPv6 routers present
Jan  9 13:16:39 Amilo-M7405 gdm-session-worker[1047]: WARNING: Unable to load file '/etc/gdm/custom.conf': Aucun fichier ou dossier de ce type
Jan  9 13:16:39 Amilo-M7405 cron[1061]: (CRON) INFO (pidfile fd = 3)
Jan  9 13:16:39 Amilo-M7405 acpid: starting up with proc fs
Jan  9 13:16:39 Amilo-M7405 anacron[1070]: Anacron 2.3 started on 2011-01-09
Jan  9 13:16:39 Amilo-M7405 init: apport pre-start process (1052) terminated with status 1
Jan  9 13:16:39 Amilo-M7405 init: apport post-stop process (1077) terminated with status 1
Jan  9 13:16:39 Amilo-M7405 cron[1081]: (CRON) STARTUP (fork ok)
Jan  9 13:16:39 Amilo-M7405 cron[1081]: (CRON) INFO (Running @reboot jobs)
Jan  9 13:16:39 Amilo-M7405 anacron[1070]: Normal exit (0 jobs run)
Jan  9 13:16:41 Amilo-M7405 acpid: 36 rules loaded
Jan  9 13:16:41 Amilo-M7405 acpid: waiting for events: event logging is off
Jan  9 13:16:41 Amilo-M7405 anacron[1180]: Anacron 2.3 started on 2011-01-09
Jan  9 13:16:41 Amilo-M7405 anacron[1180]: Normal exit (0 jobs run)
Jan  9 13:16:41 Amilo-M7405 polkitd[1128]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jan  9 13:16:43 Amilo-M7405 kernel: [   39.134148] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan  9 13:16:43 Amilo-M7405 init: plymouth-stop pre-start process (1245) terminated with status 1
Jan  9 13:16:43 Amilo-M7405 gdm-simple-greeter[1036]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Jan  9 13:16:44 Amilo-M7405 gdm-session-worker[1047]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  9 13:17:01 Amilo-M7405 CRON[1264]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  9 13:18:35 Amilo-M7405 gdm-session-worker[1047]: pam_sm_authenticate: Called
Jan  9 13:18:35 Amilo-M7405 gdm-session-worker[1047]: pam_sm_authenticate: username = [fab]
Jan  9 13:18:35 Amilo-M7405 gdm-session-worker[1268]: Passphrase file wrapped
Jan  9 13:18:38 Amilo-M7405 NetworkManager[673]: <error> [1294575518.941011] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  9 13:18:39 Amilo-M7405 NetworkManager[673]: <error> [1294575519.83528] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Successfully called chroot.
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Successfully dropped privileges.
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Successfully limited resources.
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Running.
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Watchdog thread running.
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Canary thread running.
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Successfully made thread 1390 of process 1390 (n/a) owned by '1000' high priority at nice level -11.
Jan  9 13:18:43 Amilo-M7405 rtkit-daemon[1392]: Supervising 1 threads of 1 processes of 1 users.
Jan  9 13:18:46 Amilo-M7405 rtkit-daemon[1392]: Successfully made thread 1406 of process 1390 (n/a) owned by '1000' RT at priority 5.
Jan  9 13:18:46 Amilo-M7405 rtkit-daemon[1392]: Supervising 2 threads of 1 processes of 1 users.
Jan  9 13:18:46 Amilo-M7405 rtkit-daemon[1392]: Successfully made thread 1407 of process 1390 (n/a) owned by '1000' RT at priority 5.
Jan  9 13:18:46 Amilo-M7405 rtkit-daemon[1392]: Supervising 3 threads of 1 processes of 1 users.
Jan  9 13:18:52 Amilo-M7405 pulseaudio[1390]: ratelimit.c: 2 events suppressed
Jan  9 13:20:29 Amilo-M7405 pulseaudio[1390]: ratelimit.c: 1 events suppressed
Jan  9 13:20:55 Amilo-M7405 sudo: pam_sm_authenticate: Called
Jan  9 13:20:55 Amilo-M7405 sudo: pam_sm_authenticate: username = [fab]
Jan  9 13:20:55 Amilo-M7405 sudo: pam_sm_authenticate: /home/fab is already mounted
Jan  9 14:16:23 Amilo-M7405 wpa_supplicant[805]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  9 14:16:23 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  completed -> disconnected
Jan  9 14:16:24 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jan  9 14:16:24 Amilo-M7405 wpa_supplicant[805]: Trying to associate with 00:17:9a:75:73:ce (SSID='DWL' freq=2412 MHz)
Jan  9 14:16:24 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  scanning -> associating
Jan  9 14:16:24 Amilo-M7405 wpa_supplicant[805]: Associated with 00:17:9a:75:73:ce
Jan  9 14:16:24 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  associating -> associated
Jan  9 14:16:24 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Jan  9 14:16:24 Amilo-M7405 wpa_supplicant[805]: WPA: Key negotiation completed with 00:xx:xx:xx:xx:xx [PTK=CCMP GTK=CCMP]
Jan  9 14:16:24 Amilo-M7405 wpa_supplicant[805]: CTRL-EVENT-CONNECTED - Connection to 00:xx:xx:xx:xx:xx completed (reauth) [id=0 id_str=]
Jan  9 14:16:24 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  4-way handshake -> group handshake
Jan  9 14:16:24 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  group handshake -> completed
Jan  9 14:16:32 Amilo-M7405 wpa_supplicant[805]: WPA: Group rekeying completed with 00:xx:xx:xx:xx:xx [GTK=CCMP]
Jan  9 14:16:32 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  completed -> group handshake
Jan  9 14:16:32 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  group handshake -> completed
Jan  9 14:17:01 Amilo-M7405 CRON[1755]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  9 14:30:01 Amilo-M7405 wpa_supplicant[805]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  9 14:30:01 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  completed -> disconnected
Jan  9 14:30:01 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jan  9 14:30:02 Amilo-M7405 wpa_supplicant[805]: Trying to associate with 00:xx:xx:xx:xx:xx (SSID='MySSID' freq=2412 MHz)
Jan  9 14:30:02 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  scanning -> associating
Jan  9 14:30:02 Amilo-M7405 wpa_supplicant[805]: Associated with 00:xx:xx:xx:xx:xx
Jan  9 14:30:02 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  associating -> associated
Jan  9 14:30:02 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Jan  9 14:30:02 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  4-way handshake -> group handshake
Jan  9 14:30:02 Amilo-M7405 wpa_supplicant[805]: WPA: Key negotiation completed with 00:xx:xx:xx:xx:xx [PTK=CCMP GTK=CCMP]
Jan  9 14:30:02 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  group handshake -> completed
Jan  9 14:30:02 Amilo-M7405 wpa_supplicant[805]: CTRL-EVENT-CONNECTED - Connection to 00:xx:xx:xx:xx:xx completed (reauth) [id=0 id_str=]
Jan  9 14:40:47 Amilo-M7405 wpa_supplicant[805]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  9 14:40:47 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  completed -> disconnected
Jan  9 14:40:47 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jan  9 14:40:47 Amilo-M7405 wpa_supplicant[805]: Trying to associate with 00:xx:xx:xx:xx:xx (SSID='MySSID' freq=2412 MHz)
Jan  9 14:40:47 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  scanning -> associating
Jan  9 14:40:47 Amilo-M7405 wpa_supplicant[805]: Associated with 00:xx:xx:xx:xx:xx
Jan  9 14:40:47 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  associating -> associated
Jan  9 14:40:47 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Jan  9 14:40:47 Amilo-M7405 wpa_supplicant[805]: WPA: Key negotiation completed with 00:xx:xx:xx:xx:xx [PTK=CCMP GTK=CCMP]
Jan  9 14:40:47 Amilo-M7405 wpa_supplicant[805]: CTRL-EVENT-CONNECTED - Connection to 00:xx:xx:xx:xx:xx completed (reauth) [id=0 id_str=]
Jan  9 14:40:47 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  4-way handshake -> group handshake
Jan  9 14:40:47 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  group handshake -> completed
Jan  9 15:16:32 Amilo-M7405 wpa_supplicant[805]: WPA: Group rekeying completed with 00:xx:xx:xx:xx:xx [GTK=CCMP]
Jan  9 15:16:32 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  completed -> group handshake
Jan  9 15:16:32 Amilo-M7405 NetworkManager[673]: <info> (eth1): supplicant connection state:  group handshake -> completed
Jan  9 15:17:01 Amilo-M7405 CRON[2013]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
[/PHP]

---

### Post by Byb on 2011-01-09
What else George? My wife, my credit card, my dog, a coffee maybe?..... ooops sorry I run in stock break
 :popcorn::popcorn::popcorn::popcorn: :popcorn::popcorn::popcorn::popcorn:
[COLOR=Red]**ufw.log**[/COLOR][PHP]empty[/PHP]**[COLOR=Red]user.log[/COLOR]**[PHP]Jan  9 12:18:05 Amilo-M7405 pulseaudio[1381]: ratelimit.c: 1 events suppressed
Jan  9 13:18:52 Amilo-M7405 pulseaudio[1390]: ratelimit.c: 2 events suppressed
Jan  9 13:20:29 Amilo-M7405 pulseaudio[1390]: ratelimit.c: 1 events suppressed
Jan  9 13:20:55 Amilo-M7405 sudo: pam_sm_authenticate: Called
Jan  9 13:20:55 Amilo-M7405 sudo: pam_sm_authenticate: username = [fab]
Jan  9 13:20:55 Amilo-M7405 sudo: pam_sm_authenticate: /home/fab is already mounted
[/PHP]

---

### Post by Byb on 2011-01-10
bump

---

### Post by Byb on 2011-01-23
Forum dead?
Linux community help was a myth?
Not even a link?
Not even a rtfm?

---

### Post by FreeMinded on 2011-01-23
Forum is still alive and Linux community help is still rocking. But this topic seems to have no general solution so far (you can find similar threads all over).
I hope 11.04 will finally bring working suspend back. Until a then I use hibernation which works well in my case.

Never give up! ;)

---

### Post by Byb on 2011-01-23
I can't do so as I use encrypted myhome and swap for basic security (as advised for a laptop)

---

### Post by Zundel on 2011-02-16
Check for a bios update (from manufacturers website).

But bios update did not fix it for me.

This tip:

[http://ubuntuforums.org/showpost.php?p=6105510&postcount=12](http://ubuntuforums.org/showpost.php?p=6105510&postcount=12)

seems to work for me. But I've not tested it extensively.

Give it a try.

---

### Post by Byb on 2011-02-17
Thank you for your interest Zundel

I forgot to say I already have the latest bios. My laptop is single core. I downgraded to the latest maverick kernel 2.6.35.11 for i386 and I don't know if I use xserver-xorg-video-intel (there are a lot of xserver-xorg-video-things installed on my laptop - I use gnome and my xorg.conf says device is "intel"). The xserver-xorg-video-intel installed is 2:2.12.0-1ubuntu5.1 . I've just seen there is a [COLOR=Blue][5.2]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.12.0-1ubuntu5.2")[/COLOR] proposed.
Do you advise me to install it? Is there something in my logs that would point to that?

---

### Post by akernan on 2011-02-21
The fix in post 33 seems to have fixed the problem for me.  I was able to close the lid on my laptop and suspend Ubuntu over night.  I was able to resume in the morning.  Before my laptop would not resume if left over night with the lid closed.  I have a Dell Inspiron 1564.

---

### Post by bcollignon on 2011-02-21
I have the same problem, but on a desktop.  I'm self-built, with the following: (rather lengthy)


Computer
********


Summary
-------

-Computer-
Processor		: 3x AMD Phenom(tm) 8450 Triple-Core Processor
Memory		: 7936MB (1225MB used)
Operating System		: Ubuntu 10.10
User Name		: 
Date/Time		: Mon 21 Feb 2011 02:17:43 PM EST
-Display-
Resolution		: 1680x1050 pixels
OpenGL Renderer		: GeForce 8300/PCI/SSE2
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: HDA-Intel - HDA NVidia
-Input Devices-
 Power Button
 Power Button
 AT Translated Set 2 keyboard
 Video Bus
 Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
 ViewSonic 1.3M, USB2.0 Webcam
-Printers (CUPS)-
HP-Color-LaserJet-2605		: <i>Default</i>
-SCSI Disks-
ATA WDC WD2000JB-00E
ATA ST31000520AS
HP DVD Writer 1170d
MICRONET FANTOM DRIVE

Operating System
----------------

-Version-
Kernel		: Linux 2.6.35-27-generic (x86_64)
Compiled		: #47-Ubuntu SMP Fri Feb 11 22:52:49 UTC 2011
C Library		: GNU C Library version 2.12.1 (stable)
Default C Compiler		: GNU C Compiler version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) 
Distribution		: Ubuntu 10.10
-Current Session-
Computer Name		: beethoven
User Name		: 
Home Directory		: /home
Desktop Environment		: GNOME 2.32.0
-Misc-
Uptime		: 8 minutes
Load Average		: 1.33, 1.64, 1.01

Kernel Modules
--------------

-Loaded Modules-
binfmt_misc
vboxnetadp		: Oracle VM VirtualBox Network Adapter Driver
vboxnetflt		: Oracle VM VirtualBox Network Filter Driver
vboxdrv		: Oracle VM VirtualBox Support Driver
parport_pc		: PC-style parallel port driver
ppdev
dm_crypt		: device-mapper target for transparent encryption / decryption
ip6table_filter		: ip6tables filter table
ip6_tables		: IPv6 packet filter
xt_limit		: Xtables: rate-limit match
ipt_LOG		: Xtables: IPv4 packet logging to syslog
xt_DSCP		: Xtables: DSCP/TOS field modification
nf_conntrack_irc		: IRC (DCC) connection tracking helper
nf_conntrack_ftp		: ftp connection tracking helper
ipt_MASQUERADE		: Xtables: automatic-address SNAT
xt_state		: ip[6]_tables connection tracking state match module
ipt_REJECT		: Xtables: packet &quot;rejection&quot; target for IPv4
xt_tcpudp		: Xtables: TCP, UDP and UDP-Lite match
snd_hda_codec_nvhdmi		: NVIDIA HDMI HD-audio codec
bridge
stp
snd_hda_codec_realtek		: Realtek HD-audio codec
iptable_nat
nf_nat
nf_conntrack_ipv4
nf_conntrack
nf_defrag_ipv4
iptable_mangle		: iptables mangle table
iptable_filter		: iptables filter table
ip_tables		: IPv4 packet filter
x_tables		: {ip,ip6,arp,eb}_tables backend module
nvidia
snd_hda_intel		: Intel HDA driver
snd_hda_codec		: HDA codec core
snd_hwdep		: Hardware dependent layer
snd_pcm		: Midlevel PCM code for ALSA.
snd_seq_midi		: Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi		: Midlevel RawMidi code for ALSA.
snd_seq_midi_event		: MIDI byte &lt;-&gt; sequencer event coder
snd_seq		: Advanced Linux Sound Architecture sequencer.
snd_timer		: ALSA timer interface
snd_seq_device		: ALSA sequencer device management
snd		: Advanced Linux Sound Architecture driver for soundcards.
arc4		: ARC4 Cipher Algorithm
rtl8180		: RTL8180 / RTL8185 PCI wireless driver
mac80211		: IEEE 802.11 subsystem
soundcore		: Core sound module
snd_page_alloc		: Memory allocator for ALSA system.
lp
i2c_nforce2		: nForce2/3/4/5xx SMBus driver
shpchp		: Standard Hot Plug PCI Controller Driver
eeprom_93cx6		: EEPROM 93cx6 chip driver
uvcvideo		: USB Video Class driver
k10temp		: AMD Family 10h/11h CPU core temperature monitor
edac_core		: Core library routines for EDAC reporting
videodev		: Device registrar for Video4Linux drivers v2
cfg80211		: wireless configuration support
v4l1_compat		: v4l(1) compatibility layer for v4l2 drivers.
v4l2_compat_ioctl32
edac_mce_amd		: AMD MCE decoder
parport
dm_raid45		: device-mapper raid4/5 target
xor
usb_storage		: USB Mass Storage driver for Linux
uvesafb		: Framebuffer driver for VBE2.0+ compliant graphics boards
usbhid		: USB HID core driver
hid
video		: ACPI Video Driver
output		: Display Output Switcher Lowlevel Control Abstraction
floppy
firewire_ohci		: Driver for PCI OHCI IEEE1394 controllers
firewire_core		: Core IEEE1394 transaction logic
ahci		: AHCI SATA low-level driver
crc_itu_t		: CRC ITU-T V.41 calculations
libahci		: Common AHCI SATA low-level routines
sky2		: Marvell Yukon 2 Gigabit Ethernet driver
pata_amd		: low-level driver for AMD and Nvidia PATA IDE

Boots
-----

-Boots-
Mon Feb 21 14:09		: 2.6.35-27-generi|-
Mon Feb 21 13:30		: 2.6.35-27-generi|-
Mon Feb 21 09:40		: 2.6.35-27-generi|-
Mon Feb 21 09:26		: 2.6.35-27-generi|-
Mon Feb 21 09:12		: 2.6.35-27-generi|-
Mon Feb 21 08:09		: 2.6.35-27-generi|-
Mon Feb 21 07:16		: 2.6.35-27-generi|-
Sun Feb 20 17:36		: 2.6.35-27-generi|-
Sun Feb 20 10:47		: 2.6.35-27-generi|-
Sat Feb 19 21:14		: 2.6.35-27-generi|-
Sat Feb 19 19:50		: 2.6.35-27-generi|-
Sat Feb 19 16:51		: 2.6.35-27-generi|-
Sat Feb 19 14:27		: 2.6.35-27-generi|-
Sat Feb 19 10:38		: 2.6.35-27-generi|-
Sat Feb 19 10:25		: 2.6.35-27-generi|-
Fri Feb 18 16:01		: 2.6.35-27-generi|-
Fri Feb 18 07:40		: 2.6.35-27-generi|-
Thu Feb 17 17:06		: 2.6.35-27-generi|-
Thu Feb 17 16:43		: 2.6.35-27-generi|-
Thu Feb 17 16:14		: 2.6.35-27-generi|-
Thu Feb 17 14:53		: 2.6.35-27-generi|-
Thu Feb 17 14:51		: 2.6.35-27-generi|-
Thu Feb 17 09:57		: 2.6.35-27-generi|-
Thu Feb 17 08:59		: 2.6.35-27-generi|-
Thu Feb 17 07:20		: 2.6.35-27-generi|-
Wed Feb 16 15:36		: 2.6.35-27-generi|-
Wed Feb 16 14:11		: 2.6.35-27-generi|-
Wed Feb 16 13:01		: 2.6.35-27-generi|-
Wed Feb 16 07:17		: 2.6.35-27-generi|-
Tue Feb 15 16:37		: 2.6.35-27-generi|-
Tue Feb 15 16:28		: 2.6.35-27-generi|-
Tue Feb 15 16:14		: 2.6.35-27-generi|-
Tue Feb 15 16:09		: 2.6.35-27-generi|-
Tue Feb 15 16:08		: 2.6.35-27-generi|-
Tue Feb 15 15:53		: 2.6.35-27-generi|-
Tue Feb 15 15:21		: 2.6.35-27-generi|-
Tue Feb 15 08:41		: 2.6.35-27-generi|-
Tue Feb 15 07:34		: 2.6.35-26-generi|-
Mon Feb 14 15:40		: 2.6.35-26-generi|-
Mon Feb 14 10:38		: 2.6.35-26-generi|-
Sun Feb 13 14:13		: 2.6.35-26-generi|-
Sun Feb 13 13:54		: 2.6.35-26-generi|-
Sun Feb 13 11:58		: 2.6.35-25-generi|-
Sun Feb 13 11:25		: 2.6.35-26-generi|-
Sun Feb 13 11:20		: 2.6.35-26-generi|-
Sun Feb 13 11:15		: 2.6.35-26-generi|-
Fri Feb 11 10:14		: 2.6.35-26-generi|-
Fri Feb 11 09:56		: 2.6.35-26-generi|-
Tue Feb 8 07:34		: 2.6.35-26-generi|-
Fri Feb 4 16:53		: 2.6.35-26-generi|-
Tue Feb 1 14:17		: 2.6.35-25-generi|-
Tue Feb 1 13:52		: 2.6.35-25-generi|-
Tue Feb 1 11:25		: 2.6.35-25-generi|-
Tue Feb 1 10:51		: 2.6.35-25-generi|-

Languages
---------

-Available Languages-
en_AG		: English language locale for Antigua and Barbuda
en_AG.utf8		: English language locale for Antigua and Barbuda
en_AU.utf8		: English locale for Australia
en_BW.utf8		: English locale for Botswana
en_CA.utf8		: English locale for Canada
en_DK.utf8		: English locale for Denmark
en_GB.utf8		: English locale for Britain
en_HK.utf8		: English locale for Hong Kong
en_IE.utf8		: English locale for Ireland
en_IN		: English language locale for India
en_IN.utf8		: English language locale for India
en_NG		: English locale for Nigeria
en_NG.utf8		: English locale for Nigeria
en_NZ.utf8		: English locale for New Zealand
en_PH.utf8		: English language locale for Philippines
en_SG.utf8		: English language locale for Singapore
en_US.utf8		: English locale for the USA
en_ZA.utf8		: English locale for South Africa

Filesystems
-----------

-Mounted File Systems-
/dev/sdc2	/	47.10 % (224.5 GiB of 424.4 GiB)	
none	/dev	0.01 % (3.7 GiB of 3.7 GiB)	
none	/dev/shm	0.01 % (3.8 GiB of 3.8 GiB)	
none	/var/run	0.01 % (3.8 GiB of 3.8 GiB)	
none	/var/lock	0.00 % (3.8 GiB of 3.8 GiB)	
/dev/sdc2	/media/usb0	96.83 % (5.6 GiB of 176.9 GiB)	

Display
-------

-Display-
Resolution		: 1680x1050 pixels
Vendor		: The X.Org Foundation
Version		: 1.9.0
-Monitors-
Monitor 0		: 1680x1050 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
GestureExtension
MIT-SCREEN-SAVER
MIT-SHM
NV-CONTROL
NV-GLX
RANDR
RECORD
RENDER
SECURITY
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
XVideo-MotionCompensation
-OpenGL-
Vendor		: NVIDIA Corporation
Renderer		: GeForce 8300/PCI/SSE2
Version		: 3.3.0 NVIDIA 260.19.06
Direct Rendering		: Yes

Environment Variables
---------------------

-Environment Variables-
GDM_KEYBOARD_LAYOUT		: us
GNOME_KEYRING_PID		: 4747
USER		: bill
HOME		: /home/bill
XDG_SESSION_COOKIE		: 3f78b581c6a784f6d244ec8d4be18ce3-1298315393.905341-486039143
DESKTOP_SESSION		: gnome
GTK_MODULES		: canberra-gtk-module
GNOME_KEYRING_CONTROL		: /tmp/keyring-usAS96
MANDATORY_PATH		: /usr/share/gconf/gnome.mandatory.path
LOGNAME		: bill
DEFAULTS_PATH		: /usr/share/gconf/gnome.default.path
USERNAME		: bill
WINDOWPATH		: 7
GDM_LANG		: en_US.utf8
PATH		: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DISPLAY		: :0.0
LANG		: en_US.utf8
XAUTHORITY		: /var/run/gdm/auth-for-bill-1EfOlQ/database
SHELL		: /bin/bash
GDMSESSION		: gnome
SPEECHD_PORT		: 7560
PWD		: /home/bill
XDG_CONFIG_DIRS		: /etc/xdg/xdg-gnome:/etc/xdg
XDG_DATA_DIRS		: /usr/share/gnome:/usr/local/share/:/usr/share/
SSH_AUTH_SOCK		: /tmp/keyring-usAS96/ssh
SSH_AGENT_PID		: 4859
DBUS_SESSION_BUS_ADDRESS		: unix:abstract=/tmp/dbus-9KLlIqDzLU,guid=b041937d15b72f0a1d9bd8050000003b
GNOME_DESKTOP_SESSION_ID		: this-is-deprecated
SESSION_MANAGER		: local/beethoven:@/tmp/.ICE-unix/4768,unix/beethoven:/tmp/.ICE-unix/4768
ORBIT_SOCKETDIR		: /tmp/orbit-bill

Users
-----

-Users-
root		: root
daemon		: daemon
bin		: bin
sys		: sys
sync		: sync
games		: games
man		: man
lp		: lp
mail		: mail
news		: news
uucp		: uucp
proxy		: proxy
www-data		: www-data
backup		: backup
list		: Mailing List Manager
irc		: ircd
gnats		: Gnats Bug-Reporting System (admin)
nobody		: nobody
libuuid
syslog
messagebus
avahi-autoipd		: Avahi autoip daemon
avahi		: Avahi mDNS daemon
couchdb		: CouchDB Administrator
speech-dispatcher		: Speech Dispatcher
usbmux		: usbmux daemon
haldaemon		: Hardware abstraction layer
kernoops		: Kernel Oops Tracking Daemon
pulse		: PulseAudio daemon
rtkit		: RealtimeKit
saned
hplip		: HPLIP system user
gdm		: Gnome Display Manager
bill		: 
sshd
xrdp
cbstx		: CBSTX
timidity		: TiMidity++ MIDI sequencer service
will		: William C. 
sabayon-admin
stunnel4
clamav
alice		: Alice C. 
smmta		: Mail Transfer Agent
smmsp		: Mail Submission Program
Debian-exim
libvirt-qemu		: Libvirt Qemu
snort		: Snort IDS
jean		: Jean M 
backuppc		: BackupPC
mysql		: MySQL Server
kdm

Devices
*******


Processor
---------

-Processors-
AMD Phenom(tm) 8450 Triple-Core Processor		: 1050.00MHz
AMD Phenom(tm) 8450 Triple-Core Processor		: 2100.00MHz
AMD Phenom(tm) 8450 Triple-Core Processor		: 1050.00MHz

Memory
------

-Memory-
Total Memory		: 7936216 kB
Free Memory		: 6097544 kB
Buffers		: 143560 kB
Cached		: 613244 kB
Cached Swap		: 0 kB
Active		: 916004 kB
Inactive		: 464464 kB
Active(anon)		: 624096 kB
Inactive(anon)		: 4784 kB
Active(file)		: 291908 kB
Inactive(file)		: 459680 kB
Unevictable		: 32 kB
Mlocked		: 32 kB
Virtual Memory		: 12645372 kB
Free Virtual Memory		: 12645372 kB
Dirty		: 92 kB
Writeback		: 0 kB
AnonPages		: 623764 kB
Mapped		: 157740 kB
Shmem		: 5224 kB
Slab		: 182728 kB
SReclaimable		: 154244 kB
SUnreclaim		: 28484 kB
KernelStack		: 3096 kB
PageTables		: 32648 kB
NFS_Unstable		: 0 kB
Bounce		: 0 kB
WritebackTmp		: 0 kB
CommitLimit		: 16613480 kB
Committed_AS		: 2091380 kB
VmallocTotal		: 34359738367 kB
VmallocUsed		: 363844 kB
VmallocChunk		: 34359358460 kB
HardwareCorrupted		: 0 kB
HugePages_Total		: 0
HugePages_Free		: 0
HugePages_Rsvd		: 0
HugePages_Surp		: 0
Hugepagesize		: 2048 kB
DirectMap4k		: 77440 kB
DirectMap2M		: 3854336 kB
DirectMap1G		: 4194304 kB

PCI Devices
-----------

-PCI Devices-
RAM memory		: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
ISA bridge		: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
SMBus		: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
RAM memory		: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
Co-processor		: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
RAM memory		: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
USB Controller		: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10 [OHCI])
USB Controller		: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20 [EHCI])
USB Controller		: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10 [OHCI])
USB Controller		: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20 [EHCI])
IDE interface		: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
Audio device		: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
PCI bridge		: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 01 [Subtractive decode])
IDE interface		: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
PCI bridge		: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
PCI bridge		: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
PCI bridge		: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
PCI bridge		: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 00 [Normal decode])
PCI bridge		: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 00 [Normal decode])
Host bridge		: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
Host bridge		: Advanced Micro Devices [AMD] Family 10h Processor Address Map
Host bridge		: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
Host bridge		: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
Host bridge		: Advanced Micro Devices [AMD] Family 10h Processor Link Control
Ethernet controller		: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
FireWire (IEEE 1394)		: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46) (prog-if 10 [OHCI])
VGA compatible controller		: nVidia Corporation C77 [nForce 750a SLI] (rev a2) (prog-if 00 [VGA controller])
Ethernet controller		: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)

USB Devices
-----------


Printers
--------

-Printers (CUPS)-
HP-Color-LaserJet-2605		: <i>Default</i>

Battery
-------

-No batteries-
No batteries found on this system

Sensors
-------


Input Devices
-------------

-Input Devices-
 Power Button
 Power Button
 AT Translated Set 2 keyboard
 Video Bus
 Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
 ViewSonic 1.3M, USB2.0 Webcam

Storage
-------

-SCSI Disks-
ATA WDC WD2000JB-00E
ATA ST31000520AS
HP DVD Writer 1170d
MICRONET FANTOM DRIVE

DMI
---

-BIOS-
Date		: 01/05/2009
Vendor		: American Megatrends Inc. ([www.ami.com](www.ami.com))
Version		: 080015
-Board-
Name		: MD-A72P-7509
Vendor		: XFX

Resources
---------

-I/O Ports-
<tt>0000-0cf7 </tt>		: PCI Bus 0000:00
<tt>  0000-001f </tt>		: dma1
<tt>  0020-0021 </tt>		: pic1
<tt>  0040-0043 </tt>		: timer0
<tt>  0050-0053 </tt>		: timer1
<tt>  0060-0060 </tt>		: keyboard
<tt>  0064-0064 </tt>		: keyboard
<tt>  0070-0071 </tt>		: rtc0
<tt>  0080-008f </tt>		: dma page reg
<tt>  00a0-00a1 </tt>		: pic2
<tt>  00c0-00df </tt>		: dma2
<tt>  00f0-00ff </tt>		: fpu
<tt>  0170-0177 </tt>		: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
<tt>    0170-0177 </tt>		: low-level driver for AMD and Nvidia PATA IDE
<tt>  01f0-01f7 </tt>		: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
<tt>    01f0-01f7 </tt>		: low-level driver for AMD and Nvidia PATA IDE
<tt>  0376-0376 </tt>		: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
<tt>    0376-0376 </tt>		: low-level driver for AMD and Nvidia PATA IDE
<tt>  03c0-03df </tt>		: vga+
<tt>    03c0-03df </tt>		: Framebuffer driver for VBE2.0+ compliant graphics boards
<tt>  03f2-03f2 </tt>		: floppy
<tt>  03f4-03f5 </tt>		: floppy
<tt>  03f6-03f6 </tt>		: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
<tt>    03f6-03f6 </tt>		: low-level driver for AMD and Nvidia PATA IDE
<tt>  03f7-03f7 </tt>		: floppy
<tt>  03f8-03ff </tt>		: serial
<tt>  04d0-04d1 </tt>		: pnp 00:06
<tt>  0800-080f </tt>		: pnp 00:06
<tt>  0a00-0a0f </tt>		: pnp 00:0b
<tt>  0a10-0a1f </tt>		: pnp 00:0b
<tt>0cf8-0cff </tt>		: PCI conf1
<tt>0d00-ffff </tt>		: PCI Bus 0000:00
<tt>  2000-207f </tt>		: pnp 00:06
<tt>    2000-2003 </tt>		: ACPI PM1a_EVT_BLK
<tt>    2004-2005 </tt>		: ACPI PM1a_CNT_BLK
<tt>    2008-200b </tt>		: ACPI PM_TMR
<tt>    2010-2015 </tt>		: ACPI CPU throttle
<tt>    2020-2027 </tt>		: ACPI GPE0_BLK
<tt>  2080-20ff </tt>		: pnp 00:06
<tt>  2400-247f </tt>		: pnp 00:06
<tt>  2480-24ff </tt>		: pnp 00:06
<tt>    24a0-24af </tt>		: ACPI GPE1_BLK
<tt>  2800-287f </tt>		: pnp 00:06
<tt>  2880-28ff </tt>		: pnp 00:06
<tt>  2900-293f </tt>		: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
<tt>  2d00-2d3f </tt>		: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
<tt>    2d00-2d3f </tt>		: nForce2_smbus
<tt>  2e00-2e3f </tt>		: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
<tt>  2f00-2fff </tt>		: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
<tt>  a800-a80f </tt>		: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
<tt>    a800-a80f </tt>		: AHCI SATA low-level driver
<tt>  a880-a883 </tt>		: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
<tt>    a880-a883 </tt>		: AHCI SATA low-level driver
<tt>  ac00-ac07 </tt>		: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
<tt>    ac00-ac07 </tt>		: AHCI SATA low-level driver
<tt>  b000-b003 </tt>		: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
<tt>    b000-b003 </tt>		: AHCI SATA low-level driver
<tt>  b080-b087 </tt>		: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
<tt>    b080-b087 </tt>		: AHCI SATA low-level driver
<tt>  c000-cfff </tt>		: PCI Bus 0000:01
<tt>    c800-c8ff </tt>		: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
<tt>      c800-c8ff </tt>		: RTL8180 / RTL8185 PCI wireless driver
<tt>    cc00-cc7f </tt>		: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46) (prog-if 10 [OHCI])
<tt>  d000-dfff </tt>		: PCI Bus 0000:02
<tt>    dc00-dc7f </tt>		: nVidia Corporation C77 [nForce 750a SLI] (rev a2) (prog-if 00 [VGA controller])
<tt>  e000-efff </tt>		: PCI Bus 0000:05
<tt>    e800-e8ff </tt>		: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)
<tt>      e800-e8ff </tt>		: Marvell Yukon 2 Gigabit Ethernet driver
<tt>  ffa0-ffaf </tt>		: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
<tt>    ffa0-ffaf </tt>		: low-level driver for AMD and Nvidia PATA IDE
-Memory-
<tt>00000000-0000ffff </tt>		: reserved
<tt>00010000-0009efff </tt>		: System RAM
<tt>0009f000-0009ffff </tt>		: reserved
<tt>000a0000-000bffff </tt>		: PCI Bus 0000:00
<tt>000c0000-000cffff </tt>		: pnp 00:0d
<tt>000d0000-000dffff </tt>		: PCI Bus 0000:00
<tt>  000d0000-000d3fff </tt>		: pnp 00:06
<tt>  000d4000-000d7fff </tt>		: pnp 00:06
<tt>  000de000-000dffff </tt>		: pnp 00:06
<tt>000e0000-000fffff </tt>		: reserved
<tt>00100000-cff9ffff </tt>		: System RAM
<tt>  01000000-01595242 </tt>		: Kernel code
<tt>  01595243-01ad4f6f </tt>		: Kernel data
<tt>  01bc1000-01d18113 </tt>		: Kernel bss
<tt>  20000000-23ffffff </tt>		: GART
<tt>cffa0000-cffafffe </tt>		: ACPI Tables
<tt>cffaffff-cffdffff </tt>		: ACPI Non-volatile Storage
<tt>cffe0000-cfffffff </tt>		: reserved
<tt>e0000000-efffffff </tt>		: PCI MMCONFIG 0000 [bus 00-ff]
<tt>  e0000000-efffffff </tt>		: pnp 00:0c
<tt>f0000000-febfffff </tt>		: PCI Bus 0000:00
<tt>  f0000000-fbffffff </tt>		: PCI Bus 0000:02
<tt>    f0000000-f7ffffff </tt>		: nVidia Corporation C77 [nForce 750a SLI] (rev a2) (prog-if 00 [VGA controller])
<tt>    fa000000-fbffffff </tt>		: nVidia Corporation C77 [nForce 750a SLI] (rev a2) (prog-if 00 [VGA controller])
<tt>      fb000000-fbd754ff </tt>		: Framebuffer driver for VBE2.0+ compliant graphics boards
<tt>  fce76000-fce77fff </tt>		: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
<tt>    fce76000-fce77fff </tt>		: AHCI SATA low-level driver
<tt>  fce78000-fce7bfff </tt>		: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
<tt>    fce78000-fce7bfff </tt>		: ICH HD audio
<tt>  fce7d000-fce7dfff </tt>		: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10 [OHCI])
<tt>    fce7d000-fce7dfff </tt>		: ohci_hcd
<tt>  fce7e800-fce7e8ff </tt>		: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20 [EHCI])
<tt>    fce7e800-fce7e8ff </tt>		: ehci_hcd
<tt>  fce7ec00-fce7ecff </tt>		: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20 [EHCI])
<tt>    fce7ec00-fce7ecff </tt>		: ehci_hcd
<tt>  fce7f000-fce7ffff </tt>		: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10 [OHCI])
<tt>    fce7f000-fce7ffff </tt>		: ohci_hcd
<tt>  fce80000-fcefffff </tt>		: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
<tt>  fcf00000-fcffffff </tt>		: PCI Bus 0000:01
<tt>    fcfff000-fcfff7ff </tt>		: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46) (prog-if 10 [OHCI])
<tt>      fcfff000-fcfff7ff </tt>		: Driver for PCI OHCI IEEE1394 controllers
<tt>    fcfffc00-fcfffcff </tt>		: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
<tt>      fcfffc00-fcfffcff </tt>		: RTL8180 / RTL8185 PCI wireless driver
<tt>  fd000000-feafffff </tt>		: PCI Bus 0000:02
<tt>    fd000000-fdffffff </tt>		: nVidia Corporation C77 [nForce 750a SLI] (rev a2) (prog-if 00 [VGA controller])
<tt>      fd000000-fdffffff </tt>		: nvidia
<tt>    feae0000-feafffff </tt>		: nVidia Corporation C77 [nForce 750a SLI] (rev a2) (prog-if 00 [VGA controller])
<tt>  feb00000-febfffff </tt>		: PCI Bus 0000:05
<tt>    febc0000-febdffff </tt>		: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)
<tt>    febfc000-febfffff </tt>		: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)
<tt>      febfc000-febfffff </tt>		: Marvell Yukon 2 Gigabit Ethernet driver
<tt>fec00000-fec00fff </tt>		: reserved
<tt>  fec00000-fec003ff </tt>		: IOAPIC 0
<tt>fed00000-fed003ff </tt>		: HPET 0
<tt>fed04000-fed04fff </tt>		: pnp 00:06
<tt>fee00000-feefffff </tt>		: reserved
<tt>  fee00000-fee00fff </tt>		: Local APIC
<tt>    fee00000-fee00fff </tt>		: pnp 00:09
<tt>  fee01000-feefffff </tt>		: pnp 00:06
<tt>ff700000-ffffffff </tt>		: reserved
<tt>100000000-21fffffff </tt>		: System RAM
-DMA-
<tt> 2</tt>		: floppy
<tt> 4</tt>		: cascade

Network
*******


Interfaces
----------

-Network Interfaces-
lo	0.00MiB	0.00MiB	127.0.0.1	
eth0	3.79MiB	0.72MiB	192.168.1.11	
wlan0	0.00MiB	0.00MiB		
virbr0	0.00MiB	0.01MiB	192.168.122.1	
vboxnet0	0.00MiB	0.00MiB		

IP Connections
--------------

-Connections-
0.0.0.0:8010	LISTEN	0.0.0.0:*	tcp	
127.0.0.1:3306	LISTEN	0.0.0.0:*	tcp	
127.0.0.1:587	LISTEN	0.0.0.0:*	tcp	
0.0.0.0:80	LISTEN	0.0.0.0:*	tcp	
192.168.122.1:53		0.0.0.0:*	udp	
127.0.0.1:3350	LISTEN	0.0.0.0:*	tcp	
0.0.0.0:22	LISTEN	0.0.0.0:*	tcp	
0.0.0.0:631		0.0.0.0:*	udp	
127.0.0.1:25	LISTEN	0.0.0.0:*	tcp	
0.0.0.0:3389	LISTEN	0.0.0.0:*	tcp	
0.0.0.0:6881		0.0.0.0:*	udp	
0.0.0.0:9192	LISTEN	0.0.0.0:*	tcp	
192.168.1.11:39247	ESTABLISHED	74.125.115.109:993	tcp	
192.168.1.11:40191	ESTABLISHED	205.188.254.89:5190	tcp	
192.168.1.11:58971	ESTABLISHED	64.12.29.117:5190	tcp	
192.168.1.11:40398	ESTABLISHED	69.63.181.105:5222	tcp	
192.168.1.11:38671	ESTABLISHED	98.136.48.70:5050	tcp	
192.168.1.11:39248	ESTABLISHED	74.125.115.109:993	tcp	
192.168.1.11:56142	TIME_WAIT	74.125.226.132:80	tcp	
192.168.1.11:39914	ESTABLISHED	64.12.26.245:5190	tcp	
192.168.1.11:35415	ESTABLISHED	174.129.241.144:443	tcp	
192.168.1.11:54762	TIME_WAIT	74.125.113.102:80	tcp	
:::139	LISTEN	:::*	tcp6	
:::22	LISTEN	:::*	tcp6	
:::631	LISTEN	:::*	tcp6	
:::445	LISTEN	:::*	tcp6	
:::6881	LISTEN	:::*	tcp6	
0.0.0.0:52438		0.0.0.0:*	udp	
192.168.122.1:40470		0.0.0.0:*	udp	
0.0.0.0:44651		0.0.0.0:*	udp	
127.0.0.1:8010		0.0.0.0:*	udp	
192.168.122.1:53		0.0.0.0:*	udp	
0.0.0.0:67		0.0.0.0:*	udp	
0.0.0.0:68		0.0.0.0:*	udp	
192.168.1.255:137		0.0.0.0:*	udp	
192.168.1.11:137		0.0.0.0:*	udp	
192.168.122.255:137		0.0.0.0:*	udp	
192.168.122.1:137		0.0.0.0:*	udp	
0.0.0.0:137		0.0.0.0:*	udp	
192.168.1.255:138		0.0.0.0:*	udp	
192.168.1.11:138		0.0.0.0:*	udp	
192.168.122.255:138		0.0.0.0:*	udp	
192.168.122.1:138		0.0.0.0:*	udp	
0.0.0.0:138		0.0.0.0:*	udp	
127.0.0.1:41379		0.0.0.0:*	udp	
0.0.0.0:631		0.0.0.0:*	udp	
192.168.1.11:53943		0.0.0.0:*	udp	
0.0.0.0:5353		0.0.0.0:*	udp	
0.0.0.0:34740		0.0.0.0:*	udp	
192.168.122.1:6771		0.0.0.0:*	udp	
192.168.1.11:6771		0.0.0.0:*	udp	
127.0.0.1:6771		0.0.0.0:*	udp	
0.0.0.0:6771		0.0.0.0:*	udp	
0.0.0.0:6881		0.0.0.0:*	udp	
:::49994		:::*	udp6	
:::5353		:::*	udp6	
:::43560		:::*	udp6	

Routing Table
-------------

-IP routing table-
192.168.1.0 / 0.0.0.0	255.255.255.0	U	eth0	
192.168.122.0 / 0.0.0.0	255.255.255.0	U	virbr0	
169.254.0.0 / 0.0.0.0	255.255.0.0	U	eth0	
0.0.0.0 / 192.168.1.1	0.0.0.0	UG	eth0	

ARP Table
---------

-ARP Table-
192.168.1.1	30:46:9a:4e:04:ce	eth0	

DNS Servers
-----------

-Name servers-
208.67.222.222
208.67.220.220

Statistics
----------

-IP-
5124		: Total packets received
1		: With invalid addresses
0		: Incoming packets discarded
0		: Incoming packets discarded
4814		: Incoming packets delivered
4772		: Requests sent out
25		: Outgoing packets dropped
10		: Dropped because of missing route
-ICMP-
0		: ICMP messages failed
0		: ICMP messages failed
0		: ICMP messages failed
0		: ICMP messages failed
-TCP-
137		: Active connections openings
0		: Bad segments received.
13		: Failed connection attempts
5		: Connection resets received
8		: Connections established
3393		: Segments received
2874		: Segments send out
4		: Segments retransmited
0		: Bad segments received.
164		: Resets sent
-UDP-
1430		: Packets received
0		: Packet receive errors
0		: Packet receive errors
1980		: Packets sent
-UDPLITE-
-TCPEXT-
33		: TCP sockets finished time wait in fast timer
99		: Delayed acks sent
39		: Packets directly queued to recvmsg prequeue.
30		: Bytes directly received in process context from prequeue
2230		: Packet headers predicted
219		: Acknowledgments not containing data payload received
232		: Predicted acknowledgments
2		: Congestion windows recovered without slow start after partial ack
4		: Other TCP timeouts
28		: Connections reset due to unexpected data
3		: Connections reset due to early user close
-IPEXT-

Shared Directories
------------------

-SAMBA-
-NFS-

Benchmarks
**********


CPU Blowfish
------------

-CPU Blowfish-
<big><b>This Machine</b></big>	1050 MHz	9.711	
2x Intel(R) Core(TM)2 CPU E8400@ 3.00GHz	3000 MHz	5.826	
3x AMD Phenom(tm) II X4 B55 Processor	800 MHz	3.712	
2x AMD Turion Dual-Core ZM-80	500 MHz	10.113	
8x Intel(R) Xeon(R) CPU E5335@ 2.00GHz	1994 MHz	2.147	
Intel(R) Core(TM)2 QuadCPU Q9300@ 2.50GHz	2490 MHz	15.247	
Intel(R) Pentium(R) 4 CPU 2.40GHz	2400 MHz	28.295	
PowerPC 7455, altivec supported (667.00MHz)	667 MHz	110.997	
Intel(R) Xeon(R) CPU E5520@ 2.27GHz	2260 MHz	13.218	
AMD Athlon(tm) XP	906 MHz	27.902	
AMD Phenom(tm) II X4 B50 Processor	800 MHz	11.535	
4x Intel(R) Core(TM)2 Quad CPU @ 2.93GHz	1603 MHz	2.817	
4x Intel(R) Xeon(R) CPU X3210@ 2.13GHz	2133 MHz	3.883	
16x Intel(R) Xeon(R) CPU E5530@ 2.40GHz	1600 MHz	1.390	
Intel(R) Xeon(TM) CPU 2.80GHz	2793 MHz	21.438	
Mobile AMD Sempron(tm) Processor 3400+	800 MHz	23.324	
2x AMD Athlon(tm) Dual Core Processor 5050e	2600 MHz	7.391	
2x AMD Athlon(TM) MP 2800+	2152 MHz	8.469	
Intel(R) Celeron(R) CPU560@ 2.13GHz	2128 MHz	18.709	
3x AMD Athlon(tm) II X3 400e Processor	800 MHz	6.473	
Intel(R) Pentium(R) 4 CPU 1.60GHz	1595 MHz	37.012	
8x Intel(R) Core(TM) i7 CPU 960@ 3.20GHz	3201 MHz	2.003	
2x AMD Turion(tm) II Dual-Core Mobile M500	1500 MHz	10.689	
2x Intel(R) Core(TM) i7 CPU 930@ 2.80GHz	2806 MHz	8.070	
AMD Athlon(tm) 64 Processor 3700+	1000 MHz	19.016	
4x AMD Phenom(tm) II N930 Quad-Core Processor	800 MHz	4.986	
AMD Sempron(tm) Processor 140 Processor	2713 MHz	15.204	
mobile AMD Athlon(tm) XP 2600+	1662 MHz	20.237	
4x Intel(R) Atom(TM) CPU D510 @ 1.66GHz	1667 MHz	8.336	
2x Quad-Core AMD Opteron(tm) Processor 8346 HE	1800 MHz	34.820	
12x Intel(R) Core(TM) i7 CPU X 980@ 3.33GHz	3334 MHz	1.238	
AMD Athlon(tm) 64 X2 Dual Core Processor 4400+	2300 MHz	17.847	
2x Intel(R) Core(TM)2 Duo CPU E8400@ 3.00GHz	2997 MHz	6.276	
Intel(R) Core(TM)2 CPU T5600@ 1.83GHz	1819 MHz	21.763	
3x AMD Processor model unknown	2812 MHz	5.933	
Pentium(R) Dual-CoreCPUE6500@ 2.93GHz	2933 MHz	12.963	
AMD Sempron(tm) Processor LE-1100	1908 MHz	20.762	
4x AMD Phenom(tm) II X4 B35 Processor	800 MHz	3.317	
2x Intel(R) Core(TM)2 Duo CPU L7500@ 1.60GHz	800 MHz	10.860	
2x Intel(R) Core(TM)2 Duo CPU T5470@ 1.60GHz	800 MHz	11.737	
2x AMD Phenom(tm) 9750 Quad-Core Processor	2411 MHz	10.010	
2x AMD Athlon(tm) Neo X2 Dual Core Processor L325	1500 MHz	15.456	
2x AMD Athlon(tm) 64 X2 Dual Core Processor 4200+	2200 MHz	9.421	
4x QEMU Virtual CPU version 0.12.3	2600 MHz	4.001	
AMD Athlon(TM) XP1700+	1477 MHz	33.429	
2x AMD Turion(tm) 64 X2 TL-60	800 MHz	9.704	
4x Intel(R) Xeon(R) CPU5110@ 1.60GHz	1600 MHz	5.695	
Intel(R) Celeron(TM) CPU1133MHz	1133 MHz	30.195	
Intel(R) Pentium(R) M processor 2.00GHz	800 MHz	19.526	
3x AMD Phenom(tm) II X4 B25 Processor	800 MHz	5.014	
PowerPC 7447A, altivec supported (1199,00MHz)	1199 MHz	55.119	

CPU CryptoHash
--------------

-CPU CryptoHash-
<big><b>This Machine</b></big>	1050 MHz	160.795	
AMD Athlon(tm)X2 DualCore QL-66	2199 MHz	73.730	
Intel(R) Pentium(R) 4 CPU 2.40GHz	2400 MHz	33.048	
4x Intel(R) Xeon(R) CPU5130@ 2.00GHz	1995 MHz	163.272	
4x AMD Athlon(tm) II X4 620 Processor	800 MHz	343.159	
2x AMD Turion(tm)X2 Ultra DualCore Mobile ZM-86	600 MHz	145.530	
8x Intel(R) Xeon(R) CPU E5405@ 2.00GHz	2000 MHz	319.166	
8x Intel(R) Core(TM) i7 CPU 880@ 3.07GHz	1200 MHz	534.361	
mobile AMD Athlon (tm) 2400+	1192 MHz	42.536	
2x Intel(R) Core(TM)2 CPU E7400@ 2.80GHz	2800 MHz	154.330	
AMD Athlon(tm) II X4 630 Processor	2765 MHz	93.469	
2x Intel(R) Core(TM)2 Duo CPU L9600@ 2.13GHz	2128 MHz	146.564	
Intel(R) Core(TM)2 CPU T5500@ 1.66GHz	1663 MHz	53.691	
Intel(R) Celeron(R) D CPU430@ 1.80GHz	1795 MHz	71.959	
AMD Phenom(tm) II X4 20 Processor	2800 MHz	93.492	
2x Genuine Intel(R) CPU U7300@ 1.30GHz	800 MHz	107.032	
AMD Turion(tm) 64 Mobile Technology ML-37	2000 MHz	60.043	
2x Intel(R) Core(TM)2 Extreme CPU X9100@ 3.06GHz	3059 MHz	130.311	
4x Intel(R) Core(TM) i5 CPU U 430@ 1.20GHz	666 MHz	130.074	
Intel(R) Pentium(R) 4 CPU 1.80GHz	1793 MHz	24.153	
4x Intel(R) Core(TM) i3 CPU M 330@ 2.13GHz	933 MHz	185.807	
2x AMD Turion(tm) II Ultra Dual-Core Mobile M600	2394 MHz	142.027	
8x Intel(R) Xeon(R) CPU E5462@ 2.80GHz	2400 MHz	438.856	
Mobile AMD Athlon(tm) XP 3000+	796 MHz	73.180	
2x Intel(R) Core(TM)2 Duo CPU T5870@ 2.00GHz	800 MHz	137.656	
Mobile Intel(R) Pentium(R) III CPU - M1200MHz	798 MHz	42.472	
2x AMD Athlon(tm) X2 Dual Core Processor BE-2400	2305 MHz	114.074	
3x AMD Athlon(tm) II X3 440 Processor	800 MHz	300.933	
2x AMD Turion(tm) II Ultra Dual-Core Mobile M640	800 MHz	168.257	
4x Intel(R) Atom(TM) CPU N550 @ 1.50GHz	1000 MHz	96.765	
3x AMD Athlon(tm) II X3 445 Processor	3115 MHz	313.132	
4x Intel(R) Core(TM)2 Extreme CPU X9770@ 3.20GHz	2403 MHz	455.964	
Intel(R) Pentium(R) D CPU 3.00GHz	3000 MHz	44.463	
Mobile Intel(R) Pentium(R) 4 CPU 2.30GHz	1600 MHz	27.748	
AMD Turion(tm) 64 Mobile ML-30	800 MHz	25.497	
2x Intel(R) Pentium(R)CPU E6500@ 2.93GHz	2932 MHz	121.046	
AMD Phenom(tm) II X4 945 Processor	2947 MHz	113.383	
2x Intel(R) Pentium(R) DualCPUT2310@ 1.46GHz	1463 MHz	91.247	
2x Intel(R) Core(TM)2 Duo CPU T6400@ 2.00GHz	1200 MHz	140.312	
Intel(R) Celeron(R) D CPU 3.06GHz	3067 MHz	53.712	
AMD Sempron(tm)	1663 MHz	55.622	
AMD Athlon(tm) XP 1600	1400 MHz	42.170	
2x AMD Athlon(tm) 64 X2 Dual Core Processor 3800+	2200 MHz	116.812	
2x Intel(R) Core(TM)2 Duo CPU E7300@ 2.66GHz	1600 MHz	190.853	
4x Intel(R) XEON(TM) CPU 2.20GHz	2181 MHz	90.292	
8x Intel(R) Core(TM) i7 CPU 940@ 2.93GHz	1600 MHz	442.497	
2x Intel(R) Xeon(R) CPU3065@ 2.33GHz	3500 MHz	191.399	
AMD Athlon(tm)2200+	1800 MHz	54.759	
2x Intel(R) Core(TM)2 Duo CPU P8400@ 2.26GHz	800 MHz	151.935	
Intel(R) Pentium(R) M processor 1600MHz	1600 MHz	52.018	
AMD Athlon(tm) XP 2100+	1746 MHz	50.098	

CPU Fibonacci
-------------

-CPU Fibonacci-
<big><b>This Machine</b></big>	1050 MHz	3.254	
3x AMD Phenom(tm) II X4 20 Processor	800 MHz	2.351	
4x Intel(R) Xeon(R) CPU X3350@ 2.66GHz	2666 MHz	2.843	
2x Intel(R) Core(TM)2 Duo CPU P7700@ 1.80GHz	1800 MHz	5.374	
2x Intel(R) Core(TM)2 Duo CPU P8800@ 2.66GHz	1596 MHz	3.118	
2x Intel(R) Atom(TM) CPU330 @ 1.60GHz	1595 MHz	8.312	
2x Intel(R) Core(TM)2 CPU E7400@ 2.80GHz	2800 MHz	3.866	
2x AMD Turion(tm) 64 X2 TL-62	800 MHz	4.167	
2x Intel(R) Core(TM)2 Duo CPU U7600@ 1.20GHz	800 MHz	7.715	
8x Intel(R) Core(TM) i7 CPU 930@ 2.80GHz	2834 MHz	2.366	
Intel(R) Pentium(R) M processor 2.10GHz	2100 MHz	17.899	
mobile AMD Athlon(tm) XP 2000+	1666 MHz	5.185	
2x AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57	1900 MHz	4.659	
4x Intel(R) Core(TM) i3 CPU M 380@ 2.53GHz	2533 MHz	2.275	
Mobile Intel(R) Pentium(R) 4 - M CPU 1.90GHz	1900 MHz	8.739	
AMD Athlon(tm) II X4 630 Processor	2765 MHz	2.542	
Pentium(R) Dual-CoreCPUE5300@ 2.60GHz	2590 MHz	3.225	
4x AMD Phenom(tm) II X4 910 Processor	2600 MHz	2.309	
2x Intel(R) Xeon(R) CPU E5530@ 2.40GHz	2400 MHz	2.817	
Intel(R) Core(TM)2 QuadCPU Q9300@ 2.50GHz	2490 MHz	3.461	
Intel(R) Pentium(R) 4 CPU 2.53GHz	2525 MHz	6.155	
Intel(R) Pentium(R) III CPU - S 1400MHz	1392 MHz	7.740	
Intel(R) Celeron(R) CPU723@ 1.20GHz	1196 MHz	6.910	
4x Intel(R) Xeon(R) CPU E5405@ 2.00GHz	1995 MHz	3.925	
AMD Sempron(tm) 2200+	1494 MHz	5.974	
4x AMD Phenom(tm) II N930 Quad-Core Processor	800 MHz	3.461	
AMD Athlon(tm) XP 1600	1400 MHz	5.815	
4x Intel(R) Core(TM) i5 CPU M 450@ 2.40GHz	2400 MHz	2.871	
2x Intel(R) Core(TM) i7 CPU 920@ 2.67GHz	2659 MHz	2.334	
Intel(R) Celeron(R) CPU 2.50GHz	2492 MHz	6.037	
2x Intel(R) Core(TM)2 Duo CPU T7500@ 2.20GHz	800 MHz	4.399	
2x AMD Athlon(tm) X2 Dual Core Processor BE-2400	2305 MHz	3.916	
2x Intel(R) Xeon(R) CPU5148@ 2.33GHz	2327 MHz	4.215	
Mobile AMD Athlon(tm) 64 Processor 3700+	1600 MHz	3.298	
3x AMD Phenom(tm) II X3 710 Processor	800 MHz	2.528	
4x Intel(R) Core(TM)2 Extreme CPU X9650@ 3.00GHz	1998 MHz	2.656	
4x Intel(R) Core(TM)2 Extreme CPU X9770@ 3.20GHz	2403 MHz	2.439	
2x Intel(R) Atom(TM) CPU Z530 @ 1.60GHz	1067 MHz	8.438	
2x Intel(R) Core(TM)2 Duo CPU T5750@ 2.00GHz	1994 MHz	4.962	
Mobile AMD Sempron(tm) Processor 2100+	1000 MHz	7.000	
Intel(R) Celeron(R) processor600MHz	598 MHz	17.849	
mobile AMD Athlon(tm) XP 1500+	500 MHz	7.971	
PowerPC 740/750 (350.00MHz)	350 MHz	44.427	
Intel(R) Pentium(R) III CPU family1400MHz	1048 MHz	12.665	
2x Intel(R) Core(TM)2 Extreme CPU X7900@ 2.80GHz	2800 MHz	3.652	
8x Intel(R) Xeon(R) CPU X3460@ 2.80GHz	1197 MHz	2.026	
2x Intel(R) Pentium(R) 4 CPU 3.40GHz	2400 MHz	4.132	
4x Intel(R) Xeon(TM) MP CPU 2.50GHz	2500 MHz	4.623	
AMD Athlon(tm) XP 2200+	1782 MHz	5.313	
4x Intel(R) Core(TM) i3 CPU 560@ 3.33GHz	1197 MHz	2.016	
2x AMD Turion(tm)X2 Ultra DualCore Mobile ZM-86	600 MHz	3.755	

CPU N-Queens
------------

-CPU N-Queens-
<big><b>This Machine</b></big>	1050 MHz	13.754	
2x AMD Athlon(tm) X2 Dual Core Processor BE-2400	2305 MHz	14.981	
8x Intel(R) Core(TM) i7 CPU 930@ 2.80GHz	2834 MHz	0.780	
8x Intel(R) Xeon(R) CPU E5430@ 2.66GHz	2000 MHz	0.805	
2x AMD Athlon(tm) Dual Core Processor 5000B	1000 MHz	14.474	
2x Intel(R) Atom(TM) CPU N475 @ 1.83GHz	1000 MHz	16.703	
8x Intel(R) Xeon(R) CPU E5345@ 2.33GHz	1998 MHz	0.964	
Intel(R) Xeon(TM) CPU 2.80GHz	2793 MHz	9.811	
8x Quad-Core AMD Opteron(tm) Processor 2378	800 MHz	0.828	
16x AMD Opteron(tm) Processor 6136	2400 MHz	0.861	
2x AMD Athlon(tm) 64 X2 Dual Core Processor 5000+	1000 MHz	15.152	
AMD Athlon(tm) Processor LE-1640	1000 MHz	10.766	
Mobile Intel(R) Celeron(TM) CPU 1200MHz	1200 MHz	19.105	
4x Intel(R) Xeon(TM) CPU 2.80GHz	2800 MHz	19.470	
Intel(R) Core(TM)2 Quad CPUQ8300@ 2.50GHz	2500 MHz	9.144	
8x Intel(R) Xeon(R) CPU W5580@ 3.20GHz	3193 MHz	0.831	
4x Intel(R) Core(TM)2 Quad CPUQ9550@ 2.83GHz	2830 MHz	15.537	
Intel(R) Celeron(R) M processor 1400MHz	1396 MHz	17.709	
AMD Sempron(tm) 2200+	1494 MHz	18.257	
2x Dual-Core AMD Opteron(tm) Processor 1210	1800 MHz	19.977	
Intel(R) Celeron(R) CPU 2.20GHz	2194 MHz	14.588	
2x Pentium(R) Dual-CoreCPUE2210@ 2.20GHz	2199 MHz	10.997	
2x Intel(R) Core(TM)2 Duo CPU E6850@ 3.00GHz	1998 MHz	7.157	
2x Intel(R) Pentium(R) DualCPUT2410@ 2.00GHz	800 MHz	11.984	
Intel(R) Core(TM)2 Duo CPU E6750@ 2.66GHz	2656 MHz	9.363	
2x Intel(R) Core(TM)2 CPU T5500@ 1.66GHz	1000 MHz	25.132	
2x AMD Athlon(tm) MP 2400+	1800 MHz	31.882	
AMD Phenom(tm) II X4 840T Processor	2893 MHz	6.978	
Pentium(R) Dual-CoreCPUE5200@ 2.50GHz	2500 MHz	9.247	
Intel(R) Celeron(R) D CPU 3.33GHz	3341 MHz	9.402	
Intel(R) Celeron(R) CPUE3300@ 2.50GHz	3003 MHz	8.339	
Genuine Intel(R) CPU 2.30GHz	2300 MHz	11.033	
mobile AMD Athlon(tm) XP 1500+	500 MHz	22.843	
Intel(R) Core(TM)2 Quad CPUQ6600@ 2.40GHz	2400 MHz	11.222	
3x AMD Phenom(tm) II P820 Triple-Core Processor	1800 MHz	13.754	
2x AMD Turion(tm) X2 Dual Core Processor L510	1600 MHz	19.342	
Mobile AMD Athlon(tm) 64 Processor 2700+	800 MHz	22.194	
Intel(R) Celeron(TM) CPU1066MHz	733 MHz	25.309	
Intel(R) Core(TM)2 Duo CPU E7200@ 2.53GHz	2534 MHz	13.035	
4x AMD Phenom(tm) II X4 840T Processor	800 MHz	9.612	
Intel(R) Core(TM)2 Duo CPU E7300@ 2.66GHz	2644 MHz	9.051	
4x AMD Phenom(tm) 9500 Quad-Core Processor	1100 MHz	10.745	
Intel(R) Celeron(R) M processor600MHz	599 MHz	37.586	
2x AMD Athlon(tm) 64 X2 Dual Core Processor 5800+	1000 MHz	16.877	
Intel(R) Celeron(R) CPU 2.00GHz	2000 MHz	14.716	
Intel(R) Pentium(R) 4 CPU 1.50GHz	1496 MHz	22.283	
4x Intel(R) Core(TM)2 Quad CPUQ8200@ 2.33GHz	2333 MHz	19.451	
Genuine Intel(R) CPU U1300@ 1.06GHz	1067 MHz	22.400	
8x Intel(R) Core(TM) CPUQ 820@ 1.73GHz	1199 MHz	0.824	
Intel(R) Pentium(R) III Mobile CPU1133MHz	1132 MHz	25.935	
8x Intel(R) Core(TM) i7 CPU 920@ 2.67GHz	3799 MHz	0.901	

FPU FFT
-------

-FPU FFT-
<big><b>This Machine</b></big>	1050 MHz	2.424	
AMD Phenom(tm) 9650 Quad-Core Processor	2311 MHz	9.766	
8x Intel(R) Xeon(R) CPU E5620@ 2.40GHz	2394 MHz	1.614	
Intel(R) Pentium(R) DualCPUE2160@ 1.80GHz	1781 MHz	19.621	
06/17	2333 MHz	7.746	
2x AMD Athlon(tm) Neo X2 Dual Core Processor L335	1600 MHz	11.173	
AMD Athlon(tm) Processor TF-20	1600 MHz	25.298	
2x Genuine Intel(R) CPU T2250@ 1.73GHz	1729 MHz	5.568	
Mobile Intel(R) Celeron(R) CPU 1.50GHz	1495 MHz	15.404	
2x AMD Phenom(tm) II X4 B50 Processor	3084 MHz	3.131	
AMD Athlon(tm) XP 2900+	1992 MHz	16.063	
Mobile AMD Athlon(tm) 64 Processor 3400+	2194 MHz	15.352	
Intel(R) Core(TM)2 Duo CPU L9400@ 1.86GHz	1862 MHz	8.677	
Intel(R) Pentium(R) III CPU 1200MHz	1202 MHz	38.002	
PowerPC 7447A, altivec supported (1420,00MHz)	1420 MHz	45.506	
AMD Sempron(tm) Processor 3100+	1980 MHz	19.988	
Mobile AMD Sempron(tm) Processor 4000+	2200 MHz	14.398	
AMD Duron(tm) procwss{	1792 MHz	19.122	
AMD V120 Processor	2200 MHz	9.320	
4x Intel(R) Core(TM)2 Quad CPU @ 2.93GHz	1603 MHz	1.372	
Intel(R) Pentium(R) DualCPUT2370@ 1.73GHz	1729 MHz	10.083	
4x Intel(R) Core(TM) i3 CPU 560@ 3.33GHz	1197 MHz	1.325	
4x Intel(R) Core(TM) i3 CPU 550@ 3.20GHz	1200 MHz	1.354	
8x Intel(R) Core(TM) i7 CPU 975@ 3.33GHz	1596 MHz	1.046	
AMD Sempron(tm) 2200+	1512 MHz	40.664	
Intel(R) Pentium(R) D CPU 3.00GHz	3000 MHz	9.258	
4x Intel(R) Core(TM)2 Quad CPUQ6700@ 2.66GHz	2669 MHz	1.511	
2x Dual-Core AMD Opteron(tm) Processor 1210	1800 MHz	9.780	
2x Intel(R) Core(TM)2 Duo CPU E7400@ 2.80GHz	2793 MHz	3.267	
2x Intel(R) Core(TM)2 Duo CPU@ 2.40GHz	2400 MHz	3.953	
Intel(R) Celeron(R) CPU420@ 1.60GHz	1600 MHz	12.370	
2x AMD Athlon(tm) 64 X2 Dual Core Processor 4400+	1000 MHz	7.325	
4x Intel(R) Core(TM) i5 CPU M 560@ 2.67GHz	1199 MHz	1.381	
2x AMD Athlon(tm) Dual Core Processor 4850e	2500 MHz	7.387	
VIA Nano processor U2250@1300+MHz	1600 MHz	37.459	
4x AMD Phenom(tm) II X4 B60 Processor	3700 MHz	1.187	
4x Intel(R) Xeon(R) CPU X3360@ 2.83GHz	2003 MHz	1.177	
AMD Athlon(tm) XP 1700+	1605 MHz	26.810	
Intel(R) Celeron(R) CPU 2.50GHz	2492 MHz	12.003	
4x AMD Phenom(tm) 9850 Quad-Core Processor	1300 MHz	1.998	
4x Intel(R) Core(TM)2 Quad CPU @ 2.40GHz	2400 MHz	1.689	
4x AMD Phenom(tm) 9650 Quad-Core Processor	1200 MHz	2.189	
4x Quad-Core AMD Opteron(tm) Processor 1352	2100 MHz	2.198	
Intel(R) Celeron(R) D CPU220@ 1.20GHz	1197 MHz	18.565	
2x Intel(R) Core(TM)2 Duo CPU U9300@ 1.20GHz	800 MHz	7.168	
AMD Sempron(TM) 3000+	2000 MHz	18.028	
2x AMD Athlon(tm) 7850 Dual-Core Processor	1400 MHz	3.796	
8x Intel(R) Core(TM) CPUQ 720@ 1.60GHz	933 MHz	1.509	
4x Intel(R) Xeon(R) CPU5130@ 2.00GHz	1995 MHz	2.028	
16x Intel(R) Xeon(R) CPU E5530@ 2.40GHz	1600 MHz	1.497	
VIA Nehemiah	532 MHz	101.106	

FPU Raytracing
--------------

-FPU Raytracing-
<big><b>This Machine</b></big>	1050 MHz	13.856	
8x Quad-Core AMD Opteron(tm) Processor 2354	2200 MHz	21.655	
4x Intel(R) Core(TM)2 Quad CPUQ6700@ 2.66GHz	2669 MHz	22.647	
8x Intel(R) Xeon(R) CPU E5345@ 2.33GHz	1998 MHz	38.008	
AMD Phenom(tm) 9550 Quad-Core Processor	2210 MHz	22.880	
4x Intel(R) Core(TM) i3 CPU M 370@ 2.40GHz	933 MHz	16.552	
Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz	1200 MHz	40.325	
mobile AMD Athlon(tm) 4 1600+	1395 MHz	36.589	
4x Intel(R) Xeon(TM) MP CPU 3.66GHz	3670 MHz	56.827	
Intel(R) Pentium(R) III CPU family1400MHz	1048 MHz	66.053	
Intel(R) Pentium(R) 4 CPU 1600MHz	1593 MHz	62.636	
2x Intel(R) Pentium(R) 4 CPU 3.60GHz	3600 MHz	35.879	
3x AMD Processor model unknown	2812 MHz	12.511	
Intel(R) Pentium(R) III Mobile CPU 700MHz	700 MHz	67.776	
2x AMD Athlon(tm)X2 DualCore QL-60	1900 MHz	14.138	
2x AMD Athlon(tm) 64 X2 Dual Core Processor 5600+	2800 MHz	11.763	
AMD Turion(tm) 64 X2 Mobile Technology TL-56	1795 MHz	30.323	
8x Quad-Core AMD Opteron(tm) Processor 2376	1100 MHz	28.869	
Mobile AMD Sempron(tm) Processor 2800+	1600 MHz	32.144	
Intel(R) Pentium(R) DualCPUT2370@ 1.73GHz	1729 MHz	26.954	
2x AMD Turion(tm) Neo X2 Dual Core Processor L625	800 MHz	20.530	
4x Intel(R) Core(TM) i5 CPU M 450@ 2.40GHz	2400 MHz	11.516	
2x Intel(R) Core(TM)2 Duo CPU U9300@ 1.20GHz	800 MHz	32.565	
3x AMD Phenom(tm) II X4 B25 Processor	800 MHz	12.524	
Intel(R) Pentium(R) III Mobile CPU 866MHz	665 MHz	54.409	
2x AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-82	600 MHz	15.310	
2x AMD Athlon(tm) 64 X2 Dual Core Processor 3800+	2200 MHz	15.629	
AMD Athlon(tm) Processor 2650e	1596 MHz	29.661	
Intel(R) Celeron(R) CPU 2.20GHz	2194 MHz	36.590	
2x AMD Turion(tm) X2 Dual-Core Mobile RM-74	600 MHz	15.463	
2x Intel(R) Xeon(TM) CPU 3.06GHz	3057 MHz	40.207	
8x Intel(R) Core(TM) i7 CPU X 920@ 2.00GHz	1199 MHz	4.564	
2x Intel(R) Core(TM)2 Duo CPU P8400@ 2.26GHz	800 MHz	14.968	
Mobile Intel(R) Pentium(R) III CPU - M1066MHz	731 MHz	44.109	
2x Intel(R) Core(TM)2 Duo CPU T5250@ 1.50GHz	1000 MHz	27.422	
2x AMD Turion(tm) II Dual-Core Mobile M500	1500 MHz	15.168	
2x Intel(R) Core(TM) Duo CPUL2400@ 1.66GHz	1000 MHz	32.322	
2x Pentium(R) Dual-CoreCPUE6700@ 3.20GHz	2936 MHz	8.206	
2x Genuine Intel(R) CPU T2050@ 1.60GHz	800 MHz	34.504	
AMD Athlon(tm) XP processor 1800+	1533 MHz	31.855	
Mobile AMD Athlon(tm) XP 2800+	1459 MHz	36.889	
Intel(R) Pentium(R) III Mobile CPU1200MHz	798 MHz	45.741	
2x Intel(R) Core(TM)2 Duo CPU T7300@ 2.00GHz	2001 MHz	16.273	
2x AMD Athlon(TM) MP 2800+	2152 MHz	26.849	
2x AMD Phenom(tm) II X6 1035T Processor	2604 MHz	9.521	
AMD Athlon(tm) 64 Processor 3700+	1000 MHz	21.169	
Intel(R) Core(TM)2 Duo CPU E7500@ 2.93GHz	1596 MHz	13.547	
AMD Turion(tm) 64 Mobile Technology MK-38	2200 MHz	20.935	
Mobile Pentium II	299 MHz	151.837	
AMD Athlon(tm) II X2 240 Processor	4290 MHz	14.928	
Intel(R) Celeron(R) M processor800MHz	569 MHz	109.434

---

### Post by powerslave12r on 2011-02-26
> **gesquive said:**
> You can find more info in [this thread]("http://ubuntuforums.org/showthread.php?t=1586178&page=2") and [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656631"). But the following worked for me on my  Dell Latitude E6510 (Intel Core i7-720QM, 4GB RAM, NVIDIA NVS 3100M) running 10.10 64bit:

Use the editor of your choice to edit /etc/default/grub
```
sudo nano /etc/default/grub
```

next, change
```
GRUB_CMDLINE_LINUX=""
```
to
```
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"
```

then run:
```
sudo update-grub
```

After restarting, I can now suspend without any problems again.

This helped me fix it on my Latitude E6510 with the same configuration. (i7-720QM, NVidia NVS 3100m 512MB). Thanks a lot!

---

### Post by Byb on 2011-02-27
Already tryied that before posting all my logs. Didn't work.
Now in addition to herons, ibexes, jackalopes, koalas and lynxes, whenever I see a meerkat I shoot it. Please Ubuntu devs, stop calling your distro to animals' names for this massacre gets a end. Just call it Ubuntu so that I don't have to read the news twice a year to know what new beast to fire.

---

### Post by Zanderist on 2011-03-01
If you've updated your video card (if it's ATI) from the additional drivers menu deactivate it, you should be able to suspend and resume after that.

This what I've done to work around this problem, but now I'm keeping the video driver on and waiting for a fix.

EDIT:

Yeah I just deactivated it and I was able to suspend again.

---

### Post by Byb on 2011-03-02
The huge number of Intel refs in the logs posted 2 pages before show it's not ATI.

---

### Post by gbrowne on 2011-03-03
Any more thoughts on this anyone please ? I really need to fix resume without waiting months for V11.  

I am a great fan of Ubuntu and very grateful to the developers who have made it the success it is, but for me the upgrade to 10.10 has been a big backwards step.  I really wish I had stayed at 10.04 as it was really good - very fast boot, everything worked well.  In fact I upgraded my Dell Inspiron 9300 from 10.04 to 10.10 and really the only difference I have noticed is a doubling of the time to boot and no more resume from lid-close-standby which was fine on 10.04 :(

I have also noticed that if I use ^ALt-L to lock the screen, after about 30 sec the system freezes to the extent that only a power down can regain control ?

G.

---

### Post by bcollignon on 2011-03-04
Simply a weird addendum:  In my case, with the latest headers (28, I believe) here's what happens:

Startup, login:  try to suspend, suspends then comes back w/o properly displayed graphics.  Graphics displayed as several indiscernible lines which points to a graphics driver/card problem, however...

Startup, login, logout, login again:  try to suspend, suspends and resumes with full graphics capabilities.  All normal.

Crazy, huh?

---

### Post by HankB on 2011-03-04
> **sgosnell said:**
> Install the package 'hibernate' from the repositories.  That seems to make suspend work properly.

Thanks for the suggestion. It solved the suspend problem with my Asus Eee PC 901. (I'm posting here for the benefit of any other 901 owners who are searching for a solution to this problem.)

The problem I had was that the 901 would not suspend after updating to 10.10. Instead it just locked up with a blank screen until it burned through the battery or I held the power switch. It had mostly worked well before though I did have to add stuff to unload the Ralink WiFi drivers with a previous release. 

At present here is what I have:

- No mod to [FONT="Courier New"]GRUB_CMDLINE_LINUX[/FONT] in [FONT="Courier New"]/etc/default/grub[/FONT].

- [FONT="Courier New"]/etc/pm/config.d/config[/FONT] contains:
```
hbarta@bonsai:~$ cat /etc/pm/config.d/config 
SUSPEND_MODULES="rt2860sta rt2800pci rt2800lib rt2x00usb rt2x00pci"
```

- I installed the hibernate and related package. There was much complaining about no swap partition, but it solved the problem. (For those not familiar with the 901, it has relatively slow SSD drives so I upgraded to 2GB RAM and use no swap.)

thanks,
hank

Edit: Not, it did not solve the problem. So I'm in the process of installing 10.04-2 Desktop. And... I'm doing that from a USB CD ROM. That's because a bootable USB flash drive created from the ISO image won't boot. <sigh>

---

### Post by powerslave12r on 2011-03-06
I guess my problem was solved temporarily only. It has resurfaced.

---

### Post by twshadow101 on 2011-03-06
I am having the same problem only this time its with a HP G62-435DX Notebook PC. I have tried installing the new "hibernation" package didn't solve it. And, using:

> **gesquive said:**
> You can find more info in [this thread]("http://ubuntuforums.org/showthread.php?t=1586178&page=2") and [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656631"). But the following worked for me on my  Dell Latitude E6510 (Intel Core i7-720QM, 4GB RAM, NVIDIA NVS 3100M) running 10.10 64bit:

Use the editor of your choice to edit /etc/default/grub
```
sudo nano /etc/default/grub
```

next, change
```
GRUB_CMDLINE_LINUX=""
```
to
```
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"
```

then run:
```
sudo update-grub
```

After restarting, I can now suspend without any problems again.

This didn't solve it either. I have both in there right now.

What happens is it'll suspend okay and resume if you don't let it sit a long time, but after a few hours if you open the laptop it'll just display a blank black screen..Nothing no cursor, nothing. However, you can hear the disk spin, and see the lights come back on but nothing as far as video goes.

I tried contacting HP but their tech guys only read from scripts and ignored the fact I told him 3 times I was NOT using Windows. 

So if anyone in here can help, I would owe you one.

Oh! Has anyone tried downgrading back from Ubuntu 10.10 to 10.04 and had any luck with the suspend/resume working? I am considering it.

---

### Post by bcollignon on 2011-03-06
Today, suspend worked without incident at first logon... this seems intermittent.

---

### Post by HankB on 2011-03-06
> **bcollignon said:**
> Today, suspend worked without incident at first logon... this seems intermittent.I found it to be very hit or miss with 10.10. With previous versions I became accustomed to closing my netbook and just slipping it into the case. Suspend was 100% reliable. I have reverted to 10.04 and that solves the problem for me.

I suppose I should try out the 11.04 beta when it becomes available on the theory that the problem may be fixed if it is known about before release.

---

### Post by powerslave12r on 2011-03-06
This problem combined with external hard drive mounting problems is forcing me to downgrade to 10.04. Sucks, but I guess that is a lot more stable.

---

### Post by twshadow101 on 2011-03-06
I found that setting my power management settings to hibernation when closing the laptop works, but suspend does not. Hibernation takes longer to get back to the desktop then suspend does, but till Ubuntu fixes the problem i'll stick with that.

---

### Post by bcollignon on 2011-03-14
It seems my problem may have been with Avant Window Manager (AWN).  Having it disabled and not loaded at startup, I've been able to resume from suspend with full graphics several times without incident.  Perhaps an AWN-nVidia incompatibility?

---

### Post by JMB74 on 2011-03-14
A few weeks ago, out of blind hope, I installed the latest 2.6.35 kernel from the pr-proposed kernel PPA.

[https://launchpad.net/~kernel-ppa/+archive/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/pre-proposed)

(I know that's not generally recommended)

Since then, suspend/resume seems to work without problems.

I'm not sure if that fixed the issue, or it was coincidentally something else at the same time?

However, problem gone = happy user :)

---

### Post by twshadow101 on 2011-03-14
> **bcollignon said:**
> It seems my problem may have been with Avant Window Manager (AWN).  Having it disabled and not loaded at startup, I've been able to resume from suspend with full graphics several times without incident.  Perhaps an AWN-nVidia incompatibility?

I didn't think of Avant Window Manager, but I don't use nVidia I have ATI graphics on my laptop. 

It'll be interesting though i'll have to shut down Avant Window Manager and see if that helps.

---

### Post by travlemon on 2011-03-15
> **twshadow101 said:**
> I didn't think of Avant Window Manager, but I don't use nVidia I have ATI graphics on my laptop. 

It'll be interesting though i'll have to shut down Avant Window Manager and see if that helps.

Just wanted to throw this out there.  I have a laptop that's a bit older, an IBM Thinkpad R40.  I was going nuts trying to fix the issues with suspend and hibernate.  It would go into suspend and hibernate fine.  However, on resume,  I would get quirky graphical issues and/or the whole system would just freeze.  I was actually able to fix the problem, but I don't know if this will be something that will fix it for everyone.  

_Here's what I did:_  I noticed that my laptop had two different brands of memory chips in it.  2 256mb chips, both from different brands.  I remembered that I had a spare chip that was identical to one of the installed chips.  I installed the spare so that two identical memory chips were present in the laptop.

After that, I still had the problem.  However, after completely updating my system, it actually worked.  I was hugely surprised that it actually fixed it.  I doubt the memory module was bad, as I never had any other problem with the system, just suspend and hibernate.

Just as a suggestion, if it's easy enough to do,  try removing extra memory modules from your PC so that only one is left.  Make sure your system is up to date, and try the suspend or hibernate features.  If this does fix it for you, I apologize for not having a fix for that, other than suggesting to get the same brand of memory chips.  I would that this is simply a bug that gets fixed in the near future.

---

### Post by Zanderist on 2011-03-23
My problem is completely related to the video driver being activated.

The second I activate it, I lose the ability to suspend or hibernate.

---

### Post by travlemon on 2011-03-23
> **Zanderist said:**
> My problem is completely related to the video driver being activated.

The second I activate it, I lose the ability to suspend or hibernate.

That might be my issue too.  I think I may have been wrong about the memory.  The issue came right back.  I've had trouble with other distros doing this as well.  As a test, I installed PCLinuxOS, as I've read it has superb hardware support.  I haven't had the problem at all on PCLOS.

---

### Post by Copter on 2011-04-20
> **jon.reeve said:**
> I think I figured it out, for my MSI Wind, at least. For me, the problem was probably the r8187se (realtek wireless) module. As a variation on the first suggested fix, I edited /etc/pm/config.d/unload_module and added ```
SUSPEND_MODULES="r8187se"
``` and now I got suspend to work. (It was the only line in that file, BTW). If you have r8187se or something similar listed when you run ```
lsmod
``` then maybe this will work for you, too. Otherwise maybe find the module that's acting up, or see if removing a module enables you to suspend, and then list that module in the file above, and then maybe that'll work.

Hope it helps! :)
Awsome job :) I confirm that it fixes the suspend issue on MSI Wind U100X on Kubuntu / Xubuntu 10.10. Thanks jon.reeve!

---

### Post by Byb on 2011-04-21
Here the output of my modules. Have you idea if a module here could break my resume from suspend?
Thanks
```
Module                  Size  Used by
binfmt_misc             6599  1 
sha256_generic         11267  2 
aes_i586                7280  410 
aes_generic            26875  1 aes_i586
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  1 
joydev                  8767  0 
snd_intel8x0           25664  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
pcmcia                 35973  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ipw2200               136715  0 
libipw                 39808  1 ipw2200
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              144694  2 ipw2200,libipw
yenta_socket           21518  0 
snd                    49038  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
lib80211                5058  2 ipw2200,libipw
psmouse                59033  0 
soundcore                880  1 snd
shpchp                 29886  0 
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
btrfs                 489451  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
i915                  295435  4 
drm_kms_helper         30200  1 i915
drm                   168060  4 i915,drm_kms_helper
intel_agp              26566  2 i915
firewire_ohci          21234  0 
8139too                19581  0 
8139cp                 16934  0 
firewire_core          46643  1 firewire_ohci
i2c_algo_bit            5168  1 i915
crc_itu_t               1383  1 firewire_core
mii                     4425  2 8139too,8139cp
video                  18712  1 i915
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
```

---

### Post by svendolph on 2011-05-01
> **knuton said:**
> Same problem with my Samsung N210. The `hibernate` package did not change anything for me. It worked fine using 10.04.

My hopes to New 11.04 was spoild. Same problem and after suspend my Samsung N210 is dead. Only WiFi lamp works. Power of is the only solution. 

Its work with Open Suse (crappy on Netbooks) and Fedora 14 (to difficult)
Migrated back to Win 7 Starter and crying.

---

### Post by Worp8d on 2011-05-01
> **svendolph said:**
> Migrated back to Win 7 Starter and crying.

Is that really necessary?  Why not just disable the suspend/hibernate and turn the machine of manually when you need?  That's all I've been doing.

---

### Post by svendolph on 2011-05-05
Because I use suspend :)

---

### Post by ionplay on 2011-05-19
> **bez654 said:**
> 

to get suspend to ram to work I added
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"
to grub as detailed elsewhere in this forum.
This is on a eee 1000H with the only difference from stock being additional ram (up to 2gb). running ubuntu 10.10 running 2.6.35-24



I am on a laptop - Asus X72D running Ubuntu 10.10
I do not use suspend / hibernate 
but accidentally hit suspend instead of shutdown and then hit shutdown 

could not boot anymore
used live CD to edit /etc/default/grub 
edited
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"

then booted normally
thanx

---

### Post by Byb on 2011-05-20
Maybe you could have remove the power supply and the battery to be able to boot again. These issues with suspend in ubuntu reminds me my Lada Niva and win98

---

### Post by drgrumpy on 2011-05-23
Not sure if this will be a help to anyone, but I had similar problems on desktop machine with ATI graphics card, see bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/434956/comments/52](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/434956/comments/52)

---

### Post by welcomb on 2011-06-29
> **yanaek said:**
> suspend/resume now works after this FIX on MSI wind U100
thanks a lot ;)

BUT, if i make the second patch (changing kernel options) it's NOT working - so remember, for MSI Wind U100 only one patch fixes the problem, two of them NOT

This doesn't work for my MSI U100. "xhci" did not show up in lsmod, and mine is a Atheros card, not the Realtek wireless

---

### Post by Goribuntu on 2011-10-18
Hi, 

For everybody finding this thread, if this bug affects you please go to launchpad  and mark bug 819096   as affecting you. Futhemore please add the machine/SSD info, so we can exclude specific hardware issues. The more people are affected by it, the more attention it gets from developers :  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/819096](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/819096)

---

### Post by Copter on 2011-12-07
> **Copter said:**
> Awsome job :) I confirm that it fixes the suspend issue on MSI Wind U100X on Kubuntu / Xubuntu 10.10. Thanks jon.reeve!

The same issue on fresh install (not update) of Xubuntu 11.10 on the same machine. Again fixed by following the same procedure.

---

### Post by khurtsiya on 2011-12-15
same on ideapad lenovo s10-3

---

### Post by yragnos on 2011-12-29
Same problem here with Nvidia graphics card. When resuming there is a blank screen, but the system is loading and appears to load correctly, but screens are blank and do not power up (lights do not go green on monitor).

Appears to be a real common bug/problem.:(

---

### Post by impulsionaudio on 2012-01-20
I am dealing with the same problem. I suppose Ubuntu knows?

---

### Post by bluemoon222 on 2012-01-24
I have (at the 3rd attempt) made 11.10 install on an old ASUS that my partner had a very flaky VISTA image on....fought past some wireless issues but now having screen hangs that I can only solve with a reboot....if I leave the system unattended for 10-15 minutes the screen goes blank, no response from mouse or keyboard and the only button that does anything is power off....I have a pretty vanilla install of 11.10 to which I have only added SKYPE and Chrome so far

Ideas ?

---

### Post by Byb on 2012-01-24
I discovered with  the help of numerous fresh installs that my resume problem began in Ubuntu when they introduced GRUB2. If I install and use grub legacy in a broken release, resume works !!! Thaw was always OK.

---

### Post by bluemoon222 on 2012-01-24
I found the following and whilst it is not ideal it is a workaround for now:

[http://www.liberiangeek.net/2011/10/ubuntu-screen-going-blank-dark-on-you-stop-it-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/10/ubuntu-screen-going-blank-dark-on-you-stop-it-in-ubuntu-11-10-oneiric-ocelot/)

---

### Post by atanis on 2012-02-06
On a desktop with MB Asus P5LD2 and graphic card Asus N6600 using ubuntu 10.10
When resuming from pm-suspend, the computer starts but does not switch on the screen nor answers to the keyboard or the mouse.
/etc/acpi/sleep.sh works as expected
pm-hibernate works as expected

---

### Post by heavyt on 2012-02-19
Been having the same problem with my monitor not waking/responding after resume from suspend (HP-Compaq-dc7800-Ultra-slim-Desktop). The fix I came up with is to remove xscreensaver. ```
apt-get remove xscreensaver
```

On a Xubuntu 11.10

---

### Post by norcal on 2012-05-16
I was able to finally solve this problem by updating the firmware on my ssd

---

