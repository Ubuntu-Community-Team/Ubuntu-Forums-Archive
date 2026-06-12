---
title: "Info and help for HP TX2500 Series"
date: 2008-07-01
forum: Hardware
---

### Post by isachan on 2008-07-01
I just got my brand-spanking new HP TX2500 CTO this morning, and after several hours of uninstalling the bloatwares, defragging, and partitioning, I finally got to install Kubuntu 8.04.

Immediately I stumbled into the problem of booting from a LiveCD. An hour later I found out why.

By pressing Ctrl+Alt+F1, I could see boot messages. It turns out that as soon as the kernel loads, it detects overtemp, and starts to shut down the machine. The message line reads "Critical temperature (xxC) reached: shutting down".

Funny thing is that this happens even the temp is reasonably low (even around 60).

After a few search on the forums I tried the kernel parameter "acpi=off", and lo and behold, it works !

So I installed Hardy and several other essential applications (Radeon drivers through EnvyNG, etc) and realized there is no sound. No wonder, because ACPI interrupts control the sound chip. Irony is that I wanted to watch some HD video on this machine (surprisingly, the playback is slow) !

However, this parameter is the only thing that's working so far. I also tried noapic, nolapic, noacip, irqpoll, irqfixup, acpi_irq_balance, noirqdebug, but no avail.

I need some serious help here, but my hunch is that I have to wait for BIOS updates from HP for the next several months.

I post this new thread, hoping this one parameter can help some others to get going on Linux with this tablet PC.

Isao

---

### Post by sergiom99 on 2008-07-01
please post your detailed laptop specs and the output of lspci.


Thanks.

---

### Post by wabre on 2008-07-01
check this thread, first post. i'm not sure if it works, see the sound section in the first post. it helped me on my tx2120, though not sure if it works on your (me jealous...) puma..

[http://georgia.ubuntuforums.org/showthread.php?t=792669](http://georgia.ubuntuforums.org/showthread.php?t=792669)


oh, something else..mainly hope: i installed ubuntu 8.10 intrepid ibex alpha 1...sound works out of the box!

---

### Post by isachan on 2008-07-02
wabre, thanks for the link, but adding that line didn't make any difference, since TX2500 uses different combination of integrated chipset and the same Realtek chip. So, it shows up as "HDA ATI SB". I'll do some search on it to see what I can find.

sergiom99, here is my lspci -v output :

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [9c] HyperTransport: #1a
	Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d2200000-d23fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: [44] HyperTransport: MSI Mapping
	Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: d1200000-d21fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+) IRQ 0
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Hewlett-Packard Company Unknown device 30f1
	Capabilities: [b8] HyperTransport: MSI Mapping

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: d1100000-d11fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+) IRQ 0
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Hewlett-Packard Company Unknown device 30f1
	Capabilities: [b8] HyperTransport: MSI Mapping

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b0000000-b00fffff
	Prefetchable memory behind bridge: 00000000d1000000-00000000d10fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+) IRQ 0
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: Hewlett-Packard Company Unknown device 30f1
	Capabilities: [b8] HyperTransport: MSI Mapping

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	I/O ports at 6038 [size=8]
	I/O ports at 604c [size=4]
	I/O ports at 6030 [size=8]
	I/O ports at 6048 [size=4]
	I/O ports at 6010 [size=16]
	Memory at d2409000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] #12 [0010]

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
	Memory at d2408000 (32-bit, non-prefetchable) [size=4K]

00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
	Memory at d2407000 (32-bit, non-prefetchable) [size=4K]

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 7
	Memory at d2409500 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
	Memory at d2406000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
	Memory at d2405000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 4
	Memory at d2409400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: 66MHz, medium devsel
	Capabilities: [b0] HyperTransport: MSI Mapping

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 80 [Master])
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 6000 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/1 Enable-

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: bus master, slow devsel, latency 64, IRQ 5
	Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
	I/O behind bridge: 00001000-00001fff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
	Memory at d2404000 (32-bit, non-prefetchable) [size=4K]

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] #0f [0010]

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30f1
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 5000 [size=256]
	Memory at d2300000 (32-bit, non-prefetchable) [size=64K]
	Memory at d2200000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

08:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137c
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at d1100000 (64-bit, non-prefetchable)%2

---

### Post by corwinspyre on 2008-07-02
edit: nevermind

---

### Post by isachan on 2008-07-07
New findings and a few updates :

Web cam works with "Cheese". Install it with "sudo apt-get install cheese" and enjoy. I haven't tried with Skype or Ekiga yet.

If your machine is cool enough, you can boot without "acpi=off" boot option. You only have 3 to 4 minutes though until the machine shuts itself down again, and the keyboard and the touchpad don't work without it.

For the wireless, it seems like we just have to wait until the bugs in "wl" driver will be fixed. According to these threads :

[http://ubuntuforums.org/showthread.php?p=5326382#post5326382](http://ubuntuforums.org/showthread.php?p=5326382#post5326382)
[http://ubuntuforums.org/showthread.php?t=848622&page=3](http://ubuntuforums.org/showthread.php?t=848622&page=3)
the last update has broken the driver. Let's wait and see what happens.

I have been thinking to fix up some DSDT problem with this machine, by following instructions on this thread :
[http://ubuntuforums.org/showthread.php?t=623633](http://ubuntuforums.org/showthread.php?t=623633)
but now I just found out I can't even type anything from keyboard.
My hope to get Linux going on this machine is getting slim.

Is anybody else out there have any other ideas to tackle this ?

Isao

---

### Post by isachan on 2008-07-07
Okay, so I verified that the webcam works for Skype and Ekiga.

For Ekiga, just type in a command line :
sudo apt-get install ekiga libpt-1.11.2-plugins-v4l2
After everything is installed, run Ekiga.
Go to Edit Menu -> Preferences -> Under Devices, Video Devices -> Set Video Plugin to V4L2.
Wait a few minutes, and you should be able to see yourself in the video.

For Skype :
Go to this page, and follow the direction :
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)
Then, do sudo apt-get install skype

That should be it.

As you know, at this point it's meaningless because the sound is not working. Well, someday...

Isao

---

### Post by TomtheWombat on 2008-07-10
You could try "noapic nolapic irqfixup" as suggested in [http://ubuntuforums.org/showthread.php?t=837657](http://ubuntuforums.org/showthread.php?t=837657)

That thread also contains a tip for the sound card and a link to instructions for the touch screen.

The webcam is is v4l2 device so it won't work with version 1 v4l programs (like adobe's flash).  There is a bridge for v4l2->v4l, but I forgot what it's called.

---

### Post by isachan on 2008-07-11
Thanks, but those kernel options didn't work.

I'm trying to set a higher trip-points with a script from another Ubuntu forum thread. It's still not working.

I don't have sound, but playing back some high def video with MPlayer and fglrx driver with OpenGL direct rendering is so smooth ! Image quality is just great.

Isao

---

### Post by kv11 on 2008-07-12
isachan, could you please describe what other problems do you have with tx2500 ? Does touchscreen (and pressure sensitivity) work ? Does it suspend/resume properly ?

---

### Post by isachan on 2008-07-12
So far, I haven't tested those features yet, as I haven't got a screen protector on the screen. I've been researching which one would be the best one.

I haven't tried it either, but I can only see the hibernate option. I believe we really need ACPI to enable suspending.

I'm gonna employ tx2000 tactics to try once I got my screen protector. I'll let you know later.

Isao

---

### Post by AstronomyDomine on 2008-07-14
Well it's nice to see I'm not the only one having troubles.  I've figured out that the critical trip point problem lies within the thermal module which is loaded with the initramfs, so for now we have three choices: We can boot with acpi=off, we can compile a custom kernel without the thermal module, or we can recreate our initramfs without the thermal module.

I opted for the third option, and it is working pretty well so far.  I still don't have audio, wireless, or touchscreen support, but it runs for hours without problems.  I have no idea why I don't have any touchscreen support, but no matter what I try, I can't seem to get it working.  Also, the wireless doesn't seem to want to work at all, even with ndiswrapper.

---

### Post by isachan on 2008-07-14
This could be the reason :
[http://forum.tabletpcreview.com/showpost.php?p=115568&postcount=2](http://forum.tabletpcreview.com/showpost.php?p=115568&postcount=2)

Also, see the last post, written on 2008-04-25
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/111460](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/111460)

I'm confused now. Is it the BIOS, or the kernel being the cause ?
Or the combination of both ? Or the new CPU and the chipset (Puma platform) ?

Only once before, I got lucky and had enough time to look the thermal parameters in /proc/acpi/thermal_zone/THRM/ directory. And I remember the trip point was -127C. So that's why I thought it's because of a bug in DSDT. I think I got the sound only for that time.

This morning was very cool at my place and I tried without acpi=off again, and saw the wireless light was blue. But a minute after I got to see the desktop, it shut down. With acpi=off, the light stays red no matter what you do.

So, we just have to be patient and wait for a long time for updates ?
For my TX1000, it took approx. 11 months to be fully usable.

Isao

---

### Post by fbdelivers on 2008-07-14
I am really happy to see this post.  I've been trying and trying to get things to work following all of the tx2000 instructions.  The wireless issue just about made my wife shoot me as I've been sitting in front of this computer for days now.

Short description - I just purchased the tx2500 and have been following all of the tx2000 instructions to try and get the wireless to work.  No luck just like this thread.  I too have the acpi=off setting on boot.  I put the tablet in a cold place for a couple of hours, enabled acpi, booted and BAM the wireless started working.

I'd be happy to get at least the wireless working and will start working on the acpi setting to see if I can get past that.  I've tried getting wacom to work but haven't had any luck.

Thanks for the post!

David

---

### Post by AstronomyDomine on 2008-07-14
> **fbdelivers said:**
> I put the tablet in a cold place for a couple of hours, enabled acpi, booted and BAM the wireless started working.


The wireless started working meaning that the light was blue, or that you were actually able to connect to a network?  

I don't need to boot with acpi=off since I removed thermal from the initramfs, but I still can't use the wireless.  The light is blue, but there is no interface for the device.  Even ndiswrapper doesn't seem to work.

---

### Post by fbdelivers on 2008-07-14
> **AstronomyDomine said:**
> The wireless started working meaning that the light was blue, or that you were actually able to connect to a network?  

I don't need to boot with acpi=off since I removed thermal from the initramfs, but I still can't use the wireless.  The light is blue, but there is no interface for the device.  Even ndiswrapper doesn't seem to work.

Good question and maybe I got ahead of myself.  I just had the light turn blue which was a good sign.  I haven't had it run long enough to try the wireless other then the fact that it did scan and wireless networks were available.

I'll work on removing the thermal from initramfs.  Did you do that by just removing that from the hooks directory?

David

---

### Post by AstronomyDomine on 2008-07-14
Here's how I removed the module thermal from my initramfs:

```

sudo su -
cd /boot
mkdir /tmp/directory.cpio
zcat initrd.img-2.6.24-19-generic > /tmp/directory.cpio/initrd.cpio
cd /tmp/directory.cpio
cpio -idv < initrd.cpio
rm lib/modules/2.6.24-19-generic/kernel/drivers/acpi/thermal.ko
nano conf/modules

```
Remove the line "thermal" from the file (if this file is blank, something wrong happened, post here), then hit CTRL+X, Y, to save the file.
```

rm initrd.cpio
find . -print0 | cpio -o0 -H newc -v > /tmp/initrd.img.cpio
gzip -9c /tmp/initrd.img.cpio >/tmp/initrd.img-2.6.24-19-generic
mv /boot/initrd.img-2.6.24-19-generic /boot/initrd.img-2.6.24-19-generic.bak
mv /tmp/initrd.img-2.6.24-19-generic /boot/
nano /boot/grub/menu.lst

```

Now you can find the boot line for your kernel and remove the acpi=off option.  I'd also suggest removing quiet and splash if they're still there, that way you can see what's happening.  Mine looks like:

```
kernel		/vmlinuz-2.6.24-19-generic root=UUID=ba05d9a0-8436-400d-9a6f-f0d041fb94e3 **ro noapic**
```

**Your UUID won't be the same as mine, don't change anything in this line except for the bolded text.**

Best of luck.  Post with any progress.

---

### Post by fbdelivers on 2008-07-15
Thanks for the detailed instructions.  I gave it a shot and unfortunately it didn't work.  I'm still getting the critical trip_point message on boot at (71 degrees).  I've been running the computer for a while and will let it cool down.

I didn't receive any errors when running your options and the boot loads just fine up to starting acpid.

Let me know if there is any log that you'd like to see and I'll post.  I'll also try again when my machine cools down.

---

### Post by AstronomyDomine on 2008-07-15
Found a few errors in my post.  I've corrected them.  Please try to run through it again, and post back with your results.

---

### Post by tC_Crazy on 2008-07-15
I tried the code, but had some problems. First, I believe... wait, I think you edited the code... b/c I copied down /tmp/initrd.cpio instead of /tmp/directory.cpio/initrd.cpio. 

Then, I made the stupid mistake of not sudo-ing every step, so the rm didn't work and thermal.ko was not deleted... among other things. So thermal shutdown resulted.  So i went back in, tried repeating all the steps (bad idea), and now I get a kernel panic on boot for not being able to mount the fs to "unknown media (0,0(" or something like that. No worries, I'll just reinstall ubuntu tomorrow (I just installed it today.. haven't done anything since) and try the instructions again. By the way, thanks for instructions... esp if they work! I was looking exactly for this.

---

### Post by fbdelivers on 2008-07-15
I tried the steps one more time.  (I did the original initrd to make sure that I removed the thermal file.

I'm still getting the trip_point issue on boot at (69 C).  If I go back and set the boot to acpi=off again the new kernel loads fine (minus the acpi / wireless).

I appreciate the time you have taken - I won't be able to reply for about a day.

I have the tx2525nr - latest ubuntu 
uname -r  2.6.24-19-generic

The only thing different in my menu file is:

```
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8c5aa53d-de77-4cb9-8a7d-9190d4a90d9c ro xforcevesa noapic
```

---

### Post by kv11 on 2008-07-15
You could also try altering parameters of thermal module:
```
$ modinfo thermal
filename:       /lib/modules/2.6.24-19-generic/kernel/drivers/acpi/thermal.ko
license:        GPL
description:    ACPI Thermal Zone Driver
author:         Paul Diefenbaugh
srcversion:     484C09AEA5B2FE85E9747E6
alias:          acpi*:LNXTHERM:*
depends:        processor
vermagic:       2.6.24-19-generic SMP mod_unload 586
parm:           act:Disable or override all lowest active trip points. (int)
parm:           crt:Disable or lower all critical trip points. (int)
parm:           tzp:Thermal zone polling frequency, in 1/10 seconds. (int)
parm:           nocrt:Set to take no action upon ACPI thermal zone critical trips points. (int)
parm:           off:Set to disable ACPI thermal support. (int)
parm:           psv:Disable or override all passive trip points. (int)

```

Parameters like nocrt seems to be relevant. You could try altering them by editing /etc/modprobe.d/options file in the root filesystem or in initrd.

---

### Post by kv11 on 2008-07-15
EDIT: Please see more detailed explanation [here]("http://ubuntuforums.org/showpost.php?p=5417491&postcount=69").


You could also try the following boot options (i.e. arguments for kernel command line, *NOT* for options file):
```

	thermal.act=	[HW,ACPI]
			-1: disable all active trip points in all thermal zones
			<degrees C>: override all lowest active trip points

	thermal.crt=	[HW,ACPI]
			-1: disable all critical trip points in all thermal zones
			<degrees C>: lower all critical trip points

	thermal.nocrt=	[HW,ACPI]
			Set to disable actions on ACPI thermal zone
			critical and hot trip points.

	thermal.off=	[HW,ACPI]
			1: disable ACPI thermal control

	thermal.psv=	[HW,ACPI]
			-1: disable all passive trip points
			<degrees C>: override all passive trip points to this value

	thermal.tzp=	[HW,ACPI]
			Specify global default ACPI thermal zone polling rate
			<deci-seconds>: poll all this frequency
			0: no polling (default)


```

---

### Post by tC_Crazy on 2008-07-15
kv11, this seems like an even more direct approach to the thermal module... plus it's completely nondestructive so I'll try the auto detailer's saying of "the least aggressive method first."

I'll try the following boot options when I get off of work (should be very redundant but sometimes that is necessary like with noacpi acpi=off):

thermal.act=-1 
thermal.crt=-1 
thermal.nocrt= (wait a sec, what value do i put here?.. sorry if this is a newb question)
thermal.psv=-1
thermal.off=-1

If that fails, I'll try editing the thermal module...and if that fails I'll try Astronomy's method... btw did that actually work for booting up with wifi/sound/anything else that require acpi?

Oh, does anyone get a kernel panic if they boot with JUST noapic? I can only get it to work properly with both noapic AND acpi=off. Just acpi=off results in the shutdwon. I've got a CTO tx2500z with the 2.4Ghz ZM-86 processor, 3GB RAM.

---

### Post by isachan on 2008-07-15
kv11, you're a God send !

I added the following lines to /etc/modprobe.d/options file :
(Edit: corrected options from option as per tC_Crazy)

options thermal.act=-1
options thermal.crt=-1
options thermal.nocrt=1
options thermal.psv=-1

(I removed the line "option thermal.off=-1 later on)
(tC_Crazy - a bit of googling lead me to how to specify .nocrt value)

Also, I added noapic to kernel boot option.

Now bluetooth is working ! No more full-speed fan noise ! Yeah !

I can see suspend icon on the log-off window (haven't tried).

My machine became a bit sluggish, I suppose some other services / processes are now turned on and running.

Wireless light is blue, and you can turn on and off, but it is wrongly recognized as a BCM4315. I don't see any AP with Wicd.
After sudo modprobe wl, do a dmesg and you'll see it is assigned as eth1.
For some reason, I still see ndiswrapper as a loaded module, despite of the fact I completely removed. What's with ? Let me tweak around a bit more...

No sound yet. I'm gonna try irq_debug, irq_balance, irqfixup, etc.

My TX2500 is much better than before ! Thanks !

Isao

---

### Post by tC_Crazy on 2008-07-15
isachan, I'm not positive if this is correct, but since the tx2000 and tx2500 use the same RealTek driver, I'm going to assume that they have the same sound card. If so, the info in this tx2000 sound card thread may help... [http://ubuntuforums.org/showthread.php?t=585909](http://ubuntuforums.org/showthread.php?t=585909)

By the way, any luck with the active digitizer (pen) or touchscreen?

---

### Post by pluckster on 2008-07-15
I hate to sound rude but I'm just having trouble following all these threads. I can't really understand whats going on. So can we start from the beginning. I have a tz2524ca and I would like to install Ubuntu. I am getting errors but can I just get an an in one explanation covering everything that people have encountered starting with just getting it installed.

---

### Post by tC_Crazy on 2008-07-15
I'll give you the run-down. The tx2500z has a problem in a component called ACPI which causes it to report very very high temperatures to Ubuntu. Ubuntu, in turn, shuts the system down to save the processor from overheating and damage. However, the processor isn't really overheating... it's just sending the wrong temperature. 

So, if we turn off a component called ACPI (the one that deals with thermal management, among other things), we can boot into Ubuntu. The way to do this is insert the CD, select English, and Press F6 (this lets you add boot options). Add "noapic nolapic acpi=off" to the end of that line, and hit enter. 

This will let you install and run Ubuntu. HOWEVER, turning ACPI off disables many things, including the sound card, touch screen, wireless, blutooth. Plus, the fan will run at 100% all the time.

In order to remedy this situation, we follow the instructions given by isachan to change the settings within the THERMAL MODULE  that is a part of ACPI. By overriding the Thermal Module settings, we will keep ACPI (and our Wifi, BT, sound, etc.) and avoid the premature shutdown and high fan speeds... I am about to test isachan/kv11's instructions and will report back soon if it worked for me or not.

Good luck.

---

### Post by tC_Crazy on 2008-07-15
After much fanfare, I believe I'm at the same point as isachan here. After trying his settings for /etc/modprobe.d/options (by the way, each line should read OPTIONS not OPTION... that threw errors in boot and the lines were ignored). 

Next I tried the initrd method exactly as described earlier in this thread. Still nothing. Then I went into /etc/modprobe.d/blacklist and added the line blacklist thermal.

My only boot option was nolapic (noapic throws a kernel panic)

BT works, WLAN light is on (still needs drivers), it displays battery conditions, and fan speed is reduced. :KS

---

### Post by fbdelivers on 2008-07-16
Outstanding!!  Thanks everyone for the help.

In order for me to disable acpi option I followed the initrd instructions to remove thermal.

Added the thermal options to /modprobe.d/options file

I too had to also add blacklist thermal to get things to boot.

I can no boot with acpi=off.

Wireless is working as well (BTW I followed these instructions using the 2d option - [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Sound still isn't working - I tried the following:
1. Open alsa-base configuration file:
gksu gedit /etc/modprobe.d/alsa-base

2. Add this as last row of file:
options snd-hda-intel model=hp

The mute button is working but still no sound.

Once I get sound and the touchscreen (anyone have any luck?) I can say buh bye to the vista partition.

Thanks
David

---

### Post by pluckster on 2008-07-16
Thank you Crazy for the nice and neat rundown. I tried what you gave me but I'm still getting two errors in the install process. I can't tell if they are related but I don't think they are. One is that it cannot configure my DHCP network something or other. The other is it cannot find an installable kernel in the defined APT sources. This one seems to be the deal breaker. It says I could install one later but it says I shouldn't unless I know what I'm doing. Is this normal or is this just an error I'm getting?

EDIT: It wouldn't let me install a boot loader either, which is probably because of the kernel error or at least I think.

---

### Post by tC_Crazy on 2008-07-16
Those seem to be unrelated. Have you run the CD error check yet? You may have to F6 and add the boot options noapic nolapic acpi=off with the CD error check selected. 

Did you download the newest release HH? Also, did you download the 32-bit or 64-bit version? I'm using 32-bit. It sounds like a problem with the data on the CD, but I could be wrong. If you do try to burn a new CD, keep in mind that lower speed = less errors. 

One more question, did you boot into the LiveCD and hit install, or install directly from the CD boot menu? Did it ever actually boot into Ubuntu? (wait, that's two questions... oh well!)

---

### Post by pluckster on 2008-07-16
Yeah I've made three new CDs (Line, Alt and a Live 64) after my original failed. I even downloaded Ibex Alpha 2.

But I really should have checked the CD for errors. I'll do that right now.

...


well there we go, 1 error found in 1 file. Guess its back to the burning machine.

---

### Post by tC_Crazy on 2008-07-16
slow 'n steady wins the race... if you still have trouble, try some different media.

---

### Post by isachan on 2008-07-17
Another discovery today.

I've found out I've been running with only one core with noapic boot option !I took a deep breath and tried without it this morning. Now I got my dual core back ! You can see this with the power applet (the small battery icon), just by moving the mouse cursor over it. Or you can install and see with htop app. CPU dynamic frequency thing is not working though. Maybe it works with cpufreqd ?

tC_Crazy, it's funny my machine doesn't like nolapic option and yours does. I lose my wired network connection with nolapic.

I tried suspend yesterday, and it does power down with flashing power light. However, after a recovery, the screen just stays turned-off. It's not in my urgent priority list right now, so I haven't dig deeper into troubleshooting this yet.

I'm getting tired with no sound. I even installed ALSA 1.0.17 final with a script from this thread :
[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
and it's still not working ! I had to do some driver file copying after installing from source codes, so I don't recommend for anybody. Well, it's not working anyway, so...

Isao

---

### Post by isachan on 2008-07-17
Miracle ! I have sound !

The last 2 lines of my /etc/modprobe.d/alsa-base file is like this :
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=toshiba position_fix=1

That's right, it's toshiba !

Try it with the current version of ALSA driver first to be safe.
I'm not really sure it's because I'm using ALSA 1.0.17 final ?

Make sure Master, Headphone, PCM, Front channels are not muted, and volumes are up.

I hope this works for you guys too !

Isao

---

### Post by pluckster on 2008-07-17
Still no go on the kernel installing. The DCHP(?) error still comes up to. Its weird because these CDs work on my other computer just fine but as soon as those things are disabled on the laptop, everything breaks down. 

I tried installing Ubuntu Studio of its DVD but that also didn't work. Same errors as before. Is it that hard to manually install a kernel?

EDIT: Okay well it let me finish the install this time. Still as far as I know no kernel was installed. I booted up and it let me start Ubuntu Studio. It went through to the kernel log daemon, stopped for a bit, then went to quickly through the next screen and shut itself down. Not to sure what happened but it probably has to do with the fact there is no kernel.

---

### Post by corwinspyre on 2008-07-17
Thanks to everyone in this thread!

---

### Post by corwinspyre on 2008-07-17
> **isachan said:**
> kv11, you're a God send !

I added the following lines to /etc/modprobe.d/options file :
(Edit: corrected options from option as per tC_Crazy)

options thermal.act=-1
options thermal.crt=-1
options thermal.nocrt=1
options thermal.psv=-1


This didn't work for me.  /var/log/daemon.log shows (this is also what I see at boot time):
> Jul 17 12:21:46 deathstar modprobe: WARNING: /etc/modprobe.d/options line 9: ignoring bad line starting with 'options' 
Jul 17 12:21:46 deathstar modprobe: WARNING: /etc/modprobe.d/options line 10: ignoring bad line starting with 'options' 
Jul 17 12:21:46 deathstar modprobe: WARNING: /etc/modprobe.d/options line 11: ignoring bad line starting with 'options' 
Jul 17 12:21:46 deathstar modprobe: WARNING: /etc/modprobe.d/options line 12: ignoring bad line starting with 'options' 

I copy/pasted it in from your post, so I know it's not a typo.


For the heck of it, I tried removing "options" so that it says: 
thermal.act=-1
thermal.crt=-1
thermal.nocrt=1
thermal.psv=-1
but that yields a similar error:
> Jul 17 12:21:46 deathstar modprobe: WARNING: /etc/modprobe.d/options line 14: ignoring bad line starting with 'thermal.act=-1' 
Jul 17 12:21:46 deathstar modprobe: WARNING: /etc/modprobe.d/options line 15: ignoring bad line starting with 'thermal.crt=-1' 
Jul 17 12:21:46 deathstar modprobe: WARNING: /etc/modprobe.d/options line 16: ignoring bad line starting with 'thermal.nocrt=1' 
Jul 17 12:21:46 deathstar modprobe: WARNING: /etc/modprobe.d/options line 17: ignoring bad line starting with 'thermal.psv=-1' 

Any ideas?  Thanks in advance.

---

### Post by corwinspyre on 2008-07-17
> **pluckster said:**
> Still no go on the kernel installing. The DCHP(?) error still comes up to. Its weird because these CDs work on my other computer just fine but as soon as those things are disabled on the laptop, everything breaks down. 

I tried installing Ubuntu Studio of its DVD but that also didn't work. Same errors as before. Is it that hard to manually install a kernel?

EDIT: Okay well it let me finish the install this time. Still as far as I know no kernel was installed. I booted up and it let me start Ubuntu Studio. It went through to the kernel log daemon, stopped for a bit, then went to quickly through the next screen and shut itself down. Not to sure what happened but it probably has to do with the fact there is no kernel.

If it's booting up at all, it has a kernel.  It sounds like you have the overheat issue.  You should edit the grub boot line to say acpi=off at the end, as shown in this thread, and then do one of the three various fixes (also given in this thread).

---

### Post by pluckster on 2008-07-17
I think it was just Ubuntu Studio doing something weird because it still doesn't work. I'm trying to reinstall a vanilla Ubuntu but it will not let me install the kernel or grub.

---

### Post by phrygius on 2008-07-17
> **tC_Crazy said:**
> I'll give you the run-down. The tx2500z has a problem in a component called ACPI which causes it to report very very high temperatures to Ubuntu. Ubuntu, in turn, shuts the system down to save the processor from overheating and damage. However, the processor isn't really overheating... it's just sending the wrong temperature. 

So, if we turn off a component called ACPI (the one that deals with thermal management, among other things), we can boot into Ubuntu. The way to do this is insert the CD, select English, and Press F6 (this lets you add boot options). Add "noapic nolapic acpi=off" to the end of that line, and hit enter. 

This will let you install and run Ubuntu. HOWEVER, turning ACPI off disables many things, including the sound card, touch screen, wireless, blutooth. Plus, the fan will run at 100% all the time.

In order to remedy this situation, we follow the instructions given by isachan to change the settings within the THERMAL MODULE  that is a part of ACPI. By overriding the Thermal Module settings, we will keep ACPI (and our Wifi, BT, sound, etc.) and avoid the premature shutdown and high fan speeds... I am about to test isachan/kv11's instructions and will report back soon if it worked for me or not.

Good luck.

Thank you for explaining the situation!

I just received my tx2510z on Tuesday, and was frustrated by the ACPI overheating issue before finding this thread.

I was wondering though, since I bought this tablet based on the success stories of tx2000 owners, did theirs have the same overheating problems too?  I noticed a few of those threads mention **noacpi** as a boot parameter, yet I don't remember reading anything about how turning that off yields no functionality for sound, wacom, bluetooth, etc.

Thanks,
phrygius

---

### Post by tC_Crazy on 2008-07-17
phrygius, the tx2000 is considerably different in this case, because it used a different chipset/processor/video card. The tx2500z has the new Turion 64 X2 Ultra (griffin) processors, a part of the Puma platform. I haven't looked very deep into the exact cause of the problem, but something causes ACPI to read very very high temps, and trigger a thermal shutdown. AFAIK, the tx2000 did not have thermal shutdown problems. ACPI is spidered into many components, and is pretty much essential for a USEFUL computer environment on the 2500. 

pluckster, if you have blacklisted thermal, I suggest you try futzing around with boot options. As we now see, tx2500z's react differently to different options. (mine will not work with noapic, isachan's will) The three I have messed with are noapic, nolapic, acpi=off.

isachan,
That's really interesting about the sound card... and noapic... and the fact that nolapic kills the wired connection seems to make sense to me now. My wired NIC wasn't working with nolapic, but I assumed no one's was. I followed some guide on the forums for the same NIC, and after compiling/patching a driver, it DID work. not worth the work, IMO, since wifi is probably easier to install. 

corwinspyre,
I noticed after i turned off quiet and splash boot options that I also got those "ignoring bad line" messages on boot... so I removed them. Definitely try editing /etc/modprobe.d/blacklist. Add this line ```
blacklist thermal
```
if that doesn't work, keep the blacklist and follow the initial instructions in this thread (page 2 i think). The combination of those two (or maybe just the blacklist, idk for sure) worked for me. Oh, and nolapic in the boot options, but again I'm not sure if that really did it. I'll get more evidence as to what exactly worked on my machine when i reinstall this weekend. 

btw, I think this thread has a ton of great info and collaboration... great job everyone. I'm sure many will be able to use this as a resource to get a fully-functional tablet running Ubuntu (btw2, has anyone installed the digitizer drivers yet?? that's the scary recompile-and-potentially-break-everything-wasting-your-hard-work one. Backup first!!

---

### Post by corwinspyre on 2008-07-17
> **tC_Crazy said:**
> phrygius, the tx2000 is considerably different in this case, because it used a different chipset/processor/video card. The tx2500z has the new Turion 64 X2 Ultra (griffin) processors, a part of the Puma platform. I haven't looked very deep into the exact cause of the problem, but something causes ACPI to read very very high temps, and trigger a thermal shutdown. AFAIK, the tx2000 did not have thermal shutdown problems. ACPI is spidered into many components, and is pretty much essential for a USEFUL computer environment on the 2500. 

pluckster, if you have blacklisted thermal, I suggest you try futzing around with boot options. As we now see, tx2500z's react differently to different options. (mine will not work with noapic, isachan's will) The three I have messed with are noapic, nolapic, acpi=off.

isachan,
That's really interesting about the sound card... and noapic... and the fact that nolapic kills the wired connection seems to make sense to me now. My wired NIC wasn't working with nolapic, but I assumed no one's was. I followed some guide on the forums for the same NIC, and after compiling/patching a driver, it DID work. not worth the work, IMO, since wifi is probably easier to install. 

corwinspyre,
I noticed after i turned off quiet and splash boot options that I also got those "ignoring bad line" messages on boot... so I removed them. Definitely try editing /etc/modprobe.d/blacklist. Add this line ```
blacklist thermal
```
if that doesn't work, keep the blacklist and follow the initial instructions in this thread (page 2 i think). The combination of those two (or maybe just the blacklist, idk for sure) worked for me. Oh, and nolapic in the boot options, but again I'm not sure if that really did it. I'll get more evidence as to what exactly worked on my machine when i reinstall this weekend. 

btw, I think this thread has a ton of great info and collaboration... great job everyone. I'm sure many will be able to use this as a resource to get a fully-functional tablet running Ubuntu (btw2, has anyone installed the digitizer drivers yet?? that's the scary recompile-and-potentially-break-everything-wasting-your-hard-work one. Backup first!!

Got it to work! blacklist thermal itself didn't, so I ran through the steps on page 2, and it did.  I didn't do anything else, including nolapic.  Thank you.

---

### Post by tC_Crazy on 2008-07-17
Well, I have experienced a (minor) miracle. My ubuntu partitions have NOT been wiped by the HP image =). Windows just wiped the MBR record, which was a 3 line fix using the grub console. :guitar:

I am working on wifi and sound right now.

---

### Post by phrygius on 2008-07-17
Hrm, I just tried the "options" additions to /etc/modprobe.d/options and it did not work when I removed the "acpi=off" boot option.

I **do** have the "blacklist thermal" fix in place as well :(

---

### Post by isachan on 2008-07-17
Alright guys, I got the digitizer PARTIALLY working. I got my screen protector today, so as soon as I applied, I rushed myself to go over this place :
[http://sourceforge.net/project/showfiles.php?group_id=69596](http://sourceforge.net/project/showfiles.php?group_id=69596)

and got linuxwacom-dev 0.8.1 July 9, 2008 driver.

There is a handy place for TX2000 linux info here :
[http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm)
and scroll down to the sub-topic says "Using Wacom Active Digitizer with pen".

I kinda sorta followed the instruction loosely, but let me post how I did as follows :

1. Extract the linuxwacom-0.8.1.tar.bz2 source tarball to a directory. I extracted in ~/hp-tx2500/digitizer/

2. In terminal (command line), cd to the directory created by extraction, like, "cd ~/hp-tx2500/digitizer/linuxwacom-0.8.1"

3. I had to install some more supporting libraries, as :
"sudo apt-get install libx11-dev libxi-dev x11proto-input-dev input-utils"

4. After that, do "./configure --enable-wacom --enable-hid --enable-usbmouse --enable-input" (Maybe I enabled too many things)
Check everything went good.

5. make
You may get errors depending on which supporting libraries are not installed. I'd try installing those libraries described in the TX2000 info page one by one, and recompile by typing make again.
 
6. sudo make install
6a. sudo rmmod wacom (For the first time around, you shouldn't have to do this)

7. sudo cp src/2.6.24/wacom.ko /lib/modules/2.6.24-19-generic/kernel/drivers/input/tablet/wacom.ko

8. sudo depmod -e

9. sudo modprobe wacom

10. Edit your /etc/X11/xorg.conf file as follows :

*** Add these lines to the beginning of the file:

Section "InputDevice"
	Identifier	"TabletPCStylus"
	Driver		"wacom"
	Option		"ForceDevice" "ISDV4"
	Option		"Type" "stylus"
	Option		"SendCoreEvents" "true"
	Option		"Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
	Option		"Button2" "3" # make side-switch a right button
	Option		"TopX" "225"
	Option		"TopY" "122"
	Option		"BottomX" "26365"
	Option		"BottomY" "16488"
EndSection

Section "InputDevice"
	Identifier 	"TabletPCStylus2"
	Driver		"wacom"
	Option		"ForceDevice" "ISDV4"
	Option		"Type" "stylus"
	Option		"SendCoreEvents" "true"
	Option		"Device" "/dev/input/wacom"
	Option		"TopX" "01429"
	Option		"TopY" "01150"
	Option		"BottomX" "25300"
	Option		"BottomY" "15300"
EndSection

Section "InputDevice"
	Identifier	"TabletPCStylus3"
	Driver		"wacom"
	Option		"ForceDevice" "ISDV4"
	Option		"Type" "eraser"
	Option		"SendCoreEvents" "true"
	Option		"Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
EndSection

*** And change "ServerLayout" and "Modules" sections to match the settings above :

Section "ServerLayout"
	Identifier	"Default Layout"
		screen	"Default Screen"
	Inputdevice	"Synaptics Touchpad"
	Inputdevice     "TabletPCStylus"
        Inputdevice     "TabletPCStylus2"
        Inputdevice     "TabletPCStylus3"
EndSection

Section "Module"
	Load	"wacom"
	Load	"glx"
EndSection


11. Reboot, pen should work PARTIALLY.

---

Here are the reasons why I said PARTIALLY :

Pressure sensitivity is, well, extremely sensitive. I can't draw a long stroke at all if I apply a just a bit more of extra pressure. You'll need a super-human sensitive touch. This is confirmed with Gimp. Forget about writing on CellWriter, you'll just confuse the training session.

Acts a bit funny, almost a similar experience with pressing and releasing the mouse button at the same time.

Eraser acts just like the pen.

The side button is working, acts as the right mouse button.

---

Well, it's good to see the mouse cursor follows your pen point, when it is hovering 1/4inch over the screen.

I just had to jot down my findings here quickly, so we can be headed in the right direction.

Isao

---

### Post by phrygius on 2008-07-17
As an aside, do you all think a screen protector is necessary?

---

### Post by corwinspyre on 2008-07-17
> **phrygius said:**
> As an aside, do you all think a screen protector is necessary?I never had one on my tx1000, and it wasn't a problem, but it can't hurt /shrug

---

### Post by tC_Crazy on 2008-07-17
bah, I can't get wifi to work. I had previously installed step 2b from those instructions. After doing a reinstall of ndiswrapper and then a ndiswrapper -r bcmwl5, I did the whole process again with step 2d... but even after a restart it's not detecting any new interfaces. any ideas?

---

### Post by corwinspyre on 2008-07-17
> **tC_Crazy said:**
> bah, I can't get wifi to work. I had previously installed step 2b from those instructions. After doing a reinstall of ndiswrapper and then a ndiswrapper -r bcmwl5, I did the whole process again with step 2d... but even after a restart it's not detecting any new interfaces. any ideas?
It sets it up with the wl driver automatically.  You shouldn't need ndiswrapper.  I don't know the steps you took to use ndiswrapper, but maybe try blacklisting it and un-blacklisting wl if you did when installing ndiswrapper.

---

### Post by isachan on 2008-07-17
If you'd choose to use ndiswrapper, you have to remove wl driver, and vice versa.

Also, I like screen protector from my past experience. I can see all kinds of scratches on the protector, be it on PDA, my TX1000, etc. I think it's better than exposed. Especially on TX1000, I had to touch the screen rather hard to write on it.

I'm still waiting for the next version of wl driver to be posted on the regular repository. The current one is not really working on other computers with the same wireless device either. I heard about a 2 weeks ago that it has been updated on the proposal repository, and that one should be the working version. If you search on this Ubuntu forum, you may get updates on the status of wl driver.

Isao

---

### Post by corwinspyre on 2008-07-17
> **isachan said:**
> If you'd choose to use ndiswrapper, you have to remove wl driver, and vice versa.

Also, I like screen protector from my past experience. I can see all kinds of scratches on the protector, be it on PDA, my TX1000, etc. I think it's better than exposed. Especially on TX1000, I had to touch the screen rather hard to write on it.

I'm still waiting for the next version of wl driver to be posted on the regular repository. I heard about a 2 weeks ago that it has been updated on the proposal repository. If you search on this Ubuntu forum, you may get updates on the status of wl driver.

Isao
Yep, if you enable hardy-proposed, you get the update.  I'm posting wireless from Ubuntu on my TX2500 right now, actually.  I know the dev said because of the simplicity of the fix and the positive results posted in the bug report about the fix, it got fast-tracked, so hopefully you'll have it sooner than later.

---

### Post by AstronomyDomine on 2008-07-17
Basically, inside of the acpi subsystem is a module called thermal which reads temperatures from thermal sensors in the hardware, and shuts down the computer if the temperatures reach a certain trip point.  Because the chipsets in the tx2500 are so new, thermal doesn't correctly read the sensors, and acpi shuts down the machine after the kernel is loaded.

Blacklisting thermal in /etc/modprobe.d/blacklist most likely won't solve the issue because thermal is loaded in the initramfs, so the only way to stop thermal from loading is to remove it from your initrd.  My instructions on page 2 should remove thermal from the initramfs, but this is only a temporary fix.  It will need to be done every time the kernel is upgraded until the problem is fixed.

There was also a mention of raising or eliminating the trip points in the thermal module, but I never attempted this, so I can't say whether it will work or not.

---

### Post by fbdelivers on 2008-07-18
> **isachan said:**
> Miracle ! I have sound !

The last 2 lines of my /etc/modprobe.d/alsa-base file is like this :
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=toshiba position_fix=1

That's right, it's toshiba !

Try it with the current version of ALSA driver first to be safe.
I'm not really sure it's because I'm using ALSA 1.0.17 final ?

Make sure Master, Headphone, PCM, Front channels are not muted, and volumes are up.

I hope this works for you guys too !

Isao

Sweet - your fix worked for me as well.  Thanks!

---

### Post by phrygius on 2008-07-18
Has anyone else had negative results from the **/etc/modprobe.d/options** fix?  I will try Astronomy's fix after work today and let you know how it goes.

(once again, mine is the tx2510)

Thanks,
phrygius

---

### Post by tC_Crazy on 2008-07-18
phrygius,
I didn't have a negative result per se, but Ubuntu reported on startup that it was ignoring all those lines anyway, as "bad." For me, the winning combo was AstronomyDomine's page 2 instructions, plus blacklisting thermal. I don't understand why that worked, but I know it did. Afterwards i was able to boot with no added boot options. 

Now about wireless... I never got the wl driver. Even before ndiswrapper, there was no mention of wl in the restricted drivers, and there was no wireless interface if i did an ifconfig or iwconfig. I'm pretty sure it showed up in lspci, so it does see the card.

---

### Post by isachan on 2008-07-18
tC_Crazy, what kind of wireless device came with your machine ?

You may have to use b43-fwcutter driver and firmwares.
Doing some search on Ubuntu forums may lead you to an answer.

---

### Post by isachan on 2008-07-18
I just updated my ATI fglrx graphics driver to 8.6 via EnvyNG, and man ! it's pleasing my eyes. :)

Combined with Mplayer, I can play HD 1080p content almost flawlessly with some slowdown spots.

Now I can play HD 720p content on Kaffeine player ! Before this update this movie player was too slow, and unusable. As this is my primary video content player, I was disappointed but no more !

Have you guys played racing simulation game on this machine, called Torcs ? I use that as a nice and quick benchmark tool. It's a fun way to check the performance of 3D acceleration.

---

### Post by phrygius on 2008-07-18
> **tC_Crazy said:**
> phrygius,
I didn't have a negative result per se, but Ubuntu reported on startup that it was ignoring all those lines anyway, as "bad." For me, the winning combo was AstronomyDomine's page 2 instructions, plus blacklisting thermal. I don't understand why that worked, but I know it did. Afterwards i was able to boot with no added boot options.

Update:  I tried AstronomyDomine's page 2 instructions as well, and they seem to fix the ACPI+Thermal problem!

THANK YOU Astronomy!!

I guess I wouldn't mind too much having to do this over again with new kernel updates, but it'd be awesome if a permanent fix came around.

Now, I'll have to occupy myself with attempting to get the touchscreen to work.

Thanks,
phrygius

---

### Post by isachan on 2008-07-18
Phew, I'm getting tired tweaking digitizer and the touch screen.
I'm gonna just post my in-progress results.

So now I got my touch screen part of the same wacom digitizer PARTIALLY working as well ! :)

The pressure sensing got much better, but still it releases the drag if I apply pressure slightly more. I started to get some long strokes, but still not good enough for CellWriter.

Touch screen must be calibrated, but I don't know how. I just played around with the numbers in Top X,Y and Bottom X,Y parameters, but it was a moving target. The result was just confusing by calibrating this way.

Here's my /etc/X11/xorg.conf :

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
#	Option		"SendCoreEvents" "true"
#	Option		"Device" 	"/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
#	Option		"Device"	"/dev/input/event0"	# USB ONLY
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"USB"	"on"# USB ONLY
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	Option		"Button2"	"3"# make side-switch a right button
	Option		"TopX"	"225"
	Option		"TopY"	"122"
	Option		"BottomX"	"26365"
	Option		"BottomY"	"16488"
	Option		"PressCurve"	"17,0,100,83"# Firmer Curve
	Option		"Threshold"	"-140"# sensetivity to do a "click"
	Option		"Speed"	"8.0"
#	Option		"PressCurve" 	"50,0,100,50"
#	Option		"PressCurve" 	"0,5,95,100"	#Softer Curve
#	Option		"PressCurve"	"2"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
#	Option		"SendCoreEvents" "true"
#	Option		"Device"	"/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
#	Option		"Device"	"/dev/input/event0"	# USB ONLY
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"USB"	"on"# USB ONLY
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	Option		"TopX"	"01429"
	Option		"TopY"	"01150"
	Option		"BottomX"	"25300"
	Option		"BottomY"	"15300"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
#	Option		"SendCoreEvents" "true"
#	Option		"Device"	"/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
#	Option		"Device"	"/dev/input/event0"	# USB ONLY
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"USB"	"on"# USB ONLY
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"touch"
#	Option		"SendCoreEvents" "true"
#	Option		"Device"	"/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
#	Option		"Device"	"/dev/input/event0"	# USB ONLY
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"touch"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	Option		"USB"	"on"# USB ONLY
	Option		"TopX"	"0"
	Option		"TopY"	"0"
	Option		"BottomX"	"1280"
	Option		"BottomY"	"800"
	Option		"KeepShape"	"on"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"touch"	"SendCoreEvents"
EndSection

Section "Module"
	Load		"wacom"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "ServerFlags"
#	Option		"AIGLX"	"Off"
EndSection

Section "Extensions"
#	Option		"Composite"	"Enable"
	Option		"Composite"	"Enable"
EndSection

---

### Post by AstronomyDomine on 2008-07-18
***Awesome*** job isachan.  This is the best news I've heard in a while.

I'm downloading the daily build of Intrepid right now.  I'll post back with all of my results soon.  From the sound of it, we should now have touchscreen, active digitizer, audio, and possibly wireless support now.

To those with working wireless:  Which wireless chipset do you have?  I believe that there were a few different options, one with only a/b/g, and one with a/b/g/n.

I'm also going to try to make my instructions for removing thermal on page 2 into a generic shell script so it'll be easier to run after a kernel upgrade.  I'm not exactly sure how to tell it to remove the line "thermal" from conf/module.  Anyone know how I would go about doing this?

---

### Post by isachan on 2008-07-18
Thanks, AstronomyDomine. It was truly worthwhile.

This machine really shines with Linux (Kubuntu 8.04), that I haven't boot up Vista partition for the last several days now. Ha ! I'll keep Vista until I won't see any BIOS updates from HP, like my old TX1000. I'm gonna take off Vista sticker from my TX1000 soon.

I refined my digitizer tweak with a handy tool called "Gnome Graphics Tablet Apps" : [http://alexmac.cc/tablet-apps/](http://alexmac.cc/tablet-apps/)
You can tweak and see pressure sensitivity and pressure curve very intuitively, instead of guessing values and restarting X several dozen times. For 64bit, you have to compile from the source code. It's not that hard to do.

Other very good link is here : [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

And here's my updated /etc/X11/xorg.conf :


Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"SendCoreEvents" "true"
	Option		"Device" 	"/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
#	Option		"Device"	"/dev/input/event0"	# USB ONLY
#	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"		"on"			# USB ONLY
	Option		"ForceDevice"	"ISDV4"			# Tablet PC ONLY
	Option		"Button2"	"3"			# make side-switch a right button
	Option		"TopX"		"225"
	Option		"TopY"		"122"
	Option		"BottomX"	"26365"
	Option		"BottomY"	"16488"
	Option		"PressCurve"	"20,0,100,100"		# Firmer Curve
	Option		"Threshold"	"0"			# sensetivity to do a "click"
	Option		"Speed"		"8.0"
	Option		"ClickForce"	"21"
#	Option		"PressCurve" 	"50,0,100,50"
#	Option		"PressCurve" 	"0,5,95,100"		#Softer Curve
#	Option		"PressCurve"	"2"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"SendCoreEvents" "true"
	Option		"Device"	"/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
#	Option		"Device"	"/dev/input/event0"	# USB ONLY
#	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"USB"	"on"# USB ONLY
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	Option		"TopX"	"01429"
	Option		"TopY"	"01150"
	Option		"BottomX"	"25300"
	Option		"BottomY"	"15300"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"SendCoreEvents" "true"
	Option		"Device"	"/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
#	Option		"Device"	"/dev/input/event0"	# USB ONLY
#	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"USB"		"on"			# USB ONLY
	Option		"ForceDevice"	"ISDV4"			# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"touch"
	Option		"SendCoreEvents" "true"
	Option		"Device"	"/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
#	Option		"Device"	"/dev/input/event0"	# USB ONLY
#	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"touch"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	Option		"USB"	"on"# USB ONLY
	Option		"TopX"	"0"
	Option		"TopY"	"0"
	Option		"BottomX"	"1280"
	Option		"BottomY"	"800"
	Option		"KeepShape"	"on"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"touch"		"SendCoreEvents"
EndSection

Section "Module"
	Load		"wacom"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
#	Option		"Composite"	"Enable"
	Option		"Composite"	"Disable"
EndSection

Enjoy.

---

### Post by AstronomyDomine on 2008-07-18
I have some great news.  With the daily build of intrepid, the system installs and boots ***without*** acpi=off. 

However, because it's a daily build, it's far from perfect. Ubuntu-desktop did not install, so it booted to a terminal, and I'm in the process of installing ubuntu-desktop through apt.  I'll update with progress along the way.

---

### Post by Weststar on 2008-07-18
Thanks for all of this info! =)

Would someone be able to make a Step by Step for people like me who suck at linux?

---

### Post by AstronomyDomine on 2008-07-18
> **Weststar said:**
> Thanks for all of this info! =)

Would someone be able to make a Step by Step for people like me who suck at linux?

No problem.  I'll throw together a howto if needed once we get the last few things figures out.  Right now we've fixed the acpi shutdown problems in Hardy by removing the thermal module from the initramfs.  There's a step by step on page 2 for that.  

We've also got sound working.  It only involves adding two lines to a file (more info on page 3 or 4), so that's not too bad. 

Finally, we've got basic touchscreen and active digitizer support on page 5, but make sure to use isachan's latest xorg.conf posted on page 7.




I've been having some great success using today's daily of Intrepid.  The acpi issues must be solved in 2.6.26 because I never once had to use acpi=off.  I was easily able to boot and install, so things are going pretty well.  

I'm having some troubles getting fglrx installed and running, but it seems to be because of bugs in Intrepid, nothing to do with the hardware.

I also couldn't get the wireless working.  I tried following the instructions on the link posted on page 3, but it didn't work for me.  I have the Broadcom BCM4322 a/b/g/n card.

Finally, following isachan's instructions, I was able to get the active digitizer working very well.  There are definitely some touch sensitivity problems, but we should be able to get those ironed out pretty soon.  I wasn't as lucky with the resistive digitizer (touchscreen).  It seems to work, but needs a lot of calibration.  It doesn't move the cursor anywhere near my finger.

We've made great progress everybody.  Just a few weeks ago I was seriously considering returning this tablet because of all of the problems I was having.  Now I love it! Lets keep pushing forward and we'll have the last few problems fixed in no time.

I'm going to get back to trying to get fglrx working in Intrepid.  I'll post back with any more results.

---

### Post by thegnark on 2008-07-18
> **Weststar said:**
> Thanks for all of this info! =)

Would someone be able to make a Step by Step for people like me who suck at linux?


[LIST=1]
[*]Wait until Oct 30, 2008
[*]Install Intrepid Ibex
[/LIST]
;)

Honestly it sounds like it might be a little easier to wait for Intrepid... I'm going to consider installing once Alpha 3 comes out and see how it goes... I don't mind tweaking around, and reinstalls don't bother me much.

---

### Post by tC_Crazy on 2008-07-18
Astronomy, I have the same bcm4322ag a/b/g/n/BT card. I'm going to play with it for a little while today and see if I can get wl or ndiswrapper to pick it up.

---

### Post by kv11 on 2008-07-19
A little explanation about changing trip points of thermal module (it seems that my previous post was a bit confusing). There are two ways of doing it:

1. First method: module options. Add the following lines to /etc/modprobe.d/options
```

options thermal psv=-1 act=-1 crt=-1 nocrt=1

```
(note the **space** after thermal, not a dot!). You could also try experimenting with different numerical values to retain the ability to automaticaly control fan speed and shutdown on overheat:
```

# psv is passive trip point value in degrees C
# act is active trip point value in degrees C
# crt is critical trip point value in degrees C
# nocrt should *not* be included in this line
#
# actual values in the following line are random,
# you should try-and-select them yourself (probably based on
# values of temperature in /proc/acpi/thermal_zone/*/*) and
# post here in case of success !
#
options thermal psv=60 act=100 crt=150

```

2. Second method: kernel boot parameters (should always work independing of whether thermal module is loaded from initrd or root). Add the following to your kernel command line (along with nolapic noapic and other options in /boot/grub/menu.lst):
```

thermal.psv=-1 thermal.act=-1 thermal.crt=-1 thermal.nocrt=1

```
(note the **dot** after thermal, not a space). As with previous method you could also try setting numerical values.

---

### Post by pluckster on 2008-07-19
Well I almost had it.

After finding out what my problem was with the kernel, I found this thread explaining how to install the kernel manually, [http://ubuntuforums.org/archive/index.php/t-3444.html](http://ubuntuforums.org/archive/index.php/t-3444.html). I followed the instructions and the kernel happily loaded. 

On rebooting I entered the usual commands(noacpi noapic etc) and I got to a login screen for the first time(Hooray!). Logged in fine and other than screen resolution, lack of any sort of network connection and the other usual problem you've been having, it seemed to work fine. Then I ran through Astronomy's steps to getting the thermal off and boot ready.

Rebooted and wouldn't boot up Ubuntu anymore. I think my first error was a kernel panic. I tried other boot options but they came back with either kernel panics or just other errors

---

### Post by isachan on 2008-07-19
pluckster,

I don't think you'd need any of kernel boot option if you're using a new kernel version above 2.6.26, as per AstronomyDomine's previous post. I'm not using any boot option other than the regular ones, like "ro quiet splash" after following the instruction to remove thermal module from kernel. Also, I thought AstronomyDomine has successfully ran Ibex which comes with kernel 2.6.26 without any boot option ?

Anyway, I think you have to run "sudo update-initramfs -u" from recovery boot-up. You have to somehow get to command line to run it. Then reboot, and see how it goes. I had the same problem when I was using Gutsy, and that was after a regular kernel update ! 

Isao

---

### Post by corwinspyre on 2008-07-19
Plukster, if you get it booted up again, enabling the restricted driver and restarting (or restarting the x server with ctrl-alt-backspace) will set it to the right resolution automagically

---

### Post by neutronstar21 on 2008-07-19
Hi all,

Ive just got myself a new HP TX2500 and I love this machine.  Ive followed some of the instructions in this thread and my machine is running Ubuntu 8.04 very well after the initial thermal issues.  You guys have been awesome at seeking and destroying the barriers to Ubuntu joy so a big thank you from me.  

Just for the record Ubuntu Hardy is running well after:
- Installing from Ubuntu 8.04 64-bit install with acpi=off in boot line
- Removing the module thermal from my initramfs as per page 2, post #17 of this thread
- NOT adding specific thermal options as per page 3, post #24 
- Blacklisting the thermal control, same thread, page 5, post #43
- NOT requiring nolacpi in boot line
- Sound working after specific post on page 4, post #46
- Wireless Broadcom 4328 rev 03 showing blue light after all this but requiring the instructions in this link -- [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
  
The following is not working (but i havent worked on it yet):
- Wacom touchscreen

You guys are doing a great job.  Keep it up.  Until  I work out to send official thanks, consider yourselves THANKED!

---

### Post by corwinspyre on 2008-07-19
> **neutronstar21 said:**
> Hi all,

Ive just got myself a new HP TX2500 and I love this machine.  Ive followed some of the instructions in this thread and my machine is running Ubuntu 8.04 very well after the initial thermal issues.  You guys have been awesome at seeking and destroying the barriers to Ubuntu joy so a big thank you from me.  

Just for the record Ubuntu Hardy is running well after:
- Installing from Ubuntu 8.04 64-bit install with acpi=off in boot line
- Removing the module thermal from my initramfs as per page 2, post #17 of this thread
- NOT adding specific thermal options as per page 3, post #24 
- Blacklisting the thermal control, same thread, page 5, post #43
- NOT requiring nolacpi in boot line
- Sound working after specific post on page 4, post #46
- Wireless Broadcom 4328 rev 03 showing blue light after all this but requiring the instructions in this link -- [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
  
The following is not working (but i havent worked on it yet):
- Wacom touchscreen

You guys are doing a great job.  Keep it up.  Until  I work out to send official thanks, consider yourselves THANKED!

To add to the list, the b/g (a/b/g?--I don't know for sure; whatever the basic one is) card is bcm4310 rev2, and it works as of a patch currently in hardy-proposed.

---

### Post by pluckster on 2008-07-20
Ibex wont even start for me. Can't get a desktop or install even with the boot params. It just hangs with a flashing cursor. I have to do a hard shutdown to restart.

Also having a problem with temp still. Even with acpi off its still catching the temp and shutting me down.

I tried "sudo update-initramfs -u" but I'm not sure what to think. I booted up and did some new things like try to connect through Ethernet. But when I tried to shut down it wouldn't go all the way. Trying a reboot now. And it fails. With all boot params it still fails.

---

### Post by AstronomyDomine on 2008-07-20
> **pluckster said:**
> Ibex wont even start for me. Can't get a desktop or install even with the boot params. It just hangs with a flashing cursor. I have to do a hard shutdown to restart.

Also having a problem with temp still. Even with acpi off its still catching the temp and shutting me down.

I tried "sudo update-initramfs -u" but I'm not sure what to think. I booted up and did some new things like try to connect through Ethernet. But when I tried to shut down it wouldn't go all the way. Trying a reboot now. And it fails. With all boot params it still fails.

Wait for Alpha 3.  It should be out in four days.  Maybe.

---

### Post by wabre on 2008-07-20
sorry guys for "spamming" with an older model of the tx..i've got the tx2120us and also trying the 64bit version of Ibex now (k-/and ubuntu).

the only way i managed to start it (installing and then booting after install) is to move the hard reset shutdown button. BUT, not until it fully shuts down. Here is the strange thing, just a second before it actually should shut down, the boot up continues!! i am so surprised. 

now i'm playing around with BIOS settings as well, the tx2000 series has another platform as the tx2500, but from what i can read, the problems are actually similar.

and yes, hopefully alpha 3 will be better in this regard. at least hoping we get the chance to install it without any big issues

---

### Post by corwinspyre on 2008-07-20
> **wabre said:**
> sorry guys for "spamming" with an older model of the tx..i've got the tx2120us and also trying the 64bit version of Ibex now (k-/and ubuntu).

the only way i managed to start it (installing and then booting after install) is to move the hard reset shutdown button. BUT, not until it fully shuts down. Here is the strange thing, just a second before it actually should shut down, the boot up continues!! i am so surprised. 

now i'm playing around with BIOS settings as well, the tx2000 series has another platform as the tx2500, but from what i can read, the problems are actually similar.

and yes, hopefully alpha 3 will be better in this regard. at least hoping we get the chance to install it without any big issues

the tx2500 never stops booting alone, it shuts down half way through the boot or soon thereabouts, so if I'm reading correctly, they aren't similar problems.  Plus, it was reported that that problem doesn't happen in Ibex.  I know there's a really long tx2000 thread (either 18 or 26 pages--I forget) on here, so i'd check that out if you haven't already

It could also be something with Ibex.  Have you tried Hardy, and does it do the same thing?

---

### Post by pluckster on 2008-07-20
Okay I just have to make sure I'm doing this right becasue I'm not getting to anywhere close to what  you guys are getting so here are the steps I'm taking
[LIST=1]
[*]Start Alternate Installer with acpi=off noapic nolapic
[*]Go through installation
[*]Install the kernel using aptitude just after it configures the APT sources becasue it cannot find one
[*]Finish installation
[*]Reboot and boot with acpi=off noapic nolapic
[*]Login
[*]Type in the steps given by Astronomy on page two
[*]blacklist thermal
[*]reboot
[*]leave in only noapic nolapic
[*]Hangs while running through boot sequence
[*]Hard shutdown and sigh
[/LIST]

Am I missing something or should I just wait for alpha 3?

P.S. Does acpi=off disable ethernet connections too because mine will not work.

---

### Post by tC_Crazy on 2008-07-20
OK, I have wireless! My whole wireless driver situation was screwed up, so I decided to just reinstall ubuntu. Now pluckster, this is exactly what I did from initial startup. I put in the Ubuntu standard CD (not alternate), added boot options nolapic noapic acpi=off. I started up, ran through the installer. When finished, I started up with the same boot options. Ubuntu loaded, i logged in, and followed Astronomy's instructions exactly. I then added the line "blacklist thermal" to /etc/modprobe.d/blacklist. I rebooted, this time without the boot options, and everything (including wired LAN) worked fine. 

Then to get the bcm4322ag card working, I installed ndiswrapper (both packages in synaptic--common and utils). I also blacklisted b43 and ssb, although that was on my own and idk if it was necessary. I downloaded an HP driver for the broadcom card, here: [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=447687&swItem=ob-60549-1&mode=3](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=447687&swItem=ob-60549-1&mode=3)


Next, I installed cabextract (sudo apt-get install cabextract). I ran "cabextract sp39243.exe". This gave me the driver files necessary for ndiswrapper. I then ran the following in the directory of the driver files:

```
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

```

At which point I received: bcmwl5 : driver installed
	device (14E4:432B) present

Then, ```
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

```

At this point, I could (finally) see wireless networks, and ifconfig showed wlan0. I input my WEP key and within seconds was associated to the AP. I then unplugged my ethernet cable, and was browsing! I hope this helps you guys having trouble with the bcm4322ag (a/b/g/n/BT).

---

### Post by corwinspyre on 2008-07-20
> **pluckster said:**
> Okay I just have to make sure I'm doing this right becasue I'm not getting to anywhere close to what  you guys are getting so here are the steps I'm taking
[LIST=1]
[*]Start Alternate Installer with acpi=off noapic nolapic
[*]Go through installation
[*]Install the kernel using aptitude just after it configures the APT sources becasue it cannot find one
[*]Finish installation
[*]Reboot and boot with acpi=off noapic nolapic
[*]Login
[*]Type in the steps given by Astronomy on page two
[*]blacklist thermal
[*]reboot
[*]leave in only noapic nolapic
[*]Hangs while running through boot sequence
[*]Hard shutdown and sigh
[/LIST]

Am I missing something or should I just wait for alpha 3?

P.S. Does acpi=off disable ethernet connections too because mine will not work.

Maybe try without noapic and nolapic.  I never used those.

And, acpi=off disables wireless but not wired networking.

---

### Post by AstronomyDomine on 2008-07-20
> **pluckster said:**
> Okay I just have to make sure I'm doing this right becasue I'm not getting to anywhere close to what  you guys are getting so here are the steps I'm taking
[LIST=1]
[*]Start Alternate Installer with acpi=off noapic nolapic
[*]Go through installation
[*]Install the kernel using aptitude just after it configures the APT sources becasue it cannot find one
[*]Finish installation
[*]Reboot and boot with acpi=off noapic nolapic
[*]Login
[*]Type in the steps given by Astronomy on page two
[*]blacklist thermal
[*]reboot
[*]leave in only noapic nolapic
[*]Hangs while running through boot sequence
[*]Hard shutdown and sigh
[/LIST]

Am I missing something or should I just wait for alpha 3?

P.S. Does acpi=off disable ethernet connections too because mine will not work.

Are you using Alpha 2 or a daily build?  Either way, it'd probably be easiest to wait for alpha 3.  With Intrepid, you should never need to set acpi=off.  It should just work, or I'm just really lucky.


tC:  Awesome news.  Following your instructions I was able to get the device recognized.  I'm having trouble getting it to connect to a network, but since you didn't have a problem, I'm guessing it has something to do with Intrepid.  I'll keep working at it.

Has anyone tried to run on batter power?  When I do, I get about an hour and a half battery life on my 8 cell battery.  We should be able to improve this somehow.  Any ideas?

---

### Post by tC_Crazy on 2008-07-20
I too noticed that battery life is quite horrendous right now. I think some serious power management is in order.

---

### Post by pluckster on 2008-07-20
> **AstronomyDomine said:**
> Are you using Alpha 2 or a daily build?  Either way, it'd probably be easiest to wait for alpha 3.  With Intrepid, you should never need to set acpi=off.  It should just work, or I'm just really lucky.


This happens with both Hardy and Intrepid, well the not working part at least. Hardy will at least realize its broken and shutdown while Intrepid just hangs.

I will take another crack at TCs instructions once more then if that fails I will just wait for Alpha 3

@corwinspyre - So my ethernet should be working? Ill have to try some other cables or something because it doesn't seem to work right now.

---

### Post by corwinspyre on 2008-07-20
> **pluckster said:**
> This happens with both Hardy and Intrepid, well the not working part at least. Hardy will at least realize its broken and shutdown while Intrepid just hangs.

I will take another crack at TCs instructions once more then if that fails I will just wait for Alpha 3

@corwinspyre - So my ethernet should be working? Ill have to try some other cables or something because it doesn't seem to work right now.

yeah, ethernet should be working

---

### Post by Weststar on 2008-07-21
Good to see Wifi working, tC! So what else is left? Just more touchscreen stuff?

---

### Post by isachan on 2008-07-21
Touchscreen / digitizer has a few bugs in the wacom linux driver 0.8.1-dev version. I have received a reply from author in email, that he is releasing next version soon to address some critical issues.

I'll post how it goes as soon as I install it.

---

### Post by chdist_gentoo on 2008-07-21
Thank you all very kindly for your support with this laptop, I've been able to establish a usable system because of your help.

Currently, my only kernel parameter is: "lapic_timer_c2_ok"

I recently realized that "nolapic" was disabling my second core; so, I looked in to the apic sources for additional parameters that wouldn't strictly disable LAPIC and I found the aforementioned parameter.

This seems to remove the kernel panic I was experiencing with full LAPCI enabled (timer issue) and allows the laptop to power down when halted.

Every other subsystem seems to work like a charm.
My remaining issues are:
-Better performance/battery consumption
-Functional webcam driver
-Working IR remote
-Display rotation (presumably under F/OSS driver) coupled with tablet input rotation

---

### Post by corwinspyre on 2008-07-21
> **chdist_gentoo said:**
> Thank you all very kindly for your support with this laptop, I've been able to establish a usable system because of your help.

Currently, my only kernel parameter is: "lapic_timer_c2_ok"

I recently realized that "nolapic" was disabling my second core; so, I looked in to the apic sources for additional parameters that wouldn't strictly disable LAPIC and I found the aforementioned parameter.

This seems to remove the kernel panic I was experiencing with full LAPCI enabled (timer issue) and allows the laptop to power down when halted.

Every other subsystem seems to work like a charm.
My remaining issues are:
-Better performance/battery consumption
-Functional webcam driver
-Working IR remote
-Display rotation (presumably under F/OSS driver) coupled with tablet input rotation

The webcam should be working.  Try installing cheese to test it out (if you haven't already)

---

### Post by tC_Crazy on 2008-07-22
> **chdist_gentoo said:**
> Thank you all very kindly for your support with this laptop, I've been able to establish a usable system because of your help.

Currently, my only kernel parameter is: "lapic_timer_c2_ok"

I recently realized that "nolapic" was disabling my second core; so, I looked in to the apic sources for additional parameters that wouldn't strictly disable LAPIC and I found the aforementioned parameter.

This seems to remove the kernel panic I was experiencing with full LAPCI enabled (timer issue) and allows the laptop to power down when halted.

Every other subsystem seems to work like a charm.
My remaining issues are:
-Better performance/battery consumption
-Functional webcam driver
-Working IR remote
-Display rotation (presumably under F/OSS driver) coupled with tablet input rotation

Try scanning through the tx2000 threads for the rotation instructions. They had it down to a couple scripts, I think.

---

### Post by corwinspyre on 2008-07-22
> **tC_Crazy said:**
> Try scanning through the tx2000 threads for the rotation instructions. They had it down to a couple scripts, I think.

I believe the tx2000 uses an nvidia video card, which has a function built into the driver for screen rotation and which is what they used.  If that's true, it won't work for us.

---

### Post by kg6gfq on 2008-07-22
> I believe the tx2000 uses an nvidia video card, which has a function built into the driver for screen rotation and which is what they used. If that's true, it won't work for us.

The tx2000 does use an nVidia card, but they were using xrandr for the screen rotation, which ought to work just as well with the ATI Radeon card in the tx2500.  

Here are some links to info on xrandr, info on rotating the wacom input, and a few scripts put together for the tx2000:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")  
[http://ubuntuforums.org/showthread.php?p=4731847&highlight=xrandr#post4731847]("http://ubuntuforums.org/showthread.php?p=4731847&highlight=xrandr#post4731847")
[http://ubuntuforums.org/showthread.php?p=4812335&highlight=xrandr#post4812335]("http://ubuntuforums.org/showthread.php?p=4812335&highlight=xrandr#post4812335")
[http://ubuntuforums.org/showthread.php?p=4910414&highlight=xrandr#post4910414]("http://ubuntuforums.org/showthread.php?p=4910414&highlight=xrandr#post4910414")
[http://ubuntuforums.org/showthread.php?p=4923527&highlight=xrandr#post4923527]("http://ubuntuforums.org/showthread.php?p=4923527&highlight=xrandr#post4923527")
[http://ubuntuforums.org/showthread.php?p=5020078&highlight=xrandr#post5020078]("http://ubuntuforums.org/showthread.php?p=5020078&highlight=xrandr#post5020078")
The first one is general information, the rest are solutions which become both more complex and more polished toward the end of the list.  

I would try to sort this out myself, but I don't yet have a tx2500.  I'm considering getting one, though, so thank you to everyone who has posted here with info about the laptop.  One question: Does anyone know if the S-video and VGA ports work properly?  

Thanks for all the info and solutions!

---

### Post by tC_Crazy on 2008-07-23
kg,
I assume the ports are working properly, since I'm using an ATI restricted driver. I can check for you tonight.

---

### Post by kv11 on 2008-07-24
Have anyone got touchscreen working ? How precise is the navigation using the pen ? For me, the actual position of the click could be 1-3 mm away from the position of the end of the stylus, nomater how I calibrate the screen (i.e. it's precise at the points where is was calibrated, but not precise at another points). The same issue is also seen in pre-installed windows. Is it normal for tx2500 or I just have broken screen ?

---

### Post by corwinspyre on 2008-07-24
> **kv11 said:**
> Have anyone got touchscreen working ? How precise is the navigation using the pen ? For me, the actual position of the click could be 1-3 mm away from the position of the end of the stylus, nomater how I calibrate the screen (i.e. it's precise at the points where is was calibrated, but not precise at another points). The same issue is also seen in pre-installed windows. Is it normal for tx2500 or I just have broken screen ?

Mine isn't like that.  However, I did notice the sensor is in the pen, not the tip, so holding it straight up is different than holding it at an angle (as one normally holds a pen).  At first I made the mistake of calibrating it with the pen straight up, so when I used it regularly, it seemed off.  If you calibrated it with the pen held in a way other than which you normally use it, try again with that in mind.

---

### Post by tC_Crazy on 2008-07-24
My pen is quite precise after calibration in Windows... I usually calibrate once daily, since it only takes a few seconds. Make sure you hold the pen exactly as you do when inking. The only place where I noticed a drop in accuracy is around the edges (for example, it's difficult to use taskbar tray icons with the pen.

---

### Post by ungermax on 2008-07-25
I have a tx2510us, I was able to boot without ACPI=OFF by compiling a custom kernel without including the thermal zone option.  Instantly, the Wifi works with ndiswrapper 1.53 and the light is blue!  Still working on the touchscreen and sound however.  I realize that isn't an ideal solution, but it hasn't blown up on me yet.

---

### Post by pluckster on 2008-07-25
So I've downloaded Ibex Alpha 3 and tried it out. Its working quite a bit better than the others I've tried so far. It can now boot into a desktop without noapic and nolapic but I still have to use acpi=off otherwise it will hang with a blinking cursor. I haven't tested any of the features yet, I'll try an install soon instead then see what works and what doesn't.

---

### Post by corwinspyre on 2008-07-25
> **ungermax said:**
> I have a tx2510us, I was able to boot without ACPI=OFF by compiling a custom kernel without including the thermal zone option.  Instantly, the Wifi works with ndiswrapper 1.53 and the light is blue!  Still working on the touchscreen and sound however.  I realize that isn't an ideal solution, but it hasn't blown up on me yet.

The sound fix is in this thread

---

### Post by corwinspyre on 2008-07-25
> **pluckster said:**
> So I've downloaded Ibex Alpha 3 and tried it out. Its working quite a bit better than the others I've tried so far. It can now boot into a desktop without noapic and nolapic but I still have to use acpi=off otherwise it will hang with a blinking cursor. I haven't tested any of the features yet, I'll try an install soon instead then see what works and what doesn't.

Did you try Hardy without noapic and nolapic?  Because it was fine for me without those.

---

### Post by pluckster on 2008-07-25
> **corwinspyre said:**
> Did you try Hardy without noapic and nolapic?  Because it was fine for me without those.

Yeah, I tried all the combinations  possible and I think the only time it worked without one of those is with acpi=off nolapic.

But I did an install and I'm in the same spot as usual. I'll have to disable thermal and that but my ethernet is non responsive still. Had to boot with acpi=off to get to desktop. But now I don't need to enable GNOME fail safe to get the desktop to work.

---

### Post by tC_Crazy on 2008-07-25
nolapic kills ethernet. If you have wireless, try using ndiswrapper with the instructions I posted before... it's much easier than compiling the ethernet driver. Put the tarball on a USB drive or find another way to get ndiswrapper onto your laptop, as well as the HP executable.. and cabextract.

---

### Post by pluckster on 2008-07-26
Even without nolapic my ethernet will not work. 

As for the wireless I'm sure it will work but my dorm doesn't have wifi (The rest of the campus does, go figure) so I want to get this ethernet problem solved.

On another note, after following Astronomy's directions for thermal and boot options, it will not shutdown. It will go through all the stuff and then just end with a System Halted line and stays on. And also when I restart it just hangs without acpi=off.

---

### Post by isachan on 2008-07-26
pluckster, would you list the content of your /etc/network/interfaces file by doing "cat /etc/network/interfaces" ?

If you see eth0 for wired network interface, try "sudo ifup eth0" and "dhclient eth0".

---

### Post by pluckster on 2008-07-26
Lets see here...

```
auto lo
iface lo inet loopback
```

Hmm no sign of eth0 or much of anything

---

### Post by isachan on 2008-07-26
pluckster,

Append the following lines in /etc/network/interfaces file after the two lines you already have :

auto eth0
iface eth0 inet dhcp

save, and do "sudo ifup eth0", and let me know how it goes.

---

### Post by pluckster on 2008-07-26
Still no good.

Did something along the lines of...

```
already a pid file
removed it

started listening and sending
did 5 DHCPDISCOVERs
No DHCPOFFERS
sleeping
grep /etc/resolv.conf (didnt exist)
grep /etc/network/run/ifstate (didn't exist) x2
```

Thats it. Odd

---

### Post by isachan on 2008-07-26
Seems like some important config files are missing from the Ibex Alpha 3.

Alternatively, let me suggest using "Wicd" GUI network config app.
Download it and follow the installation guide. 
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

This thing is much better than networkmanager. In fact networkmanager destroys some very crucial config files, that I hate it and avoid like a plague.

I'm sure searching and setting up network from command line is necessary at this point. There is a how-to on the Ubuntu forum.

---

### Post by AstronomyDomine on 2008-07-26
sudo dhclient eth0

How's the touchscreen progress going isachan?  I saw there was a minor revision to the linuxwacom project dev files.  Is that what we were waiting for, or are we waiting for the next official release?

Has anyone had any luck getting fglrx working in Intrepid?  I can't seem to get 8.6 or 8.7 to install.

---

### Post by isachan on 2008-07-26
AstronomyDomine,
Yeah, it's been a while since last time said something about the latest wacom development driver, hasn't it ? Well, the reason is that 0.8.1-1 is not working well. The previous version was much better. The pen no longer register any clicks, so I can't write / draw anything. The touch screen is unchanged, works like before, with off-calibration.

By using wacomdump version 0.7.4 utility, I can see the pressure sensitivity bug has been sorta fixed, but looks strange in raw value. Eraser is recognized, not as another pen tip like the previous version.

I sent off 2 emails to the author asking questions but so far, I haven't received any reply. The documentation on the web site is quite old that only few of the information is applicable. I heard somewhere that so many protocols in the driver has been straighten out, and there are many more to fix.

I've found the bug in the source code from the previous version 0.8.1, so maybe I can try that when I have some time.

---

### Post by pluckster on 2008-07-26
Okay well I tried running it without acpi=off and it seems to keep going until it reaches this line

```
[0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
```

I'm looking in to what it might mean but does anyone here have any ideas?

---

### Post by isachan on 2008-07-27
pluckster,
I think your LiveCD has been corrupted at some point.
I'm writing this post from Kubuntu 8.10 Alpha 3 I just downloaded.
It has booted successfully without any kernel boot option, and KDE 4.1 looks so pretty. I can see many little bugs, but hey, it sure looks good.

I suggest downloading the CD image again and verify the checksum with md5 command.

Since Hardy has long term support, I don't think I'll go into any version above it. And I don't know why some people are trying to use Ibex already ? Especially now that we already conquered the thermal issue ? I prefer the stable LTS version.

---

### Post by thegnark on 2008-07-27
[SIZE=4][COLOR=Red]**This has been posted as a HOWTO in the Tutorial & Tips forum. I will be updating that post instead of this one. [Take me there!]("http://ubuntuforums.org/showthread.php?t=873188")**[/COLOR][/SIZE]

I spent a long time configuring everything, and I thought I'd compile a quick writeup. I decided to re-install to meticulously document each step. This guide assume that you have at least basic working knowledge of using Ubuntu. If this is your first time using Linux, I'm recommending that you do not attempt to install Hardy Heron on the tx2500 at this time.

**This is based on [Ubuntu 8.04.1]("http://cdimage.ubuntu.com/releases/hardy/release/") x64 (Hardy Heron LTS)**. It probably works for 32-bit, but I haven't tested and don't see a specific reason to go with 32-bit over 64-bit.

Known issues:

[LIST]
[*]Digitizer *mostly* works (but not 100%)
[*]CPU scaling is NOT supported by current kernel
[*]Suspend/sleep is a bit flaky
[/LIST]
  [[SIZE=4]Installation[/SIZE]]("http://ubuntuforums.org/showpost.php?p=5426140&postcount=80")

[LIST=1]
[*]Boot installation disc
[*]Highlight your language and press [Enter]
[*]Highlight"Install Ubuntu"
[*]Press F6
[*]Press F6 (again)
[*]Highlight "acpi=off" and press [Enter].  small "x" should appear to the left of this option
[*]Press [Esc]
[*]Press [Enter]
[*]This should boot to a graphical installer
[*]*Install as normal*
[*]After installation is complete, reboot as instructed
[/LIST]
 [[SIZE=4]First boot[/SIZE]]("http://ubuntuforums.org/showpost.php?p=5426140&postcount=80")

[LIST=1]
[*]Highlight the first boot option (Ubuntu 8.04.1, kernel 2.6.24-19-generic)
[*]Press 'e' to edit the boot options
[*]Scroll down to the line that starts with "kernel"
[*]Press 'e' to edit this command
[*]Scroll to the end of the line and add the following option (no quotes): "acpi=off". The boot options should have the following options listed: "ro quiet splash acpi=off"
[*]Press '[Enter]' to confirm you are done editing the line
[*]Press 'b' to boot
[*]This should boot you to a graphical display prompt.
[/LIST]
[SIZE=4]Configuring Ubuntu[/SIZE]
This *should* get your Wireless working with an update to wl; also, a slightly newer kernel version is here. 

[LIST=1]
[*][Blacklist thermal]("http://ubuntuforums.org/showpost.php?p=5426140&postcount=80")
[LIST=1]
[*]Open a terminal
[*]Run "sudo gedit /etc/modprobe.d/blacklist"
[*]Add this text on its own line at the bottom of the file:
blacklist thermal
[*]Save and close
[/LIST]
 
[*][Enable sound]("http://ubuntuforums.org/showthread.php?p=5402251#post5402251")
[LIST=1]
[*]Open a terminal
[*]Run "sudo gedit /etc/modprobe.d/alsa-base"
[*]Add the following line to the bottom of the file:
options snd-hda-intel index=0 model=toshiba position_fix=1
[*]Save
[*]Close
[/LIST]
 
[*][Update to proposed updates]("http://ubuntuforums.org/showpost.php?p=5408040&postcount=53") (Fixes wireless and updates to kernel 2.6.24-20)
***Note:** Once these updates are moved from proposed to the standard repository, enabling "proposed" may not be required. In this case, skip this step.*
[LIST=1]
[*]Plug in to an ethernet port
[*]Verify that you have internet access
[*]Open up Synaptic
[LIST=1]
[*]System
[*]Administration
[*]Synaptic Package Manager
[/LIST]
 
[*]Enable Hardy Proposed to your repositories
[LIST=1]
[*]Settings
[*]Repositories
[*]Updates
[*]Check "Pre-released updates (hardy-proposed)
[*]Click the "Close" button
[*]Confirm the message box that pops up warning you to reload
[/LIST]
 
[*]Click "Reload"
[*]Click "Mark All Upgrades"
[LIST=1]
[*]Click "Mark"
[/LIST]
 
[*]Click "Apply"
[LIST=1]
[*]Click "Apply"
[/LIST]
 
[*]After updates are complete, click "Close"
[/LIST]
 
[*][Enable the digitizer]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447"). Instructions are somewhat complicated, so I'm just providing a link to the thread instead of replicating here.
[*]Install ATI restricted driver
[LIST=1]
[*]Go to your restricted drivers manager
[LIST=1]
[*]System
[*]Administration
[*]Hardware Drivers
[/LIST]
 
[*]Check "ATI restricted driver
[LIST=1]
[*]Click "Enable"
[/LIST]
 
[/LIST]
 
[*]**Reboot as normal**
[/LIST]
 If there's anything you would like to add or correct, post and I'll try to update as appropriate. Also, feel free to check out [**HP Pavilion tx2000 series laptop runnign (sic) Ubuntu 8.04 - My Howto**]("http://mirosol.kapsi.fi/tx2020/tx2000howto.htm").

---

### Post by AstronomyDomine on 2008-07-27
Great instructions thegnark.  Did you try booting at first without apci=off?  The reason I ask is because thermal is loaded in the initramfs, so blacklisting it really shouldn't prevent it from loading.  I'm wondering if perhaps our apic problems have been fixed in 8.04.1.  Perhaps it was a kernel update from Hardy Proposed.  I'm think I'll install 8.04.1 and see what I can find.

Thanks again!

---

### Post by pluckster on 2008-07-27
> **isachan said:**
> pluckster,
I think your LiveCD has been corrupted at some point.
I'm writing this post from Kubuntu 8.10 Alpha 3 I just downloaded.
It has booted successfully without any kernel boot option, and KDE 4.1 looks so pretty. I can see many little bugs, but hey, it sure looks good.

I suggest downloading the CD image again and verify the checksum with md5 command.

Since Hardy has long term support, I don't think I'll go into any version above it. And I don't know why some people are trying to use Ibex already ? Especially now that we already conquered the thermal issue ? I prefer the stable LTS version.

I don't think its likely. This is pretty much the same outcome on the many distros I've tested, new and old. I popped in fedora last night and it ends at the exact same line. I'll have to bust out my other Ubuntu machine to download and test the MD5 sums.

---

### Post by isachan on 2008-07-27
pluckster,

What is your BIOS setting on "Virtualization Technology" ?
Is it enabled or disabled ? Mine is disabled.

"Fan Always On" is certainly disabled.

---

### Post by fbdelivers on 2008-07-27
I'm not a huge fedora fan - but did anyone else notice this post or tried fedora with the 2500?

[http://forum.tabletpcreview.com/showthread.php?p=121795](http://forum.tabletpcreview.com/showthread.php?p=121795)

From the post it looks like everything works out of the box...

---

### Post by thegnark on 2008-07-27
> **fbdelivers said:**
> I'm not a huge fedora fan - but did anyone else notice this post or tried fedora with the 2500?

[http://forum.tabletpcreview.com/showthread.php?p=121795](http://forum.tabletpcreview.com/showthread.php?p=121795)

From the post it looks like everything works out of the box...

Actually, based on that post, I downloaded Fedora 9 with intent to test compatibility...

Turns out that it never boots to installation... Freezes at some point and just sits there forever :confused:

---

### Post by thegnark on 2008-07-27
AstronomyDomine: I tried the following additional boot options:

[LIST]
[*] <nothing>
[*] noapic
[*] nolapic
[*] noapic nolapic
[*] pci=conf1
[*] acpi=off
[/LIST]
 The only option to successfully boot was "acpi=off"

Also, I tried a couple of different configurations trying to boot into a fresh installation. Here are my findings:
2.6.24-20 fresh [COLOR=Red]**FAIL**[/COLOR]
2.6.24-20 blacklist thermal [COLOR=Red]**FAIL**[/COLOR]
2.6.24-20 remove thermal from initramfs [COLOR=Red]**FAIL**[/COLOR]
2.6.24-20 remove thermal from initramfs and blacklist thermal [COLOR=SeaGreen][B]BOOT


[/B][COLOR=Black]I've update my guide with my re-installation findings. I hope it helps someone ><[/COLOR][/COLOR]

---

### Post by pluckster on 2008-07-27
Okay well I tried another install of 8.04.1 and it went a bit differently than yours and my other previous ones.

I had to use acpi=off and nolapic to get the install started, which if I remember right disables my LAN.

I used the same commands to start after the install as well.

When I did get to the desktop, for the first time it asked if I wanted to install video drivers and it also told me there were updates available. I tried to update but it then gave me an error saying it couldn't connect. Go figure. Also I noticed my touch pad scroll decided to start working to. Awesome.

I followed your first two steps but then I didn't change grub because I wasn't going to be able to do the step after.

Rebooted without any extra commands and my XServer failed and probably some other things I didn't catch. I also keep seeing thermal trips as well

Tried with nolapic. Seem that the temp shut it down again.

Tried again with acpi=off nolapic. Still no sound. 

I'm really starting to think this laptop is much different from all for yours'.


EDIT: D'oh! I see you revised your instructions while I was doing this. I'll try the new ones.

EDITEDIT: I guess I can't do those ones either because I don't have LAN.

---

### Post by AstronomyDomine on 2008-07-27
Thanks thegnark.  I just installed 8.04.1, and I did need acpi=off to install.  I upgraded *then* tried blacklisting thermal and rebooting, and that didn't work.  With thermal still blacklisted, I ran dpkg-reconfigure for linux-headers-2.6.24-20 linux-headers-2.6.20-generic linux-image-2.6.24-20-generic linux-libc-dev linux-restricted-modules-2.6.24-20-generic linux-ubuntu-modules-2.6.24-20-generic

I think that by reconfiguring the kernel with thermal blacklisted caused thermal not to be built into the initramfs, so now I'm able to boot with no special boot options.

Now the only thing I need working is the touchscreen and active digitizer.  Hopefully there's an update to the linuxwacom driver soon which fixes all of our problems.

---

### Post by thegnark on 2008-07-27
If you install and boot first time with only "acpi=off", you still don't have LAN? Not once did I ever boot with noapic or nolapic.

If you can't get LAN working for some reason, I would skip the part where you update packages (as if you have a choice), but remember to update references from -20 to -19... If anyone can reply and tell me how to get (uname -r) integrated into those command, it would make things a little simpler. At this point, the only thing that updating it gives you is the fixed wl... which should be in the standard repo eventually... or you could download it directly and install it from flash drive...

Anyways, here are my network devices per lspci:
```
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```Completely unrelated, but I would like to get CPU scaling working... that should be a huge boon to battery life and heat reduction. I know nothing about it, so I have no idea what to test...

---

### Post by pluckster on 2008-07-28
I guess I didn't really clarify that.

After the install I tried booting without any params. It did not but and shut itself down.

I then tried booting with just acpi=off which cased a kernel panic but no temp trips.

Then I tried with just nolapic. It ran like it should but with temp trpis all the time during it, it also comes up with a blue screen telling me xserver failed in the middle of the boot sequence. It then shuts down.

On another note just noapic also causes a kernel panic at what looks to be the same spot as acpi=off.

As to the update, I have -19 so how would I update that with -20?

I doubt this is an issue but are you dual booting your laptops or are you all going full on Ubuntu.

---

### Post by AstronomyDomine on 2008-07-28
Yeah, I suppose I should have used some "uname -r"s in my original post.  Anyway, it'd be "zcat initrd.img-`uname -r` > /tmp/directory.cpio/initrd.cpio" instead of "zcat initrd.img-2.6.24-20-generic > /tmp/directory.cpio/initrd.cpio"

The ` around uname -r is the character to the left of the number 1, it's not an apostrophe. 

Also, did you try running dpkg-reconfigure on those packages I mentioned a few posts up with thermal blacklisted?  I never removed thermal from my initramfs and I'm running perfectly.

Pluckster:  Your LAN should work with acpi=off and noapic, mine did.  What are the outputs of "ifconfig" "lspci | grep Ethernet" and "sudo dhclient eth0"?

---

### Post by thegnark on 2008-07-28
pluckster:
2.6.24-20 is in the proposed repos
Also, yeah, I'm dual booting Vista Ultimate 32 with Hardy 64

AstronomyDomine:
No, I didn't run dpkg-reconfigure... however, I'm booting in now and performing these steps:
```
cd /boot
sudo mv initrd.img-`uname -r` initrd.img-`uname -r`.nothermal
sudo mv initrd.img-`uname -r`.bak initrd.img-`uname -r`
```Attempted boot and failed due to thermal trip (as expected), so I booted with acpi=off and ran:
```
sudo dpkg-reconfigure linux-headers-`uname -r`
```Attemped to boot and failed :( Boot with acpi=off again and ran:
```
sudo dpkg-reconfigure linux-headers-`uname -r` linux-image-`uname -r` linux-restricted-modules-`uname -r` linux-ubuntu-modules-`uname -r` linux-libc-dev
```Booted as normal succesfully... so it would seem that you are correct, after blacklisting thermal, we can jsut run a dpkg-reconfigure and things should be fine... I'm updating guide

---

### Post by AstronomyDomine on 2008-07-28
thegnark: It seems that once a module is blacklisted, any generated initramfs won't contain that module.  This is really awesome because now we really just need to install with acpi=off and noapic, boot with acpi=off and no apic, blacklist thermal, enable hardy-proposed, then upgrade.

Because the kernel's going to be upgraded anyway, and it will generate a new initramfs, we probably don't even need to run a dpkg-reconfigure as long as we upgrade the kernel *after* we blacklist thermal.

Your guide is going to help a lot of people.  Is there any way we could put it on the first page?  Maybe isachan could edit his first post and put your guide there, as well as any other helpful tips and information for newcomers.  

Has anybody tried using Catalyst 8.7?  I'm interested in trying to improve my battery life by following these instructions: [https://help.ubuntu.com/community/BinaryDriverHowto/Fglrx_lowpower](https://help.ubuntu.com/community/BinaryDriverHowto/Fglrx_lowpower) but when I run "aticonfig --lsp" I recieve the error "POWERplay is not supported on your hardware" although I think it should be.  Any ideas?

---

### Post by thegnark on 2008-07-28
Hrm... did you try booting with only acpi=off? I never had to supply nolapic or noapic. I'll see if I can post a HOWTO.

And regarding battery life, I think we might be SOL until a kernel that supports the Turion processor is released. I posted a METOO at [https://bugs.launchpad.net/bugs/231534](https://bugs.launchpad.net/bugs/231534)

edit: updated guide on page 12 and submitted a HOWTO for approval

---

### Post by pluckster on 2008-07-29
I feel like somewhat of an idiot right now. 

I just realized that I have been using/downloading 32bit versions of all my ISOs. So I downloaded 64bit and would you look at this, I works just fine. Still odd though that 32 bit won't work at all.

Just running through your instructions now. I have ethernet now so it seems to be doing its job.

Edit: everything is good to go except sound for me. Thanks for helping me out. I'll look to see if I mistyped those lines.

---

### Post by thegnark on 2008-07-29
> **pluckster said:**
> Edit: everything is good to go except sound for me. Thanks for helping me out. I'll look to see if I mistyped those lines.

Oh yay! Glad someone confirms it all works in that order. The only thing I can think of regarding the sound... is tghat I only included 1 of 2 lines detailed in the original post, because when I checked the bottom of alsa-base, the first line was already there... maybe it's getting added as part of the updates to hardy-proposed and our fix needs to come after update.

Can you verify if "options snd-cmipci mpu_port=0x330 fm_port=0x388" exists in alsa-base towards the bottom? If not, add it - but it was there for me when I last wrote the guide.

---

### Post by fbdelivers on 2008-07-29
> **isachan said:**
> AstronomyDomine,
Yeah, it's been a while since last time said something about the latest wacom development driver, hasn't it ? Well, the reason is that 0.8.1-1 is not working well. The previous version was much better. The pen no longer register any clicks, so I can't write / draw anything. The touch screen is unchanged, works like before, with off-calibration.

By using wacomdump version 0.7.4 utility, I can see the pressure sensitivity bug has been sorta fixed, but looks strange in raw value. Eraser is recognized, not as another pen tip like the previous version.

I sent off 2 emails to the author asking questions but so far, I haven't received any reply. The documentation on the web site is quite old that only few of the information is applicable. I heard somewhere that so many protocols in the driver has been straighten out, and there are many more to fix.

I've found the bug in the source code from the previous version 0.8.1, so maybe I can try that when I have some time.

Thanks isacan for the post.  I'm not really understanding the wacdump command.  I try the following:

wacdump /dev/input/by-id/usb-Tablet_ISD-V4-event-mouse

but it isn't giving me any feedback when I use the stylus.  I'm probably just doing something dumb.

On another note I do seem to be having a little more success with the stylus with the following pressure setting.

Option "PressCurve" "0,15,85,100"

Thanks everyone!

---

### Post by gali98 on 2008-07-29
isachan
I have the tx2000z, but I think the wacom on our tablets is similar if not exact.
That being said I have everything working in 0.8.1-1 (stylus eraser touch) with the exception of the pressure still not working, but I submited and email on the mailing lists at sourceforge and ping (one of the devs) replied back.
Here is the tutorial if you want to try it....
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

if would be interested in that bug you are talking about..
I'm no coder, but I think I could fix the source given a while :)
Kory

---

### Post by Weststar on 2008-07-30
> **pluckster said:**
> I feel like somewhat of an idiot right now. 

I just realized that I have been using/downloading 32bit versions of all my ISOs. So I downloaded 64bit and would you look at this, I works just fine. Still odd though that 32 bit won't work at all.

Just running through your instructions now. I have ethernet now so it seems to be doing its job.

Edit: everything is good to go except sound for me. Thanks for helping me out. I'll look to see if I mistyped those lines.

Hmm, I didn't realize that this only works for 64 bit! =|

Is switching from 32 to 64 much of a big deal? I hear about many compatibility issues =(

---

### Post by vokesalex on 2008-07-30
Cheers guys for all the help you've given on this thread. It's been a great help getting things working using Kubuntu 8.04 KDE4 Remix 64Bit.

I also managed to get the touchscreen working on my tx2520ea last night using the same guide as posted in #131. I compiled version 7.9-11 as I've heard this version is better.

I was just wondering how I should best go about calibrating my stylus. I've read that some people have used wacomcpl to achieve this but others have said there are problems with it. Is it just a matter of editing the TopX, TopY, BottomX, and BottomY values in xorg.conf until the stylus matches the cursor.

Apologies for my noob'ness, but all my experiences with linux so far have been with OpenSUSE and i'm not familiar with the equivalent tools in Ubuntu.

---

### Post by pluckster on 2008-07-30
Its all good actually. Your instructions are right on. I mistyped position so after I fixed that everything was good to go. 

Now on to the tablet.

---

### Post by gali98 on 2008-07-30
> **vokesalex said:**
> Cheers guys for all the help you've given on this thread. It's been a great help getting things working using Kubuntu 8.04 KDE4 Remix 64Bit.

I also managed to get the touchscreen working on my tx2520ea last night using the same guide as posted in #131. I compiled version 7.9-11 as I've heard this version is better.

I was just wondering how I should best go about calibrating my stylus. I've read that some people have used wacomcpl to achieve this but others have said there are problems with it. Is it just a matter of editing the TopX, TopY, BottomX, and BottomY values in xorg.conf until the stylus matches the cursor.

Apologies for my noob'ness, but all my experiences with linux so far have been with OpenSUSE and i'm not familiar with the equivalent tools in Ubuntu.

Well I'm glad my tutorial is being used.
Yes 7.9-11 will probably work better until the folks at linux wacom release a new package.. (I think it will be very soon)
Really the only thing wrong is the pressure sensitivty.

And yes just editing those four values will do it. Be careful though, using the wacomcpl to calibrate after calibrating using xorg.conf will mess everything up.
i.e. don't use both to calibrate, just use one....
Kory

---

### Post by pluckster on 2008-07-30
Been playing around with some stuff and one thing I've noticed is that I can't get any more than one workspace at a time. I noticed this when trying to set up a desktop cube and other compiz stuff. any ideas?

---

### Post by corwinspyre on 2008-07-30
> **pluckster said:**
> Been playing around with some stuff and one thing I've noticed is that I can't get any more than one workspace at a time. I noticed this when trying to set up a desktop cube and other compiz stuff. any ideas?

install compizconfig-settings-manager, and go to general options->desktop size and set horizontal virtual size to 4 (the others should be 1) if you want a cube

---

### Post by pluckster on 2008-07-31
Yeah I had all that going but my problem is even without the cube I only seem to be able to access one workspace. It shows four in the bottom right but I can't click on them or use any of the shortcuts to change workspace.

---

### Post by AstronomyDomine on 2008-07-31
Download to desktop: 

[http://sourceforge.net/tracker/download.php?group_id=69596&atid=525126&file_id=275579&aid=1949610](http://sourceforge.net/tracker/download.php?group_id=69596&atid=525126&file_id=275579&aid=1949610)

[http://internap.dl.sourceforge.net/sourceforge/linuxwacom/linuxwacom-0.7.9-11.tar.bz2](http://internap.dl.sourceforge.net/sourceforge/linuxwacom/linuxwacom-0.7.9-11.tar.bz2)

```
sudo rmmod wacom
cd ~/Desktop
tar -xf linuxwacom-0.7.9-11.tar.bz2
cd linuxwacom-0.7.9-11
patch -p1 < ~/Desktop/unified-patch-w-eraser_k22-k24.txt
sudo apt-get update
sudo apt-get install linux-headers-`uname -r` build-essential x11proto-core-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev libxext-dev libxi-dev linux-libc-dev libc6-dev libncurses5-dev xserver-xorg-dev tk-dev tcl-dev tcl8.4-dev tk8.4-dev libncurses5-dev xserver-xorg-dev -y
./configure --enable-wacom
make
sudo make install
sudo rm /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
sudo cp src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
sudo depmod -ae
sudo modprobe wacom
gksudo gedit /etc/X11/xorg.conf

```

```
Section "Module"
        Load            "glx"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	InputDevice    "Synaptics Touchpad"
	InputDevice    "TabletPCStylus"
	InputDevice    "TabletPCStylus2"
	InputDevice    "TabletPCStylus3"
EndSection

Section "InputDevice"
	Identifier 	"TabletPCStylus"
	Driver 		"wacom"
	Option 		"ForceDevice" 		"ISDV4"
	Option 		"Type" 			"stylus"
	Option 		"SendCoreEvents" 	"true"	
	Option 		"Device" 		"/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
	Option 		"Button2" 		"3"  							# make side-switch a right button
#	Option 		"TopX" 			"225"
#	Option 		"TopY"			"122"
#	Option		"BottomX"		"26365"
#	Option 		"BottomY" 		"16488"
EndSection

Section "InputDevice"
	Identifier	"TabletPCStylus2"
	Driver		"wacom"
	Option		"ForceDevice" 		"ISDV4"
	Option		"Type" 			"stylus"
	Option		"SendCoreEvents" 	"true
	Option		"Device" 		"/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-"
EndSection

Section "InputDevice"
	Identifier     "TabletPCStylus3"
	Driver         "wacom"
	Option         "ForceDevice" 		"ISDV4"
	Option         "Type" 			"eraser"
	Option         "SendCoreEvents" 	"true"
	Option         "Device" 		"/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
EndSection


Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Option "RandRRotation"  "on"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

Reboot or restart X.  Post with results. :)

Edit: All credit goes to Andrew Zappacky who not only wrote the TabletPC kernel-level code, but also guided me through setting it up, step by step.

---

### Post by fbdelivers on 2008-07-31
> **AstronomyDomine said:**
> 

Reboot or restart X.  Post with results. :)

Edit: All credit goes to Andrew Zappacky.  He coded the Tablet PC driver from scratch.

I just gave it a shot - and when I rebooted the tablet pen no longer worked.  I went back trough your steps and noticed the following.

```

patch -pl < ~/Desktop/unified-patch-w-eraser_k22-k24.txt 
patch: **** strip count l is not a number

```

I'll double check to see what I did wrong.

Update - I just noticed that wacom module didn't load so something must have gone wrong when booting.

---

### Post by AstronomyDomine on 2008-08-01
That should be patch -p1 (one) not -pl.  Let me know if there are any other problems.

---

### Post by fbdelivers on 2008-08-01
> **AstronomyDomine said:**
> That should be patch -p1 (one) not -pl.  Let me know if there are any other problems.

I'm an idiot :)

The patch works great!  Xjournal / gimp all work with no problem.  Thank you thank you thank you!

Your steps worked fine.

---

### Post by pluckster on 2008-08-01
Anyone played around with the media buttons on the screen? I know a couple work (as in are recognized) but I can't get some of them to work. Is this something we'll just have to live with?

---

### Post by thegnark on 2008-08-01
> **pluckster said:**
> Anyone played around with the media buttons on the screen? I know a couple work (as in are recognized) but I can't get some of them to work. Is this something we'll just have to live with?

No real answer for you, but I thought I'd toss in some info about it that might help someone else debug the situation:

To get them to work in Vista, you have to install [special HP software]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?swItem=ob-61528-1&lang=en&cc=us&idx=3&mode=4&"). It seems to launch some hard-coded locations... which stinks, but fortunately people have worked around this by replacing the EXEs with ones that run a simple batch files... [follow the thread]("http://forum.tabletpcreview.com/showthread.php?t=18651&page=2") on it...

---

### Post by corwinspyre on 2008-08-01
> **pluckster said:**
> Anyone played around with the media buttons on the screen? I know a couple work (as in are recognized) but I can't get some of them to work. Is this something we'll just have to live with?

do you mean the play, stop, next, and previous buttons?  they work in totem, rhythbox, and exaile (the only media players i've tried).

on another note, i've been working on the remote but haven't had much luck yet.

---

### Post by pluckster on 2008-08-02
> **corwinspyre said:**
> do you mean the play, stop, next, and previous buttons?  they work in totem, rhythbox, and exaile (the only media players i've tried).

on another note, i've been working on the remote but haven't had much luck yet.

No I mean the other four buttons on that corner; DVD, quicklaunch, rotate and that gear one. The DVD and quicklaunch ones work while the other two don't (At least I think its those two, I know two don't work).

---

### Post by Funk Phenomena on 2008-08-02
Hi AstronomyDomine, what do we do with those two files and code listed on post #139?  Or anyone else that knows...??

Thanks to everyone here and the efforts you've put towards this project.  It is so nice to be able to put Ubuntu 64 on this tablet.  I also tried the Fedora 9 route with no success, it hung on trying to recognize the processor...

---

### Post by fbdelivers on 2008-08-02
> **Funk Phenomena said:**
> Hi AstronomyDomine, what do we do with those two files and code listed on post #139?  Or anyone else that knows...??

Thanks to everyone here and the efforts you've put towards this project.  It is so nice to be able to put Ubuntu 64 on this tablet.  I also tried the Fedora 9 route with no success, it hung on trying to recognize the processor...

Follow his step by step in the code section.

BTW cell writer works great with the patch.

When I try to do screen rotation I get the following.

```

xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  160 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

I've seen some posts stating that ATI driver doesn't support rotation.  Others say one needs to disable just a few settings in the xorg.conf like disabling compiz.

---

### Post by corwinspyre on 2008-08-02
> **pluckster said:**
> No I mean the other four buttons on that corner; DVD, quicklaunch, rotate and that gear one. The DVD and quicklaunch ones work while the other two don't (At least I think its those two, I know two don't work).
Oh.  I just tried out xbindkeys and got them working.  Here are the steps:

1. sudo apt-get install xbindkeys xbindkeys-config
2. xbindkeys --defaults >> ~/.xbindkeysrc
3. xbindkeys-config
4. Hit the "New" button at the bottom.
5. On the right, fill out the name and action with whatever you want, and to bind the button, click on "Get Key" and once a new box/window comes up, hit the button you want to bind.

Unfortunately, it only works for the DVD button and the rotate button, not the other two :(

---

### Post by corwinspyre on 2008-08-02
> **fbdelivers said:**
> Follow his step by step in the code section.

BTW cell writer works great with the patch.

When I try to do screen rotation I get the following.

```

xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  160 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

I've seen some posts stating that ATI driver doesn't support rotation.  Others say one needs to disable just a few settings in the xorg.conf like disabling compiz.

I haven't messed with rotation myself, but I googled around and came across this post saying it's possible to rotate with compiz (well, you have to restart it): [http://forum.compiz-fusion.org/showthread.php?t=2908](http://forum.compiz-fusion.org/showthread.php?t=2908)

---

### Post by Funk Phenomena on 2008-08-03
Touch and the stylus work.  Thanks for putting this all together.  In what way can we use the eraser?

So for calibrating the digitizer and touch screen... does it matter the xorg.conf file differs from this one, post 5: [http://ubuntuforums.org/showthread.php?p=5469447#post5469447]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")?  Specifically, I was hoping to edit the four values as referenced earlier here... but got confused as there is no "touch" in this new config file.

Also, after mucking about in alsamixer, skype, and cheese, I can't get my microphone to work.  Skype and cheese take video fine, albeit no audio.  Sound output works and I tried playing around with the alsamixer mic settings without any luck.  Anyone have suggestions?

---

### Post by gali98 on 2008-08-04
I have updated my tutorial (the one Funk references to)
and now everything is working great (the pressure is fixed)
see here:
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

also on the sound I am on the same boat as you.. I think we need to play with the settings in the alsa config file (the one where you put
snd-hda-intel model=hp
or something similar... that may need some work... that is my next project :))

Kory

---

### Post by ownaginatious on 2008-08-05
Okay, here's what I've got working so far after I've been through absolutely everything in this thread.

[U]
WORKING:[/U]

**Temperature Problem** - Completely fixed by removing the thermal module from the kernel, as someone posted earlier here.
[B]
Sound[/B] - Works perfectly through speakers and headphones. Have not tested the microphone.
[B]
Webcam [/B]- Tested through Cheese after rebooting. Works perfectly, excellent quality and speed.

**Wireless** - After fixing the kernel, which at the same time upgraded me to the .20 version, wireless appeared. It's kind of slow to connect, but works fine when it does. This may be because I have a WPA secured network.

_SORT OF WORKING_


**Tablet** - Almost working. Active digitizer works properly and seems to be automatically calibrated. Eraser isn't really recognized as an eraser. Seems to do the exact same thing as the other end. Also, pressure sensitivity doesn't seem to work when I tried it in GIMP. The pressure seems to be either full, or non-existent, nothing in between. Pressure-operated digitizer is completely uncalibrated, but at least works.

_STILL BROKEN_

**Standby** - Computer is able to go to sleep, but when it awakens, the display forgets to turn back on.

_STUFF I HAVEN'T GOTTEN TO YET_

**Pretty much all the buttons** - I'm assuming this is exactly the same as the tx2000. I'll work on it later.

- In conclusion, it looks like almost everything in the computer works :). Only a bit further to go before we can tell Vista to kiss our asses.

---

### Post by thegnark on 2008-08-05
I just want to reiterate that the notion that the "temperature problem" is **fixed **is a misnomer... We've really only got a **workaround**... truth is that the CPU doesn't scale and the fans blow at full 100% of the time

We're still in need of a kernel fix that actually recognizes and correctly controls the hardware

---

### Post by chees on 2008-08-05
Well, with the kernel fix, the computer does regain some control of the fan, as well as all of the other hardware. The only problem is that it can no longer tell when to increase fan speed, unless the motherboard can handle that regardless of the operating system. Right now it's stuck somewhere around normal speed. Definitely not 100% though. I'm assuming that the computer still cannot do CPU scaling.

By the way, has anyone noticed the computer completely locking up when using GIMP with the stylus? Maybe this is a result of the computer lacking any control of the fan, and thus overheating.

---

### Post by pluckster on 2008-08-10
> **AstronomyDomine said:**
> Download to desktop: 

[http://sourceforge.net/tracker/download.php?group_id=69596&atid=525126&file_id=275579&aid=1949610](http://sourceforge.net/tracker/download.php?group_id=69596&atid=525126&file_id=275579&aid=1949610)

[http://internap.dl.sourceforge.net/sourceforge/linuxwacom/linuxwacom-0.7.9-11.tar.bz2](http://internap.dl.sourceforge.net/sourceforge/linuxwacom/linuxwacom-0.7.9-11.tar.bz2)

```
sudo rmmod wacom
cd ~/Desktop
tar -xf linuxwacom-0.7.9-11.tar.bz2
cd linuxwacom-0.7.9-11
patch -p1 < ~/Desktop/unified-patch-w-eraser_k22-k24.txt
sudo apt-get update
sudo apt-get install linux-headers-`uname -r` build-essential x11proto-core-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev libxext-dev libxi-dev linux-libc-dev libc6-dev libncurses5-dev xserver-xorg-dev tk-dev tcl-dev tcl8.4-dev tk8.4-dev libncurses5-dev xserver-xorg-dev -y
./configure --enable-wacom
make
sudo make install
sudo rm /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
sudo cp src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
sudo depmod -ae
sudo modprobe wacom
gksudo gedit /etc/X11/xorg.conf

```

```
Section "Module"
        Load            "glx"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	InputDevice    "Synaptics Touchpad"
	InputDevice    "TabletPCStylus"
	InputDevice    "TabletPCStylus2"
	InputDevice    "TabletPCStylus3"
EndSection

Section "InputDevice"
	Identifier 	"TabletPCStylus"
	Driver 		"wacom"
	Option 		"ForceDevice" 		"ISDV4"
	Option 		"Type" 			"stylus"
	Option 		"SendCoreEvents" 	"true"	
	Option 		"Device" 		"/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
	Option 		"Button2" 		"3"  							# make side-switch a right button
#	Option 		"TopX" 			"225"
#	Option 		"TopY"			"122"
#	Option		"BottomX"		"26365"
#	Option 		"BottomY" 		"16488"
EndSection

Section "InputDevice"
	Identifier	"TabletPCStylus2"
	Driver		"wacom"
	Option		"ForceDevice" 		"ISDV4"
	Option		"Type" 			"stylus"
	Option		"SendCoreEvents" 	"true
	Option		"Device" 		"/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-"
EndSection

Section "InputDevice"
	Identifier     "TabletPCStylus3"
	Driver         "wacom"
	Option         "ForceDevice" 		"ISDV4"
	Option         "Type" 			"eraser"
	Option         "SendCoreEvents" 	"true"
	Option         "Device" 		"/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
EndSection


Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Option "RandRRotation"  "on"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

Reboot or restart X.  Post with results. :)

Edit: All credit goes to Andrew Zappacky who not only wrote the TabletPC kernel-level code, but also guided me through setting it up, step by step.

Seems to work for me. The sensitivity is a little sensitive(god that sounds stupid) but it does work in GIMP and such, you just have to make sure you enable and configure it. 

On a side note your xorg is a bit different from mine. You seem to have a lot of stuff referencing ATI. Thought maybe that's why my rotation wasn't working.

---

### Post by sandlidl on 2008-08-10
Ok, first of all, thanks to everyone for clearing up all the problems. I only just purchased the tx2500 a couple days ago and a lot of the problems are ironed out thanks to you!

However, I'm still running into this problem that I can't get the pointer to line up with the pen. So I'm going to mess around with the xorg.conf to try to see if I can make it work myself, but if someone has a more informed method, I would really appreciate it.

This is my first experience with wacom so forgive me if I sound green.

---

### Post by sandlidl on 2008-08-10
Ok, nevermind. I just found another place that specified that all the Wacom info had to be placed BEFORE any Synaptics information in the Xorg.conf file. So I moved everything around and now I have a working wacom! Works great too!

Maybe this information will help someone else with the same problem.

---

### Post by gali98 on 2008-08-10
pluckster, What model laptop do you have?
If you have a tx2000 series then don't worry about ati...
tx2000 series has nvidia and tx2500 has ati.
If you have a tx2000 (it may even work for tx2500) go here to get rotation working:
[http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm)
Cheers :)
Kory

---

### Post by pluckster on 2008-08-10
Nah I've got a tz2524ca so it is ATI. I tried some of the stuff in that page that I was hoping would work but the suspend didn't seem to work to well for me. Anyone else tried it?

---

### Post by fbdelivers on 2008-08-11
This is a side note on a couple of statements earlier.  

Screen Protector - Recommendations?

Thanks!

---

### Post by tC_Crazy on 2008-08-11
Wow, I go away from this thread for a week or two and it nearly doubles! OK, well I'm glad that there's been some progress on the digitizer part. I'm going to have to try that when I get some free time (if ever!). I think it's important to note that 32-bit Ubuntu does work (at least for me... dual-booting with 32-bit Vista Home Premium btw). 

fbdelivers,
I'm rockin a Photodon.com anti-glare (they have a fitted size for the tx2500!). It is working very well for me. However, you may have a personal preference for anti-glare vs. clear. They have both for similar prices. I was hoping the anti-glare would help with the reflections, and it did. It seems to diffuse reflections a lot, but the screen is pretty much useless outdoors in direct sunlight. Check out their site, the protectors are cheap (under $11 each!).

---

### Post by kg6gfq on 2008-08-12
Just opened my tx2500 yesterday, finished all the howtos this afternoon, and everything that has a documented fix seems to work!  Thanks so much to everyone who's been working on this!

I tinkered with the screen rotation, and apparently xrandr doesn't work properly with the fglrx (proprietary ATI) driver.  I expected it to work with the (open source) Radeon or ATI drivers as it did on my previous laptop, but apparently the card is from a newer series and therefore won't work with either of those.  There's a new oss driver in development called RadeonHD that ought to support the newer cards, but I haven't had a chance to properly look into it yet.  

A while back I read something that might help with the two extra buttons on the screen that aren't working right now.  I'll try to hunt down the howto for that also.  

I did discover that aticonfig allows the use of multiple monitors, though it does something strange to the calibration of the wacom stylus.  

Thanks again to everyone who's posted here!

---

### Post by WACOMalt on 2008-08-18
Hey there, and thanks everyone who is putting in their effort to make everything run smoothly,

I am having trouble with my wireless still though. I followed thegnark's guide, and the wireless light neither turns blue, nor can I browse any wireless access points.

my Ethernet works fine though.

wireless is the main thing I want working.

so to summarize:
 
[COLOR="DarkRed"]**Not working for me are:** 
-wireless
-the touch screen/digitizer
-the quick launch buttons
-thumbprint reader
-battery information (ubuntu sees it as always on AC power)
-screen brightness control (using the addable panel control)[/COLOR]

[COLOR="Green"]**Working:**
-touchpad, including scroll areas
-graphics driver
-sound output, and the volume/mute buttons (mute doesn't turn orange -though)
-dvd drive (reading)
-usb devices
-camera, using cheese. (Havent tried in skype yet)[/COLOR]

[COLOR="Orange"]**Not tested yet:**
-bluetooth
-dvd drive writing
-line in and spdif[/COLOR]

If someone could contact me who can help me get through some of this stuff.  I am fairly used to linux, this is about my 5th distro and setup, but I still could use some help.

If we could talk over and instant messenger, that would be the best. Here are my contact infos

AIM: wacomalt
YIM: wacomalt
MSN: [email]wacomalt@gmail.com[/email]
skype: wacomalt
googletalk: [email]wacomalt@gmail.com[/email]

please, if you think you can help, contact me!

---

### Post by thegnark on 2008-08-18
Things that you should be able to get working for sure (there may be others) are:

wireless
digitizer
battery indicator (it drops like a rock due to no cpu scaling, but hey, it works!)

hit up the link in my sig and see if that's any help

---

### Post by WACOMalt on 2008-08-19
thegnark, your tutorial is th eone I tried. (great tutorial btw, it just didnt work out for me)

in fact, following your tutorial is the only thing I have done so far.  Were there any other methods for getting the wireless to work? Or what can I test to help find the problem?

---

### Post by thegnark on 2008-08-19
What the tutorial does to get wireless working, is enable hardy-proposed, which updated the driver to a newer less-broken one. It seems that those proposed updates have been pushed to the standard repos, and therefore hardy-proposed contains newer (possibly broken?) packages. The only thing I can think of off the top of my head is to manually downgrade linux-restricted-modules (I assume this is the package that provides the wl driver) to 2.6.24-20 and see if that works. If so, we can skip Step 3 in the future. I can do some extra testing tonight and see what I turn up.

Can you report which version of linux-restricted-modules-common you're using? If it's -21, right-click it, switch to the Versions tab and downgrade from there. I can give more detailed intsructions when I'm next to a power outlet (I wish ACPI and CPU scaling was correctly working :()

---

### Post by WACOMalt on 2008-08-19
> **thegnark said:**
> ...Can you report which version of linux-restricted-modules-common you're using? If it's -21, right-click it, switch to the Versions tab and downgrade from there...

How do I check which version I am running? :confused:  sorry, still fairly new to this stuff...

EDIT: nm, in the synaptics package manager, it lists 2.6.24.14-21.47 which is the newest reported version as well. I do not see 2.6.24-20 as an option on the versions tab.

---

### Post by corwinspyre on 2008-08-19
your fingerprint reader should be working out of the box, so to speak

---

### Post by gali98 on 2008-08-19
> **corwinspyre said:**
> your fingerprint reader should be working out of the box, so to speak

How so?

You would first need to install fprint and all.
It is a very new project.. doesn't always work.
Kory

---

### Post by corwinspyre on 2008-08-19
> **gali98 said:**
> How so?

You would first need to install fprint and all.
It is a very new project.. doesn't always work.
Kory
fprint is just a library of APIs to access it. libfprint is used by some fingerprint programs but not all.  

the only problem is there really isn't any useful programs that use fingerprints, and it isn't integrated into the gnome or gdn

---

### Post by thegnark on 2008-08-19
> **WACOMalt said:**
> How do I check which version I am running? :confused:  sorry, still fairly new to this stuff...

EDIT: nm, in the synaptics package manager, it lists 2.6.24.14-21.47 which is the newest reported version as well. I do not see 2.6.24-20 as an option on the versions tab.

Sorry, take a look at linux-restricted-modules-generic. I'm at 2.6.24.20.22, which should now be part of the standard repos... hardy-proposed contains 2.6.24.21.23. I'll update and report back what happens. In the meantime, you could manually downgrade and see if that helps.

EDIT: I'm fully updated with hardy-proposed enabled and wireless still works. Can you also confirm that "wl" is checked and "In use" in System->Administration->Hardware Drivers?

---

### Post by WACOMalt on 2008-08-19
> **thegnark said:**
> ... hardy-proposed contains 2.6.24.21.23...

...Can you also confirm that "wl" is checked and "In use"...?
[COLOR="Silver"]
For some reason, in the properties on synaptics package manager, It says the current hardy proposed version is 2.6.24.14-21.47. This is different than yours reports (2.6.24.21.23). am I looking in the right place? Could my repositories be added incorrectly?[/COLOR]
[COLOR="DarkRed"]EDIT: nm, I just now noted that you told me to check a different package this time :P and my version for generic is 2.6.24.21.23, so same as yours. Still no luck though...[/COLOR]

Also "wl" is check and in use in my hardware driver thingy.

[COLOR="Silver"]This very odd... Where are you checking your version number? I have just been looking in synaptic's package properties.[/COLOR] (never mind :P)

EDIT: thegnark, can you please contact me?  my infos are:
AIM: wacomalt
YIM: WACOMalt
MSN: [email]wacomalt@gmail.com[/email]
gtalk: [email]wacomalt@gmail.com[/email]
skype: wacomalt
email: [email]wacomalt@gmail.com[/email]

---

### Post by martinjochimsen on 2008-08-20
Hi

I have been following this thread for some time now. I just bought a tx2590oe a week ago, and I too have had ALL the same problems as you guys. Many things are working now but I still have a problem with my wireless. I followed the guide from tC_Crazy (#80) and my wireless card (BCM4322) seems to work. It finds my wireless router, but when it tries to connect it just keeps on searching and searching and searching and finally it doesn't connect. I've got two other laptops in the house which connects to the router without any problems, so it must be something with my laptop.
Has anybody had the same problem, and is there anything I can do?

best regards
Martin

---

### Post by gali98 on 2008-08-20
First... Does this router have encryption? (WEP WPA etc....)
Have you done a soft reset on the router? (Unplug it, replug it)
Are you sure the wireless is on?
If you still have Windows on this laptop can you connect with it?
When It "finds" the router, does is show a strong signal strength?
Are you up to date? (on updates with update manager)
What program are you using to connect? The default GNOME Network Manager?

Just some things you might want to check.

If you can test the laptop on another router. The problem may be fixed by updating the firmware of the router.

Kory

---

### Post by martinjochimsen on 2008-08-20
Hi

Good questions to answer: 

First... Does this router have encryption? (WEP WPA etc....)
- no

Have you done a soft reset on the router? (Unplug it, replug it)
- yes

Are you sure the wireless is on?
- well, the blue "wireless-light" has turned blue after I went through the guide. It was orange before. We don't live close to other houses, so my "linksys" was the only name that turned up, so I guess it's on

If you still have Windows on this laptop can you connect with it?
- yes. I have Vista, and it connects without problems

When It "finds" the router, does is show a strong signal strength?
- yes. Almost 75%

Are you up to date? (on updates with update manager)
- yes

What program are you using to connect? The default GNOME Network Manager?
-yes

I went to my brothers house tonight to test if it could connect there...but it couldn't.
I don't think it's the router. I have tried with two other laptops (and my own Vista) and they connect perfect.
It's a stupid problem, and the biggest problem is probably sitting in front of the laptop!!!! :-)
I just can't figure it out.

Martin

---

### Post by martinjochimsen on 2008-08-20
...and by the way. When the laptop tries to connect nothing else is working. Everything hangs!!!!!

Martin

---

### Post by WACOMalt on 2008-08-20
Hmm, I still am having no luck, it seems all of my packages are the propper version (or at least the same as thegnark's and his are working) my blue wireless light doesn't even come on. is there some command I can run to dump some info that might help me/you-guys figure this out?

---

### Post by AstronomyDomine on 2008-08-21
WACOMalt: The wireless light on the front of the computer (to the far right of the power switch) isn't even on?  It's not even red?  Does it work from Vista?  What does "lspci | grep Network" return?

martinjochimsen: First run iwconfig to determine what network interface your wireless netowrk is on.  All of the others should say "no wireless extensions" then there should be one that says "IEEE 802.11" etc.

Once you know your wireless interface (mine is eth1 so replace eth1 with yours from now on), try connecting manually with iwconfig.  Run "sudo iwconfig eth1 essid "NETWORK"" Of coruse, replace "NETWORK" with your essid, and don't use any quotes.  Run "iwconfig" every once in a while after that until you can see that it is connected to the network (It should list your network as the essid).  Then finally run "sudo dhclient eth1" to receive an IP from your router.  Hopefully that should work.  Post with results.

---

### Post by WACOMalt on 2008-08-21
AstronomyDomine: sorry, the light is on, just it is orange and not blue.

I also ran the iwconfig command to see if that listed anything useful. i got:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```
so my wireless is recognized to a point so I decided to try what you told martinjochimsen to do, and I got 

```
$ sudo iwconfig eth1 essid WACOMaltWireless
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Invalid argument.
```

also a question for those of you with working wireless, are you able to toggle it with the wireless slide-button on the front? Just wondering, I use that a lot as I fly quite a bit.

---

### Post by martinjochimsen on 2008-08-22
Hi Astronomy

Thanks for Your input.
Before I saw Your reply I followed a brand new guide only 1 or 2 days old
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)
Everything is working perfect now.

Best regards
Martin

---

### Post by corwinspyre on 2008-08-23
> **WACOMalt said:**
> AstronomyDomine: sorry, the light is on, just it is orange and not blue.

I also ran the iwconfig command to see if that listed anything useful. i got:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```
so my wireless is recognized to a point so I decided to try what you told martinjochimsen to do, and I got 

```
$ sudo iwconfig eth1 essid WACOMaltWireless
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Invalid argument.
```

also a question for those of you with working wireless, are you able to toggle it with the wireless slide-button on the front? Just wondering, I use that a lot as I fly quite a bit.

i have the abg wireless version, but yep, it works perfectly for me (meaning the light even turns red when it's off).

---

### Post by were_wolf on 2008-08-23
fedora 9 works great with the tx2500.
-touchscreen works very well
-stylus works very well
-rotation works but with cmd line
-wireless works very well with ndiswrapper
-finger printer not tested
-camera not tested
-buttons not tested

---

### Post by thegnark on 2008-08-24
Has anyone seen the thread on [**AMD "Puma" Laptops and C-states**]("http://ubuntuforums.org/showthread.php?t=844754")?

It seems that 2.6.26 better supports the new chipsets. I compiled and booted the new kernel and immediately noticed a difference in heat output (no more 100% fan either). I hadn't bothered to get the graphics and touchscreen working, but I'm sure it would be trivial.

Looks like we should just have to wait until Intrepid Ibex with a newer kernel ([currently 2.6.27]("http://blog.phunnypharm.org/2008/08/intrepid-ibex-810-moves-to-2627.html")) to expect easy configuration.

---

### Post by thegnark on 2008-08-24
> **were_wolf said:**
> fedora 9 works great with the tx2500.

That's strange, because I tried Fedora 9 and just like Ubuntu Hardy, I couldn't boot by default.

---

### Post by vokesalex on 2008-08-25
I read the "AMD "Puma" Laptops and C-states" thread too.

I tried Intrepid Kubuntu Alpha 2, as I noticed that it had the 2.6.26 kernel. There were a few odd things after the install had finished and it booted for the first time. The x server didn't seem to want to start but flickered back and forward between a totally black screen and the terminal based login. Once this had settled down I managed to get it to stay in terminal mode and did an apt-get dist-upgrade and then the graphical logon interface would then start properly the next boot.

I immediately noticed that the fans were quieter and there was a battery icon at the bottom of the KDE "taskbar" which wasn't present in Hardy. Hovering my mouse over the battery icon gave me some information about current battery life and power saving but I wasn't sure whether it was accurate as the CPU frequencies were blank. Remaining battery time started at 4hrs, then dropped to 15 minutes and then up to 1hr 40 mins.

I managed to get the touchscreen working with the same instructions as for Hardy. The main problem I had was that intrepid uses the newest version of xserver and there is currently no ATI driver that supports it that I could find.

Still looks promising for the final release of Intrepid...

---

### Post by morbyte on 2008-08-25
first things first: i have a HP tx2550eg.

after playing around with distros and configuration i want to add the following:

ubuntu intrepid alpha (1,2,3, dunno) worked out of the box. yet i installed debian lenny beta 2 with acpi=off. but for the modprobe stuff i was playing with it doesnt matter afaik. so here are my results:

blacklist thermal is not needed. i added "options thermal nocrt=1" to /etc/modprobe.d/options . this was enough to switch off the emergency shutdown.

furthermore i want to post my /proc/acpi/thermal_zone information with you:

```

# cat /proc/acpi/thermal_zone/THRM/*
<setting not supported>
<polling disabled>
state:               ok
temperature:         64 C
critical (S5):       -273 C <disabled>
hot (S4):            105 C <disabled>
passive:             95 C: tc1=2 tc2=3 tsp=30 devices=CPU0 CPU1

# cat /sys/module/thermal/parameters/act
0
# cat /sys/module/thermal/parameters/crt
0
# cat /sys/module/thermal/parameters/psv
0
# cat /sys/module/thermal/parameters/tzp
0

```

---

### Post by jambaiscool on 2008-08-25
Hi,

I'm going to uni next month and I'm going to get a laptop before I go. I came across the tx2520ea (which I believe is almost (if not completely) identical to the tx2500z) and really liked the look of it. Then I searched "ubuntu tx2500" and came across a handfull of horror stories about linux on this laptop. :(

anyway, from reading this thread the whole way through things are starting to look a bit more positive. I really like the look of the laptop (small, fairly powerful, tablet, good price), so do you guys think it's worthwhile getting despite the issues?

hopefully everything will be fine for intrepid? and i can live with a few hacks until then.

cheers,

jamie

---

### Post by thegnark on 2008-08-25
Just so everyone is clear, tx2500 is the generic name for any tx25?? model. We could more clearly say "tx2500 *series*", but the idea is the same.

And here's my take on your situation: If (1) your primary OS is Ubuntu, (2) comfortable with manual tweaking until Intrepid (and who knows - even maybe after Intrepid is out), and (3) planning on having the laptop plugged in most of the time, then I say go for it.

The battery life is just not acceptable IMO right now to be mobile constantly. I personally don't mind the hacks... but at the same time, I'm still dual-booting another OS until battery life is better.

---

### Post by isachan on 2008-08-25
jambaiscool,
Other than the initial thermal problem, many things are very Linux friendly on TX2500 series. If you can live with no CPU scaling, some tablet function inconvenience due to the state of driver development, suspend / hibernate, and power management issues.

I haven't tried some other things, like screen rotation, compile older digitizer driver to get the inking going.

You should be getting it going with acpi=off boot option and after the boot, adding "options thermal nocrt=1" to /etc/modprobe.d/options as per morbyte's post. That's what I have got it going without completely removing the thermal module.

I like especially after the last ATI driver update to version 8.6, 720p High Def contents are super fluid.

Still this machine needs a lot of software updates, and that takes time and patience. I'm in a waiting mode for a while.

---

### Post by isachan on 2008-08-25
Has the new wl driver in proposed repository released yet ?

I'm still waiting for the updated wl driver to come down to the release repository from proposed repository.

Right now, I can scan WLAN routers, but I can't really connect. I have to "sudo kwifimanager" to somehow connect to my router but it just flashes back and forth between "out of range" and "good link". Never stable. When I launch kwifimanager from GUI, everything is crossed out and I can't do anything. My WEP setting is good, and eth1 as the interface.

Wicd can see my router but can't connect to it either. My WEP setting is good, and eth1 as the interface.

How do I check the version for drivers ? Especially how do I compare what I have right now and the one in proposed / testing repository ?

I'm avoiding ndiswrapper as much as possible.

Help !

---

### Post by jambaiscool on 2008-08-25
thanks for the advice. I'm fairly competent with linux so I'll be able to handle a bit of hacking to get stuff working. I'll probably be getting the tx2520ea within a couple of weeks, so when I do I'll let yous know how it works. :)

---

### Post by martinjochimsen on 2008-08-27
Hi isachan 

Try to use this guide for your wireless [http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713) . I had some of the same problems (with wl), but now it works PERFECT!!!

Martin :-)

---

### Post by martinjochimsen on 2008-08-27
...and I'm on a Ubuntu 8.04.1 (tx2590)

Martin

---

### Post by thegnark on 2008-08-29
> [[IMG]https://bugs.launchpad.net/@@/person[/IMG] Leann Ogasawara]("https://bugs.launchpad.net/%7Eleannogasawara")          wrote     11 hours ago:     [              (permalink)     ]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/231534/comments/19")   
                         [FONT=monospace]The Ubuntu Kernel Team is planning to move to the 2.6.27 kernel for the upcoming Intrepid Ibex 8.10 release. As a result, the kernel team would appreciate it if you could please test this newer 2.6.27 Ubuntu kernel. There are one of two ways you should be able to test:
 1)  If you are comfortable installing packages on your own, the linux-image-2.6.27-* package is currently available for you to install and test.
 --or--
 2) The upcoming Alpha5 for Intrepid Ibex 8.10 will contain this newer 2.6.27 Ubuntu kernel. Alpha5 is set to be released Thursday Sept 4. Please watch [http://www.ubuntu.com/testing](http://www.ubuntu.com/testing) for Alpha5 to be announced.  You should then be able to test via a LiveCD.
 Please let us know immediately if this newer 2.6.27 kernel resolves the bug reported here or if the issue remains. More importantly, please open a new bug report for each new bug/regression introduced by the 2.6.27 kernel and tag the bug report with 'linux-2.6.27'. Also, please specifically note if the issue does or does not appear in the 2.6.26 kernel. Thanks again, we really appreicate your help and feedback.
[/FONT]


[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/231534/comments/19](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/231534/comments/19)

---

### Post by martinjochimsen on 2008-08-29
Great. Thanks for the update. I will try it next week.

Martin :-)

---

### Post by _francis on 2008-09-02
this is a review of my first days with my new hp tx2550eg tablet

getting ubuntu up and running:

i read thegnark's howto in this post (page 12), downloaded the daily build of 8.04.1 (august 28th) and tried to install ubuntu - without success due to "Error. Kernel panicking" (don't remember the exact message). after a lot of reading through the post I found that somewhere the boot options noapic and nolapic were mentioned and so I tried once more with the boot options:
acpi=off noapic nolapic

It worked and I installed hardy without any problems, but after starting up I had no wireless nor any wired connection.

another session of flicking through the forum pages followed and somewhere a successful installation with 8.10 alpha 3 is mentioned. I downloaded the daily build of alpha 4 and gave it a try. no success without manipulating the bootoptions, but this time acpi=off alone did it. the installation worked without any problems again and after manipulating the boot options at the first boot I couldn't wait to see the fruits of my work. after logging in my heart nearly stopped when I saw the white screen. I googled the problem, again, and found out about the "white screen of death" I solved this by pressing alt+F2 after login, typing "metacity --replace" and hitting Enter. Voila! 
I followed thegnark's guide to get sound work and also added thermal to the blacklist but no success, I cannot boot without changing the bootoptions.
I also tried AstronomyDomine's approach from this post (page 2) to remove the thermal module from the initramfs, but still no success.

Now I just tried the 2.6.27 kernel and it workes without any boot option or modifying the blacklist or initramfs. Wireless device is light blue instead of red and my spirit is up again. only problem is that i cannt see any proprietary drivers listed. in hardy i had proprietary drivers for the ati hd 3200 mobility card and the wl driver. iwconfig is just showing lo and eth0 without wireless extension. i ll try to figure this out tomorrow and maybe install wl manually. 

hope the info about the 2.6.27 kernel is useful to some of you.

---

### Post by martinjochimsen on 2008-09-02
Hi _francis

After I blacklisted thermal in /etc/modprobe.d/blacklist I added these 4 lines to /etc/modprobe.d/options

options thermal.act=-1
options thermal.crt=-1
options thermal.nocrt=1
options thermal.psv=-1

So now my /etc/modprobe.d/options looks like this

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2
options thermal.act=-1
options thermal.crt=-1
options thermal.nocrt=1
options thermal.psv=-1

and I can boot up without nolapi noapi acpi=off
I'm still useing kernel 2.6-24-21-generic

Martin :-)

By the way I used this really easy guide for my wireless from mike_1
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

---

### Post by jambaiscool on 2008-09-04
has anyone tried alpha 5 then? 
EDIT: Seems like the alpha 5 wasn't released today? Am I being an idiot?

Also, I understand that battery life is rubbish at the mo, but how rubbish is it? In hours? (or even minutes if they're a more suitable measurement:lolflag:)

---

### Post by WACOMalt on 2008-09-04
Well, sadly minutes IS a better scale. I at most get an hour.  Of course I use this computer tot he max all the time. (3d redering, Visual Effects, gaming, video editing etc...)

I would say maybe an hour and a half if you are only listening to music or something.

btw, I got the 8 cell battery, the default is 6 cell.

---

### Post by zujenbe on 2008-09-05
hi, im getting sound... but thing isnt quite as loud as it was with windows... anyone else have this too? im wondering if the sound is actually only coming out of one speaker...

---

### Post by Afief.h on 2008-09-06
Hello,

I have an HP tx2520ej(the model sold in Israel) and here are my results after installing Ibex Alpha 5:

What works:
Booting without the overheating error(no extra options needed:) simply boot)
Ethernet(didn't work in 8.04)
Screen resolution detected correctly
Wireless(I see the entry in Network Manager and iwconfig, but I don't have any networks around to test with. the light is blue)
The sound buttons(sound-, mute, sound+)
Memory card reader(tested with SD card)

What does not work:
Sound
Touchscreen(not with pen, not with fingers)
Buttons on the screen(DVD, rotate and settings, but that's expected)

Anyhow there are lots of updates out already, perhaps they'll fix some of the stuff here, and I will try the sound fix mentioned in this thread, but does anybody know how to get the touchscreen to work?

Edit: Sorry if there is stuff I haven't tested. If there is anything you'd like me to test please mention it and I'll do my best to test it.

---

### Post by zujenbe on 2008-09-06
[http://ubuntuforums.org/showthread.php?t=870640](http://ubuntuforums.org/showthread.php?t=870640)

this will more than likely help u fix ur problem with thouchscreen
gd luck!

---

### Post by martinjochimsen on 2008-09-06
Yes. Follow gali98's (#5 ) guide from the link above. It worked perfect for my tx2590oe.

Martin

---

### Post by zujenbe on 2008-09-06
oh god, im having some more problems now... 
i can no longer reboot or shutdown let alone hibernate or standby... up until recently, these two buttons worked fine. now whenever i try, i just get a blackscreen... which proceeds to absolutely nothing...
anyone any ideas?

---

### Post by lord_phantom on 2008-09-06
Hi!

First of all - thanks to all in this thread, especially Pluckster for describing his problems and saying that 64-bit version fixed his all problems. I got my tx2550ew working perfectly on Ubuntu 8.04.1 64-bit.

Now I decided to upgrade from 8.04.1 to 8.10 alpha5. I've encountered a problem. During the configuration of the new packages, suddenly my computer launched the shutdown procedure in the middle of the process. The reason was too high CPU temperature. Now i must finish the whole procedure within the good old terminal.

If someone of you would try this upgrade, I recommend to try boot the kernel with acpi=off. I don't know if this can prevent this crash, but it's worth trying.

Update: My upgrade failed. Fglrx (version from AMD's site) made most problems. Now I'll do a clean install of alpha 5. I'll try tomorrow.

Ps. It was my first post on this forum, also my English isn't good - so sorry for any language mistakes!

---

### Post by Afief.h on 2008-09-07
> **zujenbe said:**
> [http://ubuntuforums.org/showthread.php?t=870640](http://ubuntuforums.org/showthread.php?t=870640)

this will more than likely help u fix ur problem with thouchscreen
gd luck!

Thanks, I will try it this afternoon.

Any chance this will be integrated into the default Ubuntu 8.10 or will it have to wait until 9.04?

I got sound to work with the two lines of ALSA configuration, but when using earphones only one phone(left one in my case) works. Anybody encountered this?

---

### Post by martinjochimsen on 2008-09-07
Hi Afief.h

Which two lines did You put into the ALSA conf.?
Did You get the microphones to work?

Martin

---

### Post by Afief.h on 2008-09-07
> **martinjochimsen said:**
> Hi Afief.h

Which two lines did You put into the ALSA conf.?
Did You get the microphones to work?

Martin

added this to /etc/modprobe.d/alsa-bas   :
options snd-hda-intel index=0 model=toshiba position_fix=1

dunno why it appears to be one line now, but I'm not complaining:)

The microphone doesn't seem to work though

---

### Post by isachan on 2008-09-07
Well, I meant to say that _make sure_ the last two lines of /etc/modprobe.d/alsa-base file are as follows:

options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=toshiba position_fix=1

...where this line "options snd-cmipci mpu_port=0x330 fm_port=0x388" 
should be already there.

By looking at some posts in the past, I think I have confused some people.

Anyway, Afief.h, try right-clicking the sound icon on the bottom panel, and select the configuration menu. The KMixer config window should show up an look for the screen with a lot of check boxes where you can select which sound channel you can bring up on the volume setting screen.

Check Front, PCM, Headphones, etc., and go back to mixer volume setting and you should be able to crank up the left / right volumes or altogether.

Also, check your headphone plug is all the way in. 

I tried 8.10 Alpha 5 just today and that's how I brought up my sound.

Isao

---

### Post by zujenbe on 2008-09-08
hi, what doesnt work on ibex so far? im thinking about upgrading.

---

### Post by Afief.h on 2008-09-08
> **isachan said:**
> Well, I meant to say that _make sure_ the last two lines of /etc/modprobe.d/alsa-base file are as follows:

options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=toshiba position_fix=1

...where this line "options snd-cmipci mpu_port=0x330 fm_port=0x388" 
should be already there.

By looking at some posts in the past, I think I have confused some people.

Anyway, Afief.h, try right-clicking the sound icon on the bottom panel, and select the configuration menu. The KMixer config window should show up an look for the screen with a lot of check boxes where you can select which sound channel you can bring up on the volume setting screen.

Check Front, PCM, Headphones, etc., and go back to mixer volume setting and you should be able to crank up the left / right volumes or altogether.

Also, check your headphone plug is all the way in. 

I tried 8.10 Alpha 5 just today and that's how I brought up my sound.

Isao

Done that, still only getting sound from one earphone(it works correctly on windows so it's not a hardware problem)

Did you get the touchscreen to work on Alpha5? I followed the guide that was given to me, but couldn't bring it to work(was planning to try again after Ibex release)

---

### Post by zujenbe on 2008-09-09
@WACOMalt

thats very strange, i managed to push 2hrs! i was quite impressed. I think if i had the balls to attempt any acpi changes, i could get it far longer...

by the way, has anyone worked on getting suspend mode fixed? this would be great!

---

### Post by _francis on 2008-09-10
> **martinjochimsen said:**
> Hi _francis

After I blacklisted thermal in /etc/modprobe.d/blacklist I added these 4 lines to /etc/modprobe.d/options

options thermal.act=-1
options thermal.crt=-1
options thermal.nocrt=1
options thermal.psv=-1

So now my /etc/modprobe.d/options looks like this

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2
options thermal.act=-1
options thermal.crt=-1
options thermal.nocrt=1
options thermal.psv=-1

and I can boot up without nolapi noapi acpi=off
I'm still useing kernel 2.6-24-21-generic

Martin :-)

By the way I used this really easy guide for my wireless from mike_1
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

This worked great and I everythings working just fine now - thx!

---

### Post by tC_Crazy on 2008-09-11
Has anyone else had an issue with the 2.6.24-21 kernel/wl and wpa2? 
I recently upgraded to that kernel, and it started using the wl driver for wifi (which works great for unprotected networks). However, when attempting to connect to my university's WPA2 network (bypasses slow login screens), and I submit my information the first time, it causes the entire system to lock up and I have to do a manual power-off. I didn't have this problem in 2.6.24-19. Any ideas?

---

### Post by gali98 on 2008-09-11
I used the wl driver (on a tx2000 but I think it is the same card...) and connected to a wpa1 ap.... Not sure if that helps you at all. 
Oh and I am on the -21 kernel...
Kory

---

### Post by tC_Crazy on 2008-09-12
Thanks, but I'm pretty sure it's a different wireless card (this one is a/b/g/n/BT). I think it's bcm4315 or 2315 or something of that nature... the exact model escapes me. 

Not a huge issue for me, just an annoyance. It may be worse for people who utilize WPA2 for their home networks.

---

### Post by phormix on 2008-09-12
What happened to the rest of the posts in this thread? I seem to remember a lot more, and the google cache shows 19+ pages...

Edit:: They just came back. It was stuck with only two pages for awhile... weird.

tx2524ca (tx2500 series).
Ubuntu Hardy 8.04/32bit - kernel 2.6.26.5

- Ethernet: working
- Wireless [BCM4322 802.11a/b/g/n]: b43 doesn't work, ndiswrapper doesn't work, wl (broadcomm closed-source driver) works intermittently
- touchpad: working
- sound [Azalia]: working (Intel HD Audio /w Realtek driver, options model=toshiba)
- bluetooth: working
- CPU scaling: not working
- Remote control: not working
- Tablet/digitizer: working (not sure about pressure-sensitivity, no rotation yet)
- graphics [ATI fglrx driver]: working
- media buttons: (volume only)
- webcam: working (v4l2)
- cardreader: working

---

### Post by phormix on 2008-09-12
> **tC_Crazy said:**
> Has anyone else had an issue with the 2.6.24-21 kernel/wl and wpa2? 
I recently upgraded to that kernel, and it started using the wl driver for wifi (which works great for unprotected networks). However, when attempting to connect to my university's WPA2 network (bypasses slow login screens), and I submit my information the first time, it causes the entire system to lock up and I have to do a manual power-off. I didn't have this problem in 2.6.24-19. Any ideas?

On mine when using WL the wireless cuts in out and regularly. It doesn't freeze the system though...

What's your actual card show up as in lspci?

---

### Post by phormix on 2008-09-14
Did anyone manage to get the microphone working on theirs? Sound's fine but I noticed that:

a) No luck with the internal mic at all
b) With external mic, I can turn up the pass-through volume and hear it through the speakers, but get no input when recording.

Also, as some others have mentioned, it seems the max volume is lower in 'nix than in Windows?

---

### Post by kg6gfq on 2008-09-21
I've been running Intrepid for a month or so, and things work pretty well, for the most part.  

- Ethernet: Working
- Wireless (the b/g card): Working with wl driver
- touchpad: Working
- sound: Working (except built-in mic)
- CPU scaling: Working (with this howto: [http://ubuntuforums.org/showthread.php?t=844754](http://ubuntuforums.org/showthread.php?t=844754))
- Remote control: not working
- Tablet/digitizer: working (with pressure sensitivity and rotation)
- graphics: working (see below for details
- media buttons: volume works, play/pause/etc work intermittently (though that may be a problem with banshee
- webcam: working
- cardreader: untested
- suspend: nearly working (see below for details)
- hibernate: not working

Graphics issues:  I've been using the radeon driver, since fglrx doesn't work with the latest version of X.  I can use a second monitor with xinerama, but it doesn't support rotation.  I can use rotation but not the second monitor with xrandr, which is unusual because xrandr ought to support the second monitor.  When I turn it on using xrandr on the command line or a gui like "Screen Resolution" or grandr, however, the external monitor goes blank.  the mouse can move off the builtin screen, but it does not appear on the other monitor.  Any ideas on the reason for this?  

Suspend issues:  The computer suspends fine and wakes fine, but upon waking the builtin keyboard doesn't work.  An external USB keyboard works fine, but not the builtin one.  I'm going to try changing my xorg.conf to see if it helps.

---

### Post by jubej on 2008-09-22
Hi kg6gfq!

My laptop: hp tx2510us
OS: Ubuntu Intrepid ibex alpha5 and i have these results:
Kernel: 2.6.27-3

- Ethernet: Working
- Wireless (the b/g card): Working with wl driver
- touchpad: Working
- sound: Working (except built-in mic)
- CPU scaling: Working OOTB its running OnDemand from 500MHz to max :=)
- Remote control: not working
- Tablet/digitizer: not working i dont know how the wacom drivers is not uppdated to the new kernel)? how did u do?
- graphics: working? (I dont have 3d acceleration)
- media buttons: volume works, play/pause/etc work exept the ones on the lcd botton right corner.
- webcam: (Not Working, i dont know how everyone has their cameras working please help)
- cardreader: untested
- suspend: nearly working 
- hibernate: not working



How did u get the camera and Tablet/digitizer: working (with pressure sensitivity and rotation) with the new kernel? I have sound when looking movies or listening to music, but in ekiga it seem that it wont recognise the camera or the sound. do u have 3d aceleration?

I tried to install cheese to see if the camera started to work but nothing. any tips here?

By the way ubuntu 8.10 its awsome, i dont have to do the acpi=off or anything everything its great, even the cpu scaling.


i just dont get the other stuff that works for you working for me.

Thnx for any help





lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by kg6gfq on 2008-09-22
Well, I guess I hadn't tested the webcam on the -3 kernel; I'm having issues with it too.  I'll tinker with that after updating to the -4 kernel.  

Audio in ekiga works fine for me, with the exception of the internal mic which never worked.  

To get wacom working again you have to repeat the steps of the tutorial; this seems to be required for each kernel update, unfortunately.  I finally got tired of it and threw together a script for the procedure, which I've attached.  It ought to work, but if it gives any errors or doesn't work after restarting X you should check the script or just follow the tutorial again:  [http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

Because you have to re-install the driver after each kernel update, you may want to wait until you update to the -4 kernel that just came out.  I'm doing that right now, and I'll report back when I've tested it.  

Hibernate works if you do "sudo /etc/acpi/hibernate.sh force", but I would like to have a working keyboard after suspend because hibernating (at least that way) is rather slow.  I've tried the uswsusp package for hibernate/suspend with no success.  

Other issues:  Pidgin is segfaulting at startup.  Skype is missing a .so file, I'm taking a look at that now.  

I must agree that Intrepid is great!

---

### Post by gali98 on 2008-09-22
k6kfq
Nice script. When Intrepid comes out, I think I am going to put together a script that does the same thing, but has troubleshooting info and stuff. It will help with tutorial time and and when people come to the thread they will already have the info I need to help them. 
Kory

---

### Post by jubej on 2008-09-22
hi kg6gfq

I run the script and it ended with no errors. but still i did not work. here is what i did:

downloaded the script made it executable. and then in the terminal i typed:
 ./wacominstall.sh

everything whent oki. and in the tutorial its said that after run the modprobe wacom
ill get the touch screen and digitizer to work but uncalibrated. but nothing happen.

another thing i did was to upgrade to de kernel 2.6.27-4 and then restarted and then run the script again and it seems to work bacause everything runs until everything finished and im again at the terminal.with no errors, but still i cant get the mouse to move with my fingeer or the pen.

i dont know what im doing wrong, please help.

here I attached the terminal output and my xorg.conf

but as I understand even with the xorg not configured Ill still be able to move the cursor right?

---

### Post by gali98 on 2008-09-22
As far as I was aware, it does not work on the .27 kernel yet. Am I wrong?
I simply tried it on the livecd (did not want another patition to worry about) and I could insmod it, but it did nothing.... Like you are describing... Has anybody got it working on the .27 kernel?
Kory

---

### Post by jubej on 2008-09-23
Hello!

gali im happy to say that its working in my ubuntu 8.10 kernel .27!!! yeahhhh

its really good i just run the script and then editet the xorg like in the tutorual then restarted the X-server and it work really good.

TNX kg6gfq for the help. 

But I wonder somthing:

its working with the digitizer really good I did not have to calibrate or anything. but It wont move with the finger. is it somthing in the xorg.conf that i did wrong? maybe in the touch section?

Another thing how did you get skype to work on ubuntu 8.10 x64? i tryed to download and install from the webpage and its says it the wrong architecture.

Anyway thnx, and the camera its working with cheese :) but not with ekika :(

---

### Post by kg6gfq on 2008-09-23
I've got the digitizer working on the .27-4 kernel with no trouble.  I don't normally enable the touchscreen, so that may not work...  jubej, are you sure you have the devices set correctly in xorg.conf?  

The camera is working in the .27-4 kernel, no idea what the issue was in -3.  In ekiga, you should make sure it's set to use v4l2 rather than v4l.  

gali, that script sounds like a good idea.  I would do something similar, but I don't really know enough to make it output the correct troubleshooting info.  

I still can't figure out why the keyboard stops responding after returning from suspend.  

There is currently no 3d acceleration for us in 8.10 because, though we now have an fglrx driver, it doesn't seem to work.  Anyone know if this will be fixed soon?  

Skype's web site does not have a 64bit version for download, it seems.  Instead, add the medibuntu repositories ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)).  Right now, though, there seems to be a problem either with that package or with a supporting library.

---

### Post by gali98 on 2008-09-23
jubej just upload your xorg.conf and do the command:
ls -lR /dev/input

and post its output as well and I can help you get it straightened out...
Anything special to get the 27 kernel to work? Also what folder does the module build in? (2.6.24 or 2.6.26)
Wow that stinks about the video driver... I'm sure it will get fixed sooner or later, hopefully sooner.

Kory

---

### Post by jubej on 2008-09-24
hi Gali 98!!

moving the mouse with the pen works. the thing that dont work is moving the mouse with the finger, I supose that it is the touchscreen right? because moving the mouse with the mouse is the stylus option right?

what about the eraser how does it work? i  writed something with the pen and then I turn it around like you do when you have a eraser, I tryed to erase but nothing happen. Or maybe Im using the eraser in a very stupid way?

here in this tarfile is my xorg.txt and a text file with the 
ls -lR /dev/input.


Another thing i think about is this:


Does your screen get really warm at the right side of the lcd screen? if I put my hand on the right side i feel that its really warm, while the others sides are cold. is that normal? I dont remember feeling it this warm when i bougth it with vista? is it something that linux make the lcd really warm? is it dangerous?

thnx for any help.

---

### Post by gali98 on 2008-09-24
Okay one more question... What model laptop do you have?
Do you have restricted drivers(yes that was two:))
Kory

---

### Post by jubej on 2008-09-25
hi
My laptop is a hp tx2510us
OS: Ubuntu Intrepid ibex alpha5 and i have these results:
Kernel: 2.6.27-3

by the way did you feel that the right side of the lcd panel is really hot? is that normal?

---

### Post by gali98 on 2008-09-25
Yes mine gets relatively hot.... But I am pretty sure it did that in vista too..
You're probably just on ubuntu longer :)

Okay after looking at your xorg.conf for a very long time, I finally found the one little mistake..
you need to change 
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event"
under touch to:
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-"
 
(the "-" at the end) and that should work.
Also what linux wacom version do you have. Another thing to check is to run wacomcpl and see if touch shows up there.
Kory

---

### Post by martinjochimsen on 2008-09-25
Hi

I dualboot with Ubuntu 8.04.1 and Vista on my tx2590. In Vista there is a small "onscreen"-keyboard which I can use with either the stylus or my finger. I think I once saw a program for a similar keyboard for Ubuntu, but now I can't remember the name or find anything about such a program.
Does anybody now the name for that kind of app or am I just make stuff up in my sick brain!!!

Martin :-)

---

### Post by martinjochimsen on 2008-09-25
...nevermind!!!
Ofcourse right after asking I find this thread ( [http://ubuntuforums.org/showthread.php?t=236405](http://ubuntuforums.org/showthread.php?t=236405)) an "onBoard" seems to do the thing for me.
Over and Out.

Martin :-)

---

### Post by tC_Crazy on 2008-09-26
Have any of you figured out how to solve the updating problem on Intrepid Ibex? I tried a clean install of Ibex Alpha 5 and it installed smoothly. However, when I tried to update, it went into thermal shutdown midway through. I had to do a dpkg from the recovery boot option to try to fix it. Now it starts, but there's a problem in X... after logging in, I get a white screen and nothing else. tty still works. For the time being, I just reverted back to an image of my Hardy partition I made before the upgrade.

The main reason I'm trying to upgrade to Ibex is b/c of the horrendous battery life on Hardy. It's impossible to get anything done with that much battery life. I'm on Vista right now, and have been working for 2:40 with 15% battery life remaining. If I can pull 2:15 on Ubuntu, I will be satisfied.

---

### Post by fbdelivers on 2008-09-26
I was just about to do an upgrade as well to intrepid. What does everyone recommend?  Upgrade from 8.04 or do a clean install?

Thanks

---

### Post by kg6gfq on 2008-09-27
The problem you're having with X is a result of compiz trying to start when 3D acceleration isn't supported.  I forget where you can change this...  Anyone know?  You may also be able to do a Ctrl-Alt-F1 to get to a terminal.  Run "sudo killall compiz" and "sudo metacity," perhaps?  I'm not quite sure about that.  If you can get from compiz back to metacity I would suggest installing the compiz settings applet, running it, and using it to switch your window manager from compiz to metacity.  

Hopefully that works, if you like I can hunt down the exact config files you need to edit.

---

### Post by tC_Crazy on 2008-09-27
I assume this has to do with the video drivers not being supported by the new kernel? Maybe it's best to wait until the final build of intrepid is released.

---

### Post by fbdelivers on 2008-09-27
I just did a clean install of alpha 6 for intrepid.  After running the clean install I went through and marked everything to update.  This got me to kernel version 2.6.27-4.  I tried to back track through this thread (used to have most everything working with hardy) and haven't had a lot of luck.

System boots - 
WLAN doesn't work.  WL shows up in the restricted driver mode but I get no blue light for wireless.  Do I need to disable acpi=off on boot to get this to work again?  Do I still need to disable all of the thermal modules still?

WACOM - doesn't work either.  I tried the above script and it didn't generate any errors but so far no luck.  I tried an older xorg.conf file from when it worked earlier for me but I must be missing something.  Do the earlier tutorials still work for intrepid?

Thanks

---

### Post by kg6gfq on 2008-09-27
**A note on the script:** it does nothing to your xorg.conf!  You need working inputdevice sections in xorg.conf for the script to do anything worthwhile.  For that I would recommend gali98's [tutorial]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447").  

**Update on the video drivers:  **

radeonhd from git:  I can use my external monitor with xrandr now, but rotation doesn't work.  

radeon:  The external monitor does work with xinerama, though there are some issues setting the resolution.  Screen rotation works.  

fglrx:  Still no luck, and no idea what the source of the problem might be.


@fbdelivers: 

The script is merely a compilation of all the commands used in gali's tutorial, so the tutorial should work as well.  Just watch for an error in the step that copies the .ko file, because when it is compiled it seems to go into a different directory now.  The following command should work no matter where the .ko file has been placed after the installation:  

```
sudo cp ./src/2.*/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

I have acpi=off in the boot parameters, though I haven't tried changing it, and I don't think thermal is disabled...  But my wireless works fine, so long as I don't forget to switch it on.  I've had it configured since around Alpha 3, though, and at that time it couldn't be done through restricted driver manager.

---

### Post by fbdelivers on 2008-09-27
Thanks for the suggestion - I'm still struggling with Alpha 6.  I ran through the script for enabling wacom. After doing a reboot during boot I get stuck with powernowd trying to start.

Not sure what part of the wacom tutorial would cause me problems in that section.

---

### Post by tC_Crazy on 2008-09-28
If you are running Intrepid, then you should not have to use any boot parameters, nor should you have to blacklist the thermal module. It should be a normal install, just like any other computer. 

kg: where did you get that radeonhd driver from?

---

### Post by fbdelivers on 2008-09-28
I think that it's the xorg.conf file that I'm using that is causing the issues on boot.  I used an earlier version prior to making the switch to intrepid alpha 6.

---

### Post by jubej on 2008-09-29
Hi gali98 and kg6gfq

i jsut wanted to say thank you for all your help. the script worked really god on my hp tx2500us.so thnx kg6gfq.

and gali98 thnx for finding the error in my xorg.conf file, now i can move the arrow with my fingers to. is not so calibrated yet but i gues ill just haave to do the calibration in the tutorial. 

by the way, has anyone make the bottons on the down right corner of the screen work? for exampel rotation, and to launch elisa?

and the infrared control, is there any way to make it work?

---

### Post by kg6gfq on 2008-09-29
_powernowd_ has been causing problems for me too.  The pattern I've found is that unless I've had to do a hard reboot powernowd will start so long as the power cable is unplugged.  You can plug it back in immediately after powernowd has started, though.  I don't know why it happens, but I guess I should post a bug report one of these days...  

_Update on radeonhd:_ It's no longer working properly with the second monitor...  xrandr extends the desktop onto the second monitor, but the colors are wrong and the image is not clear.  I'm going to try putting an entry for the second monitor in xorg.conf, though, and see if that helps.  

(tC_Crazy: I got the radeonhd driver from the git repository listed [here]("http://www.x.org/wiki/radeonhd#head-107f8ec30e84804907b4af6cdb20fbdd0056eefb") and compiled it.  Thanks for the hint on boot options and the thermal module; I'll tinker with that as soon as I have time.)  

@jubej: As mentioned earlier in the thread, only some of those buttons work properly; the others require a driver that hasn't yet been written.  I've been tinkering with the IR remote and can't figure out how it works either; I suspect it too may require special, as-yet-unwritten drivers.

---

### Post by gali98 on 2008-09-30
For me the control worked out of box, but I have the tx2000 so I really couldn't help you on that. The bottom two buttons do not work. They are not recognized as keys, so to work, someone would have to write a driver for them.
Edit: I just now read kg6gfq's post... anyway...
Um... try using xev and see if the infrared controller picks up events... then maybe you can map the keycodes to something.
Kory

---

### Post by jingtra on 2008-10-04
kg6gfq: Could you post the xorg.conf file? Is really struggling with installing the drivers and using the external screen

---

### Post by kg6gfq on 2008-10-05
@jingtra:  The important parts of the xorg.conf for multiple monitors are as follows:
```
Section "Screen"
	Identifier      "Default Screen"
	Device          "Radeon"
	Monitor         "Generic Monitor"
	DefaultDepth	24
	SubSection "Display" # <--Add this subsection if you don't have it already.  
		Depth           24
		Virtual		1280 1824 # <--Change these values to set the maximum size of both your screens put together.  
	EndSubSection
EndSection
```
```
	Driver	"radeonhd" # <--Make sure this is set in your "Device" section.  If X won't start with this set you probably don't have the newest driver from git (or the version you downloaded is broken).
```
I've also attached the scripts I use to switch the external monitor on and off.  Read the comments in those files for more info.  Have you managed to install the radeonhd driver from their git repository?

Remote Control: Picked up by xev.  Thanks gali!!  Many of the buttons are the same as their counterparts on the laptop itself, so if you've already mapped volume, media, and side-of-screen buttons they should work.  The two bottom-of-screen buttons aren't picked up by xev though, as gali said.  Neither is the act of rotating the screen, unfortunately.  

"acpi=off": as tC_Crazy pointed out, this is not a necessary boot parameter and in fact should probably not be used in intrepid.  Remove it by editing /boot/grub/menu.lst.

powernowd: With the newer kernel powersaved seems to work far better than powernowd - I've only had it hang once during boot, and that was after a hard shutdown.  If you're having difficulty with powernowd I would recommend installing powersaved to replace it.

---

### Post by jubej on 2008-10-06
Hello

Gali98 you are right the remote control works really good. i just have to map the others bottons that don work, but i have to learn how.

By the way Im experience something really wierd. on the screen the left dvd button and the media button was working before but now they don work, nothing happens on xev. it had the keycode 200 and 201. but now it seem that the mousepad on and off button is mapped 200 for off and 201 for on. so when i activate the mouse pad it will launch like 15 instans of the mdeia player elisa. i tryed the xev and when I turn the On or off button you will see the keycod 201 go on like forever. do you have the same problem? Any ideas?

---

### Post by brainsqueezer on 2008-10-06
Anybody is having problems with latest kernels (2.6.26 or newer) in tx2000? I'm googling about it but seems that nobody else knows about it. Boot stops 2 times and I have to press start button to continue booting.


PS: My batteries are also loosing capacity so fast!!
cat /proc/acpi/battery/BAT0/info returns this:
design capacity: 5100 mAh last full capacity: 3072 mAh

---

### Post by jingtra on 2008-10-06
I think the problem is that i don't know how to install radeonhd

Have tried:
 $ git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-radeonhd
$ git pull
 $ git fetch
   $ ./autogen.sh
   $ make
$make install

---

### Post by Rangua on 2008-10-08
Hi everyone, i've been following this thread for a while now and i'm happy to be running intrepid on my tablet :D so, thank you guys ... I've updated last time today and problems began: stylus stopped working (i've reinstalled the driver and now it works again, but i have no eraser and it feels odd), and i'm getting a beep everytime i press a wrong key (like pressing tab too many times on terminal), i have no idea how to turn off the annoying sound.. has anyone had this problems??

update: i ran xset b off; xset b 0 0 0 and the beep is gone! sorry for the sort of off-topic post...

---

### Post by isachan on 2008-10-09
It's been a long time since last time I posted anything here. I had a few new discoveries I'd like to note here regarding Kubuntu 8.10 Beta.

I'm typing this post from it and used maybe for less than 30min, but I like this thing already because :

1. Finally the wireless works out of the box ! No ndiswrapper necessary. I can't believe ! Just right click on the globe icon on the lower right corner, then activate the eth1 with a few more settings (encryption keys, etc.). That's it !

2. No boot parameters needed, nor modifying the thermal modules.

3. CPU scaling works out of the box ! It's so quiet ! I don't have a time now to do a battery testing. I'll do that later.

I hope Canonical will keep solidifying their distro with a good trend like this, instead of breaking stuff after RC release and/or major release.

Isao

---

### Post by tannalv on 2008-10-10
> **isachan said:**
> 
1. Finally the wireless works out of the box ! No ndiswrapper necessary. I can't believe ! Just right click on the globe icon on the lower right corner, then activate the eth1 with a few more settings (encryption keys, etc.). That's it !

2. No boot parameters needed, nor modifying the thermal modules.

3. CPU scaling works out of the box ! It's so quiet ! I don't have a time now to do a battery testing. I'll do that later.

I hope Canonical will keep solidifying their distro with a good trend like this, instead of breaking stuff after RC release and/or major release.

Isao

Welcome back! :)

1. Hmh. What wireless card do you have? Mine doesn't seem to wish to work.
08:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

2. Yea. Made a fool of my self by asking the acpi-thread on the linux-kernel about this. They've made some quick fix on this problem, as several HP-BIOS'es seems to have the same type of problem. The quick fix means that if the trip-point is set to below 0C it will regard this as false. (The tx2500 bios has a trip point set at -273C, not even space is that cold)

Also, what arch distro did you try? I'm wondering if maybe I'd have better luck putting i586 on mine rather than x64.

But yea, getting rid of the thermal trip-point was a big relief.

---

### Post by isachan on 2008-10-11
I'm running on AMD64 architecture of Kubuntu 8.10 Beta.

I've got 802.11 b/g + bluetooth, but lshw and dmesg gives me different results as follows :

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network                                        
       description: Wireless interface             
       product: BCM4312 802.11b/g                  
       vendor: Broadcom Corporation                
       physical id: 0                              
       bus info: pci@0000:08:00.0                  
       logical name: eth1
       version: 01
       serial: *********************
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.102 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: ******************
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ********************
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

dmesg | grep 43*

[   68.782324] wl: module license 'MIXED/Proprietary' taints kernel.            
[   68.788515] wl 0000:08:00.0: setting latency timer to 64                     
[   68.880514] ieee80211_crypt: registered algorithm 'TKIP'                     
[   68.880514] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.6<3>RTNL: assertion failed at /build/buildd/linux-2.6.27/net/core/dev.c (1029)

Which one I should go by ?

---

Just to clear things up on the steps I took to wireless connection...

Right click on the gray globe icon on the lower right side of the task bar.
Choose "New Connection..." and "eth1" from the menu.
Choose your access point (wifi router) and click "Next".
Enter your encryption settings and click on next.
Keep clicking next until it's grayed out, and click "save & connect".
Wait for a minute and verify the globe icon becomes a signal strength indicator icon.
Open a web browser (Konquerer) and check your connection.

Isao

---

### Post by isachan on 2008-10-11
Bah, I just found out that there is no sound with Intrepid Beta AMD64.

I think I have to add the line I posted before to the alsa conf file and restart, but I don't want to install to HD just yet. For the same reason I can't test the fglrx driver.

EDIT:
Woops, jumped on the gun again. There is a sound, but the volume is extremely low.
I tried the headphone connected to external speakers and crank up the volume all the way up, then I finally heard some sound.
Although it's still very faint.

Also, this new version of Adept package installer is working funny.

I think I'm going back to the waiting mode again...

Isao

---

### Post by proud2bamerican on 2008-10-11
This might help

[http://www.youtube.com/watch?v=YbnKoJP1_xk](http://www.youtube.com/watch?v=YbnKoJP1_xk)

---

### Post by ricky045 on 2008-10-11
The tx2500 comes with the brand new Puma plattform from AMD. Therefore it has a slightly better CPU and more important a much better graphics solution. The tx2500 has the best graphics performance i could find on a tablet pc. Apart from these differences the tx2000 and tx2500 are almost the same.
=======================
ricky045 

[ringback tones](http://www.myringtoneshub.com/)

---

### Post by gali98 on 2008-10-11
I'm on Intrepid Beta on the tx2000z and it works great, with a bit of configuration.
One thing that the tx2000 series has going for it is that it has better support for linux. By that I mean that the 3d driver for it is much better in quality (though overall quality is tainted by being a nonfree driver - you win some you lose some)
and the the power management is much better.
Kory

---

### Post by kg6gfq on 2008-10-13
> **jingtra said:**
> I think the problem is that i don't know how to install radeonhd

Have tried:
 $ git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-radeonhd
$ git pull
 $ git fetch
   $ ./autogen.sh
   $ make
$make install

I did a fresh reinstall of 8.10 and when I tried to add the radeonhd driver I figured out your problem:  First of all, you shouldn't need to do "git pull" or "git fetch".  The problem is that "make install" installs the driver to /usr/local/lib/ rather than /usr/lib/ (which is where X expects it to be.  I think there's a more elegant solution, but here's my quick fix:
```
sudo apt-get remove xserver-xorg-video-radeonhd
sudo ln -s /usr/local/lib/xorg/modules/drivers/radeonhd_drv.so /usr/lib/xorg/modules/drivers/radeonhd_drv.so
```
The first line isn't strictly necessary, since the second line will overwrite the version of radeonhd installed by synaptic, but if the version in the repositories is ever updated it will overwrite the version installed from git.  Hopefully the current git version (or something better) will eventually make it to the repos, but until then I think we're best off doing it this way.

---

### Post by vokesalex on 2008-10-15
Just noticed this
[http://www.phoronix.com/scan.php?page=article&item=canonical_catalyst_811&num=1](http://www.phoronix.com/scan.php?page=article&item=canonical_catalyst_811&num=1)

Has anyone tried this yet? I'm hoping to give it a go when I get home from work tonight.

---

### Post by tC_Crazy on 2008-10-16
That new ATI driver sounds pretty cool! I can't believe ATI would give that kind of prerelease driver software to Canonical. That's pretty amazing.

---

### Post by lord_phantom on 2008-10-16
I tried this driver and it was working but after next upgrade the dependences broke and i were left with a plain console.

The biggest problem right now is the broken sound.

---

### Post by bdjohnso10 on 2008-10-17
From the Ubuntu 8.10 Beta 1 release,

What doesn't work:
1) Sound is extremely quiet as if some internal amp or possibly setting is not correct.

2) Wacom, I have installed some drivers and tools through synaptic package manager but no dice.

3) Quickplay buttons and screen rotation.
(both the button and the automatic rotation)

4) Remote

What does work:
1) Video, after updating I was able to install ATI 3200HD drivers and now I even have catalyst control center in accessories!

2) Wireless, with the broadcom driver and it works beautifully.

3) Dual processor and processor scaling.

Not Tested:
All the rest but there isn't much more.



Right now sound is my biggest issue then the Wacom pen.

---

### Post by gali98 on 2008-10-17
On 1)
Just use alsamixer in the terminal.
For whatever reason when you first install, some of the settings are turned down.
Just go in and maximize them. Look for things like "Front" and External Speaker.

on 2)
I thought I got them to work, but you are the second person who said they didn't.
I am using the latest release (0.8.1-5) and it works great. Here is a link to my tutorial for it:
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

on 3)
Those buttons do not magically work if that is what you mean. If you want rotation, you will need to make a script and map it to a button. If they just don't work in general then try using the command "xev" in the terminal and see if you can get any output.
On 4)
also try xev to see if you can get output.
If you can just use keyboard shortcuts (In System->Prefereneces)
to set the buttons.

Kory

---

### Post by tC_Crazy on 2008-10-17
A couple questions before I spend a couple hours downloading, burning, and installing:
1. After installing the new ATI Catalyst driver, can you update the system without it breaking X due to video problems?

2. Does updating still stop in the middle due to thermal shutdown?

3. What is battery life like? I saw you mention dual processor scaling support, but does that mean 2+ hour battery life or just that it keeps temps down? I know the two are related, but battery life is my number one priority next to #1. 

Thanks!!

---

### Post by bdjohnso10 on 2008-10-17
> **tC_Crazy said:**
> A couple questions before I spend a couple hours downloading, burning, and installing:
1. After installing the new ATI Catalyst driver, can you update the system without it breaking X due to video problems?

2. Does updating still stop in the middle due to thermal shutdown?

3. What is battery life like? I saw you mention dual processor scaling support, but does that mean 2+ hour battery life or just that it keeps temps down? I know the two are related, but battery life is my number one priority next to #1. 

Thanks!!

1 After installing the ATI driver everything was hunky dory.  No need to restart the X or anything,  you may need to restart but I don't remember correctly.

2 No shutdown in the middle of loading Ubuntu you get all the way to the desktop without any modification to boot options.

3 Battery life looks like its great.  Haven't tested it specifically but looks like its on par with vista.

---

### Post by tC_Crazy on 2008-10-17
Thats good to hear because I just started the upgrade process. Should be done within the hour!

---

### Post by tC_Crazy on 2008-10-17
OK, the ugprade was a success!
However, sound does not work, whatsoever for me. Even with headphones and full volume, there's nothing. Alsamixer isn't even showing the standard row of mixers... just master volume and that it's using PulseAudio... maybe I should uninstall pulse and see what happens...

---

### Post by bdjohnso10 on 2008-10-17
> **tC_Crazy said:**
> OK, the ugprade was a success!
However, sound does not work, whatsoever for me. Even with headphones and full volume, there's nothing. Alsamixer isn't even showing the standard row of mixers... just master volume and that it's using PulseAudio... maybe I should uninstall pulse and see what happens...

Its the same with me but I have a set of external speakers with an amp and its very faint if I tun it all the way up.

---

### Post by tC_Crazy on 2008-10-18
Bah, I tried to download and compile the realtek driver and it ended up screwing up my sound even worse! i can't even get alsamixer to work now... reinstalling alsa wont' work either... looks like i might have to revert/reinstall. i'll wait until there's a real solution to the audio problem, though.

---

### Post by tC_Crazy on 2008-10-18
I got sound to work! Realizing that my sound was fully screwed, I followed a guide to reinstate ALSA to the default Ubuntu state. Simply run ```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

Depending on your system, it may remove certain packages like VLC sound packages... I just let it go through and do its business. After that, and a simple ```
modprobe snd-hda-intel
``` sound was working at full volume!!

Try this out and let me know if it works for you guys! [intrepid beta 1 x64]

---

### Post by bdjohnso10 on 2008-10-18
No dice,
Did those exact two commands and no volume still.  Tried again with all of the settings but there is nothing that gives me the louder sound.

---

### Post by tC_Crazy on 2008-10-18
Then it must have been a combination of some of the other crap I did last night (don't remember much). I also have some other random audio stuff installed to try to reduce sound card latency for a program. That includes portaudio and JACK. Then again, it could have been something that the Realtek install script did. I'm not sure. If you guys want any config files or logs let me know, I'd be happy to provide 'em. I just don't know enough to figure out how I got it working.

---

### Post by phoenixmdm on 2008-10-18
So I've got nearly everything working on my tx2510us.

Works:
Wireless
speed control (powernowd sometimes hangs on bootup, booting without ac plugged in seems to help reduce this)
webcam (v4l2)
sound (using the tips from this thread)
media buttons just worked
digitzer works great, so does touch!
and here's the kicker:
FRONT MICROPHONES!!!!

Here's what I did, really simple. Go into alsamixer, hit tab to get to the capture levels. Crank up "front mic boost" to 100%, and change "input source" to front mic. Front mic means the pair next to the camera, mic means the input on the front, and I haven't quite worked out where line in is. My capture levels are 48 for both L and R, and digital is at 50%. Currently, it sounds great, can skype/ekiga no problem, and sound recorder hears me loud and clear.

Now to work out fan speed, since it seems to always be a bit loud...

---

### Post by tC_Crazy on 2008-10-18
phoenix,
Are you on hardy or intrepid?

---

### Post by phoenixmdm on 2008-10-19
I _was_ on hardy when I posted that. I installed the intrepid beta and now I'm completely lost in this pulseaudio stuff, but at least I've got the sound output working.

---

### Post by Rangua on 2008-10-20
hi, could anyone help me configuring my xorg.conf? i've lost screen rotation after some update (couldn't know which since i'm updating almost every day) and i've read somewhere ati drivers are working fine now.. anyone been able to use compiz? well, if anyone wants to help me i've attached my xorg.conf
thanks in advance

---

### Post by gali98 on 2008-10-20
Here you go. I fixed a bit of stuff. I only messed with wacom stuff. I did not mess with video drivers or anything. This is expecting the values of
"Device" to be right as I have a tx2000 not a tx2500.
Kory

---

### Post by Rangua on 2008-10-20
thank you very much. i'll try n' mess with the video sections myself... if anyone else had the video configured right plz ... you know..

---

### Post by gali98 on 2008-10-21
Well the video sections looked right to me... but I don't know for sure since I don't have your laptop. Is something not working right?
Kory

---

### Post by tC_Crazy on 2008-10-21
Rangua,
Do you have wacom working on Intrepid? After I updated from Hardy it broke the wacom driver. It probably has to do with the new version of X. And yes, the new fglrx driver works perfectly on the current (fully updated) Intrepid Beta. That includes Compiz (works perfectly).

---

### Post by tC_Crazy on 2008-10-22
So I finally put the CPU scaling to the test today. Results? I'm still running at 2:45. Oh wait, just got a popup saying 1 minute left. 30% brightness, wifi on but using ethernet. =)

---

### Post by Rangua on 2008-10-22
hi, i have the wacom working. the touch is not calibrated and i can't do that with wacomcpl.. i have a little script that helps me recompile the driver whenever it stops working, it's just some instructions i got from some forum i can't remember right now (probably thegnark's tutorial)... if you'd like, you could try the script, just download the .tar and run the script on the folder you saved it. run it as root, or add sudo to the beggining of lines with #<- sudo... just read the script, it's really simple, i'm just lazy to go through all the commands every time... i've attached the script, you'll have to download the driver, the one i'm currently using is linuxwacom-0.8.1-4.tar.bz2  (could synaptic update the driver?, i mean, if i compile it myself)
 

As for the video driver, it's the only thing that's not working (i think). If i try to activate the visual effects through the system->appearance menu, it says Composite is not enabled. and:
> 
rangua@metacafe:~$ xrandr -d $DISPLAY -o inverted
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  158 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

otherwise, i wouldn't think it's not working.. the video part of the xorg.conf is set to defaults, does anyone know the correct parameters? (maybe i've messed up the default parameters :confused:)

i think i broke my camera too.. but that i think it's a hardware problem (since it works sometimes on linux and never on windows, it actually crashes the soft that's using it and later i have to hard shut the computer (on windows)), so don't worry about it (if anyone has any reason to think it's not a hardware issue... say so)

---

### Post by kg6gfq on 2008-10-22
> **Rangua said:**
> hi, could anyone help me configuring my xorg.conf? i've lost screen rotation after some update (couldn't know which since i'm updating almost every day) and i've read somewhere ati drivers are working fine now.. anyone been able to use compiz? well, if anyone wants to help me i've attached my xorg.conf
thanks in advance

You should be able to use compiz now, since you're using the proprietary ati (fglrx) driver.  However, that means you won't be able to use screen rotation because fglrx still doesn't support it.  If you want screen rotation back and don't mind losing the ability to use compiz you can change the line:
```
	Driver	"fglrx"
```
to
```
	Driver	"radeon"
```

---

### Post by Rangua on 2008-10-22
thanks!! that's great news, and i figured out why i couldn't use compiz, i had to install it first! XD sorry for the troubles.. thank you again

---

### Post by Rangua on 2008-10-22
um.. one more thing.. does X controls usb ports? i can't stop the xserver without loosing keyboard and mouse, and i think they're both usb.. anyone had similar experiences? 

PD: cool!! now i can show off my ubuntu tx2500 to everyone!!, but i think i'll keep with the radeon driver, rotation is nice having, maybe more than some flashy cool looking lights and things.. anyways: \\:D/

tc_crazy.. post if you've tried my script, i'm willing to help you in any way i can!

---

### Post by tC_Crazy on 2008-10-22
Thanks man, I just got back from class... will try the script in a few minutes. And about the webcam... it probably isn't a hardware problem. The YouCam crapware that HP bundles with the system is horribly unstable. I had to remove it in order to get my webcam to work. It used to freeze on launch and the only solution was a hard restart (it would cause the shutdown process to freeze). Uninstall Youcam from your Windows partition and see if that helps.

---

### Post by tC_Crazy on 2008-10-22
Wow, it works! I used that xorg.conf from above and this script (manually ran the commands in the terminal). Xournal picks up the ink perfectly! (I was having problems before with it stretching the ink and creating wierd vertical stretched blocks.. not aproblem anymore)
Wacomcpl also works for calibration! Thanks a lot!!!
Now just gotta wait until someone can get OneNote working in Wine haha.

---

### Post by gali98 on 2008-10-22
Wow a lot of posts went on!
@Tc_crazy
I used to get those weird lines in xournal and Gournal... I don't think it was wacom, I think it was the actual program doing it. Glad to here it is working...

On the webcam, I guess you using Cheese. I have the same problem. I think it is cheese on Intrepid (in hardy it almost never did it)

Also on the wacom in Intrepid, I have just given up using it on the beta because I update everyday and it almost always replaces the modules, but when I do have the module (from 0.8.1-5) it works perfect...

On the usb, no the kernel controls usb. It creates a device (in /dev) which X can access. However X may still be messing it up. Have you tried booting into recovery and seeing if it works?
Kory

---

### Post by Rangua on 2008-10-22
great! are you using fglrx or radeon driver? in case anyone wonders, to rotate screen (only with radeon) you need to run 

xrandr -o {inverted, normal, left, right} 

and to rotate the wacom input just do 

sudo xsetwacom set device rotate {NONE, HALF, CW, CCW} 

you need to change device with the name that's being given in xorg.conf (for me it's 'stylus', 'eraser' and 'touch')

as for the camera.. i booted windows and uninstalled the drivers for the camera and the software. after booting ubuntu i ran cheese but after waiting a while i forced quit (my hand was over the cursor) and the camera didn't worked... i tried to reinsert the module uvcvideo, but still no luck..

one last thing.. i've never tried wine, is it going to make my system slower? is it easy to remove everything that has to do with it afterwards?.. 

and a warning for all the tx2500 owners.. don't uninstall the vista that came with your computer, it voids the warranty.. i know, i've called hp and let them access my desktop only so they could tell me i had reinstalled vista and my warranty is voided... it sucks, it's corporate, it's hp ](*,)

---

### Post by Rangua on 2008-10-22
you're right kory, i had entered in recovery mode before and got the keyboard and mouse working.. so it's just X crashing (and when it does, i can't do alt+f1 to reboot from shell).
As for cheese, when it fails to turn on the camera, can you still use it on ekiga or other soft? once i can't use it on cheese, i can't use it ekiga.. dmesg tells me this
[   79.204184] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[   91.456193] uvcvideo: Failed to query (135) UVC control 2 (unit 3) : -110 (exp. 2).
[   98.624641] uvcvideo: Failed to query (135) UVC control 2 (unit 3) : -110 (exp. 2).

---

### Post by tC_Crazy on 2008-10-22
Rangua,
As long as you keep your recovery partition intact, you can keep your warranty. Just make sure you back up everything (especially the linux partition!) and then do a HP restore from the boot menu (shows up in GRUB as well). That writes the HP factory image to the standard Windows partition. HP techs won't be able to see ****.
And I'm using fglrx (love compiz too much use radeon). Plus, all of my note taking happens in OneNote so I don't have a dire need to use the tablet features in Ubuntu. Maybe I'll find a good reason, though.

---

### Post by gali98 on 2008-10-22
Thats why you don't let them rdp into your computer :)
I killed Vista for good finally. I was tired of its stink :)
anywho, I think we have different webcams.... I'm on the tx2000...
you have install luvcview right?
sudo apt-get install luvcview

Also, though this seems weird, I think if you move really fast in front of the camera while cheese has the gnome logo running, it increases the chances of working, but it may just be a coinky-dink :)
I read that 2.6.27 was supposed to merge a whole other group of support for webcams (used to be just uvc, and now there is something else, but I don't know what..)


on Wine, it doesn't take that much space, and doesn't run anything that I am aware of until you run a windows binary. It actually works well and fast.
Kory

---

### Post by Rangua on 2008-10-22
now, back to the camera... i've just installed luvcview, i don't know how to use it though.. tc_crazy, do you know where is the camera installed on the tx2500? (like /dev/????? ), or maybe the tx2000 has it in the same place.. or even better, how can i ask it to my system?

tc_crazy: don't you want the screen rotation? i hate to have the fan pointing at me when using the computer with the screen folded :S

kory: you could try the camera moving your hand at the same speed, rebooting, and repeating the process 20 times, and then 20 more without the hand, and maybe 20 more with different speeds.. then you could write a paper if you discover anything :P (make sure you get those uncertainties right!)

---

### Post by tC_Crazy on 2008-10-22
yeah screen rotation would be nice, but as I said the vast majority of my work in tablet mode is taking notes in class. that all happens in OneNote in Windows...  In my experience it is an unparalleled program. Organization rocks, all the input modes flow together seamlessly, and the search is amazing when studying for tests. I'll always have Windows because I have to work with OneNote and some Autodesk engineering software that is Windows-only.

---

### Post by gali98 on 2008-10-23
luvcview is just the webcam library. It does not have a program involved with it. I don't know where it ends up in dev... probably /dev/video or something similar.
To test it, you can also use multimedia systems selector to test it.
run
gstreamer-properties
in the terminal to test it.
I think I'll wait on the paper :)
Kory

---

### Post by bdjohnso10 on 2008-10-25
So, I guess that it is impossible to get wacom working on intrepid because it has the new Xorg.  I figured this out form the output of trying to makeinstall where it says it can't find x11.

I still haven't been able to get the sound working has anyone had any luck on intrepid?

```
brian@brian-laptop:~/Desktop/linuxwacom-0.8.1-6$ sudo make install
Making install in src
make[1]: Entering directory `/home/brian/Desktop/linuxwacom-0.8.1-6/src'
Making install in .
make[2]: Entering directory `/home/brian/Desktop/linuxwacom-0.8.1-6/src'
make[3]: Entering directory `/home/brian/Desktop/linuxwacom-0.8.1-6/src'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/man/man4" || mkdir -p -- "/usr/local/man/man4"
 /usr/bin/install -c -m 644 'wacom.4x.gz' '/usr/local/man/man4/wacom.4x.gz'
make[3]: Leaving directory `/home/brian/Desktop/linuxwacom-0.8.1-6/src'
make[2]: Leaving directory `/home/brian/Desktop/linuxwacom-0.8.1-6/src'
Making install in wacomxi
make[2]: Entering directory `/home/brian/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
make[3]: Entering directory `/home/brian/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
make[3]: Nothing to be done for `install-exec-am'.
test -z "" || mkdir -p -- ""
test -z "" || mkdir -p -- ""
test -z "" || mkdir -p -- ""
make[3]: Leaving directory `/home/brian/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
make[2]: Leaving directory `/home/brian/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
Making install in util
make[2]: Entering directory `/home/brian/Desktop/linuxwacom-0.8.1-6/src/util'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic  -g -O2 -D__amd64__ -MT wacomcfg.lo -MD -MP -MF ".deps/wacomcfg.Tpo" -c -o wacomcfg.lo wacomcfg.c; \
	then mv -f ".deps/wacomcfg.Tpo" ".deps/wacomcfg.Plo"; else rm -f ".deps/wacomcfg.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -pedantic -g -O2 -D__amd64__ -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o
In file included from wacomcfg.c:35:
wacomcfg.h:26:22: error: X11/Xlib.h: No such file or directory
wacomcfg.h:27:35: error: X11/extensions/XInput.h: No such file or directory
wacomcfg.h:28:36: error: X11/extensions/XIproto.h: No such file or directory
In file included from wacomcfg.c:35:
wacomcfg.h:58: error: expected specifier-qualifier-list before 'Display'
wacomcfg.h:62: warning: struct has no members
wacomcfg.h:67: error: expected specifier-qualifier-list before 'XDevice'
wacomcfg.h:75: error: expected ')' before '*' token
In file included from wacomcfg.c:38:
../include/Xwacom.h:23:24: error: X11/keysym.h: No such file or directory
wacomcfg.c: In function 'CfgError':
wacomcfg.c:71: error: 'WACOMCONFIG' has no member named 'pfnError'
wacomcfg.c:72: error: 'WACOMCONFIG' has no member named 'pfnError'
wacomcfg.c: In function 'CfgGetDevs':
wacomcfg.c:82: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:82: warning: implicit declaration of function 'XListInputDevices'
wacomcfg.c:82: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:83: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:85: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c: At top level:
wacomcfg.c:95: error: expected ')' before '*' token
wacomcfg.c: In function 'WacomConfigListDevices':
wacomcfg.c:135: error: 'XDeviceInfo' undeclared (first use in this function)
wacomcfg.c:135: error: (Each undeclared identifier is reported only once
wacomcfg.c:135: error: for each function it appears in.)
wacomcfg.c:135: error: 'info' undeclared (first use in this function)
wacomcfg.c:139: warning: ISO C90 forbids mixed declarations and code
wacomcfg.c:145: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:159: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:161: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:163: error: 'IsXExtensionDevice' undeclared (first use in this function)
wacomcfg.c:185: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:187: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c: In function 'WacomConfigOpenDevice':
wacomcfg.c:293: error: 'XDevice' undeclared (first use in this function)
wacomcfg.c:293: error: 'pDev' undeclared (first use in this function)
wacomcfg.c:294: error: 'XDeviceInfo' undeclared (first use in this function)
wacomcfg.c:294: error: 'pDevInfo' undeclared (first use in this function)
wacomcfg.c:294: error: 'info' undeclared (first use in this function)
wacomcfg.c:294: warning: left-hand operand of comma expression has no effect
wacomcfg.c:300: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:304: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:306: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:319: warning: implicit declaration of function 'XOpenDevice'
wacomcfg.c:319: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:331: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c: In function 'WacomConfigCloseDevice':
wacomcfg.c:340: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:341: warning: implicit declaration of function 'XFree'
wacomcfg.c:341: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c: In function 'WacomConfigSetRawParam':
wacomcfg.c:350: error: 'XDeviceResolutionControl' undeclared (first use in this function)
wacomcfg.c:350: error: expected ';' before 'c'
wacomcfg.c:351: error: 'XDeviceControl' undeclared (first use in this function)
wacomcfg.c:351: error: 'dc' undeclared (first use in this function)
wacomcfg.c:351: error: expected expression before ')' token
wacomcfg.c:351: error: 'c' undeclared (first use in this function)
wacomcfg.c:357: error: 'DEVICE_RESOLUTION' undeclared (first use in this function)
wacomcfg.c:363: warning: implicit declaration of function 'XChangeDeviceControl'
wacomcfg.c:363: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:363: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:368: error: 'BadValue' undeclared (first use in this function)
wacomcfg.c:368: error: 'BadRequest' undeclared (first use in this function)
wacomcfg.c:377: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:377: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:389: warning: implicit declaration of function 'XSetDeviceMode'
wacomcfg.c:389: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:389: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c: In function 'WacomConfigGetRawParam':
wacomcfg.c:397: error: 'XDeviceResolutionControl' undeclared (first use in this function)
wacomcfg.c:397: error: expected ';' before 'c'
wacomcfg.c:398: error: 'XDeviceResolutionState' undeclared (first use in this function)
wacomcfg.c:398: error: 'ds' undeclared (first use in this function)
wacomcfg.c:399: warning: ISO C90 forbids mixed declarations and code
wacomcfg.c:405: error: 'c' undeclared (first use in this function)
wacomcfg.c:405: error: 'DEVICE_RESOLUTION' undeclared (first use in this function)
wacomcfg.c:411: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:411: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:412: error: 'XDeviceControl' undeclared (first use in this function)
wacomcfg.c:412: error: expected expression before ')' token
wacomcfg.c:414: error: 'BadValue' undeclared (first use in this function)
wacomcfg.c:414: error: 'BadRequest' undeclared (first use in this function)
wacomcfg.c:420: error: expected expression before ')' token
wacomcfg.c:435: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:436: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:437: error: expected expression before ')' token
wacomcfg.c:445: error: expected expression before ')' token
wacomcfg.c:457: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:457: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:458: error: expected expression before ')' token
wacomcfg.c:460: warning: implicit declaration of function 'XFreeDeviceControl'
wacomcfg.c:460: error: expected expression before ')' token
make[2]: *** [wacomcfg.lo] Error 1
make[2]: Leaving directory `/home/brian/Desktop/linuxwacom-0.8.1-6/src/util'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/brian/Desktop/linuxwacom-0.8.1-6/src'
make: *** [install-recursive] Error 1
brian@brian-laptop:~/Desktop/linuxwacom-0.8.1-6$ 

```

---

### Post by gali98 on 2008-10-25
Well sound probably still isn't working...
But wacom works perfect. 
download the new release (0.8.1-6 just came out thursday)
[http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.1-6.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.1-6.tar.bz2)
You probably don't have all the dev packages... that's why you are getting all those errors.
Use these commands:

sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade

then use 
./configure --enable-wacom --prefix=/usr
make 
sudo make install
sudo cp ./src/2.6.27/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

in the linux-wacom folder you download.
if you still have trouble, upload your xorg.conf
(etc/X11/xorg.conf)

Kory

---

### Post by bdjohnso10 on 2008-10-25
Thanks so much, that worked.  What is the best way to input text.  Is there any side dock like in vista that you can handwrite to text or at least just type the letters.  Already tried character map but there is no return or other keyboard keys.

Lastly, has anyone had any luck getting the sound to work?

---

### Post by Rangua on 2008-10-25
tc_crazy, you were right! :KS camera works flawlessly if i stick with ekiga (if i try using it with another soft it may or may not work, but won't work afterwards). So it's not a hardware problem! :) (i actually got two dead pixels, but that's not the issue :mad: )

bdjohnso, you can use cellwriter, it's pretty much the same thing, but it doesn't have the continuos writing option. You could also try dasher, you'd have to train though, but you have to train cellwriter too anyways. There's also a soft called easystroke, it's a gesture recognition program that lets you run shell commands with a single stroke :) (or tap keys, so you could configure it to be a keyboard). 

by the way, anyone managed to get the touchscreen calibrated?

---

### Post by gali98 on 2008-10-25
You can just use wacomcpl...
What I did was use the extra nibs that came with my lappy to calibrate the touch.....
That worked good.
Kory

---

### Post by tC_Crazy on 2008-10-26
I got sound working... but I don't exactly know how. In my attempts to install the Realtek "HD Audio Codec" for linux, it wiped out my current driver and then failed. I then tried a few different things to get my driver reinstalled, and after two lines (it's a couple pages back) my sound started working perfectly.

---

### Post by Rangua on 2008-10-26
mm, wacomcpl can calibrate only the stylus... i meant the "touch" device, i've tried messing up the parameters given in xorg, but i think it makes no difference..
also, tc_crazy, can you restart Xorg using fglrx? my computer freezes if i try to do it.. haven't tried using the radeon driver.. 
one more thing, the side buttons.. how do i install them? i can use the play/pause/next/stop buttons, but i can't get the other four working..

---

### Post by gali98 on 2008-10-26
No... You can calibrate touch too :)
what version of linux wacom do you have? 
Also if you upload your xorg.conf I can look at it.
While you're at it also give me the output of 
ls -lR /dev/input
@tc_crazy

I tried the audio stuff too :)
to fix it, all you should have to do is reinstall the kernel image. the package may be slightly different, but something like:
sudo apt-get install --reinstall linux-image-2.6.27-7-generic
that has all the audio modules in it.
All that package from realtek did was try to compile the source modules then stick it into your module configuration, but it doesn't compile completely for one, then it sticks the modules in the wrong place.
The best way to get our audio working is either to:
1. fix the driver ourselves (I've tried it... pretty hard :) May this Christmas I can get it working)
or
2. Spam the Alsa devs on the mailing lists with requests :)
I submitted one email and it pretty much just got ignored...

Any way, good luck!
Kory

---

### Post by tannalv on 2008-10-27
I don't know if anyone else has noticed, but there's a new BIOS out. It takes care of that #¤"%@!!! thermal-problem.

[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-65538-1&lc=en&dlc=en&cc=ru&product=3744020&os=2100&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-65538-1&lc=en&dlc=en&cc=ru&product=3744020&os=2100&lang=en)

However, the program that comes with this (InsydeFlash.exe) only works under windows.
If someone here speaks chinese they might help us getting this to work under DOS? 
[http://bbs.gaodi.net/forumdisplay.php?fid=36&filter=type&typeid=75](http://bbs.gaodi.net/forumdisplay.php?fid=36&filter=type&typeid=75)

Seems like "Insyde Flash BIOS dos&#19979;&#21047;&#26032;&#24037;&#20855;FLASHIT.EXE 1.2n&#29256;" is meant for DOS. Which'd mean FreeDOS or something alike would be enough to get the BIOS replaced.
Also, if you do run the InsydeFlash.exe under windows there is a platform.ini-file that has a bunch of interesting options.
If it is too much then it is simply a matter of setting [Option] to Flag=1 and you'll get an "Option"-button on the InsydeFlash-window. Might be useful for replacing the boot up logo.

Play around with it.
**_But don't flash unless you are sure you know what you are doing._**

---

### Post by harak on 2008-10-27
"Have any of you figured out how to solve the updating problem on Intrepid Ibex? I tried a clean install of Ibex Alpha 5 and it installed smoothly. However, when I tried to update, it went into thermal shutdown midway through. I had to do a dpkg from the recovery boot option to try to fix it. Now it starts, but there's a problem in X... after logging in, I get a white screen and nothing else. tty still works. For the time being, I just reverted back to an image of my Hardy partition I made before the upgrade."



I am on RC... tx2500
I also experienced the same problem. The thermal reboot is probably because of the new blacklist file that the upgrade introduces. When I tried starting again the new kernel was not on the list. So I logged in to recovery mode with "acpi=off" in my booting options. Did a recovery and fixed broken packages. Turned out I had to run the command "dpkg --configure -a". But it gave errors. Resumed in normal mode got just a black screen. so pressed "CTRL-ALT-F1" and logged into the console mode. Ran "dpkg --configure -a". got errors again. Turns out that the wireless is not working. So used a wired connection and ran the command. To get the wireless working simply reinstalled the drive. Now My system works pretty well.

But there is only one problem Sound still doesn't work...!!??

---

### Post by harak on 2008-10-27
The sound works now...
just added the following to /etc/modprobe.d/alsa-base

options snd-hda-intel index=0 model=toshiba position_fix=1

---

### Post by Rangua on 2008-10-27
oh, nevermind gali.. i've updated the driver to 0.8.1-6 and touch calibration is enabled.. everything works well, mm, not everything.. i still can't restart X (the screen turns black and i have to pseudo-hard shut the computer, i say pseudo because when i press the power button it does something, i can't look what it is, but i guess that's the system shutting down.. and if i hard shut it after it's done doing that it makes a different, more calm sound than if i hard shut it right when the screen turns black)... i also can't play videos while running compiz.. just minor things.. do you still want the xorg.conf and the ls output or was it just for helping me calibrate touch? 

btw, i've tried installing kde, but it ran sooo slooow!! anyone tried kde4?

---

### Post by Rangua on 2008-10-27
oh.. and tc_crazy.. i think i'm getting addicted to compiz too, haven't used the radeon driver for days now... it's just so good-looking i would take her out for a date :P

---

### Post by harak on 2008-10-28
Has anyone worked with Suspend or Reboot on Intrepid? On Reboot my system hangs before it shuts down. When I suspend the system it hangs after it has resumed.. i.e. does not respond to keyboard, I am using intrepid!

---

### Post by tC_Crazy on 2008-10-28
Reboot works fine, but when coming off of suspend the mouse and keyboard don't work. And Hibernate fails. I just realized I have 217 updates and I'm kinda scared something's (or everything) is gonna break. eek

---

### Post by harak on 2008-10-28
tC_crazy... For me hibernate works ok... suspend and reboot do not!!!!

The following solution now works for me!

[https://bugs.launchpad.net/ubuntu/+bug/274995](https://bugs.launchpad.net/ubuntu/+bug/274995)

---

### Post by tannalv on 2008-10-28
There is a new bios out. (since October 15th)

After upgrading to this new BIOS my computer reboots fine, shuts down fine, hibarnates fine, and saves to RAM fine.
I also no longer have any trouble with Thermal complaining about overheating any more. Even on old kernels.

---

### Post by harak on 2008-10-28
Tannalv.... whats the version of your kernel? I installed the new version of  BIOS but suspend does not work. Hibernate and reboot issues were not because of BIOS. Did you do anything else?

---

### Post by tannalv on 2008-10-28
> **harak said:**
> Tannalv.... whats the version of your kernel? I installed the new version of  BIOS but suspend does not work. Hibernate and reboot issues were not because of BIOS. Did you do anything else?

root@tx2500:~# uname -a
Linux tx2500 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux

Hmmm... Also, in xorg.conf I have Driver "fglrx".
Rebooting, shuting off, suspend to ram and suspend to disk works fine for me.
And also, I'm living on the edge, i.e. used a kubuntu-daily install. And I do an apt-get update/-grade every day. Or there about...

---

### Post by harak on 2008-10-28
Ok... I will try using KDM to see if its because of gdm

---

### Post by gali98 on 2008-10-28
I'm on the tx2000... Everything works great (as in the Hibernate and suspend stuff)
I am about to attempt to install the new BIOS, but I already deleted Vista :)
I remember seeing a thread though about updating the BIOS from ubuntu. I'm going to check it out and see if it will work.
Just for everyone to know, the bios update for the tx2500 will work for the tx2000.
I emailed HP and they told me. I will post back after a while with my progress :)
Kory

---

### Post by tannalv on 2008-10-28
> **gali98 said:**
> Just for everyone to know, the bios update for the tx2500 will work for the tx2000.
I emailed HP and they told me. I will post back after a while with my progress :)
Kory

Whooaaa! Whaaaa...?!?! Wait a sec? Really! You HAVE to let me know how that turns out! Beacuse then I'd like to know if the other way around is an option as well, if it is possible to use a Phoenix BIOS on the tx2500 instead of the cruddy Insyde-thing. Yeah, I'd like to go Atheros again!
Insyde BIOS is unhackable for the wireless whitelist hack.

---

### Post by gali98 on 2008-10-29
Ok...... Bad news.... Only Vista guys. I don't think even Xp works.... It's that stupid Insyde thing. So I am going to install Vista tonight, and upgrade my bios, then I'm going to install Intrepid tomorrow.... Stupid Windows..... I'll come back and say if it is worth it or not.... I doubt you could use a phoenix bios....
Kory

---

### Post by tannalv on 2008-10-29
> **gali98 said:**
> I am going to install Vista tonight, and upgrade my bios.
...
I doubt you could use a phoenix bios....
Kory

It is what you use originally on the tx2000... And if you can use both that and the Insyde one I'd suppose I should be able to shift to your bios as well? Just a wild hope...

Good luck btw! :)

---

### Post by gali98 on 2008-10-29
Wait what do you mean? The one that came on the laptop? I for one am not going to go play around with a bios. I want my lappy intact for the next ten years I am probably going to own it :)
Kory

---

### Post by tannalv on 2008-10-29
> **gali98 said:**
> Wait what do you mean? The one that came on the laptop? I for one am not going to go play around with a bios. I want my lappy intact for the next ten years I am probably going to own it :)
Kory

Uhm... Now I am confused... :confused:

> **gali98 said:**
> I'm on the tx2000... Everything works great (as in the Hibernate and suspend stuff)
I am about to attempt to install the new BIOS, but I already deleted Vista :)
I remember seeing a thread though about updating the BIOS from ubuntu. I'm going to check it out and see if it will work.
Just for everyone to know, the bios update for the tx2500 will work for the tx2000.
I emailed HP and they told me. I will post back after a while with my progress :)
Kory

Anyways, if you do, and if it works, let us know. I want to try it the other way around, if that works. (putting the tx2000 bios on the tx2500)

Thanks :D

---

### Post by fbdelivers on 2008-10-29
I have been using Intrepid for a while.  I've been happy with the configuration and wanted to give a quick update after updating my bios.

I have the tx2500 series.

Since updating the BIOS the system has been running great.  Better Fan and CPU usage since running the upgrade.  I'm still dual booting so I just used vista for the update.

The only thing that I do not have running now on the system is WACOM.  I have tried the latest released version and some of the scripts on this thread.  At one point I actually had things running but after a few updates have yet to recreate that success.  Attached is my xorg.conf file if anyone would like to take a look.  let me know if there is some other information you may need.

**Update:**  WACOM is now working with the attached file.  I'm not 100% sure what I did.  I installed the wacom tools using the package manager and tracking began to work.  I couldn't click on things but tracking the stylus was reponsive.  I think downloaded the released package from the linuxwacom site and now things are working.

One more question - So it's possible to get rotation to work, but now that I have WACOM working, is there a way to get the system to automatically re-calibrate when the resolution changes?

---

### Post by isachan on 2008-10-31
After I updated my 8.04 hardy to the latest huge update (approx. 167MB download), I noticed there was no entry for the 2.6.24-21 on the grub menu.

So I manually added one and rebooted. Now I can't connect to any network, even the wired connection ! Argh. Canonical always breaks very crucial stuff right at the time of major release ! I can't believe it !  Makes me wanna switch to another distro.

I verified this even after my BIOS update to F.08. I tried everything from the command line but no avail.

I can go back to 2.6.24-19 kernel easily, but does anyone knows how to fix this ?

Isao

---

### Post by isachan on 2008-10-31
Oops, I solved my own problem.

All I had to do was to add network interface entries to /etc/network/interfaces file. I guess Network Manager has erased all others except lo entry.

So at least my wired connection is working and wireless doesn't even show up. My machine is not slow and doesn't pause anymore.

Isao

---

### Post by tC_Crazy on 2008-10-31
isachan,
Any specific reasons for not using the 2.6.27 kernel?

---

### Post by gali98 on 2008-10-31
Yeah so after the complete run around with HP, I basically found out that the tx2500 bios won't work on the tx2000. When you try and run it, it tells you the laptop is wrong. So basically I am about to zap Vista again, and be Ubuntu'n again. I think I'm gonna write another wacom tutorial. One that's better. So anyone looking to update the t2000 bios again is out of luck :)
*off to zap vista - cd in the drive
Kory

---

### Post by isachan on 2008-10-31
Do you mean to say to switch to Intrepid ?
The main reason is that Hardy will be supported for another year and half.

I have seriously started using Kubuntu from 7.04, and that was very unstable. Then 7.10 broke many things when I upgraded. So this is the very first time I have been experiencing how much of stability I can get out of the LTS.

However, it seems like for TX2500, switching to 8.10 would be a far better choice than sticking with 8.04 at this point. A functioning CPU scaling feature alone be worth it, even though I finally made wireless driver to work just after my last post.

Although unlike 8.10 beta, with 8.10 LiveCD release, the fan just keeps running and never stops. What's with ?

Isao

---

### Post by manu7irl on 2008-11-01
> **harak said:**
> The sound works now...
just added the following to /etc/modprobe.d/alsa-base

options snd-hda-intel index=0 model=toshiba position_fix=1

this is really worked for me !!! i have 2.6.27-7-generic kernel version on tx2500 intrepid. thanks
I can't get my wacom to work the method with the new driver didn't work for me got many errors. but i did everythings right and also the line :
sudo cp ./src/2.6.27/wacom.ko /lib/modules/2.6.27-7-generic/kernel/drivers/input/tablet/wacom.ko gave me a cannot find ./src/2.6.27/wacom.ko
please help

---

### Post by gali98 on 2008-11-01
@manu7irl
Are you refering to my tutorial?

Here are the basic commands you need to run:
```

   sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev
  
  sudo apt-get install linux-headers-generic
  
  cd Desktop/
  
  wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.1-6.tar.bz2
  
  tar xjvf linuxwacom-0.8.1-6.tar.bz2
  
  cd linuxwacom-0.8.1-6/
 
  ./configure --enable-wacom --prefix=/usr
  
  make
  
  sudo make install
  
 sudo cp src/2.6.27/wacom.ko /lib/modules/2.6.27-7-generic/kernel/drivers/

```

I just ran those exact commands on Intrepid and it installed wonderfully.
but you might get more help for the wacom part by posting on the actual tutorial thread.
Kory

---

### Post by manu7irl on 2008-11-01
thanks for all but again the same :
cp: cannot stat `src/2.6.27/wacom.ko': No such file or directory
is there any solution?

---

### Post by gali98 on 2008-11-01
Okay here is what I want you to do....
Go to your desktop and delete anything with linux wacom in the name (i.e tar.gz files and folders )
now open a terminal (a brand new one.) and copy each of those commands to the terminal and run them. After you run everyone, copy all the output (everything in the terminal) and post it here for me to see.
Kory

---

### Post by manu7irl on 2008-11-01
i did everything you said and it worked! think it was b/c of my os language switched to english and the commands resulted with no errors but how i get it to actually work now??

[PHP]> ----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.27
  module versioning - no 
      kernel source - yes /lib/modules/2.6.27-7-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
         usbmouse.o - no
            evdev.o - no
         mousedev.o - no
            input.o - no
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - Uninit-called IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
manu@manu-laptop:~/Desktop/linuxwacom-0.8.1-6$ make
Making all in src
make[1]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src'
Making all in .
make[2]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src'
rm -f wacom.4x.gz
gzip -9c < ./wacom.4x > wacom.4x.gz
make[2]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src'
Making all in wacomxi
make[2]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF ".deps/wacomxi.Tpo" -c -o wacomxi.lo wacomxi.c; \
	then mv -f ".deps/wacomxi.Tpo" ".deps/wacomxi.Plo"; else rm -f ".deps/wacomxi.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c  -fPIC -DPIC -o .libs/wacomxi.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c -o wacomxi.o >/dev/null 2>&1
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4   -o libwacomxi.la -rpath /usr/lib/TkXInput -no-undefined wacomxi.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomxi.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomxi.so.0 -o .libs/libwacomxi.so.0.0.0
(cd .libs && rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0)
(cd .libs && rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so)
ar cru .libs/libwacomxi.a  wacomxi.o
ranlib .libs/libwacomxi.a
creating libwacomxi.la
(cd .libs && rm -f libwacomxi.la && ln -s ../libwacomxi.la libwacomxi.la)
make[2]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
Making all in util
make[2]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/util'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomcfg.lo -MD -MP -MF ".deps/wacomcfg.Tpo" -c -o wacomcfg.lo wacomcfg.c; \
	then mv -f ".deps/wacomcfg.Tpo" ".deps/wacomcfg.Plo"; else rm -f ".deps/wacomcfg.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c -o wacomcfg.o >/dev/null 2>&1
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4   -o libwacomcfg.la -rpath /usr/lib -no-undefined -version-info 0:1:0 wacomcfg.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomcfg.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomcfg.so.0 -o .libs/libwacomcfg.so.0.0.1
(cd .libs && rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0)
(cd .libs && rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so)
ar cru .libs/libwacomcfg.a  wacomcfg.o
ranlib .libs/libwacomcfg.a
creating libwacomcfg.la
(cd .libs && rm -f libwacomcfg.la && ln -s ../libwacomcfg.la libwacomcfg.la)
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacdump.o -MD -MP -MF ".deps/wacdump.Tpo" -c -o wacdump.o wacdump.c; \
	then mv -f ".deps/wacdump.Tpo" ".deps/wacdump.Po"; else rm -f ".deps/wacdump.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacscrn.o -MD -MP -MF ".deps/wacscrn.Tpo" -c -o wacscrn.o wacscrn.c; \
	then mv -f ".deps/wacscrn.Tpo" ".deps/wacscrn.Po"; else rm -f ".deps/wacscrn.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wactablet.o -MD -MP -MF ".deps/wactablet.Tpo" -c -o wactablet.o wactablet.c; \
	then mv -f ".deps/wactablet.Tpo" ".deps/wactablet.Po"; else rm -f ".deps/wactablet.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacserial.o -MD -MP -MF ".deps/wacserial.Tpo" -c -o wacserial.o wacserial.c; \
	then mv -f ".deps/wacserial.Tpo" ".deps/wacserial.Po"; else rm -f ".deps/wacserial.Tpo"; exit 1; fi
wacserial.c: In function ‘WacomFlush’:
wacserial.c:1345: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacusb.o -MD -MP -MF ".deps/wacusb.Tpo" -c -o wacusb.o wacusb.c; \
	then mv -f ".deps/wacusb.Tpo" ".deps/wacusb.Po"; else rm -f ".deps/wacusb.Tpo"; exit 1; fi
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4   -o wacdump  wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -o wacdump wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o  -lncurses
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT xidump.o -MD -MP -MF ".deps/xidump.Tpo" -c -o xidump.o xidump.c; \
	then mv -f ".deps/xidump.Tpo" ".deps/xidump.Po"; else rm -f ".deps/xidump.Tpo"; exit 1; fi
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4   -o xidump -L/usr/lib -lX11 -lXi -lm xidump.o wacscrn.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -o xidump xidump.o wacscrn.o  -L/usr/lib -lX11 -lXi -lm -lncurses
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT xsetwacom.o -MD -MP -MF ".deps/xsetwacom.Tpo" -c -o xsetwacom.o xsetwacom.c; \
	then mv -f ".deps/xsetwacom.Tpo" ".deps/xsetwacom.Po"; else rm -f ".deps/xsetwacom.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wcmAction.o -MD -MP -MF ".deps/wcmAction.Tpo" -c -o wcmAction.o wcmAction.c; \
	then mv -f ".deps/wcmAction.Tpo" ".deps/wcmAction.Po"; else rm -f ".deps/wcmAction.Tpo"; exit 1; fi
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4   -o xsetwacom  xsetwacom.o wcmAction.o libwacomcfg.la 
gcc -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -o .libs/xsetwacom xsetwacom.o wcmAction.o  ./.libs/libwacomcfg.so -L/usr/lib -lX11 -lXi -Wl,--rpath -Wl,/usr/lib
creating xsetwacom
make[2]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/util'
Making all in xdrv
make[2]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/xdrv'
gcc -MM -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -I../include -I/usr/include/xorg  ./xf86Wacom.c ./wcmSerial.c ./wcmUSB.c ./wcmISDV4.c ./wcmXCommand.c ./wcmCommon.c ./wcmCompat.c ./wcmConfig.c ./wcmFilter.c > .depend
make[2]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/xdrv'
make[2]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/xdrv'
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o xf86Wacom.o -c ./xf86Wacom.c
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmSerial.o -c ./wcmSerial.c
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmUSB.o -c ./wcmUSB.c
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmISDV4.o -c ./wcmISDV4.c
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmXCommand.o -c ./wcmXCommand.c
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmCommon.o -c ./wcmCommon.c
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmCompat.o -c ./wcmCompat.c
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmConfig.o -c ./wcmConfig.c
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmFilter.o -c ./wcmFilter.c
gcc -shared -nostdlib -o wacom_drv.so xf86Wacom.o wcmSerial.o wcmUSB.o wcmISDV4.o wcmXCommand.o wcmCommon.o wcmCompat.o wcmConfig.o wcmFilter.o -Bstatic -lgcc
make[2]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/xdrv'
Making all in 2.6.27
make[2]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/2.6.27'
cp -f ../2.6.19/wacom_wac.c .
cp -f ../2.6.22/wacom_wac.h .
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.27-7-generic/build M=/home/manu/Desktop/linuxwacom-0.8.1-6/src/2.6.27
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/manu/Desktop/linuxwacom-0.8.1-6/src/2.6.27/built-in.o
  CC [M]  /home/manu/Desktop/linuxwacom-0.8.1-6/src/2.6.27/wacom_wac.o
  CC [M]  /home/manu/Desktop/linuxwacom-0.8.1-6/src/2.6.27/wacom_sys.o
  LD [M]  /home/manu/Desktop/linuxwacom-0.8.1-6/src/2.6.27/wacom.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/manu/Desktop/linuxwacom-0.8.1-6/src/2.6.27/wacom.mod.o
  LD [M]  /home/manu/Desktop/linuxwacom-0.8.1-6/src/2.6.27/wacom.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[2]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/2.6.27'
make[1]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src'
make[1]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6'
manu@manu-laptop:~/Desktop/linuxwacom-0.8.1-6$ sudo make install
Making install in src
make[1]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src'
Making install in .
make[2]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src'
make[3]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/man/man4" || mkdir -p -- "/usr/man/man4"
 /usr/bin/install -c -m 644 'wacom.4x.gz' '/usr/man/man4/wacom.4x.gz'
make[3]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src'
make[2]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src'
Making install in wacomxi
make[2]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
make[3]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
 /usr/bin/install -c 'wacomcpl' '/usr/bin/wacomcpl'
 /usr/bin/install -c 'wacomcpl-exec' '/usr/bin/wacomcpl-exec'
test -z "/usr/lib/TkXInput" || mkdir -p -- "/usr/lib/TkXInput"
 /usr/bin/install -c -m 644 'pkgIndex.tcl' '/usr/lib/TkXInput/pkgIndex.tcl'
test -z "/usr/lib/TkXInput" || mkdir -p -- "/usr/lib/TkXInput"
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  'libwacomxi.la' '/usr/lib/TkXInput/libwacomxi.la'
/usr/bin/install -c .libs/libwacomxi.so.0.0.0 /usr/lib/TkXInput/libwacomxi.so.0.0.0
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so.0 || { rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0; }; })
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so || { rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so; }; })
/usr/bin/install -c .libs/libwacomxi.lai /usr/lib/TkXInput/libwacomxi.la
/usr/bin/install -c .libs/libwacomxi.a /usr/lib/TkXInput/libwacomxi.a
chmod 644 /usr/lib/TkXInput/libwacomxi.a
ranlib /usr/lib/TkXInput/libwacomxi.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/TkXInput
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/TkXInput

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
make[2]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
Making install in util
make[2]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/util'
make[3]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/util'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  'libwacomcfg.la' '/usr/lib/libwacomcfg.la'
/usr/bin/install -c .libs/libwacomcfg.so.0.0.1 /usr/lib/libwacomcfg.so.0.0.1
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so.0 || { rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0; }; })
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so || { rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so; }; })
/usr/bin/install -c .libs/libwacomcfg.lai /usr/lib/libwacomcfg.la
/usr/bin/install -c .libs/libwacomcfg.a /usr/lib/libwacomcfg.a
chmod 644 /usr/lib/libwacomcfg.a
ranlib /usr/lib/libwacomcfg.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /bin/bash ../../libtool --mode=install /usr/bin/install -c 'wacdump' '/usr/bin/wacdump'
/usr/bin/install -c wacdump /usr/bin/wacdump
  /bin/bash ../../libtool --mode=install /usr/bin/install -c 'xidump' '/usr/bin/xidump'
/usr/bin/install -c xidump /usr/bin/xidump
  /bin/bash ../../libtool --mode=install /usr/bin/install -c 'xsetwacom' '/usr/bin/xsetwacom'
/usr/bin/install -c .libs/xsetwacom /usr/bin/xsetwacom
test -z "/usr/include/wacomcfg" || mkdir -p -- "/usr/include/wacomcfg"
 /usr/bin/install -c -m 644 'wacomcfg.h' '/usr/include/wacomcfg/wacomcfg.h'
make[3]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/util'
make[2]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/util'
Making install in xdrv
make[2]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/xdrv'
make[3]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/xdrv'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/xorg/modules/input" || mkdir -p -- "/usr/lib/xorg/modules/input"
 /usr/bin/install -c -m 644 'wacom_drv.so' '/usr/lib/xorg/modules/input/wacom_drv.so'
make[3]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/xdrv'
make[2]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/xdrv'
Making install in 2.6.27
make[2]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/2.6.27'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src/2.6.27'
make[1]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6/src'
make[1]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6'
make[2]: Entering directory `/home/manu/Desktop/linuxwacom-0.8.1-6'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6'
make[1]: Leaving directory `/home/manu/Desktop/linuxwacom-0.8.1-6'
manu@manu-laptop:~/Desktop/linuxwacom-0.8.1-6$  sudo cp src/2.6.27/wacom.ko /lib/modules/2.6.27-7-generic/kernel/drivers/
manu@manu-laptop:~/Desktop/linuxwacom-0.8.1-6$ 

[/PHP]

---

### Post by gali98 on 2008-11-02
You will need to configure your xorg.conf as per the tutorial. if you would like you can upload your xorg.conf after you are finished to make sure you did it right...
Basically after you get it right, you just need to restart and the stylus and touch should work.
Then you run the command
wacomcpl

and that opens a window where you can calibrate everything.
Kory

---

### Post by shm on 2008-11-02
thanks to all for this posts!

i have tx2520er, and after two days i have everything working in ubuntu 8.10 except buttons (dvd, reload, rotate, settings)

i found program getscancodes, from project keytouch
[http://keytouch.sourceforge.net/howto_keyboard/node4.html](http://keytouch.sourceforge.net/howto_keyboard/node4.html)

if i shut down gdm (/etc/init.d/gdm stop)
and run 
 sudo ./getscancodes /dev/input/event1
Input driver version is 1.0.0
Input device ID: bus 0x11 vendor 0x1 product 0x1 version 0xab41
Input device name: "AT Translated Set 2 keyboard"

and can get scancodes for DVD and Reload buttons (142 136)

but when i run xev, seems that xev don't receive this keycodes (if i press other keys than i can see key codes).

so, does any one know where could be the problem?


by the way
for my sound card i use following option  
options snd-hda-intel index=0 model=acer

in attached files my system and xorg configuration

sorry for English.

---

### Post by manu7irl on 2008-11-02
do i have to do this ? sorry but i m really stuck...
[PHP]```
manu@manu-laptop:~$ sudo rmmod wacom
[sudo] password for manu: 
ERROR: Module wacom does not exist in /proc/modules
manu@manu-laptop:~$ sudo modprobe wacom
```[/PHP]

---

### Post by chikko on 2008-11-03
hey guys,

i spent most of yesterday trying to enable the wacom driver - but with no success so far, and thought maybe you could help me out here..

i'm running Kubuntu Intrepid on my tx2520ej, using the fglrx video driver, sound is working, wifi, CPU scaling etc - all good.  wacom, on the other hand.. well..

i tried following Kory's manual more than a few times, but every time i get stuck just after running the command which afterwards, as Kory said, the screen should react to my touch/stylus.

i haven't yet touched the xorg file, but i'm attaching the compiling sequence (from "configure" and right up to "sudo modprobe wacom". commands are in **bold**).

output of 'uname -a', btw, is:
Linux kishkashta 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64 GNU/Linux

hopefully someone could tell me what's wrong here.. :(

thanks alot!!

```

chikko@kishkashta:~/linuxwacom-0.8.1-6$ **ls** 
aclocal.m4      config.guess  docs        Makefile.am     prebuilt
AUTHORS         config.sub    GPL         Makefile.in     README  
autom4te.cache  configure     install-sh  missing         src     
bootstrap       configure.in  LGPL        mkxincludes.in          
ChangeLog       depcomp       ltmain.sh   NEWS                    
chikko@kishkashta:~/linuxwacom-0.8.1-6$ **./configure --enable-wacom --prefix=/usr **                                                     
checking for a BSD-compatible install... /usr/bin/install -c       
checking whether build environment is sane... yes                  
checking for gawk... no                                            
checking for mawk... mawk                                          
checking whether make sets $(MAKE)... yes                          
checking whether to enable maintainer-specific portions of Makefiles... no                                                            
checking for gcc... gcc                                            
checking for C compiler default output file name... a.out          
checking whether the C compiler works... yes                       
checking whether we are cross compiling... no                      
checking for suffix of executables...                              
checking for suffix of object files... o                           
checking whether we are using the GNU C compiler... yes            
checking whether gcc accepts -g... yes                             
checking for gcc option to accept ANSI C... none needed            
checking for style of include used by make... GNU                  
checking dependency style of gcc... gcc3                           
checking for gawk... (cached) mawk                                 
checking build system type... x86_64-unknown-linux-gnu             
checking host system type... x86_64-unknown-linux-gnu              
checking for a sed that does not truncate output... /bin/sed       
checking for egrep... grep -E                                      
checking for ld used by gcc... /usr/bin/ld                         
checking if the linker (/usr/bin/ld) is GNU ld... yes              
checking for /usr/bin/ld option to reload object files... -r       
checking for BSD-compatible nm... /usr/bin/nm -B                   
checking whether ln -s works... yes                                
checking how to recognise dependent libraries... pass_all          
checking how to run the C preprocessor... gcc -E                   
checking for ANSI C header files... yes                            
checking for sys/types.h... yes                                    
checking for sys/stat.h... yes                                     
checking for stdlib.h... yes                                       
checking for string.h... yes                                       
checking for memory.h... yes                                       
checking for strings.h... yes                                      
checking for inttypes.h... yes                                     
checking for stdint.h... yes                                       
checking for unistd.h... yes                                       
checking dlfcn.h usability... yes                                  
checking dlfcn.h presence... yes                                   
checking for dlfcn.h... yes                                        
checking for g++... g++                                            
checking whether we are using the GNU C++ compiler... yes          
checking whether g++ accepts -g... yes                             
checking dependency style of g++... gcc3                           
checking how to run the C++ preprocessor... g++ -E                 
checking for g77... no                                             
checking for f77... no                                             
checking for xlf... no                                             
checking for frt... no                                             
checking for pgf77... no                                           
checking for fort77... no                                          
checking for fl32... no                                            
checking for af77... no                                            
checking for f90... no                                             
checking for xlf90... no                                           
checking for pgf90... no                                           
checking for epcf90... no                                          
checking for f95... no                                             
checking for fort... no                                            
checking for xlf95... no                                           
checking for ifc... no                                             
checking for efc... no                                             
checking for pgf95... no                                           
checking for lf95... no                                            
checking for gfortran... no                                        
checking whether we are using the GNU Fortran 77 compiler... no    
checking whether  accepts -g... no                                 
checking the maximum length of command line arguments... 32768     
checking command to parse /usr/bin/nm -B output from gcc object... ok                                                                 
checking for objdir... .libs                                       
checking for ar... ar                                              
checking for ranlib... ranlib                                      
checking for strip... strip                                        
checking if gcc supports -fno-rtti -fno-exceptions... no           
checking for gcc option to produce PIC... -fPIC                    
checking if gcc PIC flag -fPIC works... yes                        
checking if gcc static flag -static works... yes                   
checking if gcc supports -c -o file.o... yes                       
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes                                          
checking whether -lc should be explicitly linked in... no          
checking dynamic linker characteristics... GNU/Linux ld.so         
checking how to hardcode library paths into programs... immediate  
checking whether stripping libraries is possible... yes            
checking if libtool supports shared libraries... yes               
checking whether to build shared libraries... yes                  
checking whether to build static libraries... yes                  
configure: creating libtool                                        
appending configuration tag "CXX" to libtool                       
checking for ld used by g++... /usr/bin/ld -m elf_x86_64           
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes                                          
checking for g++ option to produce PIC... -fPIC                    
checking if g++ PIC flag -fPIC works... yes                        
checking if g++ static flag -static works... yes                   
checking if g++ supports -c -o file.o... yes                       
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes                                          
checking dynamic linker characteristics... GNU/Linux ld.so         
checking how to hardcode library paths into programs... immediate  
appending configuration tag "F77" to libtool                       
checking for pkg-config... /usr/bin/pkg-config                     
checking pkg-config is at least version 0.9.0... yes               
checking for arch type... x86_64-linux-gnu                         
checking for kernel type... Linux                                  
checking for linux-based kernel... yes                             
checking for kernel source/headers... /lib/modules/2.6.27-7-generic/build                                                             
checking kernel version... 2.6.27-7-generic                        
checking for kernel module support... yes                          
checking for Xlib... yes                                           
checking for XSERVER... yes                                        
checking for xserver libc-wrapper header-files... no               
checking if scaling tablet to screen size is needed... no          
checking if Uninit is called... yes                                
checking if Xorg SDK defines IsXExtensionPointer... yes            
checking if Xorg SDK defines dixScreenOrigins... yes               
checking XInput extension version... >= 2.0                        
checking for lib xf86config... checking for X... libraries , headers                                                                  
checking for gethostbyname... yes                                  
checking for connect... yes                                        
checking for remove... yes                                         
checking for shmat... yes                                          
checking for IceConnectionNumber in -lICE... yes                   
checking for tclsh... /usr/bin/tclsh                               
checking for tcl version... 8.4                                    
checking for tcl header files... found, /usr/include/tcl8.4        
checking for tk header files... found, /usr/include/tcl8.4         
checking ncurses.h usability... yes                                
checking ncurses.h presence... yes                                 
checking for ncurses.h... yes                                      
checking if libwacomcfg should/can be built... yes                 
checking if libwacomxi should/can be built... yes                  
checking if wacdump should/can be built... yes                     
checking if xidump should/can be built... yes                      
checking if xsetwacom should be built... yes                       
checking for Wacom X driver module path... /usr/lib/xorg/modules/input                                                                
checking for dynamic driver loading support... yes                 
checking if wacom_drv.{o,so} should be compiled... yes             
checking if gcc accepts -fno-merge-constants... yes                
checking if gcc accepts -fno-stack-protector... yes                

configure: creating ./config.status
config.status: creating Makefile   
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.4/Makefile 
config.status: creating src/2.4.22/Makefile
config.status: creating src/2.6.8/Makefile 
config.status: creating src/2.6.9/Makefile 
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/2.6.22/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.26/Makefile
config.status: creating src/2.6.27/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: creating src/include/kernel-config.h
config.status: creating src/include/util-config.h  
config.status: executing depfiles commands         

----------------------------------------
  BUILD ENVIRONMENT:                    
       architecture - x86_64-linux-gnu  
       linux kernel - yes 2.6.27        
  module versioning - no                
      kernel source - yes /lib/modules/2.6.27-7-generic/build
     XFree86 source - no                                     
           Xorg SDK - yes /usr/include/xorg                  
          XSERVER64 - yes                                    
           dlloader - yes                                    
               XLib - yes /usr/lib                           
         xf86config - no                                     
                TCL - yes /usr/include/tcl8.4                
                 TK - yes /usr/include/tcl8.4                
            ncurses - yes                                    

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes 
         libwacomxi - yes 
          xsetwacom - yes 
              hid.o - no  
         usbmouse.o - no  
            evdev.o - no  
         mousedev.o - no  
            input.o - no  
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no                              
  wacom*_drv quirks - Uninit-called IsXExtensionPointer key-events dixScreenOrigins                                                   
----------------------------------------                           
chikko@kishkashta:~/linuxwacom-0.8.1-6$ **make**                       
Making all in src                                                  
make[1]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src'  
Making all in .                                                    
make[2]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src'  
rm -f wacom.4x.gz                                                  
gzip -9c < ./wacom.4x > wacom.4x.gz                                
make[2]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src'   
Making all in wacomxi                                              
make[2]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src/wacomxi'                                                             
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF ".deps/wacomxi.Tpo" -c -o wacomxi.lo wacomxi.c; \   
        then mv -f ".deps/wacomxi.Tpo" ".deps/wacomxi.Plo"; else rm -f ".deps/wacomxi.Tpo"; exit 1; fi                                
mkdir .libs                                                        
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c  -fPIC -DPIC -o .libs/wacomxi.o                                           
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c -o wacomxi.o >/dev/null 2>&1                                              
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4   -o libwacomxi.la -rpath /usr/lib/TkXInput -no-undefined wacomxi.lo -L/usr/lib -lX11 -lXi               
gcc -shared  .libs/wacomxi.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomxi.so.0 -o .libs/libwacomxi.so.0.0.0                     
(cd .libs && rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0)                                                      
(cd .libs && rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so)                                                          
ar cru .libs/libwacomxi.a  wacomxi.o                               
ranlib .libs/libwacomxi.a                                          
creating libwacomxi.la                                             
(cd .libs && rm -f libwacomxi.la && ln -s ../libwacomxi.la libwacomxi.la)                                                             
make[2]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src/wacomxi'                                                              
Making all in util                                                 
make[2]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src/util'                                                                
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomcfg.lo -MD -MP -MF ".deps/wacomcfg.Tpo" -c -o wacomcfg.lo wacomcfg.c; \                                   
        then mv -f ".deps/wacomcfg.Tpo" ".deps/wacomcfg.Plo"; else rm -f ".deps/wacomcfg.Tpo"; exit 1; fi                             
mkdir .libs                                                        
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o         
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c -o wacomcfg.o >/dev/null 2>&1            
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4   -o libwacomcfg.la -rpath /usr/lib -no-undefined -version-info 0:1:0 wacomcfg.lo -L/usr/lib -lX11 -lXi                                      
gcc -shared  .libs/wacomcfg.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomcfg.so.0 -o .libs/libwacomcfg.so.0.0.1                  
(cd .libs && rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0)                                                   
(cd .libs && rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so)                                                       
ar cru .libs/libwacomcfg.a  wacomcfg.o                             
ranlib .libs/libwacomcfg.a                                         
creating libwacomcfg.la                                            
(cd .libs && rm -f libwacomcfg.la && ln -s ../libwacomcfg.la libwacomcfg.la)                                                          
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacdump.o -MD -MP -MF ".deps/wacdump.Tpo" -c -o wacdump.o wacdump.c; \                      
        then mv -f ".deps/wacdump.Tpo" ".deps/wacdump.Po"; else rm -f ".deps/wacdump.Tpo"; exit 1; fi                                 
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacscrn.o -MD -MP -MF ".deps/wacscrn.Tpo" -c -o wacscrn.o wacscrn.c; \                      
        then mv -f ".deps/wacscrn.Tpo" ".deps/wacscrn.Po"; else rm -f ".deps/wacscrn.Tpo"; exit 1; fi                                 
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wactablet.o -MD -MP -MF ".deps/wactablet.Tpo" -c -o wactablet.o wactablet.c; \              
        then mv -f ".deps/wactablet.Tpo" ".deps/wactablet.Po"; else rm -f ".deps/wactablet.Tpo"; exit 1; fi                           
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacserial.o -MD -MP -MF ".deps/wacserial.Tpo" -c -o wacserial.o wacserial.c; \              
        then mv -f ".deps/wacserial.Tpo" ".deps/wacserial.Po"; else rm -f ".deps/wacserial.Tpo"; exit 1; fi                           
wacserial.c: In function ‘WacomFlush’:                             
wacserial.c:1345: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result                                
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacusb.o -MD -MP -MF ".deps/wacusb.Tpo" -c -o wacusb.o wacusb.c; \                          
        then mv -f ".deps/wacusb.Tpo" ".deps/wacusb.Po"; else rm -f ".deps/wacusb.Tpo"; exit 1; fi                                    
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4   -o wacdump  wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o -lncurses                                                                 
gcc -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -o wacdump wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o  -lncurses                                              
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT xidump.o -MD -MP -MF ".deps/xidump.Tpo" -c -o xidump.o xidump.c; \                          
        then mv -f ".deps/xidump.Tpo" ".deps/xidump.Po"; else rm -f ".deps/xidump.Tpo"; exit 1; fi                                    
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4   -o xidump -L/usr/lib -lX11 -lXi -lm xidump.o wacscrn.o -lncurses        
gcc -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -o xidump xidump.o wacscrn.o  -L/usr/lib -lX11 -lXi -lm -lncurses                                                       
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT xsetwacom.o -MD -MP -MF ".deps/xsetwacom.Tpo" -c -o xsetwacom.o xsetwacom.c; \              
        then mv -f ".deps/xsetwacom.Tpo" ".deps/xsetwacom.Po"; else rm -f ".deps/xsetwacom.Tpo"; exit 1; fi                           
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wcmAction.o -MD -MP -MF ".deps/wcmAction.Tpo" -c -o wcmAction.o wcmAction.c; \              
        then mv -f ".deps/wcmAction.Tpo" ".deps/wcmAction.Po"; else rm -f ".deps/wcmAction.Tpo"; exit 1; fi                           
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -D__amd64__ -I/usr/include/tcl8.4   -o xsetwacom  xsetwacom.o wcmAction.o libwacomcfg.la                    
gcc -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -o .libs/xsetwacom xsetwacom.o wcmAction.o  ./.libs/libwacomcfg.so -L/usr/lib -lX11 -lXi -Wl,--rpath -Wl,/usr/lib       
creating xsetwacom                                                 
make[2]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src/util'                                                                 
Making all in xdrv                                                 
make[2]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src/xdrv'                                                                
gcc -MM -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -I../include -I/usr/include/xorg  ./xf86Wacom.c ./wcmSerial.c ./wcmUSB.c ./wcmISDV4.c ./wcmXCommand.c ./wcmCommon.c ./wcmCompat.c ./wcmConfig.c ./wcmFilter.c > .depend                                                   
make[2]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src/xdrv'                                                                 
make[2]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src/xdrv'                                                                
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \                                                                  
                -pedantic -Wall -Wpointer-arith -fno-merge-constants \                                                                
                -fno-stack-protector -I. -I../include -I/usr/include/xorg  \                                                          
                -D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \                                                          
                -o xf86Wacom.o -c ./xf86Wacom.c                    
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \                                                                  
                -pedantic -Wall -Wpointer-arith -fno-merge-constants \                                                                
                -fno-stack-protector -I. -I../include -I/usr/include/xorg  \                                                          
                -D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \                                                          
                -o wcmSerial.o -c ./wcmSerial.c                    
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \                                                                  
                -pedantic -Wall -Wpointer-arith -fno-merge-constants \                                                                
                -fno-stack-protector -I. -I../include -I/usr/include/xorg  \                                                          
                -D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \                                                          
                -o wcmUSB.o -c ./wcmUSB.c                          
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \                                                                  
                -pedantic -Wall -Wpointer-arith -fno-merge-constants \                                                                
                -fno-stack-protector -I. -I../include -I/usr/include/xorg  \                                                          
                -D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \                                                          
                -o wcmISDV4.o -c ./wcmISDV4.c                      
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \                                                                  
                -pedantic -Wall -Wpointer-arith -fno-merge-constants \                                                                
                -fno-stack-protector -I. -I../include -I/usr/include/xorg  \                                                          
                -D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \                                                          
                -o wcmXCommand.o -c ./wcmXCommand.c                
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \                                                                  
                -pedantic -Wall -Wpointer-arith -fno-merge-constants \                                                                
                -fno-stack-protector -I. -I../include -I/usr/include/xorg  \                                                          
                -D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \                                                          
                -o wcmCommon.o -c ./wcmCommon.c                    
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \                                                                  
                -pedantic -Wall -Wpointer-arith -fno-merge-constants \                                                                
                -fno-stack-protector -I. -I../include -I/usr/include/xorg  \                                                          
                -D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \                                                          
                -o wcmCompat.o -c ./wcmCompat.c                    
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \                                                                  
                -pedantic -Wall -Wpointer-arith -fno-merge-constants \                                                                
                -fno-stack-protector -I. -I../include -I/usr/include/xorg  \                                                          
                -D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \                                                          
                -o wcmConfig.o -c ./wcmConfig.c                    
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \                                                                  
                -pedantic -Wall -Wpointer-arith -fno-merge-constants \                                                                
                -fno-stack-protector -I. -I../include -I/usr/include/xorg  \                                                          
                -D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \                                                          
                -o wcmFilter.o -c ./wcmFilter.c                    
gcc -shared -nostdlib -o wacom_drv.so xf86Wacom.o wcmSerial.o wcmUSB.o wcmISDV4.o wcmXCommand.o wcmCommon.o wcmCompat.o wcmConfig.o wcmFilter.o -Bstatic -lgcc                                           
make[2]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src/xdrv'                                                                 
Making all in 2.6.27                                               
make[2]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src/2.6.27'                                                              
cp -f ../2.6.19/wacom_wac.c .                                      
cp -f ../2.6.22/wacom_wac.h .                                      
    Building linuxwacom drivers for 2.6 kernel.                    
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built                           
make -C /lib/modules/2.6.27-7-generic/build M=/home/chikko/linuxwacom-0.8.1-6/src/2.6.27                                              
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'                                                                 
  LD      /home/chikko/linuxwacom-0.8.1-6/src/2.6.27/built-in.o    
  CC [M]  /home/chikko/linuxwacom-0.8.1-6/src/2.6.27/wacom_wac.o   
  CC [M]  /home/chikko/linuxwacom-0.8.1-6/src/2.6.27/wacom_sys.o   
  LD [M]  /home/chikko/linuxwacom-0.8.1-6/src/2.6.27/wacom.o       
  Building modules, stage 2.                                       
  MODPOST 1 modules                                                
  CC      /home/chikko/linuxwacom-0.8.1-6/src/2.6.27/wacom.mod.o   
  LD [M]  /home/chikko/linuxwacom-0.8.1-6/src/2.6.27/wacom.ko      
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'                                                                  
make[2]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src/2.6.27'                                                               
make[1]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src'   
make[1]: Entering directory `/home/chikko/linuxwacom-0.8.1-6'      
make[1]: Nothing to be done for `all-am'.                          
make[1]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6'       
chikko@kishkashta:~/linuxwacom-0.8.1-6$ **sudo make install**
Making install in src                                    
make[1]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src'
Making install in .                                              
make[2]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src'
make[3]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src'
make[3]: Nothing to be done for `install-exec-am'.               
test -z "/usr/man/man4" || mkdir -p -- "/usr/man/man4"           
 /usr/bin/install -c -m 644 'wacom.4x.gz' '/usr/man/man4/wacom.4x.gz'                                                                 
make[3]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src'   
make[2]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src'   
Making install in wacomxi                                          
make[2]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src/wacomxi'                                                             
make[3]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src/wacomxi'                                                             
make[3]: Nothing to be done for `install-exec-am'.                 
test -z "/usr/bin" || mkdir -p -- "/usr/bin"                       
 /usr/bin/install -c 'wacomcpl' '/usr/bin/wacomcpl'                
 /usr/bin/install -c 'wacomcpl-exec' '/usr/bin/wacomcpl-exec'      
test -z "/usr/lib/TkXInput" || mkdir -p -- "/usr/lib/TkXInput"     
 /usr/bin/install -c -m 644 'pkgIndex.tcl' '/usr/lib/TkXInput/pkgIndex.tcl'                                                           
test -z "/usr/lib/TkXInput" || mkdir -p -- "/usr/lib/TkXInput"     
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  'libwacomxi.la' '/usr/lib/TkXInput/libwacomxi.la'                        
/usr/bin/install -c .libs/libwacomxi.so.0.0.0 /usr/lib/TkXInput/libwacomxi.so.0.0.0                                                   
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so.0 || { rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0; }; })                                                   
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so || { rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so; }; })                                                         
/usr/bin/install -c .libs/libwacomxi.lai /usr/lib/TkXInput/libwacomxi.la                                                              
/usr/bin/install -c .libs/libwacomxi.a /usr/lib/TkXInput/libwacomxi.a                                                                 
chmod 644 /usr/lib/TkXInput/libwacomxi.a                           
ranlib /usr/lib/TkXInput/libwacomxi.a                              
PATH="$PATH:/sbin" ldconfig -n /usr/lib/TkXInput                   
----------------------------------------------------------------------                                                                
Libraries have been installed in:                                  
   /usr/lib/TkXInput                                               

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:      
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
     during execution                                          
   - add LIBDIR to the `LD_RUN_PATH' environment variable      
     during linking                                            
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag              
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.   
----------------------------------------------------------------------                                                                
make[3]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src/wacomxi'                                                              
make[2]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src/wacomxi'                                                              
Making install in util                                             
make[2]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src/util'                                                                
make[3]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src/util'                                                                
test -z "/usr/lib" || mkdir -p -- "/usr/lib"                       
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  'libwacomcfg.la' '/usr/lib/libwacomcfg.la'                               
/usr/bin/install -c .libs/libwacomcfg.so.0.0.1 /usr/lib/libwacomcfg.so.0.0.1                                                          
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so.0 || { rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0; }; })                                                       
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so || { rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so; }; })                                                             
/usr/bin/install -c .libs/libwacomcfg.lai /usr/lib/libwacomcfg.la  
/usr/bin/install -c .libs/libwacomcfg.a /usr/lib/libwacomcfg.a     
chmod 644 /usr/lib/libwacomcfg.a                                   
ranlib /usr/lib/libwacomcfg.a                                      
PATH="$PATH:/sbin" ldconfig -n /usr/lib                            
----------------------------------------------------------------------                                                                
Libraries have been installed in:                                  
   /usr/lib                                                        

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:      
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
     during execution                                          
   - add LIBDIR to the `LD_RUN_PATH' environment variable      
     during linking                                            
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag              
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.   
----------------------------------------------------------------------                                                                
test -z "/usr/bin" || mkdir -p -- "/usr/bin"                       
  /bin/bash ../../libtool --mode=install /usr/bin/install -c 'wacdump' '/usr/bin/wacdump'                                             
/usr/bin/install -c wacdump /usr/bin/wacdump                       
  /bin/bash ../../libtool --mode=install /usr/bin/install -c 'xidump' '/usr/bin/xidump'                                               
/usr/bin/install -c xidump /usr/bin/xidump                         
  /bin/bash ../../libtool --mode=install /usr/bin/install -c 'xsetwacom' '/usr/bin/xsetwacom'                                         
/usr/bin/install -c .libs/xsetwacom /usr/bin/xsetwacom             
test -z "/usr/include/wacomcfg" || mkdir -p -- "/usr/include/wacomcfg"                                                                
 /usr/bin/install -c -m 644 'wacomcfg.h' '/usr/include/wacomcfg/wacomcfg.h'                                                           
make[3]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src/util'                                                                 
make[2]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src/util'                                                                 
Making install in xdrv                                             
make[2]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src/xdrv'                                                                
make[3]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src/xdrv'                                                                
make[3]: Nothing to be done for `install-exec-am'.                 
test -z "/usr/lib/xorg/modules/input" || mkdir -p -- "/usr/lib/xorg/modules/input"                                                    
 /usr/bin/install -c -m 644 'wacom_drv.so' '/usr/lib/xorg/modules/input/wacom_drv.so'                                                 
make[3]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src/xdrv'                                                                 
make[2]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src/xdrv'                                                                 
Making install in 2.6.27                                           
make[2]: Entering directory `/home/chikko/linuxwacom-0.8.1-6/src/2.6.27'                                                              
make[2]: Nothing to be done for `install'.                         
make[2]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src/2.6.27'                                                               
make[1]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6/src'   
make[1]: Entering directory `/home/chikko/linuxwacom-0.8.1-6'      
make[2]: Entering directory `/home/chikko/linuxwacom-0.8.1-6'      
make[2]: Nothing to be done for `install-exec-am'.                 
make[2]: Nothing to be done for `install-data-am'.                 
make[2]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6'       
make[1]: Leaving directory `/home/chikko/linuxwacom-0.8.1-6'       
chikko@kishkashta:~/linuxwacom-0.8.1-6$ sudo **cp ./src/2.6.27/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko**    
chikko@kishkashta:~/linuxwacom-0.8.1-6$                            
chikko@kishkashta:~/linuxwacom-0.8.1-6$ **sudo rmmod wacom**           
chikko@kishkashta:~/linuxwacom-0.8.1-6$ **sudo depmod -e             **
chikko@kishkashta:~/linuxwacom-0.8.1-6$ **sudo modprobe wacom**

```

---

### Post by shm on 2008-11-03
i found decision!

i add two lines in to 
/etc/rc.local
```
#8e == 142 DVD
setkeycodes 8e 193
#88 == 136 RELOAD
setkeycodes 88 194

```

after reboot i have keycodes in xev 
201  for DVD 
and 
202 for RELOAD

i add them in to modmap

~/.Xmodmap 
```
keycode 201 = XF86Launch2
keycode 202 = XF86Launch3

```

i also write script to rotate screen (in attach)

my resume for hp tx2520er:

1)wifi BCM4312 802.11b/g working good with opensource driver

2)touch screen working well with latest linuxwacom-0.8.1-6

3)fingerprint working with fprint (packages libfprint0 libpam-fprint fprint-demo)
but to use it with gnome-screensaver (or other screensavers)
user need permission to usb device AES1600
i create special group usbusers then add myself in to it and correct udev rules:
```
sudo addgroup --system usbusers
sudo usermod -a -G usbusers $USER
```

find lines
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",MODE="0664"
SUBSYSTEM=="usb_device",                MODE="0664"

and change to

nano /etc/udev/rules.d/40-basic-permissions.rules

```
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",GROUP="usbusers", MODE="0664"
SUBSYSTEM=="usb_device",                GROUP="usbusers",MODE="0664"

```

after that reboot

4)web-camera working well out of the box.

5) sound card working with cpecial setting in
/etc/modprobe.d/alsa-base
```
options snd-hda-intel index=0 model=acer
```

6)cpu cooler working well out of the box (or may be with latest bios form hp) but full silent only when laptop lid is closed (for example in vista it silent after one minute nothing do)

7)hibernate (and resume) working well (i use radeon video driver)
but after resume if switch to console i see garbage
network manager automaticaly changes network settings for current available wifi network after resume.

thanks for all, and good luck!

---

### Post by gali98 on 2008-11-03
@manu7irl and chiko

You might go to the tutorial again.
I have updated it just a few minutes ago to deal with some of the issues faced by Intrepid.

Basically you don't need to run any of those modprobe commands.
after you copy the module, you just need to restart.
I would just start over (I know that's not what you wanted to hear, but it really isn't that bad. Don't skip any commands as some are the ones that are added and needed. Just delete any linux wacom folders already on your desktop and troop on :))
After you do all that, take a shot at messing with your xorg.conf. If you can't figure it out, upload it here and I can help you.
Kory

---

### Post by gali98 on 2008-11-03
Oh... and shm... what version of fprint did you use (i.e. where did you get the packages, or did you just compile?)
Also, how well does the scanning work. I remember when I tried it, I could never get a positive scan, and it would always fail.
thanks,
Kory

---

### Post by OnionMan on 2008-11-04
Hi,
I'm new here and I'm also new to linux.
I have tried Ubuntu 8.04 on my TX2524ca but there was a lot of problem including no CPU scaling and unstable wireless.

So I have been waiting for 8.10 to fix my main problem; the CPU scaling and the power consumption. Now 8.10 is installed, battery life good, wireless is not bad (but wpa2 enterprise is not working at all). My sound, which was working on 8.04, is not working anymore, I've tried some tips here for the alsa-base file but still no sound... The Wacom tutorial seems to install correctly but nothing works!

I've downloaded some Linux book, I want to learn, started to read but, I'm lost! hahaha I would like to have my hardware working before I invest a lot of time on this. Can you guys try to help me on this? I can see that some of you now have a tx2500 series laptop completely working with Ubuntu 8.10.

Thx

The OnionMan:p

---

### Post by Draugr on 2008-11-04
I have the same problem, i have a tx2532, sound works well but the touchscreen not (sorry but i don't speak english just a little)
I tried some tips here but touchcreen doesn't works, I hope somebody can help us

---

### Post by shm on 2008-11-04
> **gali98 said:**
> Oh... and shm... what version of fprint did you use (i.e. where did you get the packages, or did you just compile?)
Also, how well does the scanning work. I remember when I tried it, I could never get a positive scan, and it would always fail.
thanks,
Kory

fprint available in intrepid repo.
scanning work very terrible, i use fprint_demo and enroll to all fingers the same finger, but even with this settings percent of positive scan about 5% :( 
if look at verify page then you will see that very often image are blur. 
i think that should be some sensitivity settings in libfprint, but i don't research it yet.
  
also in attach my new version of script to rotate screen, i add xft rgba settings (but it will be work only for gnome, or newly run programs )
when used hinted fonts and screen are inverted, with xft.rgba == bgr fonts looks better.

---

### Post by gali98 on 2008-11-04
@Draugr

Here is the link to my tutorial. As long as you just follow along and do the whole thing, you should be able to get it working.
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

@shm
that's what I thought... I was reading on the fprint wiki and mailing lists. Aparently the driver for our reader isn't that great (I don't think the reader itself is that great either...)
and in the latest sources (at least when I last checked) they actaully had our driver set not to compile....
Maybe someday it can be good though...

On that rotate script, I actually use a daemon that runs in the background that does the same thing. I just modified some source I found out on the net one time. If you want, I can upload the source....
Kory

---

### Post by harak on 2008-11-05
> **shm said:**
> thanks to all for this posts!

i have tx2520er, and after two days i have everything working in ubuntu 8.10 except buttons (dvd, reload, rotate, settings)

i found program getscancodes, from project keytouch
[http://keytouch.sourceforge.net/howto_keyboard/node4.html](http://keytouch.sourceforge.net/howto_keyboard/node4.html)

if i shut down gdm (/etc/init.d/gdm stop)
and run 
 sudo ./getscancodes /dev/input/event1
Input driver version is 1.0.0
Input device ID: bus 0x11 vendor 0x1 product 0x1 version 0xab41
Input device name: "AT Translated Set 2 keyboard"

and can get scancodes for DVD and Reload buttons (142 136)

but when i run xev, seems that xev don't receive this keycodes (if i press other keys than i can see key codes).

so, does any one know where could be the problem?
.

i could reproduce your results... But the buttons seem respond only in the console(ctr+alt+f1-6) and not when my desktop(gdm on ctr-alt-f7) is on. I have mapped  the keys to some other applications to check if they are working.. but could not launch them.

---

### Post by gali98 on 2008-11-05
harak, I replied with a fix on the other post :)
for all others who don't know what I'm talking about, this is a fix so that the media buttons will work. You only need to run two commands:
[http://ubuntuforums.org/showpost.php?p=6114189&postcount=101](http://ubuntuforums.org/showpost.php?p=6114189&postcount=101)
Kory

---

### Post by Draugr on 2008-11-07
Thanks gail98 I going to try it this weekend

---

### Post by OnionMan on 2008-11-07
Can someone help me with my sound?

8.04 was working but now ... no sound at all... Only those loud internal DOS like sounds...  :confused:

Thx

---

### Post by Favux on 2008-11-07
OnionMan have you tried going to System>Preferences>Sound Control and see if all you need to do is turn up your speaker volumes?  When I updated to Intrepid I also had no sound and that was the problem.  For some reason the update turned to volume down to zero.  If you don't see volume control go to System>Preferences>Main Menu to enable it.  Good luck.

---

### Post by toobaz on 2008-11-07
> **shm said:**
>   
also in attach my new version of script to rotate screen,



Thank you very much, I'm using it.

However, for those who download it: pay attention, there is a typo in the last "xsetwacom" command, a "2" attached at the end that must be removed.

Pietro

---

### Post by gali98 on 2008-11-07
Onionman, if you are still having trouble with sound, see my post I just made:
[http://ubuntuforums.org/showpost.php?p=6128598&postcount=4](http://ubuntuforums.org/showpost.php?p=6128598&postcount=4)
Kory

---

### Post by tC_Crazy on 2008-11-07
Anyone have success with WPA2 Enterprise? Network Manager never seems to find the certificate.

---

### Post by gali98 on 2008-11-07
This post may help:
[http://ubuntuforums.org/showpost.php?p=6125655&postcount=24](http://ubuntuforums.org/showpost.php?p=6125655&postcount=24)
and the thread has some good info in it as well. I have not tested it since I don't use wpa, but it seemed to work for him.
Kory

---

### Post by mck182 on 2008-11-08
Hi,
I have a few questions about tx2500. I'm running Fedora 10 (KDE4), but there's no such thread about tx2500/2000 on fedora forums, so I'm posting here. Hope you don't mind.

1) Do you know what package handles the remote control? Fedora's xev doesn't picking it up. I have lirc and some related packages installed. But still nothing. Though the keys on the screen (those for playback control only) works.

2) The cpu fan is way too loud when running on ac power. I read in some post, that in (K)ubuntu it's kinda quiet. What power manager does ubuntu use? Fedora uses powernow-k8. And it's too loud...

3) And how does the suspend works with ubuntu?

Then I just want to say, that the fprint works awesome on F10. Including pam_fprint. Scans are clear in frpint_demo and recognition rate is about 94%. Everything else is working great, including wacom (thanks to tutorial on this site), sound (thanks again), wireless (using wl), just the webcam doesn't work with either Ekiga or Cheese, but it works with some Qt cam demo, but only once. After closing that app, I can't use the cam anymore. Any ideas?

Also I'm about to write a firefox extension for logins using fingerprints with fprint as a backend. Anyone interested with help?

Thanks in advance,
Marty

---

### Post by OnionMan on 2008-11-08
> **gali98 said:**
> Onionman, if you are still having trouble with sound, see my post I just made:
[http://ubuntuforums.org/showpost.php?p=6128598&postcount=4](http://ubuntuforums.org/showpost.php?p=6128598&postcount=4)
Kory

Hi Kory,
thx for the help but it didn't work... I'm still having those internal sounds... All my sound faders are at max.. but in my sound preferences I can see HDA ATI SB, The option you made me add was about a HDA INTEL...

Could this be the problem?


Onionman

---

### Post by keabler on 2008-11-08
hey, so im pretty new to linux, but I love it already.  I just got a tx2500 and want to put ubuntu.  There  is tons of stuff for 8.04, and 8.10 is suppose to help with battery life.  I guess my question is what version should I put on my tablet.  Has any one gotten 8.10 to work as good as 8.04?

---

### Post by gali98 on 2008-11-08
@Onionman
no... the hda intel refers to the snd-hda-intel model, which is the sound module for all HD sound cards....
Have you restarted? I don't really know what else to tell you....

@keabler
I would go for 8.10... It has more support for graphics and for thermal stuff....
The only problem seen so far is wpa2 enterprise encryption.
Kory

---

### Post by wallmalker1 on 2008-11-08
@gali98 - I just wanted to say my thanks for all the work you've done on this.  I have the tx2510us tablet, and I have everything (that matters to me) working now.

The sound, webcam, and 2 out of the 4 multimedia buttons are working.  I haven't done much work with the fingerprint reader, but I think it works.

@Onionman - I have the HDA ATI SB sound card as well, and it works for me using - 
options snd-hda-intel index=0 model=acer

Other than that all I did for the sound was to open the volume control and turn everything up.  Good luck.

---

### Post by karrou on 2008-11-09
I posted a question about my tx2500 sound problem when upgrading to 8.10 and am waiting for help:

[http://ubuntuforums.org/showthread.php?p=6139618#post6139618](http://ubuntuforums.org/showthread.php?p=6139618#post6139618)

Thanks gali98  but your method could not solve my problem.

Thanks folks. I did added this line on my new 8.10 OS just like what I did on 8.04. The problem is in this new OS I only can hear big noise when I login.

In my Volume Control I saw three options:
HDA ATI SB (Alsa mixer)
Realtek ALC268 (OSS Mixer)
Capture:ALSA PCM on front:0 (ALCC268 Analog) via DMA .....

The wired thing is that I installed a WinXP OS in my virtualbox and it has sound!

I upload my alsa-base file below and hope some one would give me some advises.

---

### Post by gali98 on 2008-11-09
That is interesting... Onionman, did you upgrade to Intrepid, or do a clean install?
I can't see it working on some and not others. There has to be something we can track down...
And the Virtual Box thing is very weird....
Kory

---

### Post by gali98 on 2008-11-09
Just saw this post and it may be helpful to those people with sound problems...
Kory

---

### Post by OnionMan on 2008-11-09
> **gali98 said:**
> That is interesting... Onionman, did you upgrade to Intrepid, or do a clean install?
I can't see it working on some and not others. There has to be something we can track down...
And the Virtual Box thing is very weird....
Kory

It was an upgrade from the last 8.10 beta. I thought that it could be the problem so I tried to download a clean 8.10 final. With a live CD boot I saw that the hardware test failed, there was no sound and it was not a fader problem... I did not clean install it...

As I said, there is those internal sounds that reminds me of an audio driver problem. 

If you guys think it could be a good idea to reinstall 8.10 even if the hardware test fails, I will do it.

Thx again

---

### Post by shm on 2008-11-10
> **gali98 said:**
> harak, I replied with a fix on the other post :)
for all others who don't know what I'm talking about, this is a fix so that the media buttons will work. You only need to run two commands:
[http://ubuntuforums.org/showpost.php?p=6114189&postcount=101](http://ubuntuforums.org/showpost.php?p=6114189&postcount=101)
Kory

thanks! this work for me, but also only DVD and reload buttons (as in my method) but others key codes (102 and 202)  rotate and settings buttons don't work.

fprint work better with little fingers :) i use my left index finger besides thumb finger, and now positive scans about 80% 


> On that rotate script, I actually use a daemon that runs in the background that does the same thing. I just modified some source I found out on the net one time. If you want, I can upload the source....

yes, it will bee nice :)

---

### Post by gali98 on 2008-11-10
Okay OnionMan.. I don't know anything else to do... let us know how it goes..
Thanks for the fprint tip... Those two other buttons will not work until some kind of driver is written for them.
I am uploading the source... (rename it to rotate.c) basically you need to do:
sudo apt-get install libxrandr-dev
then just cd to where the source is and run
gcc -lX11 -lXrandr -o rotate rotate.c
and it will make the daemon program "rotate" just put it in your home folder (named something like ".rotate" then add it to sessions so it starts when you log in.
then just make your script like mine (im attaching it too..) and when you run the script, it does some background stuff for you...
Kory

---

### Post by bdjohnso10 on 2008-11-10
Has anyone taken a look at the suspend and hibernate problem yet?

I have the tx2525nr and have gotten the sound working and the tablet working but to save power and start-up time suspend is VERY useful.

Suspend works when going into the off state but when resuming I get video and the login screen but the keyboard and the mouse don't work.  Can't end X or ctrl alt del out of it because the keyboard and mouse are "dead".  

From the other forums that I have read it looks like suspend doesn't wake the keyboard and mouse correctly.   Some people have made scripts or changed the suspend files so it wakes the keyboard but I don't know much about that and get confused.

I use ibex and here is the bug for hardy
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257293](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257293)

This is a post in a thread that may be helpful
[http://ubuntuforums.org/showpost.php?p=5993819&postcount=177](http://ubuntuforums.org/showpost.php?p=5993819&postcount=177)
Looks like he found something but I have no idea what he is editing

---

### Post by manu7irl on 2008-11-14
Kory thanks for all i'd just what you said about the wacom driver into intrepid and it actually did it thanks again. i'm on ubuntu 2.6.27-7-generic kernel version.
I'm wondering if there's a solution to the hibernate and sleep mode??

---

### Post by bdjohnso10 on 2008-11-14
I have noticed one other thing, when the computer goes to sleep in vista I can wake it by just hitting any key but when it goes to sleep in Ubuntu the keyboard is non responsive so I think it may be shutting down the keyboard and track pad when its not supposed to.

---

### Post by gali98 on 2008-11-14
I am on the tx2000 (which both hibernate and suspend work on)
I have heard tale that the tx2500 was having problems, but I thought hibernate was working.
I think I read somewhere that someone wrote a script (either that or someone was going to try to :)) that would fix the errors..
I will try and find that, and see if I can find anymore info for you..
Kory

---

### Post by gali98 on 2008-11-14
Okay I have a few things for you to try....

First edit /boot/grub/menu.lst

and find the line that looks like:
# defoptions=quiet splash 
and make it 
# defoptions=quiet splash i8042.reset

then run 
sudo update-grub 
and restart and try suspending...

Next,
edit /etc/default/acpi-support
and uncomment the line

 DOUBLE_CONSOLE_SWITCH=true

Next:

and here is a post I found that may help (there are some duplicates, I know...)
```

Both my touchpad and keyboard on my laptop fail after resume. I'm working around it by:

1) Adding to defoptions in /boot/grub/menu.list:
> i8042.reset
(Some people recommend i8042.nomux, but doing this caused my keyboard and touchpad to occasionally freeze up largely at random during use, requiring the use of an external mouse/keyboard to suspend & resume before they worked again)

2) Creating /etc/acpi/suspend.d/71-mouseunload.sh:
> #!/bin/sh
> modprobe -r psmouse
> echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind

3) Creating /etc/acpi/resume.d/34-mouseload.sh
> #!/bin/sh
> echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
> modprobe psmouse

4) Setting DOUBLE_CONSOLE_SWITCH=true in /etc/default/acpi support (I haven't actually tested if this is still neccesary, but it used to make all the difference)
```

And
```
> $ sudo gedit /boot/grub/menu.lst
> Find this line:
> # kopt=root=UUID***************** ro
> Change to this (leave the # at the beginning!):
> # kopt=root=UUID***************** ro i8042.reset=1
> $ sudo update-grub
>
> Reboot. Magic (hopefully). Good luck. 

and also try:
the same thing, but with i8042.nomux=1
```

This was the main page I looked at. You can post there with your info if you want...:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/59867](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/59867)
hopefully one of those things will work...
Kory

---

### Post by manu7irl on 2008-11-15
Thanks again Kory I tried this stuff :
the two lines on the menu.lst without the double screen option (it says that it's optional.
And guess what there's a new problem when i do suspend and wake up the laptop, the keyboard, the mouse, and the touchscreen worked but when i loggin the X server goes wrong. it blinks and duplicates the image and i cannot do anything but ctrl +  alt + backspace then everythings normal again. for the record the nomux option didn't work anyway

---

### Post by tC_Crazy on 2008-11-15
manu,
try doing this before you go into suspend:
alt+f2, type "metacity --replace"
The screen might flicker for a sec, and window decorators will change slightly. Then go in to suspend. See if the video displays properly when you come back from suspend. If so, it is probably the 3D acceleration problem. If that seems to be it, maybe someone can write a short script to switch to metacity, then sedn ubuntu into suspend. Then when you come back, it will switch back to compiz. Maybe that's not possible/trivial, but if it works that's a temporary solution.

---

### Post by gali98 on 2008-11-15
Hmmmm... A_toff said it worked for him.. A_toff, could you tell us what exactly you did?
Kory

---

### Post by bdjohnso10 on 2008-11-16
I got my suspend working perfectly with just the > First edit /boot/grub/menu.lst

and find the line that looks like:
# defoptions=quiet splash
and make it
# defoptions=quiet splash i8042.reset

then run
sudo update-grub
and restart and try suspending...

And now its working beautifully.

Thank you so much gali98 you are such a big help.  I can't tell you how many hours I searched for a fix.

---

### Post by manu7irl on 2008-11-16
For the suspend mode did you run on metacity or on compiz??

---

### Post by bdjohnso10 on 2008-11-16
> **manu7irl said:**
> For the suspend mode did you run on metacity or on compiz?? I dont run any desktop compisition because its a laptop and I want to conserve battery power.

---

### Post by manu7irl on 2008-11-16
if we're talking about the battery power with the 6 cells how many time can you actually work on?

---

### Post by bdjohnso10 on 2008-11-16
I have the tx2525nr and I get about 2hrs battery life when i am using medium brightness and turning everything off I don't need.  Also make sure you set you laptop to turn off display as often as possible and go to sleep as soon as possible.  Saves a ton of battery.

One other tip you should turn off the wireless and any video programs like a music player visualation or dvd.

---

### Post by manu7irl on 2008-11-17
my laptop just F***ed up with the sleep mode i cannot boot on. Yesterday i installed a brand new ubuntu 8.10 !! lol.
now from the begenning...

---

### Post by bdjohnso10 on 2008-11-17
[http://ubuntuforums.org/showthread.php?t=67407](http://ubuntuforums.org/showthread.php?t=67407)

if its not too late you may be able to save all of your settings

---

### Post by manu7irl on 2008-11-17
already did it but it's ok it's just a few things and it was on a 8 gigs disk on key... don't want to ruined my warranty. Thanks anyway it's usefull.

---

### Post by a_toff on 2008-11-18
> **gali98]Hmmmm... A_toff said it worked for him.. A_toff, could you tell us what exactly you did?
Kory[/quote]


Oops, haven't been watching this thread for a few days... sorry for the delay. I just followed the first part of [your post]("http://ubuntuforums.org/showpost.php?p=6182143&postcount=370"), as follows:


[QUOTE=gali98 said:**
> 
First edit /boot/grub/menu.lst

and find the line that looks like:
# defoptions=quiet splash 
and make it 
# defoptions=quiet splash i8042.reset

then run 
sudo update-grub 
and restart and try suspending...


Looks like bdjohnso10 also [found your method to work]("http://ubuntuforums.org/showpost.php?p=6189450&postcount=374")...

---

### Post by manu7irl on 2008-11-19
Where can i found the radeon driver ?

---

### Post by isachan on 2008-11-19
There are 3 types of drivers for Radeon in Linux world, and I'm using fglrx driver installed with envyng. Simply you can install envyng with "sudo apt-get install envyng" and then choose "K menu" -> "System" -> "EnvyNG", then select ATI driver to install.

---

By the way, anyone tried the new BIOS F.09 ? I tried it for a short period of time (say, about 2 hours) and had a lot of USB external drive problems. Especially the Western Digital My Book 1TB was not recognized at all.

---

Also, another topic : a new HP tablet is coming soon.
Check this out : [http://www.tabletpcreview.com/default.asp?newsID=1307](http://www.tabletpcreview.com/default.asp?newsID=1307)

Seems like it has some nice small increment of improvements.

Isao

---

### Post by manu7irl on 2008-11-20
thanks a lot...
i'm feeling stupid i knew that before...
i' m wondering if there's any "how to" for the multimedia buttons to work??

---

### Post by kjamo36 on 2008-11-20
Anyone help me with this ?? i got my digitizer working everytime i enter this command in terminal": sudo modprobe wacom

but as soon as i restart it doesnt work anymore untill reenter it in terminal again... the eraser doesnt work neither

and touchscreen is not working =( 

I need help!! in running ubuntu 8.10

---

### Post by manu7irl on 2008-11-23
DO EXACTLY THAT FROM GALI STUFF...

> **gali98 said:**
> ***** UPDATED November 3, 2008 *****

NOTES:

If you are on Intrepid Do only that :


~~~~TUTORIAL FOR USB WACOM TABLET PC~~~~


I now put the Code boxes around the all terminal input so you don't have to worry about copying the > :)

```
cd ./Desktop

wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.1-6.tar.bz2
```

(all of the apt-get commands install the packages we need and updates the system to the latest packages)

```
sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade

sudo apt-get install wacom-tools xserver-xorg-input-wacom

sudo apt-get purge wacom-tools xserver-xorg-input-wacom
```

Okay now you need to add the kernel headers for your kernel. Most people will just do

```
sudo apt-get install linux-headers-generic
```

to check your kernel version do:

```
uname -r
```


If during any time you got a notice to restart or if you have a little restart icon in the top right system try (looks kinda like a blue recycle icon) then by goodness restart. If you are not sure, then go ahead and restart just to be safe. The reason is if you update to a newer kernel, then the module won't work on restart as the module is compiled for a specific kernel.

Okay now we get to the good stuff....

```
tar xjvf linuxwacom-0.8.1-6.tar.bz2

cd linuxwacom-0.8.1-6

./configure --enable-wacom --prefix=/usr

make

sudo make install

```

If this returns an error saying "wacom" is not loaded, Do not worry. Just means you've never installed wacom before. Continue...


Now do :
```
sudo cp ./src/2.6.27/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

[COLOR="Red"]You will now need to restart !!![/COLOR]. This is necessary on Intrepid!

Okay that installed it, but now we need to configure our xserver....

Okay I will try to make this as simple as possible. Unfortunately for some reason the stylus and touch events do not go by the same event number every time so we have to go another way...
first of all If you have made any changes to
/etc/X11/xorg.conf concerning wacom delete all those changes Unless you have followed this tutorial before and know what you are doing. (make sure to also remove wacom references in the server layout section!)

Also do:
```
gedit ~/.xinitrc
```

and delete any line with "xsetwacom" at the beginning Unless you know why it is there. This will make it easier to calibrate. Save that then restart.

If when you do the command the file is blank, do not worry. Just close out of gedit and continue on.

After you restart the stylus and touch should work. If it does not, restart again. It took me like three times before it kicked in. Don't ask me why...
It should move it, though probably very  uncalibrated. Make sure you cover the entire screen to see if it moves.
If it does not move then post the results of

```
./configure --enable-wacom --prefix=/usr

make

sudo make install

sudo rmmod wacom

sudo modprobe wacom
```

and also post the contents of xorg.conf (/etc/X11/xorg.conf)

If you have got this far good!

Open up a terminal

```
gksudo gedit /etc/X11/xorg.conf &
```

(leave the terminal open...)

In the text editor add the following lines under the Synaptic InputDevice Section (check the bottom of this post for my xorg.conf to see what I mean....)



```

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Type" "stylus"
Option "USB" "on"
Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse"
Option "Button2" "3" # make side-switch a right button
Option "TopX" "225"
Option "TopY" "225"
Option "BottomX" "26300"
Option "BottomY" "16375"
EndSection

Section "InputDevice"
Identifier "touch"
Driver "wacom"
Option "Type" "touch"
Option "USB" "on"
Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.1-event-"
Option "TopX" "200"
Option "TopY" "225"
Option "BottomX" "4000"
Option "BottomY" "3875"
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Type" "eraser"
Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse"
Option "USB" "on"
EndSection

```


Now Find the part that says 'Section "ServerLayout"'

In there add:

```

Inputdevice "stylus"	"SendCoreEvents"
Inputdevice "touch"	"SendCoreEvents"
Inputdevice "eraser"	"SendCoreEvents"

```

Now we need to fix the synaptic touch pad part. Since it has the word "touch" in it it is wrongly detected.
find the part that says:

```
	Identifier	"Synaptics Touchpad"
```
and change it to 

```
	Identifier	"Synaptics Pad"
```

then in the server layout section also change it****

if this is all confusing, you can download my xorg.conf to look at. It is at the bottom of this post. Do not use any other xorg.conf of mine uploaded on any other thread or post as it is probably old. 
note: if you are on another tablet (not a tx2000 series) it would not be wise to just paste my xorg into yours. It will probably not work. In fact it will probably break stuff :)
If you have the tx2000 if you just renamed it to xorg.conf and pasted it over yours, it would probably work, but I don't suggest doing it. 

Now Maximize the termial....
now in the termial type :

```
reset

dmesg | grep Wacom
```

there should be two lines similar to this:

```
[ 45.460644] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:0b.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input9
[ 45.478030] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:0b.1/usb2/2-2/2-2.3/2-2.3:1.1/input/input10
```


now do:

```
ls -l /dev/input/by-path
```

That should give you something similar to:


```
lrwxrwxrwx 1 root root 9 2008-07-27 12:07 pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse -> ../event9
lrwxrwxrwx 1 root root 9 2008-07-27 12:07 pci-0000:00:0b.1-usb-0:2.3:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2008-07-27 12:07 pci-0000:00:0b.1-usb-0:2.3:1.1- -> ../mouse2
lrwxrwxrwx 1 root root 10 2008-07-27 12:07 pci-0000:00:0b.1-usb-0:2.3:1.1-event- -> ../event10
lrwxrwxrwx 1 root root 9 2008-07-27 12:07 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root 10 2008-07-27 12:07 platform-i8042-serio-1-event-mouse -> ../event11
lrwxrwxrwx 1 root root 9 2008-07-27 12:07 platform-i8042-serio-1-mouse -> ../mouse3
lrwxrwxrwx 1 root root 9 2008-07-27 12:07 platform-pcspkr-event-spkr -> ../event2
```


Now find the file that matches the output of dmesg i.e:

input9 (from dmesg) matches with event9 (in the ls command) So The File

pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse

is one that we need.

next input10 (from dmesg) matches with event10 (in the ls command) So The File

pci-0000:00:0b.1-usb-0:2.3:1.1-event-

is the other we need.

Now just amend your xorg.conf with those two names that you just got. The one ending with "mouse" should be in the stylus and eraser sections
and the one ending in "event-" should be in the touch section.
In theory since we have the same basic laptops these files should be the same as mine but you need to check....
If you have anything other than a tx2000 it probably will be different.

And that should be it.
Press Ctrl + Alt + Backspace to restart the xserver.

Login and we will now calibrate.

Just open up a terminal and do:

```
wacomcpl
```

A gui!!!! everything you will probably ever need to do with wacom is here. Just read the buttons :)

To make the wacomcpl settings stay after you reboot you need to:

```
chmod +x ~/.xinitrc
```

Then go to System->Preferences->Session

click on add and for the command write "~/.xinitrc" (without the quotes) title it whatever.....

This will only work for the user though. So before you log in it is still uncalibrated.

So to make it system wide (if that is what you want) here is a short how-to:

First do:
```
rm ~.xinitrc
```
Now go into wacomcpl and make it how you want it. (calibrate included)

Now open up .xinitrc and xorg.conf:

```
gedit ~/.xinitrc & gksudo gedit /etc/X11/xorg.conf
```

now you just transfer the stuff over to the xorg.conf.

For example the line in my .xinitrc is:

xsetwacom set touch bottomy "3951"

if you open up a terminal you can use xsetwacom to figure out how to translate it to the xorg.conf.

so what you would do for the line above is:

```
xsetwacom -x get touch bottomy
```
the x stands for xconf.. get obviously gives you the value.

that command outputs

Option	"BottomY"	"3951"

which I would put in my xorg.conf under the touch section.

Here is another short example.

.xinitrc:

xsetwacom set stylus Button3 "Button 3"

command:

```
xsetwacom -x get stylus button3
```

part to put in xorg.conf

	Option	"Button3"	"BUTTON 3"


It will work that worked for me. on intrepid

---

### Post by manu7irl on 2008-11-25
i observed something strange when i plugged my headphone it actually didn't turn the speakers off... If there's any one that observes this too?

---

### Post by martinjochimsen on 2008-11-25
My laptop is doing the same thing. I have to unplug and then plug them in(?) (english is not my first language) to turn off the speakers. The same thing happend for me in 8.04. I haven't yet found out why!!!

Martin

---

### Post by tC_Crazy on 2008-11-25
Yup, same thing here. If I take them out and plug them back in that usually turns the speakers off. And another thing, it tends to freeze on startup on "starting powernowd." If I uninstall powernowd, will I lose cpu scaling?

---

### Post by OnionMan on 2008-11-25
Hi,
I'm back and my sound is now working, I did a fresh install from the CD and with the line [...] model=acer it worked!

New question: I am using the Broadcom-STA driver, my wpa connection at home is dropping every 10 minutes and wpa-enterprise is not working at all. I saw on the broadcom website [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php") and the latest driver version is 5.10.27.6. How can I know my current version and will it update with the update manager or do I have to put a new source.

Also:
> **tC_Crazy said:**
> Yup, same thing here. If I take them out and plug them back in that usually turns the speakers off. And another thing, it tends to freeze on startup on "starting powernowd." If I uninstall powernowd, will I lose cpu scaling?

I have this problem too...


Thx

---

### Post by tC_Crazy on 2008-11-29
Onionman, you could always go to that broadcom link and compile the driver from source. Probably a good idea to uninstall/disable the current STA driver first.

---

### Post by tah123 on 2008-11-29
Hi,

Thanks for all of the authors of the previous threads. I am running intrepid on a tx2500 and a lot of things works fine now (stylus, sounds, buttons on the screen, cam).

I still have problems with the touchscreen calibration and the eraser doesn't work. Moreover, when I use xournal within unmaximised window, the stylus works fine but when I modify the dimension of the window, I can't see the digital ink unless I "refresh" it (like reduce and then maximize). However, in GIMP every thing is ok.

> **manu7irl said:**
> i observed something strange when i plugged my headphone it actually didn't turn the speakers off... If there's any one that observes this too?

I have that problem too! 
And the build-in mic is still not working.
I anyone have a clue, please tell me!

thanks

---

### Post by manu7irl on 2008-11-29
get a new kernel version today so i have to re-install the wacom again!!
2.6.27-9-generic

---

### Post by a_toff on 2008-11-29
> **tah123 said:**
>  Moreover, when I use xournal within unmaximised window, the stylus works fine but when I modify the dimension of the window, I can't see the digital ink unless I "refresh" it (like reduce and then maximize). However, in GIMP every thing is ok.


Check these posts by th89, in the thread called [Tablet PC Issues]("http://ubuntuforums.org/showthread.php?t=870640"):

[quote=th89]For those wanting to use Xournal in Intrepid. Apparently there is a bug with libgnome canvas, that causes Xournal to be unusable.[/quote]

the fix:

[http://ubuntuforums.org/showpost.php?p=6107207&postcount=235](http://ubuntuforums.org/showpost.php?p=6107207&postcount=235)

and for 64bit systems:

[http://ubuntuforums.org/showpost.php?p=6210786&postcount=344](http://ubuntuforums.org/showpost.php?p=6210786&postcount=344)

---

### Post by martinjochimsen on 2008-11-29
To manu7irl:

I don't think that's the newest kernel. I've got the 2.6.27-10-generic kernel.

Martin

---

### Post by Favux on 2008-11-29
martin,

The 2.6.27-9-generic kernel is the latest kernel if you've only got Recommended updates checked in updates in Software Sources.  If you've got the 2.6.27-10-generic kernel then you must have the Pre-released updates (Intrepid proposed) checked in Updates in Software Sources.  You must like living on the edge.

By the way I posted the rotation tutorial you asked for this morning to Tips & Tutorials.  Now we wait while the moderators decide if it deserves posting.  If not I'll post it to Hardware & Laptops.

---

### Post by martinjochimsen on 2008-11-29
To fauvx. 
Of course you are right about the Pre-released updates. I didn't think about that. :-)
I'm looking forward to try the rotation howto! 
I am having problems to get the pressure working. Is it working for you? I couldn't get it to work with the 2.6.27-8 kernel either.
Martin

---

### Post by Favux on 2008-11-30
Hi martin,

Yes pressure sensitivity is working for me, even in Gimp.  I suggest you go to the Linux Wacom Project's _Using Xsetwacom_ HOWTO at:
   [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom]("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom")
if you haven't already.  Lots of good info, esp. on using terminal to check your pressure sensitivity, etc.  Remember the tool names are case sensitive so stylus is not the same as Stylus.  Check your xorg.conf if you don't remember.

Now to Gimp.  You want Drawing Tablets-Wilber's Wiki at:
   
   [http://wiki.gimp.org/gimp/DrawingTablets]("http://wiki.gimp.org/gimp/DrawingTablets") 

Good info but you want the hotlink Pressure Sensitivity under Enabling Gimp Pressure Sensitivity.  When it says File>Preferences it means Edit>Preferences.  Also the Device Status dialog is located in Windows>Dockable Dialogs>Device Status.  Just follow the steps and you should have pressure working in short order.  Hope this helps.

---

### Post by a_toff on 2008-11-30
Does anyone know where I will find info on getting the VGA output working? I'm  trying to get set up to use the tx2500 with a projector at the school where I'm working...

After plugging in a projector, I can see that the projector is recognized as an external monitor in menu/System/Preferences/Screen Resolution, but no output shows up on the projector (which I am confident has been set up properly).

---

### Post by tah123 on 2008-11-30
To a_toff

Thanks for the link, it really worked :)

---

### Post by Favux on 2008-12-01
Hey martin,

They posted the screen rotation tutorial here:
[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")
Let me know what you think.

---

### Post by martinjochimsen on 2008-12-01
Great. Thanks Favux.
I will give it a try tomorrow night.

Martin :-)

---

### Post by Draugr on 2008-12-01
The screen rotation script works on tx2500?

---

### Post by Favux on 2008-12-01
Hi Draugr,

It should since it basically depends on the xrandr command through X to work.  Your "Q" key code might be different on the TX2500 but you can get that through xev as I describe.  Give it a shot and let me know.

---

### Post by Ang on 2008-12-02
> **OnionMan said:**
> Hi,
I'm back and my sound is now working, I did a fresh install from the CD and with the line [...] model=acer it worked!

New question: I am using the Broadcom-STA driver, my wpa connection at home is dropping every 10 minutes and wpa-enterprise is not working at all. I saw on the broadcom website [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php") and the latest driver version is 5.10.27.6. How can I know my current version and will it update with the update manager or do I have to put a new source.

Also:


I have this problem too...


Thx

I have same problem! The wireless is working like sh"t!

Tried the "touch/stylus" guide and it didn't work for me. But as long the wireless isn't working properly won't Ubuntu be usable!

By the way, if someone not already have sad this, thanks gali98 for helping all of us all the time! :guitar:

---

### Post by tah123 on 2008-12-03
Hi,

> **manu7irl said:**
> get a new kernel version today so i have to re-install the wacom again!!
2.6.27-9-generic

I tried to use the new kernel but I couldn't get the stylus working again, even by reinstalling wacom as before. But I get the mic and the speaker/headphone working perfectly on 8.10 by (re-)installing the latest alsa driver : [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Favux :

The screen is rotating when I use the script but the mouse (stylus) isn't working fine. In fact, the pointer moves in the wrong directions :( (I have to use the normal direction ex:to move to  the top I have to move the cursor to the right  and so on)
How can I solve that problem?

Thanks.

---

### Post by Favux on 2008-12-03
Hi tahl123,

Which kernel were you using?  The Linux Wacom Project says at its download site as of 10-24-08 that 0.8.1-6 is good to kernel 2.6.27.  I'm using 2.6.27-9 with only occasional intermittent loss of eraser and touch.  I just reboot X.

As to rotation, that shouldn't happen!  If I understand you the stylus isn't rotating because the on screen cursor is moving 90 degrees to the stylus.  You are on a TX2500 right?  Which are you using, method 1 or method 2?

I'm going to guess method 1.  First thing to do is check to see if your name for stylus (or whatever your calling it, e.g. pencil) is the same in "xorg.conf" and in the ".rotation.sh" script you stuck in "/home/user name".  At least in a terminal X is case specific and "stylus"  is not the same as "Stylus".

Let me know.

---

### Post by tah123 on 2008-12-03
Hi Favux,

I am runing the kernel 2.6.27-7 on a tx2500. I up graded to 2.6.27-9 but I couldn't fix the stylus, so I had to stick with the -7 since it is working well over there. 

With the method 1, I could get back to the normal screen because it gets stuck after turning 90 degrees to the right. So I tryed the method 2 but as I already said, the mouse/stylus are not working well. I don't know where to check the name "stylus" in the method 2, but my xorg.conf file uses that name to identify the pen.

---

### Post by Favux on 2008-12-03
Hi tah123,

Yeah, I may go back to 2.6.27-7 too, if the intermittant loss of eraser and touch bugs me enough.

method 1:  Should work since it's just X commands.  But you are saying the stylus didn't turn with the screen with either method?  To figure out why it isn't working I need you to post your xorg.conf file in /etc/X11/.

method 2:  Sure in this one you wouldn't be matching the xorg.conf to a script because that function is performed by the wacomrotate daemon which is written in C.  Did you go to System>Preferences>Sessions and find "wacomrotate" and edit it to add the -t so that the command looks like "wacomrotate -f -t " ?  In other words is at least touch reorienting with the screen?

I really think I need you to post your xorg.conf file in /etc/X11/.

We'll get it working.

---

### Post by tah123 on 2008-12-03
Hi Favux,

I tried to add the option -t in the command wacomrotate but still the same issue. By the way, my touch is not calibrated (I can't calibrate it using wacomcpl, maybe I miss a stupid thins :( ), so I don't use it.

I have attached below my xorg file.

Thanks :)

---

### Post by Favux on 2008-12-04
Hi tah123,

Boy I am glad you posted your xorg.conf.  Sorry this took so long but I had to check into a lot of stuff.  What wacom tutorial did you follow?  Like I mentioned in an earlier post we're using linuxwacom 0.8.1-6, which one are you using?  With screen in laptop position what works?  Stylus, eraser, or touch?

Your xorg.conf looks old style, like from a tutorial for a wacom tablet not a tablet pc.  I don't know why you have a cursor section, I would comment it out.  I would comment out your Pad (formerly Touchpad) section also as HAL (Hardware Abstraction Layer) handles your synaptic touchpad now.  It can't handle the wacom stuff, which is why we still have to use xorg.conf.

I can't tell which driver you're using for your ATI video chipset.  If it is the "Radeon" driver rotation is supported.  If it is the proprietary "fglrx" driver (check System>Administration>Hardware Drivers) it didn't support rotation a month or two ago, but I believe an update was suppose to be coming out that did support rotation.  It may be out by now.

You said wacomcpl doesn't calibrate touch.  Does it calibrate stylus and eraser?

My rotation tutorial assumes you have wacom installed and that your xorg.conf is correct and functioning.  I'm not sure that applies to you.  Since we're beyond my expertise I should stop now and tell you to get help from a fellow TX2500 owner or an "expert" like gali98.  

But I don't want to abandon you.  So here goes.

I would do gali98's wacom tutorial for tablet pc's found here:
   [http://ubuntuforums.org/showthread.php?p=5469447#post5469447]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")
or follow the shortened version posted on this thread:
   [http://ubuntuforums.org/showthread.php?t=845911&page=39]("http://ubuntuforums.org/showthread.php?t=845911&page=39")
and follow the instructions exactly using the latest linuxwacom development driver 0.8.1-6 if you're using Intrepid (8.10) which I believe is the version of Ubuntu you're on, right?

When you're done my best guess is that your xorg.conf will look more like this:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Option		"RandRRotation"		"on"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Type" "stylus"
	Option	    "USB" "on"
	Option	    "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
	Option	    "Button2" "3" # make side-switch a right button
	Option	    "TopX" "225"
	Option	    "TopY" "225"
	Option	    "BottomX" "26300"
	Option	    "BottomY" "16375"
EndSection

Section "InputDevice"
	Identifier  "touch"
	Driver      "wacom"
	Option	    "Type" "touch"
	Option	    "USB" "on"
	Option	    "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-"
	Option	    "TopX" "200"
	Option	    "TopY" "225"
	Option	    "BottomX" "4000"
	Option	    "BottomY" "3875"
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Type" "eraser"
	Option	    "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
	Option	    "USB" "on"
EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "pad"
#  Option        "Device"        "/dev/input/wacom"    # USB ONLY
##  Option        "Device"        "/dev/ttyS0"         # SERIAL ONLY
#  Option        "Type"          "pad"
#  Option        "USB"           "on"                  # USB ONLY
#EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "eraser"  "SendCoreEvents"
#  InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
#  InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
  InputDevice   "touch"   "SendCoreEvents" # Only a few TabletPCs support this type
EndSection


```
Notice also that I added to your video section:
```
	Option		"RandRRotation"		"on"
```
which is needed for rotation.

Now if your linuxwacom driver is relatively recent and installed correctly all you may need is a xorg.conf from one of your fellow TX2500 owners.  I would not use my example xorg.conf above, as it is just my best guess.

Once wacom is installed and xorg.conf is correct then we can go on to rotation.  If you're using "flgrx" you may need to check with ATI if your version supports rotation.

Good Luck!

---

### Post by martinjochimsen on 2008-12-04
Hi Favux

I have been working with your rotation-howto, but I can't get it to work with either method 1 or 2. I'm using the first script and made it executable (I named it .rotation.sh) and made a launcher on my desktop (launcher is the same as a link, right?). When I double-click the launcher nothing happens....well something happens, but it's the same problem as tah123 from post 407 gets. When I move the stylus to the right the mouse/arrow/pointy-thingy moves up. When I move the stylus left the mouse goes down. The stylus and touch have rotated but not the desktop.
I think I might be missing something in my xorg. Could you please take a look at it?
After rebooting X stylus and touch is working normally again.
My laptop is a tx2590oe with a ATI&#8482; Mobility Radeon&#8482; HD 3200 card

Martin :-)

---

### Post by martinjochimsen on 2008-12-04
By the way favux. 
Would you prefer to keep this rotation-talk in the rotation-howto-thread?

Martin

---

### Post by Favux on 2008-12-04
Hi martin,

I think I can help you because you have the first xorg.conf that looks correct to me!  In other words you have followed gali98's tutorial or some version of it.  The proprietary ATI video driver flgrx didn't do rotation up to a month or two ago.  The new release supports it or so I've heard.  Hopefully you will be the one to provide proof.  The flgrx that supports rotation may be Catalyst 8.11, but I can't be sure.  Even if you don't have that version, note down your version and we'll try with it.

Most likely you just need to change your xorg.conf video section from:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```
to:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
	Option		"RandRRotation"		"on"
EndSection
```
Rotation should now work for you after you restart X (<ctrl><alt><backspace>).

Sure we could move to the rotation thread if you would like.  If not I sure would appreciate it, if we get rotation working for you, for you to post that on the rotation thread.  That way we could change it into a HOW TO for TX2000's and TX2500's.

---

### Post by martinjochimsen on 2008-12-05
...hmmmm....it didn't help to put in " Option "RandRRotation" "on" " in the xorg. Nothing happens to the desktop but the stylus still goes crazy!!! :-)
Maybe it's something with the fglrx-driver as you say?!? Do you now how I can see which version I've got?

Martin

---

### Post by Favux on 2008-12-05
Hey martin,

Ok, you may be right and you have the pre-rotation flgrx driver.  There should be at least two ways.  In System>Administration>Hardware Drivers, which is where your proprietary drivers are, my nVidia driver has its version number.  Also if you highlight it it shows the version number in the info. box below.  Also I have an nVidia control panel called:  System>Administration>NVIDIA X Server Settings.  It has the nVidia driver version number in several places.  Does ATI give you a similar video applet?  The nVidia one actually has a limited rotation feature, meant to move a monitor from landscape to portrait mode.

Also aren't there two more ATI drivers.  The "Radeon" driver and an "ati" driver?  I know those would be a step back in function but I'm pretty sure at least the "Radeon" driver supports rotation.  As a last resort maybe you could try that one to at least show yourself your tablet can rotate.

---

### Post by manu7irl on 2008-12-05
hi everybody.
i found a script to install the new catalyst 8.11 on ubuntu 
the file is attached at the bottom
you have to save the file in a folder (like ~/Desktop, in my example) and [COLOR="Red"]do a ctrl + alt + F1 to go to the plain text console.[/COLOR] After you're open this black screen do a login.

first you have to be "root" and type your password.
```
sudo -s
``` 
do a cd command to the folder you save
```
cd /Desktop
```
and type
```
sh install-fglrx-debian.sh
```
this will install the new driver 
Bad news : i can tell you that it doesn't support rotate anyway...
Good news : my wacom's back and the front microphones work.
download the file from : [URL="http://www.kanotix.com/files/install-fglrx-debian.sh"]http://www.kanotix.com/files/install-fglrx-debian.sh
[/URL]

---

### Post by Favux on 2008-12-05
Hi manu7irl,

Thanks for the info., even is it is discouraging.  How do you know it doesn't rotate.  Did you try?  If so what method did you use?  I can't find any ATI info. on rotation for linux drivers, so it's not like I'm doubting you.  Have you checked with HP to see if there is a video bios update for your video chipset?  Forlorn hope I know but maybe that would add functionality.  It must be a bummer to have a tablet pc that you can't use as a tablet!

martin,

Given manu7irl's info., as I see it there are three choices:
1)  Give up.  The easiest.
2)  Go to Hardware Drivers and deactivate flgrx and see what your system wants to do about video.  Or I checked Synaptic and there is a xserver-xorg-video-radeon driver.  So you could uninstall fglrx with Synaptic and then install xorg's radeon driver.  See if that rotates.  If you have a lot of eye candy installed you might have trouble with it.  You can always uninstall it and reinstall fglrx through Synaptic.
3)  Try the new catalyst 11 flgrx driver any way and hope your system is somehow different from man7irl's and it rotates.  The ATI site:
   [http://ati.amd.com/support/drivers/linux/linux-radeon.html]("http://ati.amd.com/support/drivers/linux/linux-radeon.html")
has info. on installing the new Catalyst.  As does the Unofficial Wiki:
   [http://wiki.cchtml.com/index.php/Main_Page]("http://wiki.cchtml.com/index.php/Main_Page")
I'm nervous about you installing a driver that you don't know how to completely uninstall.  But if the script is installing a deb package you should be able to uninstall it.

Decisions, decisions.  Let me know.

---

### Post by Favux on 2008-12-05
manu7irl and martin,

I now have "proof" that a TX2500 can rotate.  Starting on page 34 of this thread Shm posts several messages.
post #336:
He says he has a TX2520er with-
Computer
Processor	2x AMD Turion(tm) X2 Dual-Core Mobile RM-70
Memory	1796MB (550MB used)
Operating System	Ubuntu 8.10
User Name	denis (denis)
Date/Time	&#1042;&#1089;&#1082; 02 &#1053;&#1086;&#1103; 2008 23:51:01
Display
Resolution	1280x800 pixels
OpenGL Renderer	Software Rasterizer
X11 Vendor	The X.Org Foundation
Version	1.5.2
post #339:
he posts a rotation script
post #344:
he posts an improved rotation script

Notice he's using the X.org driver ("radeon" I think) 1.5.2 and he says he's getting rotation.  And the xserver-xorg-video-radeon driver in Synaptic is v. 1:6.9.0.

---

### Post by martinjochimsen on 2008-12-05
Hi Favux

I tried manu7irl small guide but I couldn't install the new fglrx-driver.
I tried to install the driver following the guide from this link [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide) - but I couldn't get it to work. I then deactivated the fglrx driver and your rotation-script suddenly worked (I guess its yours, but I have been messing around so much, so I don't know enymore! :-) ). The only problem then is, that I can't go back from portrait-mode to landscape-mode....and the mouse is moving the complete uppeset directions, that I want it to do....aaaaand the stylus and touch stopped working, because all the importent stuff in xorg disappeared when I deactiveted fglrx. I think its time to start all over, so I'll get back to you, when I have a fresh Ibex. then I will look into what you wrote in post 420.
Thanks again for your work.

Martin :-)

---

### Post by Favux on 2008-12-06
Hi martin,

Wow!  I'm sorry that happened to you.

So after you deactivated flgrx you rebooted (at least X), right?  Then you rotated using the script, not wacomrotate daemon, correct?  Of course the mouse wouldn't have followed if all the wacom settings had been removed from xorg.conf.  HAL must have been handling the stylus.  So your xorg.conf resembled tah123's xorg.conf with a video section like:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection
```
maybe.

I'm not at all sure why the wacom settings were removed from xorg.conf.  Tentatively try this theory on for size.  You might have ended up with Ubuntu's default video driver (which may be what tah123 is running), say a VESA driver without any wacom support through xorg.conf.  This is why when you rebooted your xorg.conf was wiped clean.  Our mistake may have been after deactivating the flgrx driver not immediately installing the Radeon driver before a reboot.  Does this seem to track with you?  And maybe the ATI video card doesn't need:
```
	Option		"RandRRotation"		"on"

```
Something else to keep in mind.

I'm not sure you need to reinstall Ibex.  Perhaps just a wacom supporting video driver and redo the tutorial?  Either way good luck!  I really appreciate you working on this with me.

---

### Post by manu7irl on 2008-12-06
hi favux and martin 
it takes me time to answer because I'm from Israel...
I gonna explain what I did :
Yesterday when I find this new driver which is by the way not the driver you've attached favux because the driver we need on the TX2500 (mine is TX2520 amd64 bit version) is the 64 bit version that I brought you.
after a successful installation, I tried you're second method and installed both C program for the wacom rotation and do a launcher for the screen rotation. When I clicked on the launcher nothing happened. 
after many tests also with you're first method, I gave up and deside to try to return back to the Radeon driver (just write in xorg.conf driver "radeon"). I gave a second try with your scripts favux but they never worked. So I returned back to the old rotate script that I saw before on this thread, surprise when click on the launcher the screen rotates (just when I tried with the radeon driver) but the wacom and the touchpad don't, so I took a look at this script and there's inside the wacom rotation's functionality but it didn't work. 
I saw another thing we talked about here a while ago, when I used the new driver the sleeping mode just didn't work (problem with refreshing the screen makes the screen stays black), the same as the previous fglrx driver. 
I attached at the bottom the old script I told you about and my xorg.conf too. I quoted it before when it was with the radeon driver now i just want to play a little with compiz.
An open question : maybe if someone could write a compiz plugin that could rotate the screen, it'll be the best thing ever!

my Xorg.conf :

[PHP]```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier "stylus"
	Driver "wacom"
	Option "Type" "stylus"
	Option "USB" "on"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
	Option "Button2" "3" # make side-switch a right button
	Option "TopX" "225"
	Option "TopY" "225"
	Option "BottomX" "26300"
	Option "BottomY" "16375"
EndSection

Section "InputDevice"
	Identifier "touch"
	Driver "wacom"
	Option "Type" "touch"
	Option "USB" "on"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-"
	Option "TopX" "200"
	Option "TopY" "225"
	Option "BottomX" "4000"
	Option "BottomY" "3875"
EndSection

Section "InputDevice"
	Identifier "eraser"
	Driver "wacom"
	Option "Type" "eraser"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
	Option "USB" "on"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver      "fglrx"
#	Option      "UseInternalAGPGART" "yes"
#	Option      "VideoOverlay" "on"
#	Option      "OpenGLOverlay" "off"
#	Option      "MonitorLayout" "LVDS, AUTO"
#	Option		"RandRRotation"		"on"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24
	SubSection	"Display"
		Depth	24
		Modes
	EndSubSection
EndSection

Section "Extensions"
#	Option	"Composite"	"1"
#	Option	"RENDER"	"1"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen		"Default Screen"
	Inputdevice     "stylus"	"SendCoreEvents"
        Inputdevice     "touch"		"SendCoreEvents"     
	Inputdevice     "eraser"	"SendCoreEvents"
EndSection
```[/PHP]

---

### Post by Favux on 2008-12-06
To martin and manu7irl,

Success!!  Congratulations manu7irl you achieved rotation with "radeon"!

What we now think we know:

ATI proprietary driver "flgrx" (up to and including Catalyst 8.11):
   Rotation:  **NO**
   3-D acceleration:  yes
   Blank screen on wake up problem:  yes
(I can't find rotation mentioned anywhere on the ATI site, much less if they plan to add it)

Xorg driver "radeon":
   Rotation:  **YES**
   3-D acceleration:  ???
(according to the Xorg driver site as of 9/08 3-D acceleration wasn't enabled on the ATI Radeon HD 3200, but they planned to add it)

Now let's try to synchronize as much as possible:
1)  We all have basically the same Wacom Graphire(?) usb active digitizer touchscreen tablet.
2)  TX2000 has nVidia GeForce Go 6150
    TX2500 has ATI HD 3200
3)  We're all on 64-bit AMD Ubuntu 8.10 (on our dual core 64-bit AMD processors).
4)  Are we all using the Linux Wacom Project's development linuxwacom driver 0.8.1-6?  I am.  I use gali98's tutorial at:
   [http://ubuntuforums.org/showthread.php?p=5469447#post5469447]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")
(remember linuxwacom just recently added usb support)
(if not what version of the linuxwacom driver are you using and how did you install it?)
5)  Remember Ubuntu 8.10 introduced HAL.  Martin isn't using HAL at all.  Manu7irl and I are using HAL for the mouse and touchpad.  Manu7irl is using HAL for the keyboard. I am not so that I can do single key key binding to my "Q" key for screen rotation.

manu7irl,
The key thing is the "radeon" driver allows rotation.  Did you reboot either X or your computer with "radeon" installed between running my script and running Shm's script?  I am wondering if the "radeon" driver wasn't active when you tried my script. 
Were your stylus, eraser, and touch working before running each of the scripts?  I suspect that your linuxwacom driver is not successfully installed or you are using an older version of it.
Did rotation on "radeon" happen with " Option   "RandRRotation"        "on" " in xorg.conf or without it?
I can't see a functional difference between Shm's script and mine because basically both are using xsetwacom commands.  Shm's script doesn't even include the eraser.  I'll keep looking at it.
The wacomrotate daemon and C script didn't work with "flgrx" because it doesn't support rotation.  Did you try them with "radeon"?  If rotation happens but stylus etc. doesn't reorient:  I would take that as further evidence that there is a problem with your linuxwacom install.

After going down the blind alley of "flgrx" we are finally making some progress.  To enable rotation making the TX2500 a functional tablet pc we need to concentrate on Xorg's "Radeon".  At least until ATI explicitly adds rotation to "flgrx".

---

### Post by manu7irl on 2008-12-06
Hi favus 
every thing's right without my wacom driver and you're right I restarted and the 2nd method worked for me but the wacom driver didn't do the same after the tom's package install, I changed [COLOR="DarkOrange"]the wacomrotate -f[/COLOR] to [COLOR="DarkOrange"]wacomrotate -f -t[/COLOR] but with no changes.
the first method worked too with the first script rotating the screen 90 degrees each time but it stopped after the first rotation and without any possibility to change it back.

the new driver comes definitely with no supporting rotation and also has the same bugs that had the previous one.


[COLOR="Blue"]work until today on HP TX2520 ubuntu 8.10, kernel version 9 :
[/COLOR]
wacom touch and pen calibrated with the gali98 method
wireless and bluetooth out of the box
lightscribe with the lacie 32 bit program
sound with the line (the sound comes both from headphone and speakers, at the same time yet): 
options snd-hda-intel index=0 model=toshiba position_fix=1
update the bios to the new version it didn't do anything better that I saw before.
rotation works only with radeon driver through the shm's script. I'll try to link the script to a button.
I did little tests with fprint but i prefer a real password.

---

### Post by Favux on 2008-12-06
manu7irl,

Good, more progress.  Maybe instead of going to Shm's script, let us try with the two simple scripts I started with.  This will give us the simplest possible case and make it easier to debug.  Create two launchers and name them Tablet (portrait) and Laptop (landscape).  Point them to the associated script name:

.portrait.sh
```
#!/bin/bash

xrandr -o right
xsetwacom set "stylus" Rotate CW
xsetwacom set "touch" Rotate CW
xsetwacom set "eraser" Rotate CW

```

.landscape.sh
```
#!/bin/bash

xrandr -o normal
xsetwacom set "stylus" Rotate NONE
xsetwacom set "touch" Rotate NONE
xsetwacom set "eraser" Rotate NONE

```

Switch between modes by double clicking on the appropriate launcher.  Or if you put the launcher in a panel, single click it.

I am assuming the TX2500 doesn't like something about:
```
rotation="$(xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5)"

```
Because it flips back and forth on my TX2000 and does not get stuck.

---

### Post by manu7irl on 2008-12-06
maybe you know about a trick to do that from the same launcher and without the :
```
rotation="$(xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5)"
```
maybe the first rotation line that is quoted will work on ubuntu 8.10 ?? don't you think?

---

### Post by Favux on 2008-12-06
Hi manu7irl,

No the first one won't work, at least not for me on 8.10.  I'll come back and show you why in a couple hours.  I'll breakdown the command:
```
rotation="$(xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5)"
```
and show you my output and how it works.  We'll open up a terminal and pipe "|" each part of:
```
xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5
```
and try and figure out what's going on.  If it rotates the first time it should be returning "normal".  Why it isn't returning "right" the second time I don't have a clue.  In the mean time you'll have to stick with two launchers and there isn't much point in binding it to a key.

Sorry, got to go.

---

### Post by martinjochimsen on 2008-12-06
Hi favux and manu7irl

I see you guys have been very active today. It looks really interesting. I have made a clean install of Ibex and now I'm going to install the wacomdriver again using gali98s guide. Then I will try out the things you have been working with. By the way I'm using a 32-bit Ubuntu and not 64-bit. I'm sorry I haven't been clear about that. I'll get back to you later.

Martin :-)

---

### Post by martinjochimsen on 2008-12-06
...and 3 hours later rotation WORKS!!!!!! :-D
As I told you, I made a clean install of Ibex and I didn't activate the fglrx-driver in Hardware Drivers. One of you wrote earlier that the fglrx-driver might be the problem so I didn't do anything about the drivers.
I then followed galis guide ([http://ubuntuforums.org/showpost.php?p=5469447&postcount=5](http://ubuntuforums.org/showpost.php?p=5469447&postcount=5)) and made some changes in my xorg. I used an old xorg because after installing the wacom driver nothing was added to the xorg. I have attached my new xorg.
After the final reboot stylus and touch were working from the start - before I always had to reboot X to get it to work. Now I was ready to fight for rotation!!!
I followed and used the little rotation guide (and script) from this wiki [http://www.pietrobattiston.it/wiki/doku.php?id=intrepid_on_hp_pavilion_tx2500](http://www.pietrobattiston.it/wiki/doku.php?id=intrepid_on_hp_pavilion_tx2500) . I can't remember where I got this link, was it from this thread? I would surely like to give this guy some credits for his small tx2500-wiki. Now my stylus, touch and rotation works! I'm a happy dude!!!
...the only set back is, that I (again) have to restart X to get stylus and touch working - but hey....that's a small price to pay.

Martin :-)
(tx2590oe - Ubuntu 8.10)

---

### Post by martinjochimsen on 2008-12-06
I forgot to tell you, that stylus and touch also is working (the right way) when the screen/desktop has rotated.

Martin :-)

---

### Post by Favux on 2008-12-06
Hi manu7irl,
Welcome back martin!

Great work martin!  It may be that the linuxwacom development branch is just a little buggy and that's why you have to keep restarting X.  I'll look at the rest of the stuff in your post in a minute.  Right now I'd appreciate your help.

Xrandr actually knows what our screen orientation is (normal, left, inverted, or right).  Getting xrandr to tell us what it knows isn't so easy.  What I need is for you to type these commands into a terminal and capture the output so we can see what is going on.  I'll show you my output so you can compare.

First we have to query xrandr and get it to respond in a complete or wordy way.  In a terminal type “xrandr -q –verbose” (ignore quotes) which should give you output similar to this:
```
dave@dave-laptop:~$ xrandr -q --verbose

Screen 0: minimum 320 x 240, current 1280 x 800, maximum 1280 x 800

default connected 1280x800+0+0 (0x1ad) normal (normal left inverted right) 0mm x 0mm

	Identifier: 0x1ac

	Timestamp:  121636

	Subpixel:   unknown

	Clones:    

	CRTC:       0

	CRTCs:      0

  1280x800 (0x1ad)   51.2MHz *current

        h: width  1280 start    0 end    0 total 1280 skew    0 clock   40.0KHz

        v: height  800 start    0 end    0 total  800           clock   50.0Hz

  1024x768 (0x1ae)   40.1MHz

        h: width  1024 start    0 end    0 total 1024 skew    0 clock   39.2KHz

        v: height  768 start    0 end    0 total  768           clock   51.0Hz

  800x600 (0x1af)   25.0MHz

```
and a whole bunch more.  Notice the second line of the output.  That's the one we want because it tells us our current state is “normal”.  Next we want to pipe “|” this output to “ sed -n '2 {p;q}' “ to strip out only the line we want.  So now type into the terminal “xrandr -q --verbose | sed -n '2 {p;q}'” (ignore quotes) which gives us:
```
dave@dave-laptop:~$ xrandr -q --verbose | sed -n '2 {p;q}'

default connected 1280x800+0+0 (0x1ad) normal (normal left inverted right) 0mm x 0mm

```
This is the line we are interested.  Notice that “normal” is the fifth word.  So here you might be partially right manu7irl and what we want is “-f4”.  But let's find out for sure.  To cut out the fifth word we pipe “|” the previous output to “cut -d' ' -f5
”.  So in the terminal type “xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5)” and tada:
```
dave@dave-laptop:~$ xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5

normal

```
Long way to go, huh?  But this is the output the rest of the script is running on.        
We can then do the same thing with the screen rotated:
```
dave@dave-laptop:~$ xrandr -q --verbose

Screen 0: minimum 320 x 240, current 800 x 1280, maximum 1280 x 800

default connected 800x1280+0+0 (0x1ad) right (normal left inverted right) 0mm x 0mm

	Identifier: 0x1ac

	Timestamp:  121636

	Subpixel:   unknown

	Clones:    

	CRTC:       0

	CRTCs:      0

  1280x800 (0x1ad)   51.2MHz *current

        h: width  1280 start    0 end    0 total 1280 skew    0 clock   40.0KHz

        v: height  800 start    0 end    0 total  800           clock   50.0Hz

  1024x768 (0x1ae)   40.1MHz

        h: width  1024 start    0 end    0 total 1024 skew    0 clock   39.2KHz

        v: height  768 start    0 end    0 total  768           clock   51.0Hz

  800x600 (0x1af)   25.0MHz

```
Notice now the second line contains “right” instead of “normal”.  Piping again:
```
dave@dave-laptop:~$ xrandr -q --verbose | sed -n '2 {p;q}'

default connected 800x1280+0+0 (0x1ad) right (normal left inverted right) 0mm x 0mm
```
Notice now that the fifth word of the second line is now “right”!

From what you are telling me manu7irl the output the first time is “normal” but the second time, when you are rotated, the output is something other than “right”.  Which is the only thing that would make the script flip your screen counterclockwise and back to “normal”.  So manu7irl and martin we also need your output when your screen is rotated.  Up to at least “xrandr -q --verbose | sed -n '2 {p;q}'”.

A little tricky sure, but doable.  We need to know the number of the word in the second line that is changing from “normal” to “right” (and would give inverted and left if we were rotating that far).  Then we should be able to fix the script, with luck.

---

### Post by Favux on 2008-12-06
Hi martin (and manu7irl),

Ok, the new rotation script you're using is actually Shm's script.  Manu7irl is also working with it.  Pietro Battiston apparently found and corrected a typo in Shm's script, which might explain some of the trouble manu7irl is having with it.

What kernel are you on martin?  Is it 2.6.27-10 like before?  Maybe that's why you have to restart X.  I loose eraser and touch occasionally with 2.6.27-9.  We may be running into the limits of Linux Wacom Project's development linuxwacom driver 0.8.1-6 given the advancing kernel updates.

What video driver are you running on I wonder?  It's not listed in xorg.conf.  Do you know a way to tell?  Maybe a search for "radeon" in Synaptic?  See if the box to xserver-xorg-video-radeon is checked.  But xserver-xorg-video-ati is probably checked to.  Also the ATI card apparently doesn't need " Option   "RandRRotation"   "on" ".  Which is good to know.

Why don't we try to use HAL on your synaptic pad and mouse and see if that helps with the restarting X thing.  I commented them out in the attached xorg.conf.

---

### Post by martinjochimsen on 2008-12-07
Hi favux

Here is the output you asked for. It's a bit different from your output - and yes I'm on kernel 2.6.27-10.

Screen: normal

```
martin@martin-laptop:~$ xrandr -q --verbose
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA-0 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3b
	Timestamp:  122729
	Subpixel:   no subpixels
	Clones:    
	CRTCs:      0 1
	load_detection: 1 (0x00000001) range:  (0,1)
None disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3c
	Timestamp:  122729
	Subpixel:   no subpixels
	Clones:    
	CRTCs:      0 1
	load_detection: 1 (0x00000001) range:  (0,1)
LVDS connected 1280x800+0+0 (0x3e) normal (normal left inverted right x axis y axis) 260mm x 170mm
	Identifier: 0x3d
	Timestamp:  122729
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       0
	CRTCs:      0
	EDID_DATA:
		00ffffffffffff000daf261200000000
		2d100103801a11780a9f059656508827
		20505400000001010101010101010101
		0101010101011b1b008450201330281a
		250004aa10000018000000fe004e3132
		3149412d4c30320a2020000000fe0043
		4d4f0a202020202020202020000000fe
		004e31323149412d4c30320a20200072
		scaler: full
	backlight: 255 (0x000000ff) range:  (0,255)
  1280x800 (0x3e)   69.4MHz -HSync -VSync *current +preferred
        h: width  1280 start 1320 end 1346 total 1412 skew    0 clock   49.1KHz
        v: height  800 start  802 end  807 total  819           clock   60.0Hz
  1024x768 (0x3f)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x40)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x41)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
```

and 

```

martin@martin-laptop:~$ xrandr -q --verbose | sed -n '2 {p;q}'
VGA-0 disconnected (normal left inverted right x axis y axis)
```

and 

```
martin@martin-laptop:~$ xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5
inverted
```


screen: rotated once counterclock (to the left)

```
martin@martin-laptop:~$ xrandr -q --verbose
Screen 0: minimum 320 x 200, current 800 x 1280, maximum 1280 x 1280
VGA-0 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3b
	Timestamp:  122729
	Subpixel:   no subpixels
	Clones:    
	CRTCs:      0 1
	load_detection: 1 (0x00000001) range:  (0,1)
None disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3c
	Timestamp:  122729
	Subpixel:   no subpixels
	Clones:    
	CRTCs:      0 1
	load_detection: 1 (0x00000001) range:  (0,1)
LVDS connected 800x1280+0+0 (0x3e) left (normal left inverted right x axis y axis) 260mm x 170mm
	Identifier: 0x3d
	Timestamp:  122729
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       0
	CRTCs:      0
	EDID_DATA:
		00ffffffffffff000daf261200000000
		2d100103801a11780a9f059656508827
		20505400000001010101010101010101
		0101010101011b1b008450201330281a
		250004aa10000018000000fe004e3132
		3149412d4c30320a2020000000fe0043
		4d4f0a202020202020202020000000fe
		004e31323149412d4c30320a20200072
		scaler: full
	backlight: 255 (0x000000ff) range:  (0,255)
  1280x800 (0x3e)   69.4MHz -HSync -VSync *current +preferred
        h: width  1280 start 1320 end 1346 total 1412 skew    0 clock   49.1KHz
        v: height  800 start  802 end  807 total  819           clock   60.0Hz
  1024x768 (0x3f)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x40)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x41)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
```

and

```
martin@martin-laptop:~$ xrandr -q --verbose | sed -n '2 {p;q}'
VGA-0 disconnected (normal left inverted right x axis y axis)
```

and

```
martin@martin-laptop:~$ xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5
inverted
```



screen: rotated once more (real tablet-mode" screen twisted and laying down)

```
martin@martin-laptop:~$ xrandr -q --verbose
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA-0 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3b
	Timestamp:  122729
	Subpixel:   no subpixels
	Clones:    
	CRTCs:      0 1
	load_detection: 1 (0x00000001) range:  (0,1)
None disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3c
	Timestamp:  122729
	Subpixel:   no subpixels
	Clones:    
	CRTCs:      0 1
	load_detection: 1 (0x00000001) range:  (0,1)
LVDS connected 1280x800+0+0 (0x3e) inverted (normal left inverted right x axis y axis) 260mm x 170mm
	Identifier: 0x3d
	Timestamp:  122729
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       0
	CRTCs:      0
	EDID_DATA:
		00ffffffffffff000daf261200000000
		2d100103801a11780a9f059656508827
		20505400000001010101010101010101
		0101010101011b1b008450201330281a
		250004aa10000018000000fe004e3132
		3149412d4c30320a2020000000fe0043
		4d4f0a202020202020202020000000fe
		004e31323149412d4c30320a20200072
		scaler: full
	backlight: 255 (0x000000ff) range:  (0,255)
  1280x800 (0x3e)   69.4MHz -HSync -VSync *current +preferred
        h: width  1280 start 1320 end 1346 total 1412 skew    0 clock   49.1KHz
        v: height  800 start  802 end  807 total  819           clock   60.0Hz
  1024x768 (0x3f)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x40)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x41)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
```

and

```
martin@martin-laptop:~$ xrandr -q --verbose | sed -n '2 {p;q}'
VGA-0 disconnected (normal left inverted right x axis y axis)

```

and

```
martin@martin-laptop:~$ xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5
inverted
```


screen: rotated once more

```
martin@martin-laptop:~$ xrandr -q --verbose
Screen 0: minimum 320 x 200, current 800 x 1280, maximum 1280 x 1280
VGA-0 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3b
	Timestamp:  122729
	Subpixel:   no subpixels
	Clones:    
	CRTCs:      0 1
	load_detection: 1 (0x00000001) range:  (0,1)
None disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3c
	Timestamp:  122729
	Subpixel:   no subpixels
	Clones:    
	CRTCs:      0 1
	load_detection: 1 (0x00000001) range:  (0,1)
LVDS connected 800x1280+0+0 (0x3e) right (normal left inverted right x axis y axis) 260mm x 170mm
	Identifier: 0x3d
	Timestamp:  122729
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       0
	CRTCs:      0
	EDID_DATA:
		00ffffffffffff000daf261200000000
		2d100103801a11780a9f059656508827
		20505400000001010101010101010101
		0101010101011b1b008450201330281a
		250004aa10000018000000fe004e3132
		3149412d4c30320a2020000000fe0043
		4d4f0a202020202020202020000000fe
		004e31323149412d4c30320a20200072
		scaler: full
	backlight: 255 (0x000000ff) range:  (0,255)
  1280x800 (0x3e)   69.4MHz -HSync -VSync *current +preferred
        h: width  1280 start 1320 end 1346 total 1412 skew    0 clock   49.1KHz
        v: height  800 start  802 end  807 total  819           clock   60.0Hz
  1024x768 (0x3f)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x40)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x41)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz

```

and

```
martin@martin-laptop:~$ xrandr -q --verbose | sed -n '2 {p;q}'
VGA-0 disconnected (normal left inverted right x axis y axis)
```

and

```
martin@martin-laptop:~$ xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5
inverted
```

....hmmmm....something to work with!!! :-)

Videodriver:
xserver-xorg-video-radeon and xserver-xorg-video-ati is checked in Synaptic.
I have now idea of what HAL is, but I will try your corrected xorg later today.
I think I once saw you write that you were a linux-novice?!?! I don't understand ANYTHING what all these commands is about, so I must be like a linux-microbe - but I'm glad I can help!!! :-D
I'll get back to you.

Martin :-)

---

### Post by Favux on 2008-12-07
Hi martin,

Alright, you did it!  I had no idea xrandr would give such different output for an ATI card vs a nVidia card.  Amazing.

Notice my second line of output is the equivalent of your 16 th line of output.  This is the line where xrandr tells us the current screen orietation-"normal", "right", etc.  Notice on your line it is the fifth "word" in, just like on my second line.  So if I have counted right the command should change from:

for a **TX2000**
```
rotation="$(xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5)"

```
to:

for a **TX2500**
```
rotation="$(xrandr -q --verbose | sed -n '16 {p;q}' | cut -d' ' -f5)"

```

So (**martin and manu7irl**) please try this TX2500 command with the rotation script.  It should work.  If it doesn't it almost doesn't matter, because we are very close.  We will just tweak the commands you ran before with 16, and you only have to do "normal" or laptop orientation.

HAL stands for Hardware Abstraction Layer.  It's new technology that allows usb hot plugging among other stuff.  Different things, like the synaptic pad, are controlled by fdo files instead of by xorg.conf.  Fdo files are like little script files, telling the OS what to do with the input.  Unfortunately it looks like HAL inherently can't work with things like wacom tablets.  This is for technical reasons to tedious to discuss (in other words I'm not sure I understand it).  The developers apparently only started realizing that by the time Intrepid was feature frozen.  So in Intrepid HAL was suppose to start replacing xorg.conf.

Yes I am a newbie.  I've just been playing with this command on and off since I ran across the script, what, a month or two ago.  I pretty much have figured out what it does.  But on the how it does what it does I'm more iffy.

I still wish we could figure out what video driver you are using.  I have seen some xorg.conf with "radeon" in the video section.  Also I saw on pre-release sources a slew of ATI updates are pending.

---

### Post by martinjochimsen on 2008-12-07
Hi favux

I have attached my Xorg.o.log. Maybe you can see what graphicsdriver I'm using?

Martin :-)

- it comes from /var/log

---

### Post by martinjochimsen on 2008-12-07
Hi favux

I'm not sure  about what you mean when you say I should try this line: rotation="$(xrandr -q --verbose | sed -n '16 {p;q}' | cut -d' ' -f5)" with the script? how/where/when?

Today I'm using your corrected xorg that you posted, but there is no difference...rotation still works!!! YES :-)

Martin

---

### Post by Favux on 2008-12-07
Hi martin,

You did it again.  You're using Xorg's "radeon" driver according to /var/log.

What I meant is to swap out the new command line for the old command line in the rotation script for the new TX2500 command line script.  The rest is the same as in the HOW TO.  As soon as you show it's working we can add it and the TX2500 to the rotation HOW TO.

right handed script:
```
#Uncomment next line to use script on 6.06 (Dapper Drake) (and comment later one):
#rotation="$(xrandr -q | grep 'Current rotation' | cut -d' ' -f4)"

#This line is for use with 8.04 (Hardy Heron) and 8.10 (Intrepid Ibex):
#For TX2000 uncomment next line.
#rotation="$(xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5)"
#For TX2500 with Xorg's “radeon” driver uncomment next line.
rotation="$(xrandr -q --verbose | sed -n '16 {p;q}' | cut -d' ' -f5)"

case "$rotation" in 
    normal) 
        xrandr -o right 
        xsetwacom set "stylus" Rotate CW 
        xsetwacom set "touch" Rotate CW 
        xsetwacom set "eraser" Rotate CW 
        ;; 
    right) 
        xrandr -o normal 
        xsetwacom set "stylus" Rotate NONE 
        xsetwacom set "touch" Rotate NONE 
        xsetwacom set "eraser" Rotate NONE 
        ;; 
esac

```

left handed script:
```
#Uncomment next line to use script on 6.06 (Dapper Drake) (and comment later one):
#rotation="$(xrandr -q | grep 'Current rotation' | cut -d' ' -f4)"

#This line is for use with 8.04 (Hardy Heron) and 8.10 (Intrepid Ibex):
#For TX2000 uncomment next line.
#rotation="$(xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5)"
#For TX2500 with Xorg's “radeon” driver uncomment next line.
rotation="$(xrandr -q --verbose | sed -n '16 {p;q}' | cut -d' ' -f5)"

case "$rotation" in
    normal) 
        xrandr -o left 
        xsetwacom set "stylus" Rotate CCW 
        xsetwacom set "touch" Rotate CCW 
        xsetwacom set "eraser" Rotate CCW 
        ;; 
    left)
        xrandr -o normal
        xsetwacom set "stylus" Rotate NONE
        xsetwacom set "touch" Rotate NONE
        xsetwacom set "eraser" Rotate NONE
        ;;
esac

```

I shouldn't have said corrected xorg.conf.  What we did was have HAL take over from xorg.conf on the mouse and the synaptic pad.  The hope is this will help your stylus and touch work better and keep you from restarting X.
As you can see HAL does as good a job as xorg.conf and in Intrepid they're suppose to be commented out because Ubuntu is moving to HAL.  The key board section is suppose to be commented out too, but we don't want that.  That's because HAL breaks single key key bindings.  We want to go on the prove the new rotation script works and then bind it to your "Q" like the HOW TO shows, if you want to that is.

---

### Post by martinjochimsen on 2008-12-07
Now we are getting somewhere!!! :-)
Both scripts works beautifully now.
Since you are the brain regarding the scripts, how do we get the screen to rotate 180 degrees?
I tried to chance the "left" to "inverted" in the script and the screen rotated 180 degrees - but not stylus and touch.

Martin

---

### Post by Favux on 2008-12-07
Hi martin,

Try this:
```
#Uncomment next line to use script on 6.06 (Dapper Drake) (and comment later one):
#rotation="$(xrandr -q | grep 'Current rotation' | cut -d' ' -f4)"

#This line is for use with 8.04 (Hardy Heron) and 8.10 (Intrepid Ibex):
#For TX2000 uncomment next line.
#rotation="$(xrandr -q --verbose | sed -n '2 {p;q}' | cut -d' ' -f5)"
#For TX2500 with Xorg's “radeon” driver uncomment next line.
rotation="$(xrandr -q --verbose | sed -n '16 {p;q}' | cut -d' ' -f5)"

case "$rotation" in
    normal)
        xrandr -o inverted
        xsetwacom set "stylus" Rotate HALF
        xsetwacom set "touch" Rotate HALF
        xsetwacom set "eraser" Rotate HALF
        ;;
    inverted)
        xrandr -o normal
        xsetwacom set "stylus" Rotate NONE
        xsetwacom set "touch" Rotate NONE
        xsetwacom set "eraser" Rotate NONE
        ;;
esac

```

---

### Post by martinjochimsen on 2008-12-07
Nice.
That works perfect to.
Next thing is: 
Now I have 3 launchers on my desktop (for this test): Rotate left 90 degrees, rotate right 90 degrees and rotate 180 degrees.
With Shm's script I can rotate all the way round counterclock (just like in Vista), should we (meaning you) make this script do the same thing, or would you prefer to keep it more simple and just rotate 90 degrees and back or 180 degrees and back?

---

### Post by Favux on 2008-12-07
Hi martin,

Well my preference is to just rotate 90 degrees and then back. It's a lot faster that way.  In the rotation HOW TO, the general case script I start with, actually rotates you through 360 degrees.  Only it goes clockwise, the opposite of Windows Vista of course! What I did was simplify it and speed things up by breaking it up into a right and left handed script.  I personally never need or want the screen inverted or to the left.  But I can give you that script too if you want.

So the next step is to make a key binding if you want to try that.  That's also in the HOW TO.  If you need help with it holler.

Have you given up on method two and Tom Jaeger's wacomrotate daemon?  I'm not clear where we left that.

I'm a belt and suspenders kind of guy.  I have Tom Jaeger's method set up on (key bound to) my "Q" key and I have a launcher in my dock with the script method.  So if something changes and knocks out one method I still have the other one.  I must not be left without rotation!

---

### Post by Favux on 2008-12-08
Hi martin,

Cool!  You will never guess what.  The reason I didn't seem to be paying attention to Shm's script is that it didn't work on my TX2000.  But by comparing the output you gave me from your TX2500 and my TX2000 output and modifying it I now have it working on my laptop too.  If the modification works on your TX2500 we now have a script that will work on a TX2500 or a TX2000 directly without needing to change the command at the beginning of the script.
Even more exciting this may be a general script for any Wacom usb tablet!
Could I impose on you to check it out?  How do you want it to function?  Rotate 360 degrees clockwise or counterclockwise?  Or flipping from Landscape to Portrait to Landscape?  To the left or right?
I'm not sure if the color stuff is doing anything and I may strip it out.  I guess we could test it with and without color.  It seems to me that I read stuff on artifacts when the screen flipped and this stuff fixed that.  But I think the kernel, video driver, and wacom updates have fixed that and we don't need the color correction anymore.
Also he doesn't include the eraser so that needs to be added.

Let me know what you think.

---

### Post by martinjochimsen on 2008-12-08
sooooo....can I have the script to test?

Edit:
Forget my comment!!! I was to fast. :-)
I would like it to go counterclockwise and at least to potrait and landscape.
I haven't had eny problems with the colors.

Martin :-)

---

### Post by martinjochimsen on 2008-12-08
About the eraser:
I only (at least for now) use the stylus' eraser in xournal, and in that program the eraser automatically is assigned to the small button on side of the stylus. I think thats more handy instead of turning the stylus the whole way around to erase something.
Of course the eraser-function that way is a bit different from the way it works in Windows, where you can erase a long line with only one click.
What is yours preferences for the eraser?

Martin :-)

---

### Post by Favux on 2008-12-08
Hi martin,

I like the eraser as eraser.  It really only works that way in Gimp and kinda Inkscape, at least with the programs I have now.  I use Xournal too.

Ok, give me a while to work on the script.  You want it to go counterclockwise from landscape to portrait, right.  I only just figured out how to get it to work.  I'll post it tomorrow.

---

### Post by Favux on 2008-12-08
Hi martin (and manu7irl),

OK I have the requested scripts.  The both are working fine on my TX2000.  If they work on your TX2500 we have the long sought for "general" script.

I included a script that rotates counterclockwise 360 degrees and one that rotates counterclockwise to portrait and then back to landscape (the way I prefer).  If you and manu7irl (or anyone else with a TX2500) could test them out and post the results I would really appreciate it.

If you want scripts with different functions let me know.

---

### Post by martinjochimsen on 2008-12-08
Hi favux

Both scripts works perfect as they should. BUT I noticed something that all the scripts are doing including Shm's. I have a 12.1" screen with using 1280x800. When I rotate the screen the last 5 cm to the right is missing. I'v got some icons that is missing every time  I rotate to potrait, and I can't scroll to get to the icons.
Any ideas?

Martin

---

### Post by Favux on 2008-12-08
Hey martin,

Outstanding we have a general script!!!  It may even work with any usb wacom (I doubt serial wacom, but who knows?).

To manu7irl or any other TX2500 user out there:  Further confirmation would be helpful.

Yeah I noticed the missing right part of the screen too, so I don't put any icons over there.  I don't know if this happens in Vista or not, because the Sidebar takes up that area and it reorients itself to the new screen edge.  It does make my cairo-dock off center, and if it is full, cuts off the right edge.  Which is annoying.

Xrandr does allow you to change screen resolution.  I don't know how to do that, but it probably isn't that hard.  But I don't think that gets us where we want to go.  We're at 1280x800 right?  That's the native screen resolution of our LCD.  If we go down to say 1024x768 doesn't that blur our image?  Besides that might not be the problem.

It may be a problem with Xserver, where it doesn't preserve the center when it rotates (ie it has a bug that offsets the center a little).  Xrandr may allow us to shift our screen a little up and down, or left or right.  I'd have to look into that and see if it's possible.  And I don't know if it would be the same for a TX2000 and a TX2500.

Or maybe the screen image stretches horizontally when in portrait mode, but keeps the left edge anchored making some of the right edge fall of the screen?  Actually this sounds like what is happening.  I wonder if xrandr lets you address that?  It may be a MHz type setting.

Thank you for your help martin.  Do you need any other scripts?  I'll get around to modifying the HOW TO in a day or two.  I'm hoping for confirmation from at least 1 other TX2500 user.  After that could I talk you into posting a success story on the HOW TO.  You know describing your system and how you got it working.  By the way, did you do a key binding?

Also did you mess any more with wacomrotate daemon or do you just want to drop that?

---

### Post by martinjochimsen on 2008-12-08
Hi favux

Sure, I'll wright about the happy ending - I LOVE happy endings!!! :-D
I think for now  I don't need any more scripts. You have done a great job and I'm now using your 360_rotation script.
I didn't go further with the wacomrotate deamon, but maybe I should give it a try now that I no longer is using the fglrx-driver. I'll get back to that.
It would be great with a key binding to the "Q"-button, but no one of the 4 keys on the screen gives any respons in xev. Every other keys gives a respons. Do I need to install something else? The "DVD"-button actully used to work in 8.04 but nothing happens now.

Martin :-)

---

### Post by Favux on 2008-12-08
Hi martin,

The DVD and Q buttons went away in 8.10 for me to.  But when I removed the comment outs HAL had put in front of my keyboard section in xorg.conf they came back in xev.  I thought your keyboard was active in xorg.conf, ie not commented out.  Might want to check.

---

### Post by martinjochimsen on 2008-12-08
hmmm....actually I don't see anything about my keyboard in xorg except for

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection
```

I don't see anything else about keyboard or HAL.
What does your xorg say about the keyboard or HAL?

---

### Post by Favux on 2008-12-08
Hi martin,

Let me show you what I'm talking about.  When I update 8.04 to 8.10 my wacom stopped working.  Even after going through the tutorial it didn't work.  This is what I found in my xorg.conf.
```
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection
```
Intrepid, because of the introduction of HAL, also commented out my mouse, my touchpad, stylus, eraser, touch etc.  No wonder wacom "didn't work!"
There was a fdo file for the stylus included with Intrepid, so my stylus was suppose to work out of the box.  It didn't.
I uncommented everything except keyboard, touch pad and mouse, because HAL handled them fine.  Then I found out single key key bindings (think Q key) didn't work.  When I removed HAL's comment out marks (#) from keyboard like so:
```
# commented out by update-manager, HAL is now used
# uncommented out 11-27-08 as test for key bindings
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection
```
suddenly single key binding (I could use my Q key) started working.

Now to get your DVD and Q key to work.  I thought about it and finally remembered how I got them to work after the update to Intrepid.  It took me forever to find this.  I knew it was a post by gali98.  It was in the Re: Tablet PC Issues thread, post #313.  Ironically he answers a question of yours in the same post.

"So that the keys will work right, you need to run the two following commands:
```
sudo update-rc.d -f hotkey-setup remove
sudo update-rc.d  hotkey-setup start 99 1 2 3 4 5 6 .
```
(You need that period!)

Now reboot to see if it works (and it should...)"

He seems to be answering zoomy94 (#305) who has a TX2710p and a_toff (#307) who has a TX2617.  So it should be safe for you, and it worked for me on my TX2110us.

---

### Post by martinjochimsen on 2008-12-08
Hi Favux

You must be some kind of a wizard!!! Or at least gali must! :-)
I did the commands and restarted X - but nothing happened. Then I rebooted the computer and opened a terminal to check what xev now would show. I pushed the "DVD"-button and Rhythmbox opened up. I crossed my fingers and push the "Q"-button and....BAM! the screen rotates. What the beeeeep?!?!? :-D
How did THAT happen? I now wonder which script is being used.
Any way I'm happy now and I will go to work.
Talk to you later.

Martin :-D :-D :-D

---

### Post by Favux on 2008-12-09
Hi martin,

Am I right in thinking that the TX2500 screen hinge only rotates one way like the TX2000's?  In other words it doesn't rotate 360 degrees like some tablet pc's do?

---

### Post by Docaltmed on 2008-12-09
I'm doing a lot of head-scratching trying to get my rotation to work, and I don't know much, so I'm hoping someone can hold my hand, here. I went through the procedures in the tutorial, with no success. Of course, then I went back and re-read things, and realized that the driver I'm using, fglrx, doesn't support rotation. So I guess I need to change drivers: (1) How do I do that, and (2) will I lose all my eye candy in doing so?

---

### Post by Favux on 2008-12-09
Hi Dolctamed,

To remove the fglrx driver you need to deactivate fglrx by going to System>Administration>Hardware Drivers and choose deactivate fglrx.  Then reboot.  Please backup your xorg.conf before doing this!  Martin lost his xorg.conf for some reason when doing this.  So you may have to use your backed up xorg.conf to restore your wacom settings.

It is not clear to me if Xorg's driver "radeon" supports Compiz since I don't have an ATI card.  But Xorg is constantly updating "radeon" and they do plan to add 3d support, if they haven't done it yet.  In Software Sources in the pre-release stuff I see that Ubuntu has a bunch of ATI updates pending, including "radeon" and fglrx.  I don't know if they include 3d for "radeon" or rotation for fglrx, but you could hope.  The thing is that while Xorg has promised to add 3d support to "radeon" ATI doesn't even say anything about rotation at their site.

I'm about to update to rotation HOW TO with another script (the one martin helped me with) that works for the TX2500 among other stuff.

---

### Post by martinjochimsen on 2008-12-09
Yes, the screen on the tx2500 only rotates one way - clockwise.

Martin

---

### Post by Favux on 2008-12-09
Thanks

Also the rotation HOW TO is updated.  It's at:

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

---

### Post by Docaltmed on 2008-12-10
Favux, you're the bomb!

I had to manually edit xorg.conf and inserted "ati" where it said "fglrx" because the GUI froze up every time I tried to remove the driver through it.

After that, everything worked like a charm.  I confess that I do miss my cube, I'm looking forward to a 3D upgrade sometime soon.

Two questions, though:

1. In the process of all this, I realized I'm not using the amd64 version of Ubuntu. Over the long run, will this cause me any problems?

2. As of last week, I am back to having to restart the X server after booting up in order to get stylus capability. Does anyone have any idea why this happens?

---

### Post by Favux on 2008-12-10
Hi Docaltmed,

Great, I am glad you're enjoying rotation.

That's weird.  My GUI doesn't freeze when I deactivate the proprietary nVidia driver.  I wonder what's going on.

Despite all the stuff I've read to this point on ATI it's still not clear to me if "ati" and "radeon" are two different drivers.  I sort of have the impression that they're the same Xorg driver but different ATI cards require one name or the other.  I hope Xorg comes through with 3d support soon too.

re AMD 64:  I think it depends on how long the long run is.  64-bit is suppose to be faster than 32-bit, but I'll bet it's not real noticeable on our machines.  Mine came with 4 Gb of memory which 64-bit AMD can use "all" of.  32-bit AMD would only be able to use about 3.2 Gb's worth of it though.  So do you have over 3 Gb's of RAM?

The down side is that not all drivers & software come in 64-bit versions.  That's getting to be less and less of a problem.  I also have the impression that it's still less of a problem in Linux than Windows.  HP shipped my machine with 32-bit Vista, but I noticed more of the TX2500's were shipping with 64-bit Vista.

re Xserver reboot:  I don't know what that's about.  A couple hazy guesses would be that we are running up against the limits of the Linux Wacom Projest's development branch driver 0.8.1-6 in terms of its ability to work with kernel 2.6.27-9.  Or the shift over to HAL in Intrepid is the cause.  HAL is suppose to have a fdo file to enable the stylus to work out of the box (it didn't on my machine).  I really don't see how that could happen though.  As an experiment though, I wonder what would happen if you temporarily renamed the stylus fdo file and rebooted?  I looked at it, but now can't remember where it is.  Probably nothing.

Enjoy tablet mode!

---

### Post by Docaltmed on 2008-12-10
Something has gone very, very wrong. As I noted in an earlier post, my synaptic programs were locking up. This afternoon, I lost wireless -- the wireless network suddenly disappeared, according to ubuntu. Of course, all of the other computers are using it just fine. I tried to use the hardware manager to uninstall/reinstall the broadcom driver, but it locked up just like the package manager and update managers did. Then I went to look at my xorg.conf file, just cuz I couldn't think of anything else that had changed recently, and my "gksudo gedit" command line was just ignored.

I'm using the Broadcom STA wireless proprietary driver, which had worked pretty well before. I thought to maybe use the ndiswrapper, but of course I can't install it through the gui, and don't know how on the command line.

I can't tell if this is a wireless-specific problem, but I tend to think not, because of everything else that's going wrong at the same time, which is why I posted it here.

Suggestions?

EDIT: Just rebooted, and for no apparent reason, wireless returned. However, I am still left with the synaptic lock-up problem. Maybe I need an exorcism?

---

### Post by martinjochimsen on 2008-12-10
How I got the wacom-driver to work when I start my laptop:

sudo nano /etc/modules
add wacom
ctrl-o (save)
ctrl-x (exit)
reboot the computer

It worked for me!!!

Martin :-)

---

### Post by Favux on 2008-12-10
Hi Docaltmed,

My system just hung while I was running Update Manager.  Since I was running FireFox and knew it could  be the culprit I shut it down.  Ran Update Manager, no problem.  Had just updated plug-in for Firefox-DownThemAll.  Restarted Firefox, deactivated the DownThemAll plug-in, restarted Firefox and now Update Manager runs fine.  Firefox plug-ins that hang are known to do this.  They can also make the system unstable.

Sometimes the Software Sources package cache gets corrupted.  I have several times just gone to Updates and unchecked a box.  When it closes down it asks to reload and I tell it fine.  Then I start it again and recheck the box (maybe after running Update Manager) and again let it reload.  That seems to usually work.

Otherwise enter in a terminal:
```
dpkg --configure -a
```

if that doesn't work start diagnostics, output of:
```
tail /var/log/dpkg.log
```

---

### Post by Docaltmed on 2008-12-15
Now that I've had a fully-functioning and trouble-free laptop for 3-4 days, it's time to start messing with things again...

I originally installed ubuntu, but I'm seeing that several of my favorite programs are for the KDE desktop, not gnome. 

I've read that adding KDE is no problem, but given the amount of customizing I've done with the xorg.conf file, as well as others, before I do that, I just want to make sure that I'm not going to break something.

What do you guys recommend? Is it a safe move?

---

### Post by Favux on 2008-12-15
Hi Docaltmed,

While KDE 4.1 is a big improvement over 4.0 it still isn't quite there yet.  I personally would wait for 4.2.  As far as I know there aren't any compatability issues.  Let's see if someone knows more.

I know Easystroke was messed up by the way KDE handled windows, or something, but Tom Jaeger's been addressing that.  If you decide to go for it let us know how it goes.

---

### Post by Docaltmed on 2008-12-15
> **Favux said:**
> I know Easystroke was messed up by the way KDE handled windows, or something, but Tom Jaeger's been addressing that.  If you decide to go for it let us know how it goes.

Maybe I'll let somebody else go first...:popcorn:

---

### Post by Riverhed on 2008-12-15
Hi all,

I've been struggling with getting my touchscreen to work for the past few days on my HP Pavilion tx2500 running Intrepid 32-bit. I'm very new to Linux, so I've been reading forum posts like it's my job. I followed tons of tutorials and had not a lot of luck, but learned a good deal about the process and eventually was able to get it working.

gali98's tutorial was immensely helpful, yet it never quite worked for me, and I found out it had to do with installing the wacom drivers. I also found out eventually, reading elsewhere, that I could just install wacom-tools using the package manager. I did that and, because I had already tooled around with xorg.conf, my stylus started working (mostly) and touch worked perfectly. The problem I'm having still, though, is that while the side button on my stylus pen works as right-click, the eraser works, and the touch works, it doesn't click when I touch the pen to the screen. This is, to me, the most important feature of the stylus and the one I'd most like to resolve, but it's where I'm hitting a roadblock and could use some help. I've attached my xorg.conf, and would be grateful if someone could take a look at it and see if I've gone wrong somewhere.

A lot of people have reported problems with temperature and whatnot when installing Ubuntu, and luckily I didn't have any of that. Wireless, sound buttons, hibernate all worked out of the box. However, even though the volume/mute buttons work, I don't get any sound. I checked volume control to make sure the volume was up, and that's not it, and I tried a couple other walkthroughs but haven't really tackled it since I wanted to get the stylus working first, and I'm going to do that next. I've also seen scripts for rotating the screen and I'm fairly confident I can get that working, but the other main issue I have is that the fan constantly runs. I'm a total newbie when it comes to Linux and don't really know where to start on that one and would love some help if anyone is so inclined.

I'm excited to be a new Ubuntu user and would be glad to help anyone who might need it with at least getting to the point I'm at, and I hope you guys can help me get this fixed so I can move on with my life (my wife's probably going to kill me soon if I spend another whole day in front of my computer).

Thanks.

---

### Post by Riverhed on 2008-12-16
Since my last post I figured out my sound issues and I've found an acceptable-enough-for-me temporary fix for the stylus. I remapped the side-button from right-click to left-click and set my mouse preferences so that if I hold left-click it does a right-click. So now I have perfect tracking of my stylus and I can use that button to click and right-click. It would be nice to have the pressure sensitivity so I could use it the way it's supposed to be, but at least I can use the stylus in the meantime.

Thanks to everyone for the advice and how-to's.

---

### Post by tkb123 on 2008-12-25
Today is my first day scouring the web for help configuring my new tx2500 for the ubuntu distribution I downloaded last night, I have it a duel boot with Vista.

I did find an answer to the sound problem riverhed mentioned at [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1011108:](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1011108:)

Add this to /home/yourLoginName/alsa-base
[CODE] options snd-hda-intel index=0 model=toshiba position_fix=1 [!CODE]
The same post mentioned to add this next line if the first didn't work, which I did not need to do. So I didn't, but here it is:
[CODE] options snd-hda-intel index=0 model=acer [!CODE]

I'm going for the pen, and the screen rotation next; so it looks like this thread is the place for me. Is there a how-to avail? I thought I saw a mention to one, but no link?

In case it isn't obvioius, I'm not sure if I even qualify as a newbee yet, Although I do know my way around the command line, I don't know what a tag is (like the [code] tag mentioned in the forum guidelines,which I guessed at in this post).

---

### Post by Favux on 2008-12-25
Hi tkb123,

To install linuxwacom drivers follow gali98's tutorial exactly.  There is a new driver out 0.8.2, rather than the 0.8.1-6 in the tutorial.  You could subsitute the new version # for the old.  Don't type the commands, copy and paste them.

[http://ubuntuforums.org/showthread.php?p=5469447#post5469447]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")

You also need tablet entries for your xorg.conf, located in /etc/X11/.  I'll include a TX2500 sample xorg.conf so you can see what I mean.  Even with the wacom kernel module installed the stylus etc. won't work without these entries in xorg.conf.

Unfortunately ATI's proprietary driver "fglrx" does not support rotation.  You'll need to switch to Xorg's "radeon" driver if you are using it.  Deactivate in System>Administration>Hardware Drivers.  Be careful, some people say that it destabilized their laptop.  Maybe already have the "radeon" video section from the sample xorg.conf installed before deactivating.  That way you can restart X with
<ctrl><alt><backspace>.

Then to go on to rotation, see:

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

Don't worry if it seems complicated.  If you take it one step at a time it really isn't hard.

---

### Post by tkb123 on 2008-12-25
Thanks Favux,

I will start with your instructions now. Merry Christmas!

I also had to turn my key repeat off, I never noticed how much I use that (usually with the backspace key). The delay before it starts repeating is too short even when it is set to the longest. I tried setting it at the command line too, but that gave the same range as the control panel.

I'm still struggling with forums too, as well as entering tags, I don't see the thanks button that was there yesterday. I guess I should look for another thread for that.

---

### Post by tkb123 on 2008-12-25
Thank you gali98 & Favux

A couple of things I think would be useful to add for anyone following these instructions (although they may be covered in other posts; I'm still struggling navigating this thread...

References to 0.8.1-6 should be changed to 0.8.2 for the latest version (as Favux told me)

The main instructions for activating the touchscreen and pen is at:
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447) (as Favux told me)

An addendum that is also needed is in the same thread at:
[http://ubuntuforums.org/showthread.php?p=5478097#post5478097](http://ubuntuforums.org/showthread.php?p=5478097#post5478097)

In the addendum,

Before you do the command
>./configure --enable-wacom
change the path to where you were in that step:
>add> cd ~/Desktop/linuxwacom-0.8.1-6

If you are on Intrepid, replace 2.6.24 with 2.6.27 in this line:
>sudo cp ./src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet

Also of note (or maybe just ridiculous):
At the command:
>sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev
You get the message: 
  48.2MB of additional disk space will be used.
  Do you want to continue [Y/n]?
I tried  y  Y  n  and yes, but it kept saying abort afterwards.
When I started everything over, the capital Y worked.... (and, of course, subsequent commands worked much better)  

For extreme Linux newbies like me, I could also clarify:
when you do 
> uname -r
You will see either the word 'generic', or (what I assume to be) 'rt'
You then always use the commands that end with -generic and not the ones that end with -rt when given a choice in the instructions.

This got my pen working. I'm excited. Now I'm getting to the fun part, editing configuration files!
:guitar:

---

### Post by tkb123 on 2008-12-25
tx2500 keyboard problem

I have what I consider an abnormality, that I am surprised I have not seen any mention of on-line....

After working for a day or two, My keyboard went completely non-functional. (all the special buttons around the monitor, and the volume controls, still worked)

I looked up HP support when my keyboard stopped working in Vista, I ended up with a support chat person who took me through a series of steps, including removing all the keyboard drivers and letting them re-install. The steps she took me through didn't even include a reboot, yet she concluded that I had a hardware failure and directed me on how to return the laptop.

Undaughnted, I tried a few more idea's I had, and found that if the laptop was in slate position around the time the bios startup is complete and the OS takes control, the keyboard stopped working. This occurred even if the monitor wasn't all the way clicked down, but as long as it was within a few inches of it and in the position to be used as a tablet.

Once this happened, no mater what I did (rebooting, off/on, etc), I could not get it to work again (hence my call to HP Support).

What I found to make it work again was to unplug the Laptop  AND  Remove the Battery. 

Once this was done I could get into the BIOS, but found that nothing in there was helpful. I did try the option to reset the BIOS, but that didn't change anything. Again everything works fine now as long as I don't turn it on (or take it out of hibernation) while it is positioned in tablet position.

I still did not want to return it right away... I wanted to try Ubuntu.

I planned to install Ubuntu anyway. 

The same thing happens using Ubuntu, so it looks like it is a hardware problem, although a weird one.

Has no one else experienced this?
:confused:

---

### Post by Favux on 2008-12-25
Hi tkb123,

Glad to see you have Wacom working!  Good info./corrections to the tutorial.  Unforturnately gali98 hasn't posted in about 6 weeks.  So there's nobody to look at them and maybe update the tutorial.  Hopefully he'll be back after the holidays.

Sorry about the keyboard thing.  I've never heard of it.  Could it maybe be a loose connector?  I guess you can't check because it would probably void warranty.

---

### Post by tkb123 on 2008-12-25
Thanks Favux,

It could be a connector, I was wondering if it might even be firmware, it is just so consistent for a connector problem, but I'm still in agreement it is most likely a connection. Something that still baffles me is, if a wire is not connected when pulled that far, the system may not see the keyboard and never set it up; but then why doesn't it work when I turn it off and on? Why do I have to remove the battery and ac power to convince the system it should be used again?

I'm not sure what I want to do about it, I have the next two weeks off work, so I hate to send it back and not be able to play. My current thought is I really want to tinker with the Ubuntu install and try to get it configured well by January so when I have to regulate my time to accommodate 40 hours at work each week again I have a good start at understanding the OS. I'm a tweaker, I'll spend hours at work to automate a one hour job so next time it will go faster, then next time I'll spend more time to make it even easier.... I'm sure I'll never stop messing with this OS (unless something wins me over to another distro) I tried Fedora many years ago, I didn't last half a year with that one. Linux has obviously come a long way since then.

So I'm thinking I can image the drive in January and send the laptop back then. They say the turn around is about a week. I haven't asked when I need to send it back by (30 days? 90 days?). I guess I need to do that soon.

Do you (or anyone) know about a good drive imager, and what they are capable of? I can take this to another forum (or research it on Google). But I've never noticed any mention of Linux and Windows in the same advertisement I've read in the past. The optimist in me says I can download a freeware imager, then image the Vista/Ubuntu/grub installation as one image to an external USB hard drive as one big file. And just image it back later in case HP feels they have to re-install the Vista OS (or replace the laptop instead of fixing it). 

If you can, could you put your monitor in the tablet position, except lift the monitor up just enough to get you fingers in there? does the keyboard then work? Mine doesn't, yet it does when I do that with the monitor swiveled to the normal laptop position (the monitor turns off about 2 inches from closed, but the keyboard still works).

---

### Post by Favux on 2008-12-25
Hi tkb123,

My monitor also goes off but keyboard works as I close it in normal laptop position.  The keyboard also works when screen swiveled into tablet position and resting on my flattened fingers.  Sorry, still sounds like a hardware issue.  Removing power probably justs allows clearing whatever buffer is getting messed up by the hardware glitch.

Bad time to have a glitch when you're trying to set up.  Temptation is to get it fixed so it doesn't mess up your set up.  But can you trust HP for 1 week, or if you're lucky, less turn around?

Backup or disk imager is something I haven't tackled yet.  You might want to look at:

[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

Good luck.

---

### Post by martinjochimsen on 2008-12-26
Hi

What/where or how can I work with the cpu-scaling?
I'm using Ibex on a HP tablet tx2590oe. The fan is working the whole time (not on 100% but still really noisey) even when nothing is going on.
It would be nice to have a more quite laptop!!!

Martin :-)

---

### Post by Favux on 2008-12-26
Hi martinjochimsen,

This thread probably has information you're looking for.  It's weird, I just ran into it today.  I'd think twice about using any of it though unless I was real sure.

[http://ubuntuforums.org/showthread.php?t=844754&highlight=puma]("http://ubuntuforums.org/showthread.php?t=844754&highlight=puma")

If you do, let me know how it goes.

---

### Post by tC_Crazy on 2008-12-26
martinjochimsen,
All I did was apt-get install powernowd. That automatically controls scaling. I also added the "CPU Scaling" panel gadget that comes with ubuntu. It lets you switch to a solid frequency: 600, 1200, 2400 (mhz/core), as well as switching modes: conservative, on-demand, performance. I find it to work very well, plus it lets you constantly monitor what frequency your cores are running at.

---

### Post by Docaltmed on 2008-12-26
Installed KDE and it works...sort of...

Everything has been working just fine in my ubuntu installation, with the small exception of synaptic just refusing to work from the gui. I have to start it from the terminal, and then it works fine.

So I decided to install kubuntu, because I like the aesthetics better. Everything went without a hitch except for two problems:

1. the screen rotation .sh will rotate the screen, but then I get a double-taskbar at the top of the screen. This stays until I logout an log back in again.

2. Xournal, my favorite tablet program, won't work! It works fine in gnome, but when I run it under kde, it just dies. Here's the error message when I run it from the terminal:

```
avery@arran:~$ xournal
QApplication: Invalid Display* argument

(xournal:32758): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xournal:32758): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
The program 'xournal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 781 error_code 9 request_code 14 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Anybody have any suggestions?

---

### Post by mememe on 2008-12-27
**tkb123:** The problem with keyboard happened to me once when I switched on the laptop in tablet position. I was absolutely desperate - I tried to reboot many times but nothing happened. Then I switched on the laptop in that tablet position again and when Ubuntu asked me for login I switched it back to the "normal notebook" position and KEYBOARD STARTED WORKING!
Then I read also on some windows forums that it is known problem with this laptop and that they don't recommend booting it in different than the normal position...
I hope that it can be helpful for you...

**Everyone:** Has anyone got the microphone working to state when you can recognize a voice? I got mine working but quality is just terrible and it can't be used for anything.

---

### Post by martinjochimsen on 2008-12-27
Hi tC_Crazy

It seemed that I already had powernowd installed but it wasn't added in /etc/modules. It is now! I think I maybe can feel/hear a little difference now, but it's not much. I have also now added the small CPU Scaling gadget, but I don't think I'm managing it right. I feel now change when I change the mhz or the different modes.
Do you still have Vista on your laptop? When I'm in Vista my laptop is almost completely silent - that would be nice in Ubuntu.

Hi Favux

I looked at the other tread where Trebaruna in post 3 is talking about changing a number indicating the cpufamily, but I don't have the loadcpufreq in /etc/init.d/ (or any other place). Do you have an idea what file it could be in Ibex?

Martin

---

### Post by Favux on 2008-12-27
Hi martinjochimsen,

When I use "cat /proc/cpuinfo | grep family" I get 15, so I'm in the included processors.  So I really didn't look into it much further.  But if you search Synaptic with "cpufreq"  there's a daemon, utilities, and some libraries.  Could that be what he's talking about?

---

### Post by tC_Crazy on 2008-12-27
When I'm running ubuntu, and it's in any mode except performance or manual 2.4ghz, I get it to run as quiet as vista. I believe powernowd is dependent on cpufreq. Also, make sure that it runs on startup. I always know it does because it freezes on boot 1/3 of be time... But that's another story.

---

### Post by antroid on 2008-12-28
i did some research on these forums and found a lot information on running ubuntu on this model (it seems to be a very exotic one), unfortunately, i lost the information due to several system resets.

you may blame me for these questions: ;D
-> ive read about the failing pressure detection. in gimp, using the 3rd axis of wacom, i dont get anything drawn. on desktop moving icons works. is there already a definitive solution for the problem? 
-> ive seen a screen rotation script somewhere around, which changes to the ATI driver on normal rotation, could you please leave me the link to it? would it work with a dual head configuration also?
-> like some posts above: has anyone got the microfone working? it seems mono-connected and crackles when i poke it, but otherwise it doesnt work.

:guitar: on! :D

---

### Post by Favux on 2008-12-28
Hi antroid,

Rotation and pressure and pressure in Gimp is discussed here:

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

After the rotation HOW TO just read a little way into the thread to get Gimp pressure etc.  I don't know about dual head rotation.  You may be the first to try, so keep us posted.

I don't think anyone has the microphone working well, but I could be wrong.

---

### Post by antroid on 2008-12-28
thanks, thats what i looked for. it doesnt seem as it reacts to change to tablet mode... or does it?

when i have my dual head +rotation configuration done ill sure post it with explanations and graphics. its going to be a lot work for me. :)

---

### Post by martinjochimsen on 2008-12-28
You are right Favux.
I installed cpufreq and I then got the loadcpufreq-file in /etc/init.d.
My cpu-family is 17 so I also changed that in loadcpufreq. Only thing is that I had to uninstall powernowd to get cpufreq.
I have also added powernow-k8 to /etc/modules ....but I'm not sure that will work, now that I have uninstalled powernowd?!?
I'll just have to wait and see if it has any effect.

Martin :-)

---

### Post by martinjochimsen on 2008-12-28
The only thing that has changed is that the cpu-widget shows 100% the whole time now and the fan is making a lot of noise. I then tried to remove cpufreq but Synaptic also wants to remove ubuntu-desktop. When I try to install powernowd it also wants to remove ubuntu-desktop. How can I remove cpufreq without removing ubuntu-desktop?

Martin

---

### Post by martinjochimsen on 2008-12-28
I managed to remove cpufreq and reinstall powernowd.
I added powernow-k8 to /etc/modules
my cpu-family is 17
```
martin@martin-laptop:~$ cat /proc/cpuinfo | grep family
cpu family	: 17
cpu family	: 17
```
so I changed the value for K8 in /etc/init.d/loadcpufreq.
The important part in loadcpufreq looks like this now:

.
.
.
```
 # Hurrah. This is nice and easy.
            case $CPU_FAMILY in
                5)
                    # K6
                    MODULE=powernow-k6
                    ;;
                6)
                    # K7
                    MODULE=powernow-k7
                    ;;
                17)
                    K8
                    MODULE=powernow-k8
                    ;;
            esac
```

Am I right to remove the "#" infront of the K8?

before:
17)
                    # K8
                    MODULE=powernow-k8

now:
17)
                    K8
                    MODULE=powernow-k8

I've just been away from the computer for an hour, and when I came back it clearly was more silent - maybe it works?

to tC_Crazy
I have set the cpu-gadget to powersave (500 mhz). Is it supposed to chance to another level when more power is required?
The laptop has got 2 cpu's. Is the mode individual for the cpu's or is the mode automatically set for both cpu's?

---

### Post by Docaltmed on 2008-12-29
I hate to drag this thread back into the stylus/touch doldrums, but I've gone and messed things up again.

I did a clean reinstallation, this time of kubuntu. And while I was able to get stylus and touch working previously, now I'm getting stalled. Specifically, at the "make" command, things start to fall apart.

I've attached a file of my terminal, and I'm hoping that one of you can help me out. I really have only a vague sense of what these commands are doing and what the responses mean.

Thanks a lot.

---

### Post by tC_Crazy on 2008-12-29
martinjochimsen,
If you set it to one of the static levels (denoted by it's frequency in MHz or GHz), it will stay there all the time. The modes, like conservative, ondemand, etc., however, will automatically change levels as more power is needed. They just react differently (performance will tend to increase clock speed for more simple tasks than powersave, for instance). 

As far as powernow-k8 goes, I never had to mess with the module settings. I have the ZM-86 processor (2.4GHz dual-core). Not sure if that's relevant.

Docaltmed,
Try sudo make. I have to run nearly every command as root when compiling the wacom driver or it gives me annoying errors. I also had to re-download the tar once because wacom.ko would never appear when unzipped. And every update breaks it =p

---

### Post by tuxStyle on 2009-01-06
Hi.

I have a tx2524ca and i tried to use lm_sensors but sensors-detect doesn't detect anything. How can i monitor CPU temperature?

Also, i want to use conky.
Anyone have a config/script for temperature monitor?

Thank you.

---

### Post by kjamo36 on 2009-01-19
My fellow linux brothers, i need some serious help getting my stylus and touch working. i follow the first 6 steps where it ends with

[B]
" You will now need to restart !!!. This is necessary on Intrepid!

Okay that installed it, but now we need to configure our xserver...." 
[/B]

 its says if it doesn't kick in restart it again but i've restarted like 8x with no luck. I've been going at the for a few months and i really dont wanna go back to windows but i cant stay with this OS if i cant get the touch/stylus working. I got aim, skype, yahoo, and msn.

---

### Post by martinjochimsen on 2009-01-19
Hi Kjamo36

I don't know which guide you have been following, but Favux' guide (gali's guide updated), worked for me just yesterday.....but I have done it before and I did some tricks also! :-)
It also never worked for me with the restarts (10 times or so), so this time (yesterday) I did something else. I used the Favux_TX2500_xorg.conf from Favux' guide ([http://ubuntuforums.org/showthread.php?p=6559068#post6559068](http://ubuntuforums.org/showthread.php?p=6559068#post6559068)) and then I also added "wacom" to /etc/modules.

I didn't continue with the guide from where you stopped and I didnt open the xintrc file or anything else.

Well I knew it would work, because as I said I have done it before and the xorg.conf is from my laptop (tx2590oe).

Do you know how to replace the xorg.conf and add the module "wacom"?
Just remember to do a backup of your original xorg.conf.

Martin

---

### Post by mdb17 on 2009-01-27
Hey i am sorry if there is a better place to ask this but i have a tx 2500 and i can not get my speakers to work. i get very low sound out of my headphone jacks but nothing out of my speakers.
Can you please help me?

EDIT: I forgot to say i am running Ubuntu 8.10 64 bit

---

### Post by Favux on 2009-01-27
Hi mdb17,

gali98 found the fix for you.  See the second post here:

[http://ubuntuforums.org/showthread.php?t=972552&highlight=sound]("http://ubuntuforums.org/showthread.php?t=972552&highlight=sound")

So in a terminal type:  
```
sudo gedit /etc/modprobe.d/alsa-base
```
And then add at the bottom:
```
options snd-hda-intel index=0 model=toshiba position_fix=1
```
Why this works I do not know.  I just know it does!

Also be sure to right click on the sound icon (upper right corner) and turn up the sliders including (PCM)

Hope this helps.

---

### Post by mdb17 on 2009-01-28
ok thank you so much

---

### Post by mdb17 on 2009-01-28
ok i tried that but it didnt work. i am still having the same problem

---

### Post by Favux on 2009-01-28
Hi mdb17,

Did you restart?  Did you turn up the volume sliders?  You're sure you have a TX2500?  What's your model number?

Gali98 may have even posted the fix on this thread, maybe with more info., maybe more than once.  It would have been sometime between September to December.  Probably October or November.  Quite a few posts to go through though.

---

### Post by mdb17 on 2009-01-28
hey thank you for the quick response and yes i did all those things but i didnt copy and paste the last letter but as soon as i did it worked great,
thank you for all the help.

---

### Post by mdb17 on 2009-01-28
i have another question, the volume buttons on the top of my keyboard will bring up the on screen volume meter but it doesnt actuall change the volume what can i do to fix that?

---

### Post by tC_Crazy on 2009-01-28
Going along with the sound questions, has anyone made any progress with the internal mic (or even an external one plugged into the mic jack)? I really want to use skype, but not waste money on a USB microphone. Chances are, I would get one that wouldn't work with Linux, anyway.

---

### Post by Favux on 2009-01-28
Hi mbd17,

They work fine on my TX2000.  Let me ask you a question, does the DVD key on the bezel work for you?

Hi tC_Crazy,

I'm not sure.  I'll have to think about it.  I may have seen someone saying they got it working after doing a bunch of Alsa files changes.  I may have seen someone say don't bother, quality is terrible.  I just don't remember right now.

---

### Post by mdb17 on 2009-01-28
the play pause buttons work and i haven't tried the dvd one. the buttons respond and when you press then the master volume pops up and will go up and down and mute it just doesn't actually make any changes to actual sound levels.

---

### Post by Favux on 2009-01-28
Hi mdb17,

Try the DVD key.  It probably works too if play/pause does.  I don't know what to tell you.  Like I said mine work.

---

### Post by mdb17 on 2009-01-28
no the dvd key doesnt work. oh well its not a big deal. has anyone coame up with a soulution for the mic yet?

---

### Post by Favux on 2009-01-28
Hi mdb17,

At the bottom of this HOW TO is the Key code Addendum.  It has gali98's fix for the DVD key and gets the play/pause key to give a key code so we can bind it for rotation.  We call it the "Q" key.  I don't know if it will help your volume keys or not.

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

I do not understand the fix, and it sounds like it will break your play/pause button.  Mine didn't work before using the "fix", so it didn't matter to me.  Since I don't understand it I don't know how to reverse it.  So think about it before you decide to use it.

---

### Post by mdb17 on 2009-01-28
thank you for your help. i think i would rather have play pause then the volume

---

### Post by findelmundo on 2009-01-28
Hi.
I'm considering to buy a used HP tx2590 (AMD Turion™ X2), and install Ubuntu8.10(64bit). Can anyone tell me if it's just lots of trouble, or if it will be fairly easy to make things work?

---

### Post by mememe on 2009-01-28
**mdb17** - Do your volume buttons really control Master Volume? Check it in System -> Preferences -> Sound. In the list in the bottom of the sound config window should be chosen 'Master'. This silly thing happened to me once when I was trying to get mic working...

**Everybody** - I just noticed that [THIS]("http://ubuntuforums.org/showthread.php?p=5991798#post5991798") post is talking about getting front mic working... Was that guy only one successful?

---

### Post by Favux on 2009-01-28
Great spot mememe!

Unless I'm confabulating, I think I saw one other post, where like I said, the guy went through a bunch more elaborate Alsa stuff.  Maybe backporting Jaunty files?

---

### Post by mememe on 2009-01-29
**Favux** - Ok, I got microphone working. I installed newest version of alsa-driver, alsa-firmware etc. (everything in the folder) from [HERE]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/"),  restarted Ubuntu, set all Audio preferences to 'OSS - Open Sound System' and then I played with *alsamixer*.
I tested it in *Sound Recorder* and it works well with different alsamixer settings. *Skype* wants little bit more playing with settings in *alsamixer* and perfect is probably:
Capture - 55
Digital - 50
Internal Mic - 100
Volume is still pretty low but sound is clear and I hope this is step forward.

**findelmundo** - I have tx2510us which should have same specifications as yours and I think that it is pretty easy now to get things to work. I just reinstalled Ubuntu 8.10 few days ago and next day everything was working. Except microphone - it is working now, finally.

**Everybody** - I tried Jaunty alpha3 few days ago and I found out that it is too early to try. fglrx isn't ready for xserver 1.6 yet, other drivers (ati, radeonhd) are not perfect either because whole screen is flickering and I really suffered for exapmle during scroll in Firefox. I hope that ATI will release new fglrx soon.
EDIT 10min later: ATI just released new fglrx... :D

---

### Post by tC_Crazy on 2009-01-29
LOL. I just switched to radeonhd the other day because i wanted to try rotation (wanted to run OneNote through virtualbox... had problems with rotation not syncing with virtual Windows). Does the new fglrx support rotation? I'm going to try the mic thing right now and I'll let you guys know how it goes.

btw mememe, any advantages to using Jaunty yet?

---

### Post by Favux on 2009-01-29
Hi mememe,

Alright!  Kewl.  So I wasn't confabulating.

Pretty much everything works.  Are you guys as eager as I am to upgrade to Jaunty in a few months?  And break a bunch of stuff?  Lol.

---

### Post by mememe on 2009-01-29
**tC_Crazy** - I have no problem with rotation on present (previous) fglrx 8.12 using [Favux's 360 script]("http://ubuntuforums.org/showthread.php?p=6331527") (thanks Favux) and allowed xrandr in xorg.conf. 

I haven't tried the newest fglrx yet because I'm not able to download it from [ati website]("http://ati.amd.com/support/drivers/linux/linux-radeon.html"). 
Is anyone experiencing the same problem?

**Favux** - Hi! Yeah, you weren't and it made me to try the newest release. It seems like last completed thing (before breaking everything in Jaunty again, off course lol).

Only noticable advantage of Jaunty seemed to me new ext4, I couldn't enjoy much more though because of graphic problems. I hope it is fixed with today's fglrx!

---

### Post by Favux on 2009-01-29
Hi mememe,

Are you saying "fglrx" 8.12 (comes with Catalyst 8.12) supports rotation and Compiz?  I couldn't find anything on the ATI site saying they had finally introduced rotation in 8.12.  What's the new one called Catalyst 8.13 ("fglrx" 8.13)?

---

### Post by mememe on 2009-01-29
Hi Favux!

Rotation works for me since Catalyst 8.12 (fglrx 8.561) but I can either rotate screen or use Compiz (rotation with Compiz is messed up) - I don't use Compiz anymore so I forgot about it. Maybe it is problem of Compiz because when I switch Compiz off (without restarting xserver, just switching off) rotation works fine.
I have still driver 'fglrx' in xorg.conf so I think that I am using it whole time...

I finally installed the new version of Catalyst and this (rotation x compix) is same as on the older one. The new one is Catalyst 9.1 (month of release) - fglrx 8.572.

Have you tried the microphone?

---

### Post by Favux on 2009-01-29
Thanks mememe, that's the information I was looking for!  I think it's the driver, I don't have any problem rotating with Compiz with the nVidia driver.

No, I haven't tried the microphone.  I'm feeling too lazy tonight to do the updates you suggested.  I'm watching the boob tube.

---

### Post by tC_Crazy on 2009-01-29
Well, the mic worked... but the ALSA updates broke Skype. I get the following error when running Skype from the terminal:
```
ALSA lib pcm_dmix.c:975:(snd_pcm_dmix_open) unable to create IPC semaphore
skype: relocation error: skype: symbol snd_pcm_hw_params_get_channels_min, version ALSA_0.9.0rc4 not defined in file libasound.so.2 with link time reference
```

And, interestingly, just this when running sudo skype:
```
skype: relocation error: skype: symbol snd_pcm_hw_params_get_channels_min, version ALSA_0.9.0rc4 not defined in file libasound.so.2 with link time reference
```

Not sure where to go from here

---

### Post by tC_Crazy on 2009-01-29
OK, I fixed it. I reinstalled libasound2 in synaptic, which subsequently broke alsa. Then I recompiled/reinstalled alsa-lib (the newest snapshot) and set up alsamixer again. Everything works. An added bonus? The new fglrx driver finally stopped compiz flickering on video! This is on skype, as well as youtube (i already had vlc set up for x11 output so it didn't flicker). Can't remember if YouTube flickered or not before, but skype definitely did. Thank you, AMD!

---

### Post by tC_Crazy on 2009-01-31
Has anyone done the recent kernel upgrade to  2.6.27-11? If so, does it break anything (besides Wacom, which you have to rebuild every update)?

---

### Post by mememe on 2009-02-01
Yes, I have without any problems. It didn't break anything (besides that wacom).

I am experiencing another (1st for me) problem with the new alsa drivers. It broke the alacarte (menu editor)... Terminal says this:

```
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gtk.glade, gmenu, gobject, gio, gnome.ui
  File "/var/lib/python-support/python2.5/gtk-2.0/gnome/__init__.py", line 13, in <module>
    from _gnome import *
ImportError: /usr/lib/libesd.so.0: symbol snd_pcm_hw_params_set_rate_near, version ALSA_0.9.0rc4 not defined
``` in file libasound.so.2 with link time reference
Anyone has the same problem?

btw - good to hear that flickering is gone!

---

### Post by AxelK on 2009-02-01
Hello everyone,

i finally got most of my **tx2650eg** working thanks to this thread.

my **current OS**:
8.10 Intrepid Ibex
Linux 2.6.27-11-generic x86_64 GNU/Linux

**audio:**

added this to /etc/modprobe.d/alsa-bas :
```
options snd-hda-intel index=0 model=toshiba position_fix=1
```

sound works properly and even the mic works ootB i just have to switch between mic and front mic in Mixer->options(tab)->input source

**hibernate:** ootB

**suspend: **
this worked for me: [http://ubuntuforums.org/showpost.php?p=5220536&postcount=19](http://ubuntuforums.org/showpost.php?p=5220536&postcount=19)
without this the keyboard doesn't wake up

**wacom:**
installed it with gali's tutorial: [http://ubuntuforums.org/showpost.php?p=5469447&postcount=5](http://ubuntuforums.org/showpost.php?p=5469447&postcount=5)
but installed linuxwacom-0.8.2-2.
on the upgrade from 2.6.27-9 to 2.6.27-11 i made myself a little script for the installation(attached)
i encountered a little problem but just now i found the reason:
i could't find my wacom with
```
dmesg | grep wacom 
```
now i retried it for this post and i found out i just have to write Wacom with a capital letter.
[SIZE="1"](still my eraser tip isn't working, tried it in cellwriter, xournal and gimp. i've attached my xorg.conf so if anyone knows how i can fix this please let me know.)[/SIZE]
[COLOR="Lime"]Now working thanks to Favux. i just had to comment out the coordinates in the eraser section.[/COLOR] so actually it should have worked before as i added these lines on my own to get the eraser working. now it turns out that the eraser just doesn't behave as intuitively as in vista( gimp see's it just as another pen with wich you can select a second tool in the toolbar)
the remaining problem is that i wanted to simulate right clicks by holding down the tip with mousetweaks but that doesn't really work (in fact it just alters my mousepointer to a strange symbol so i deactivated it) 

**login in tablet mode:**
added this to my /etc/gdm/Init/Default just before exit 0:
```
cellwriter --dock-window=2 --keyboard-only --read-only &
```
i also had to disable the nice looking graphical login screen to make this work. is there a more elegant way for this now as the tutorial i followed was already a year old.
the next problem is to enter the password in the unlock dialog. the cellwriter manpage says something about this. i'll try it out and post my results.
for the sudo dialogs i had to make them normal windows in the assistive technologies dialog. is this a great problem with the security/is there a better way to do this?

**fingerprint reader**: ootB with fprint-demo but i'm using a real password anyway

**webcam**: works with cheese and ekiga, weird thing is that it also shows up in xsane but it doesn't work there

**remote control**: ootB
some keys send special media control events, others simple hotkey kombinations.

**wireless lan**: ootB: activated the proprietary driver and network-manager applet did the rest.
i have: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

**rotation**: i use the radion driver as rotation requires it.
i have a rotation script wich allows me to rotate in 90° steps.
(attached)
what i'm missing most is a way to turn the screen accordingly to the display state (open or folded) automatically like in vista. but it doesn't send any events when i fold it with xev. 

**buttons**: did't really try them but sound and media buttons work

**cpu & fan:** i don't know much about this topics, here's what i have found out:
the gnome applett shows me the current clock settings and lets me configure it
i can't get any temperatures. not with /proc/acpi/thermal_zone and not with lm-sensors.
```
cat /proc/acpi/processor/CPU0/throttling
```
this tells me that my cpu is running at 100% even the gnome-applet shows it at 600Mhz. which one's right?

my second information source beside this post was:
[http://www.pietrobattiston.it/wiki/doku.php?id=intrepid_on_hp_pavilion_tx2500](http://www.pietrobattiston.it/wiki/doku.php?id=intrepid_on_hp_pavilion_tx2500)

that's all for now and thank you all for this thread

axel

---

### Post by Favux on 2009-02-01
Hi AxelK,

In your xorg.conf try commenting out ("#") the "TopX" to "BottomY" lines in the eraser section.  Then restart X; <ctrl><alt><backspace>.  See if that helps.

Oh, and in Xournal, the side-switch is the eraser.

---

### Post by Dual Cortex on 2009-02-01
[Disregard]

---

### Post by psycho on 2009-02-03
[quote=tC_Crazy]The new fglrx driver finally stopped compiz flickering on video![/quote]

yes...but only if you're not using screen rotation, it seems.

the new fglrx supports xrandr screen rotation (which we need, of course, for our tx2500's) as soon as you```
sudo aticonfig --set-pcs-str="DDX,EnableRandR12,TRUE"
```to configure the settings database in /etc/amdpcsdb (or you can edit it manually).

unfortunately, on my tablet at least, this same setting re-introduces the compositing+3d=flickering problem. EnableRandR12=TRUE=flickering 3d but rotation. EnableRandR12=FALSE=steady 3d but NO rotation. i haven't found a way to have both work simultaneously.

despite this i've decided to stick with fglrx (i've been using radeon) for a while as the colour is so much better (radeon produces hicolor banding for some reason) and the flickering video can mostly be worked around (if you use mplayer) by setting the video output driver to unaccelerated "x11" video (i.e. ```
vo = x11
```in your .mplayer/config, or without the spaces on the command line). with xfce you can also very quickly disable compositing by attaching a button or key combination or whatever to a script with```
killall xfwm4 && xfwm4 --compositor=off &
```(and bring it back via compositor=on) so i can keep the rotation and compositing happening, and for now i can live with working around the flicker.

if anyone has figured out a way to wrestle screen rotation AND non-flickering compositing / accelerated video out of the new fglrx driver, i'd love to hear from them.

:)

---

### Post by Qjet on 2009-02-10
Hey um some people have being posting that their audio keys arn't actually changing the sound of anything. Well I think i know why that is. See I did a little looking around through all the volume sliders for all the devices for audio

It seems, at least for me, that my audio keys are connected to the "Capture: ALSA PCM on front:0 (ALC268 Analog) via dma (Pulse Audio)"
device.

I'm not sure why exactly or how that happened. I'm wondering how I go about changing that.

edit: oh wait there's a dialog box just above it.

*sigh* never mind... that was too easy...

---

### Post by roberta_aguilles on 2009-02-23
Hi, thanks all for the info here which really helps me to get started with my brand new tx2522au.

I have a question related to power management. While on battery, the cpu speed is limited to 1100Mhz no matter what (my cpu variation is 500Mhz, 1100Mhz, and 2100Mhz). I have tried to set the governor to performance, or to the frequency manually to 2100Mhz (using the userspace driver), the end result is still the same - 1100Mhz is the max. 

Anybody has a clue? While on ac power - I can get to the max, no problem. (This is a new laptop so no problem with dirty fans etc), and I'm quite sure it's not a hardware/BIOS limitation because I have another distro installed in it (puppy linux) and it happily chugs alon to 2100Mhz if I ask it to.

Not that I don't appreciate Ubuntu's power management to save my battery, but there are times that I need to run at fullspeed regardless of whether I'm on battery or on ac power.

Thank you !

---

### Post by isachan on 2009-03-11
For those who have sound problems, I found a good info how to get it work here :

[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

Sorry, I can't confirm at this as I'm still running 8.04. Also since my sound is fine, I don't want to mess my setting up.

Isao

---

### Post by deepbluedna on 2009-03-15
> **manu7irl said:**
> thanks for all but again the same :
cp: cannot stat `src/2.6.27/wacom.ko': No such file or directory
is there any solution?

Hi, I have a same problem here. here is what i got from the terminal. It seems like there is no file of wacom.ko in my kernal folder. 



 BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.27
  module versioning - no 
      kernel source - yes /lib/modules/2.6.27-11-generic/build
     XFree86 source - no 
           Xorg SDK - no 
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib64
         xf86config - no
                TCL - no 
                 TK - no 
            ncurses - no

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - no 
             xidump - yes (no ncurses)
        libwacomcfg - yes
         libwacomxi - no
          xsetwacom - yes
              hid.o - no 
         usbmouse.o - no
            evdev.o - no
         mousedev.o - no
            input.o - no
       wacom_drv.so - no /usr/lib64/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks -

---

### Post by deepbluedna on 2009-03-15
Here is the complete one.
Anyone can help me to figure out the "cp: cannot stat `src/2.6.27/wacom.ko': No such file or directory" problem? Thanks in advance

linuxwacom-0.8.1-6/config.guess
linuxwacom-0.8.1-6/Makefile.am
linuxwacom-0.8.1-6/docs/
linuxwacom-0.8.1-6/docs/docs_files/
linuxwacom-0.8.1-6/docs/docs_files/sflogo.png
linuxwacom-0.8.1-6/docs/docs_files/null.gif
linuxwacom-0.8.1-6/docs/docs.html
linuxwacom-0.8.1-6/autom4te.cache/
linuxwacom-0.8.1-6/autom4te.cache/output.1
linuxwacom-0.8.1-6/autom4te.cache/output.0
linuxwacom-0.8.1-6/autom4te.cache/traces.1
linuxwacom-0.8.1-6/autom4te.cache/traces.0
linuxwacom-0.8.1-6/autom4te.cache/requests
linuxwacom-0.8.1-6/ltmain.sh
linuxwacom-0.8.1-6/aclocal.m4
linuxwacom-0.8.1-6/GPL
linuxwacom-0.8.1-6/ChangeLog
linuxwacom-0.8.1-6/LGPL
linuxwacom-0.8.1-6/configure.in
linuxwacom-0.8.1-6/Makefile.in
linuxwacom-0.8.1-6/missing
linuxwacom-0.8.1-6/config.sub
linuxwacom-0.8.1-6/AUTHORS
linuxwacom-0.8.1-6/bootstrap
linuxwacom-0.8.1-6/NEWS
linuxwacom-0.8.1-6/configure
ming@ming-laptop:~/Desktop$ cd linuxwacom-0.8.1-6/
ming@ming-laptop:~/Desktop/linuxwacom-0.8.1-6$  ./configure --enable-wacom --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) mawk
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for arch type... x86_64-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.27-11-generic/build
checking kernel version... 2.6.27-11-generic
checking for kernel module support... yes
checking for Xlib... checking for X lib directory... found, /usr/lib64
checking for XSERVER... checking for valid Xorg SDK... "xf86Version.h missing"
Tried /usr/include, /usr/include/xorg, and /usr/xc/include
checking for lib xf86config... checking for X... no
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... configure: WARNING: not found; tried /usr/include, tcl, and tcl8.4; 
***
*** The tcl development environment can not be found.
*** The header file tcl.h does not appear at the normal
*** (or provided) include path. Some build features
*** will be unavailable.
***
checking for tk header files... configure: WARNING: not found; tried /tk.h and /usr/include/tk.h
***
*** The tk development environment can not be found.
*** The header file tk.h does not appear at the normal
*** (or provided) include path. Some build features
*** will be unavailable.
***
checking ncurses.h usability... no
checking ncurses.h presence... no
checking for ncurses.h... no
checking ncurses/ncurses.h usability... no
checking ncurses/ncurses.h presence... no
checking for ncurses/ncurses.h... no
configure: WARNING: ncurses not available, ncurses UI disabled
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... configure: WARNING: tcl environment missing, libwacomxi not built
checking if wacdump should/can be built... configure: WARNING: ncurses environment missing, wacdump not built
checking if xidump should/can be built... yes, no ncurses
checking if xsetwacom should be built... yes
checking for Wacom X driver module path... /usr/lib64/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... configure: WARNING: requires Xorg SDK or XFree86 build environment, wacom_drv not built
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.4/Makefile
config.status: creating src/2.4.22/Makefile
config.status: creating src/2.6.8/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/2.6.22/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.26/Makefile
config.status: creating src/2.6.27/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: creating src/include/kernel-config.h
config.status: creating src/include/util-config.h
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.27
  module versioning - no 
      kernel source - yes /lib/modules/2.6.27-11-generic/build
     XFree86 source - no 
           Xorg SDK - no 
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib64
         xf86config - no
                TCL - no 
                 TK - no 
            ncurses - no

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - no 
             xidump - yes (no ncurses)
        libwacomcfg - yes
         libwacomxi - no
          xsetwacom - yes
              hid.o - no 
         usbmouse.o - no
            evdev.o - no
         mousedev.o - no
            input.o - no
       wacom_drv.so - no /usr/lib64/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks -
----------------------------------------
ming@ming-laptop:~/Desktop/linuxwacom-0.8.1-6$ make
Making all in src
make[1]: Entering directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src'
Making all in .
make[2]: Entering directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src'
rm -f wacom.4x.gz
gzip -9c < ./wacom.4x > wacom.4x.gz
make[2]: Leaving directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src'
Making all in wacomxi
make[2]: Entering directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
Making all in util
make[2]: Entering directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src/util'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic  -g -O2 -D__amd64__ -MT wacomcfg.lo -MD -MP -MF ".deps/wacomcfg.Tpo" -c -o wacomcfg.lo wacomcfg.c; \
	then mv -f ".deps/wacomcfg.Tpo" ".deps/wacomcfg.Plo"; else rm -f ".deps/wacomcfg.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -pedantic -g -O2 -D__amd64__ -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o
In file included from wacomcfg.c:35:
wacomcfg.h:26:22: error: X11/Xlib.h: No such file or directory
wacomcfg.h:27:35: error: X11/extensions/XInput.h: No such file or directory
wacomcfg.h:28:36: error: X11/extensions/XIproto.h: No such file or directory
In file included from wacomcfg.c:35:
wacomcfg.h:58: error: expected specifier-qualifier-list before 'Display'
wacomcfg.h:62: warning: struct has no members
wacomcfg.h:67: error: expected specifier-qualifier-list before 'XDevice'
wacomcfg.h:75: error: expected ')' before '*' token
In file included from wacomcfg.c:38:
../include/Xwacom.h:23:24: error: X11/keysym.h: No such file or directory
wacomcfg.c: In function 'CfgError':
wacomcfg.c:71: error: 'WACOMCONFIG' has no member named 'pfnError'
wacomcfg.c:72: error: 'WACOMCONFIG' has no member named 'pfnError'
wacomcfg.c: In function 'CfgGetDevs':
wacomcfg.c:82: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:82: warning: implicit declaration of function 'XListInputDevices'
wacomcfg.c:82: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:83: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:85: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c: At top level:
wacomcfg.c:95: error: expected ')' before '*' token
wacomcfg.c: In function 'WacomConfigListDevices':
wacomcfg.c:135: error: 'XDeviceInfo' undeclared (first use in this function)
wacomcfg.c:135: error: (Each undeclared identifier is reported only once
wacomcfg.c:135: error: for each function it appears in.)
wacomcfg.c:135: error: 'info' undeclared (first use in this function)
wacomcfg.c:139: warning: ISO C90 forbids mixed declarations and code
wacomcfg.c:145: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:159: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:161: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:163: error: 'IsXExtensionDevice' undeclared (first use in this function)
wacomcfg.c:185: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:187: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c: In function 'WacomConfigOpenDevice':
wacomcfg.c:293: error: 'XDevice' undeclared (first use in this function)
wacomcfg.c:293: error: 'pDev' undeclared (first use in this function)
wacomcfg.c:294: error: 'XDeviceInfo' undeclared (first use in this function)
wacomcfg.c:294: error: 'pDevInfo' undeclared (first use in this function)
wacomcfg.c:294: error: 'info' undeclared (first use in this function)
wacomcfg.c:294: warning: left-hand operand of comma expression has no effect
wacomcfg.c:300: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:304: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:306: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:319: warning: implicit declaration of function 'XOpenDevice'
wacomcfg.c:319: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:331: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c: In function 'WacomConfigCloseDevice':
wacomcfg.c:340: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:341: warning: implicit declaration of function 'XFree'
wacomcfg.c:341: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c: In function 'WacomConfigSetRawParam':
wacomcfg.c:350: error: 'XDeviceResolutionControl' undeclared (first use in this function)
wacomcfg.c:350: error: expected ';' before 'c'
wacomcfg.c:351: error: 'XDeviceControl' undeclared (first use in this function)
wacomcfg.c:351: error: 'dc' undeclared (first use in this function)
wacomcfg.c:351: error: expected expression before ')' token
wacomcfg.c:351: error: 'c' undeclared (first use in this function)
wacomcfg.c:357: error: 'DEVICE_RESOLUTION' undeclared (first use in this function)
wacomcfg.c:363: warning: implicit declaration of function 'XChangeDeviceControl'
wacomcfg.c:363: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:363: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:368: error: 'BadValue' undeclared (first use in this function)
wacomcfg.c:368: error: 'BadRequest' undeclared (first use in this function)
wacomcfg.c:377: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:377: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:389: warning: implicit declaration of function 'XSetDeviceMode'
wacomcfg.c:389: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:389: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c: In function 'WacomConfigGetRawParam':
wacomcfg.c:397: error: 'XDeviceResolutionControl' undeclared (first use in this function)
wacomcfg.c:397: error: expected ';' before 'c'
wacomcfg.c:398: error: 'XDeviceResolutionState' undeclared (first use in this function)
wacomcfg.c:398: error: 'ds' undeclared (first use in this function)
wacomcfg.c:399: warning: ISO C90 forbids mixed declarations and code
wacomcfg.c:405: error: 'c' undeclared (first use in this function)
wacomcfg.c:405: error: 'DEVICE_RESOLUTION' undeclared (first use in this function)
wacomcfg.c:411: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:411: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:412: error: 'XDeviceControl' undeclared (first use in this function)
wacomcfg.c:412: error: expected expression before ')' token
wacomcfg.c:414: error: 'BadValue' undeclared (first use in this function)
wacomcfg.c:414: error: 'BadRequest' undeclared (first use in this function)
wacomcfg.c:420: error: expected expression before ')' token
wacomcfg.c:435: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:436: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:437: error: expected expression before ')' token
wacomcfg.c:445: error: expected expression before ')' token
wacomcfg.c:457: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:457: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:458: error: expected expression before ')' token
wacomcfg.c:460: warning: implicit declaration of function 'XFreeDeviceControl'
wacomcfg.c:460: error: expected expression before ')' token
make[2]: *** [wacomcfg.lo] Error 1
make[2]: Leaving directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src/util'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src'
make: *** [all-recursive] Error 1
ming@ming-laptop:~/Desktop/linuxwacom-0.8.1-6$ sudo make install
Making install in src
make[1]: Entering directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src'
Making install in .
make[2]: Entering directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src'
make[3]: Entering directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/man/man4" || mkdir -p -- "/usr/man/man4"
 /usr/bin/install -c -m 644 'wacom.4x.gz' '/usr/man/man4/wacom.4x.gz'
make[3]: Leaving directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src'
make[2]: Leaving directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src'
Making install in wacomxi
make[2]: Entering directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
make[3]: Entering directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
make[3]: Nothing to be done for `install-exec-am'.
test -z "" || mkdir -p -- ""
test -z "" || mkdir -p -- ""
test -z "" || mkdir -p -- ""
make[3]: Leaving directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
make[2]: Leaving directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src/wacomxi'
Making install in util
make[2]: Entering directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src/util'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic  -g -O2 -D__amd64__ -MT wacomcfg.lo -MD -MP -MF ".deps/wacomcfg.Tpo" -c -o wacomcfg.lo wacomcfg.c; \
	then mv -f ".deps/wacomcfg.Tpo" ".deps/wacomcfg.Plo"; else rm -f ".deps/wacomcfg.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -pedantic -g -O2 -D__amd64__ -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o
In file included from wacomcfg.c:35:
wacomcfg.h:26:22: error: X11/Xlib.h: No such file or directory
wacomcfg.h:27:35: error: X11/extensions/XInput.h: No such file or directory
wacomcfg.h:28:36: error: X11/extensions/XIproto.h: No such file or directory
In file included from wacomcfg.c:35:
wacomcfg.h:58: error: expected specifier-qualifier-list before 'Display'
wacomcfg.h:62: warning: struct has no members
wacomcfg.h:67: error: expected specifier-qualifier-list before 'XDevice'
wacomcfg.h:75: error: expected ')' before '*' token
In file included from wacomcfg.c:38:
../include/Xwacom.h:23:24: error: X11/keysym.h: No such file or directory
wacomcfg.c: In function 'CfgError':
wacomcfg.c:71: error: 'WACOMCONFIG' has no member named 'pfnError'
wacomcfg.c:72: error: 'WACOMCONFIG' has no member named 'pfnError'
wacomcfg.c: In function 'CfgGetDevs':
wacomcfg.c:82: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:82: warning: implicit declaration of function 'XListInputDevices'
wacomcfg.c:82: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:83: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:85: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c: At top level:
wacomcfg.c:95: error: expected ')' before '*' token
wacomcfg.c: In function 'WacomConfigListDevices':
wacomcfg.c:135: error: 'XDeviceInfo' undeclared (first use in this function)
wacomcfg.c:135: error: (Each undeclared identifier is reported only once
wacomcfg.c:135: error: for each function it appears in.)
wacomcfg.c:135: error: 'info' undeclared (first use in this function)
wacomcfg.c:139: warning: ISO C90 forbids mixed declarations and code
wacomcfg.c:145: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:159: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:161: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:163: error: 'IsXExtensionDevice' undeclared (first use in this function)
wacomcfg.c:185: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:187: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c: In function 'WacomConfigOpenDevice':
wacomcfg.c:293: error: 'XDevice' undeclared (first use in this function)
wacomcfg.c:293: error: 'pDev' undeclared (first use in this function)
wacomcfg.c:294: error: 'XDeviceInfo' undeclared (first use in this function)
wacomcfg.c:294: error: 'pDevInfo' undeclared (first use in this function)
wacomcfg.c:294: error: 'info' undeclared (first use in this function)
wacomcfg.c:294: warning: left-hand operand of comma expression has no effect
wacomcfg.c:300: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:304: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:306: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:319: warning: implicit declaration of function 'XOpenDevice'
wacomcfg.c:319: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:331: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c: In function 'WacomConfigCloseDevice':
wacomcfg.c:340: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:341: warning: implicit declaration of function 'XFree'
wacomcfg.c:341: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c: In function 'WacomConfigSetRawParam':
wacomcfg.c:350: error: 'XDeviceResolutionControl' undeclared (first use in this function)
wacomcfg.c:350: error: expected ';' before 'c'
wacomcfg.c:351: error: 'XDeviceControl' undeclared (first use in this function)
wacomcfg.c:351: error: 'dc' undeclared (first use in this function)
wacomcfg.c:351: error: expected expression before ')' token
wacomcfg.c:351: error: 'c' undeclared (first use in this function)
wacomcfg.c:357: error: 'DEVICE_RESOLUTION' undeclared (first use in this function)
wacomcfg.c:363: warning: implicit declaration of function 'XChangeDeviceControl'
wacomcfg.c:363: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:363: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:368: error: 'BadValue' undeclared (first use in this function)
wacomcfg.c:368: error: 'BadRequest' undeclared (first use in this function)
wacomcfg.c:377: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:377: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:389: warning: implicit declaration of function 'XSetDeviceMode'
wacomcfg.c:389: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:389: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c: In function 'WacomConfigGetRawParam':
wacomcfg.c:397: error: 'XDeviceResolutionControl' undeclared (first use in this function)
wacomcfg.c:397: error: expected ';' before 'c'
wacomcfg.c:398: error: 'XDeviceResolutionState' undeclared (first use in this function)
wacomcfg.c:398: error: 'ds' undeclared (first use in this function)
wacomcfg.c:399: warning: ISO C90 forbids mixed declarations and code
wacomcfg.c:405: error: 'c' undeclared (first use in this function)
wacomcfg.c:405: error: 'DEVICE_RESOLUTION' undeclared (first use in this function)
wacomcfg.c:411: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:411: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:412: error: 'XDeviceControl' undeclared (first use in this function)
wacomcfg.c:412: error: expected expression before ')' token
wacomcfg.c:414: error: 'BadValue' undeclared (first use in this function)
wacomcfg.c:414: error: 'BadRequest' undeclared (first use in this function)
wacomcfg.c:420: error: expected expression before ')' token
wacomcfg.c:435: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:436: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:437: error: expected expression before ')' token
wacomcfg.c:445: error: expected expression before ')' token
wacomcfg.c:457: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:457: error: 'WACOMDEVICE' has no member named 'pDev'
wacomcfg.c:458: error: expected expression before ')' token
wacomcfg.c:460: warning: implicit declaration of function 'XFreeDeviceControl'
wacomcfg.c:460: error: expected expression before ')' token
make[2]: *** [wacomcfg.lo] Error 1
make[2]: Leaving directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src/util'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/ming/Desktop/linuxwacom-0.8.1-6/src'
make: *** [install-recursive] Error 1
ming@ming-laptop:~/Desktop/linuxwacom-0.8.1-6$ sudo cp src/2.6.27/wacom.ko /lib/modules/2.6.27-7-generic/kernel/drivers/
cp: cannot stat `src/2.6.27/wacom.ko': No such file or directory
ming@ming-laptop:~/Desktop/linuxwacom-0.8.1-6$ 
ming@ming-laptop:~/Desktop/linuxwacom-0.8.1-6$

---

### Post by Favux on 2009-03-15
Hi deepbluedna,

Compare:
```
BUILD ENVIRONMENT: 
       architecture - x86_64-linux-gnu 
       linux kernel - yes 2.6.27 
  module versioning - no 
      kernel source - yes /lib/modules/2.6.27-11-generic/build 
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg 
          XSERVER64 - yes 
           dlloader - yes 
               XLib - yes /usr/lib 
         xf86config - no 
                TCL - yes /usr/include/tcl8.4 
                 TK - yes /usr/include/tcl8.4 
            ncurses - yes 

  BUILD OPTIONS: 
            wacom.o - yes 
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes 
         libwacomxi - yes 
          xsetwacom - yes 
              hid.o - no 
         usbmouse.o - no 
            evdev.o - no 
         mousedev.o - no 
            input.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no 
  wacom*_drv quirks - Uninit-called IsXExtensionPointer key-events dixScreenOrigins 

```
as it says:
```
*** The tcl development environment can not be found.
*** The header file tcl.h does not appear at the normal
*** (or provided) include path. Some build features
*** will be unavailable.
***
checking for tk header files... configure: WARNING: not found; tried /tk.h and /usr/include/tk.h
***
*** The tk development environment can not be found.
*** The header file tk.h does not appear at the normal
*** (or provided) include path. Some build features
*** will be unavailable.
```
the tcl and tk libraries missing.

See:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

Hope this is helpful.

---

### Post by deepbluedna on 2009-03-15
hi, i googled the "tcl" libraries in ubunbu packages, but it gave me a lot of different versions of tcl libraries, like "package tcl 8.5" "package tcl 8.4", im confused which one i should complie on my ubuntu?? thanks

---

### Post by deepbluedna on 2009-03-15
here is what I have now, but i still have that"cp: cannot stat `src/2.6.27/wacom.ko': No such file or directory" 


 BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.27
  module versioning - no 
      kernel source - yes /lib/modules/2.6.27-11-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl
                 TK - yes /usr/include/tcl
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
         usbmouse.o - no
            evdev.o - no
         mousedev.o - no
            input.o - no
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - Uninit-called IsXExtensionPointer key-events dixScreenOrigins

---

### Post by Favux on 2009-03-15
Hi deepbluedna,

I promise you that this is not as hard as it seems.  Somehow you are inadvertently making it seem difficult.  So just be patient.

You shouldn't need to worry about the tcl version (8.4).  It should be done for you automatically by the commands of the tutorial.  I guess I need more context.  You have a TX2500 correct?  It's on the plate on the bottom of your laptop.

Which tutorial if any are you following?  I suggest going to [http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012") as I linked above.

I would suggest starting over.  Go to your desktop (or wherever you downloaded the linuxwacom drivers and delete anything with linuxwacom in the name (i.e tar.gz files and folders ).  Close any terminals and start a new terminal.  The tutorial assumes you are doing everything as user on the user Desktop.  Copy and paste the commands into the terminal rather than type them.

It could be the problem is that the copy command:
```
sudo cp ./src/2.6.27/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
Is wrong for you because you are in a different directory.  You may need to alter the directory path for what you are doing.  Are you using KDE?  Also `uname -r` just returns the kernel name you are on.  So in the path it would read 2.6.27-11 or whatever.

Also please enclose your outputs in the [code][code] brackets from "#" at the top of the text box.  This makes things more readable.  You can also do this to your old posts by clicking on edit and then advanced edit.  Then highlight & cut the output, insert it between [code][code] and paste.

---

### Post by deepbluedna on 2009-03-16
> **Favux said:**
> Hi deepbluedna,

I promise you that this is not as hard as it seems.  Somehow you are inadvertently making it seem difficult.  So just be patient.

You shouldn't need to worry about the tcl version (8.4).  It should be done for you automatically by the commands of the tutorial.  I guess I need more context.  You have a TX2500 correct?  It's on the plate on the bottom of your laptop.

Which tutorial if any are you following?  I suggest going to [http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012") as I linked above.

I would suggest starting over.  Go to your desktop (or wherever you downloaded the linuxwacom drivers and delete anything with linuxwacom in the name (i.e tar.gz files and folders ).  Close any terminals and start a new terminal.  The tutorial assumes you are doing everything as user on the user Desktop.  Copy and paste the commands into the terminal rather than type them.

It could be the problem is that the copy command:
```
sudo cp ./src/2.6.27/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
Is wrong for you because you are in a different directory.  You may need to alter the directory path for what you are doing.  Are you using KDE?  Also `uname -r` just returns the kernel name you are on.  So in the path it would read 2.6.27-11 or whatever.

Also please enclose your outputs in the [code][code] brackets from "#" at the top of the text box.  This makes things more readable.  You can also do this to your old posts by clicking on edit and then advanced edit.  Then highlight & cut the output, insert it between [code][code] and paste.


Hi Favux, thanks for your advice. I repeated the whole precess and I figured the old problem. Yeah my laptop is Tx2500. There is a new problem comes out. When I tried to modify the "serverlayout" scripts, I found out that I don't have this serverlayout. Then i googled it and paste other people's serverlayout scripts in mine and the system cannot log in normally. Which is very frustrated. Do you have any idea where I can find the right severlayout file for my ubuntu? Thanks a lot.

---

### Post by Favux on 2009-03-16
Hi deepbluedna,

The link I posted above has a TX2500 xorg.conf and in it a "ServerLayout".  It should work with your TX2500.  It is at the bottom of the first post.  The link is:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

If you would like I can try to fix your xorg.conf "ServerLayout".  Please post a copy of your xorg.conf.

---

### Post by farmercyst on 2009-03-20
well i have spent about three hours trying to get the latest ati driver to rotate with the xrandr commands that i found in this thread [http://ubuntuforums.org/showthread.php?t=996830&highlight=intrepid+tx2500+screen+rotation](http://ubuntuforums.org/showthread.php?t=996830&highlight=intrepid+tx2500+screen+rotation)  
every time i would get this error. 
```
X Error of failed request: BadMatch (invalid parameter attributes)
Major opcode of failed request: 159 (RANDR)
Minor opcode of failed request: 2 (RRSetScreenConfig)
Serial number of failed request: 12
Current serial number in output stream: 12
```

the solution is on this page. [http://wiki.cchtml.com/index.php/Features#Screen_Rotation](http://wiki.cchtml.com/index.php/Features#Screen_Rotation)
after running the commands, rotation works great, rxcept with compiz. 
Hopefully this will help someone else out there trying to get their ati card to rotate.

and one more thing, THANKS Favux. without your help, setup would have been very painful!

---

### Post by Favux on 2009-03-20
Hi farmercyst,

You're welcome.

Do you think I should add:
```
aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE" 
```
to the HOW TO?

---

### Post by farmercyst on 2009-03-21
> **Favux said:**
> Hi farmercyst,

You're welcome.

Do you think I should add:
```
aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE" 
```
to the HOW TO?

i think it would help. that is one of the first threads i found when looking for help with rotation.

---

### Post by tannalv on 2009-03-29
Hi.

I am running the latest Jaunty on my tx2500z CTO. However, when I look in thermal_zone it is empty, like so:

$ ls /proc/acpi/thermal_zone/
$

Trying to load the thermal-module doesn't work, it's now compiled in to the kernel.

$ cat /boot/config-2.6.28-11-generic | grep -i therm
CONFIG_ACPI_THERMAL=y
CONFIG_THERMAL=y
CONFIG_THERMAL_HWMON=y
CONFIG_USB_CYTHERM=m
CONFIG_W1_SLAVE_THERM=m
$

So why is it I don't have anything in my /proc/acpi/thermal_zone/?
Any hints, ideas?

---

### Post by Favux on 2009-03-29
Hi tannalv,

The following may help answer your question as to why it seems like acpi is being deprecated.

From Bryce Harrington at [http://www2.bryceharrington.org:8080/drupal/node/63]("http://www2.bryceharrington.org:8080/drupal/node/63")
> Non-functioning hotkeys - A large chunk of time this month went into investigating hotkey issues, particularly around the sleep/battery keys. That involved into digging through 'acpi-support', which I'm wondering if we need to just drop and go with straight HAL/pmutils. There are a ton of outstanding patches from Debian that we don't have, and even with them I think it may redundant. It's too late in Intrepid to do much more than duct tape, but for Jaunty this is going to need a lot of focus.

Would another way to phrase your question be:  Why are they moving thermal support away from acpi to the kernel?  So it seems it has to do with the move to HAL (hardware abstraction layer)/dBUS & pmutils which will be supplanted by DeviceKit (which missed Jaunty but will be in Karmic, 9.10) which will be subsumed into udev-extras.  The time line I think goes something like this.  In April last year the lead HAL dev. (Red Hat/Fedora?) decided HAL was a dead end and then announced DeviceKit.  Then within the last month he announced the last version of DeviceKit and that it was going to become udev-extras.

Hope this helps fill some of it in.  I'm sure there's more involved I don't know about.

---

### Post by kg6gfq on 2009-03-31
> **tannalv said:**
> I am running the latest Jaunty on my tx2500z CTO. 

I'm trying Jaunty too, and having some difficulties with the wacom drivers.  Has anyone else got them working?  The version packaged ought to support our tablets, but...

```
$ dmesg | grep wacom
[   15.548681] wacom: probe of 7-2:1.0 failed with error -113
[   15.572879] usbcore: registered new interface driver wacom
[   15.573005] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
```

I've filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/350036](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/350036)

---

### Post by Favux on 2009-04-06
Hi Everyone, and kg6gfq, and tannalv,

Timo Aaltonen has new linuxwacom drivers for Jaunty in his PPA.  These drivers will hopefully offer the hotplug support through HAL/.fdi that Intrepid and Jaunty were meant to have.  If you are **interested in testing** Timo Aaltonen has pre-packaged the modified linuxwacom xserver-xorg-input-wacom 0.8.2-2 and wacom-tools 0.8.2-2 for you on his ppa (3-24-09).   Note this includes a modified 10-wacom.fdi file:

[https://launchpad.net/~tjaalton/+archive/ppa](https://launchpad.net/~tjaalton/+archive/ppa)

Then click on:  wacom-tools - 1:08.2.2-OubuntuO.2

Update(4-9-09): Above link is now invalid. Timo's ppa has been accepted already. It's in the repositories. Either check Synaptics in Jaunty or go to: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and select Jaunty. Then X Window System software. It's listed as xserver-xorg-input-wacom.

You will see the i386 and amd64 debs.  Use them to upgrade from the 0.8.1-6 versions that come with Jaunty.  Since the patches support hotplugging through HAL you should not need to configure your xorg.conf.  I'm assuming you can calibrate through wacomcpl.  You will have to re-enable each tool with Gimp, etc.  This should work for hotplugging usb Wacom tablets and usb tablet pc's.  And the updates should also provide HAL/.fdi support  for serial tablets and serial tablet pc's!

**If you are testing** it is important for you to give feed back to this lauchpad site **[FFe] Please allow a new version of wacom-tools** posted (4-4-09):
 
[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340)

If enough positive feedback is received there is a chance they will update the Jaunty repository to the patched 0.8.2-2.  This could get Wacom on Ubuntu close to where we want it.

The announcement comes from Timo Aaltonen by way of Loïc2.  This post by Timo Aaltonen on the ubutu-devel mailing list will fill in some background.

[https://lists.ubuntu.com/archives/ubuntu-devel/2009-March/027865.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-March/027865.html)

> **Timo Aaltonen** (3-24-09):
For jaunty, there's a new wacom-tools in my PPA which should do proper 
input hotplugging by using a hal callout program to set up the extra 
devices that the fdi file lists the hardware should support. It should 
also work on builtin serial devices like on tablet laptops. The patches, 
including some bugfixes, are borrowed from Fedora.

I'm guessing the callout program uses the information in the .fdi file to query dBUS for your Wacom input devices.  They appear to have figured out how to do multiple input devices for HAL.  Or think they have.

Good luck!

---

### Post by Favux on 2009-04-12
Hi Everyone,

This is a continuation of post #546. It looks like there may be a few glitches with the non-xorg.conf HAL/.fdi file dBUS method in Jaunty.

While that shakes out it appears you can still get Wacom in Jaunty. Just go to the Compile HOW TO: [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949) and compile 0.8.3-2. Make sure that libhal1-dev is not installed when you compile, otherwise you'll get unwanted HAL features.

---

### Post by farmercyst on 2009-04-17
ok. i have just recently upgraded to jaunty on my tx2500 and here are my results. 

wacom works for the stylus and the eraser with 0.8.3-2 per Favux's guide. the problem i have is with the touch. after modifying my xorg and putting touch in, all i get on a restart is a black screen. i had to comment out touch to get it to work. now touch is horribly uncalibrated, as would be expected, but i have stylus and eraser just like on 8.10. 

the next thing i noticed is that upon resuming from suspend, the stylus and eraser are uncalibrated just like touch is. i dont know why? i guess someone else will have to figure that out cause i have no clue. 

the last thing i have noticed, so far, is that when i press the "Q" button, the media player comes up. i dont think it did that on 8.10. is there some way that i can link that to my rotation script that i made from Favux's rotation guide?

---

### Post by Favux on 2009-04-18
Hi farmercyst,

And I assume you made sure libhal1-dev wasn't installed when you compiled, correct?  It shouldn't be installed by default anyway.

Assuming you've stayed on the compiled 0.8.3-2.  Can you post your current xorg.conf?  And are you saying without touch in xorg.conf you are getting reaction to your finger, just not very well calibrated?

It sounds like when you are resuming from suspend and X is restarting /home/username/.xinitrc isn't being run.

Could you run this script and post the output?
```
#!/bin/sh

#
# translate the names used for wacom tablet inputs
# by xinput into the names used by the wacom driver
# using hal-find-by-property and hal-get-property
#

for udi in `hal-find-by-property --key input.x11_driver --string wacom`; do
product="`hal-get-property --udi $udi --key info.product`"
type="`hal-get-property --udi $udi --key input.x11_options.Type`"
echo "product '$product' is type '$type'"
done
```

Thanks.

---

### Post by Favux on 2009-04-18
Hi farmercyst,

Breaking news.  Please see post #104 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  This should get Jaunty working for you.  I hope!

---

### Post by Favux on 2009-04-18
Sorry farmercyst,

I should have asked if you had tried the old hot plug commands after a suspend.  First ctrl-alt-F1 and then ctrl-alt-F7.  See if that gives you your stylus and eraser calibration back.

---

### Post by farmercyst on 2009-04-18
Favux,

> And I assume you made sure libhal1-dev wasn't installed when you compiled, correct? It shouldn't be installed by default anyway.
yes, i made sure libhal1-dev wasn't installed when i compiled 0.8.3-2. 

> And are you saying without touch in xorg.conf you are getting reaction to your finger, just not very well calibrated?
yes, thats correct. 

> It sounds like when you are resuming from suspend and X is restarting /home/username/.xinitrc isn't being run.
well now that you say that, i remember that i didnt set .xinitrc because it was calibrated close enough with my old xorg. 

> Breaking news. Please see post #104 here: [http://ubuntuforums.org/showthread.p...038949&page=11](http://ubuntuforums.org/showthread.p...038949&page=11) This should get Jaunty working for you. I hope!
thats exciting, im going to try this when i get home tonight!

---

### Post by marranzano on 2009-04-24
> **Favux said:**
> Hi tannalv,

The following may help answer your question as to why it seems like acpi is being deprecated.

From Bryce Harrington at [http://www2.bryceharrington.org:8080/drupal/node/63]("http://www2.bryceharrington.org:8080/drupal/node/63")


Would another way to phrase your question be:  Why are they moving thermal support away from acpi to the kernel?  So it seems it has to do with the move to HAL (hardware abstraction layer)/dBUS & pmutils which will be supplanted by DeviceKit (which missed Jaunty but will be in Karmic, 9.10) which will be subsumed into udev-extras.  The time line I think goes something like this.  In April last year the lead HAL dev. (Red Hat/Fedora?) decided HAL was a dead end and then announced DeviceKit.  Then within the last month he announced the last version of DeviceKit and that it was going to become udev-extras.

Hope this helps fill some of it in.  I'm sure there's more involved I don't know about.

have this problem too...
so how am I supposed to read the cpu temp?
any advice??

thnx
marranzano

---

### Post by marranzano on 2009-04-26
> **marranzano said:**
> have this problem too...
so how am I supposed to read the cpu temp?
any advice??

thnx
marranzano

i've fixed the dsdt following this
[https://wiki.edubuntu.org/LaptopTestingTeam/HPdv5z](https://wiki.edubuntu.org/LaptopTestingTeam/HPdv5z)
and now /proc/acpi/thermal_zone directory is populated and giving temperature...
;)

---

### Post by Afief.h on 2009-04-30
My keyboard seems to not work when I try to resume from suspend, stylus and touch do work for me.

Any ideas?

---

### Post by martinjochimsen on 2009-04-30
Hi Afief.h

I have a tx2590eo and the script in this link helped me with the same problems. (and I'm using Ubuntu 9.04 now)
[http://ubuntuforums.org/showpost.php?p=5220536&postcount=19](http://ubuntuforums.org/showpost.php?p=5220536&postcount=19)

```

Okay, I finally read up on how pm-utils works, 
and here is a solution that should work with Hardy.

Create the following file: sudo nano /etc/pm/sleep.d/25i8042

Code:

#!/bin/bash

case "$1" in
	hibernate|suspend)
		# Unbind the AT keyboard interface.
		if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
			echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
		fi
		;;
	thaw|resume) 
		# Rebind the AT keyboard interface.
		if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
			echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
		fi
		;;
	*)
		;;
esac

exit $?

Make sure this file is executable. There is no need to reboot your computer
 - your next suspend should work.
Please let me know if this works for anyone else.

Scott

```

Martin :-)

---

### Post by Afief.h on 2009-04-30
Now I have a keyboard after suspend but no mouse(touchpad) but the wacom works so I can use that as a mouse(for now)


Do you know what I should read on so I can understand what that script did and apply it to my touchpad as well?

---

### Post by martinjochimsen on 2009-04-30
Sorry, but I have NO idea what anything means in the script. It just worked!
Strange about the mouse though. What kind of laptop do you have? Maybe there is a function that have locked the mouse? (fn+f1-12)

Martin

---

### Post by marranzano on 2009-04-30
> **Afief.h said:**
> Now I have a keyboard after suspend but no mouse(touchpad) but the wacom works so I can use that as a mouse(for now)


Do you know what I should read on so I can understand what that script did and apply it to my touchpad as well?

As mentioned [here]("http://ubuntuforums.org/showpost.php?p=6182143&postcount=370") adding i8042.reset to grub is wat worked best for me (tx2510us):

$ sudo gedit /boot/grub/menu.lst
[INDENT]Find this line:
# kopt=root=UUID***************** ro
Change to this (leave the # at the beginning!):
# kopt=root=UUID***************** ro i8042.reset
save and close
[/INDENT]
$ sudo update-grub
then reboot...

---

### Post by Rangua on 2009-04-30
hi marranzano, i've tried doing what you mentioned to solve the suspend issue, and though it worked, i lost my wifi ip gathering abilities in the process :confused: any ideas why?
i'm gonna try the script on /etc/pm/sleep.d now, let's see if that works..

this is ridiculous. i tried the script and not only i had just the keyboard as Afief.h, but i also lost my wifi connection and after 10 seconds the keyboard stopped working :/
oh well..

---

### Post by Rangua on 2009-05-01
yay!! it did worked after all! :)
the only thing that stopped working was wicd, but when i configured manually my wireless connection i got my ip using dhclient
\\:D/
now i got the tablet, sound, suspend, fglrx (i *think* i have opengl), wifi, webcam... i think that's 'everything' and using jaunty :)
btw, i used the i8042.reset option.

---

### Post by harak on 2009-05-11
Well, tried the grub option. my laptop doesnot sleep on closing the lid. I had made a fresh install of jaunty by the  way. I remember that in in intrepid I had guidance power-manager installed. I will try again using that.

---

### Post by harak on 2009-05-11
Yup my suspicion was right! after installing guidance-power-manager... everything works fine. Though initially it appeared that I got the same problems as Rangua. The wireless took some time to connect

---

### Post by toobaz on 2009-05-23
Hello.

As I had done with intrepid, I have written a page where I try to collect all the [information about jaunty on the HP tx2500]("http://www.pietrobattiston.it/wiki/doku.php?id=jaunty_on_hp_pavilion_tx2500"). I have not much time to browse the forums, neither intend to replicate information (just to catalogue it): if some of you want to contribute some info missing, just write me.

bye

Pietro

---

### Post by ed021990 on 2009-06-22
hi mememe
i also have the tx2510 us. Did you have an issue with the volume buttons? I can't get them to work. When I press them, the volume bar does come up but won't do anything. Always seems to be on 0%. The mute button doesnt do anything either.

---

### Post by phormix on 2009-06-23
> **ed021990 said:**
> hi mememe
i also have the tx2510 us. Did you have an issue with the volume buttons? I can't get them to work. When I press them, the volume bar does come up but won't do anything. Always seems to be on 0%. The mute button doesnt do anything either.

Gnome or KDE? I believe mine worked fine in gnome, but in KDE it was changing the volume for the wrong mixer item. If you go into the system settings area, and find the hotkeys section, you can reassign it to change the volume for the MAIN mixer instead of whatever item it does by default.

---

### Post by ed021990 on 2009-06-27
> **phormix said:**
> Gnome or KDE? I believe mine worked fine in gnome, but in KDE it was changing the volume for the wrong mixer item. If you go into the system settings area, and find the hotkeys section, you can reassign it to change the volume for the MAIN mixer instead of whatever item it does by default.

thanks man, this worked for me

---

### Post by Red_Lion on 2009-07-30
// This message was deleted because of its senselessness. Sorry

---

### Post by gali98 on 2009-08-01
Red_Lion - Have you actually gotten those keys to work? I have the tx2000z.
Also, when I decompiled my DSDT, I did not find that last bit you listed (about Windows and Linux.)

Kory

---

### Post by Red_Lion on 2009-08-03
> **gali98 said:**
> Red_Lion - Have you actually gotten those keys to work? I have the tx2000z.
Also, when I decompiled my DSDT, I did not find that last bit you listed (about Windows and Linux.)

Kory

No, buttons not work. Also i fown what loading with _OS and _OSI "Windows 2006" turn off remoute on my tablet.

---

### Post by tannalv on 2009-08-03
> **Red_Lion said:**
> No, buttons not work. Also i fown what loading with _OS and _OSI "Windows 2006" turn off remoute on my tablet.

Ok. Try adding acpi_osi="!Windows 2006".
! means "not", i.e. you are NOT booting "windows 2006" (Vista).
Simple as that. No decompiling of DSDT needed.

---

### Post by Red_Lion on 2009-08-04
> **tannalv said:**
> Ok. Try adding acpi_osi="!Windows 2006".
! means "not", i.e. you are NOT booting "windows 2006" (Vista).
Simple as that. No decompiling of DSDT needed.

I know what mean "!". Adding you osi var not work, did you know? :)

---

### Post by tannalv on 2009-08-04
> **Red_Lion said:**
> I know what mean "!". Adding you osi var not work, did you know? :)

However now you have thermal and everything else that you need.
Again, there is no need to do DSDT-decompiling/compiling.

How good for you that you understand !. Shame that you don't understand that you're not the only one reading on this forum and that posts are rarely read by one single person.
But now perhaps you do...

---

### Post by Red_Lion on 2009-08-04
> **tannalv said:**
> However now you have thermal and everything else that you need.
Again, there is no need to do DSDT-decompiling/compiling.

How good for you that you understand !. Shame that you don't understand that you're not the only one reading on this forum and that posts are rarely read by one single person.
But now perhaps you do...

Sorry - about thermal i did not know. But buttons? It's just one why i decompile dsdt (for search how it mapped to system)

---

### Post by Favux on 2009-08-04
Hi Red_Lion,

Please don't overreact to some "constructive" criticism.

Looking for the bezel buttons in the DSDT, or at least trying to find where they are mapping their signal, seems perfectly reasonable.  It makes as much or more sense than things I have tried.

Right now my suspicion is the signal is directed to the HP-WMI kernel module.  MisteR2 discovered that's where the swivel hinge signal was going.  He persuaded Matthew Garrett to seperate the signal out of the docking event and provide a patch.  We almost have auto-magic rotation now.  See Recent News towards the bottom here:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)

Please take a look.  We still haven't quite figured it out.  Running a script isn't quite auto-magic.

---

### Post by Red_Lion on 2009-08-04
:) Hehe... I try to fix this with no patching.
It's runnig under user:
```

#!/bin/bash

old="0"
while true; do
	if [[ -e /sys/devices/platform/hp-wmi/dock ]]; then
		new=`cat /sys/devices/platform/hp-wmi/dock`
		if [[ $new != $old ]]; then
			if [[ $new == "0" ]]; then
				echo "Rotate to normal, hide cellwriter"
				xrandr -o normal 
				xsetwacom set stylus rotate NONE 
				xsetwacom set touch rotate NONE 
				xsetwacom set eraser rotate NONE
				cellwriter --hide-window
			elif [[ $new == "4" ]]; then
				echo "Rotate to tablet, show cellwriter"
				xrandr -o right 
				xsetwacom set stylus rotate CW 
				xsetwacom set touch rotate CW 
				xsetwacom set eraser rotate CW
				cellwriter --show-window
			fi 
		fi
		old=$new
		sleep 1s
	fi
done

```

Also this make work remoute/bezel buttons in tablet mode (need run under root)
```

#!/bin/bash

old="0"
while true; do
	if [[ -e /sys/devices/platform/hp-wmi/dock ]]; then
		new=`cat /sys/devices/platform/hp-wmi/dock`
		if [[ $new != $old ]]; then
			echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
			echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
		fi
		old=$new
		sleep 1s
	fi
done

```

Also (if we go back to DSDT) look to this:
```

                    Method (_Q16, 0, NotSerialized)
                    {
                        Store ("!!! DVD/Music Button pressed !!!", Debug)
                        Store (QBBB, Local0)
                        If (LEqual (Local0, 0x03))
                        {
                            Notify (MBTN, 0x02)
                        }

                        If (LEqual (Local0, 0x06))
                        {
                            Notify (PBTN, 0x02)
                        }

                        If (LEqual (Local0, 0x09))
                        {
                            Notify (VBTN, 0x02)
                        }

                        If (LEqual (Local0, 0x12))
                        {
                            Notify (TBTN, 0x02)
                        }

                        Store (0x04, ^^^^WMID.WEID)
                        Store (Zero, ^^^^WMID.WEDT)
                        Notify (WMID, 0x80)
                    }

```

If you see  "Method (GBBV, 0, NotSerialized)" (i will find this by QBBB) you will see what all events listed in _Q16 not present in GBBV (it's hp_wmi?)

---

### Post by Favux on 2009-08-04
Hi Red_Lion,

Right, that's my guess, HP-WMI.

Are you are saying this works for you?:
```
#!/bin/bash

old="0"
while true; do
	if [[ -e /sys/devices/platform/hp-wmi/dock ]]; then
		new=`cat /sys/devices/platform/hp-wmi/dock`
		if [[ $new != $old ]]; then
			if [[ $new == "0" ]]; then
				echo "Rotate to landscape"
				xrandr -o normal 
				xsetwacom set stylus rotate NONE 
				xsetwacom set touch rotate NONE 
				xsetwacom set eraser rotate NONE
			elif [[ $new == "4" ]]; then
				echo "Rotate to portrait"
				xrandr -o right 
				xsetwacom set stylus rotate CW 
				xsetwacom set touch rotate CW 
				xsetwacom set eraser rotate CW
			fi 
		fi
		old=$new
		sleep 1s
	fi
done
```
It gives you auto-magic rotation?  How exactly are you setting it up under "user"?

Are you on Jaunty (9.04)?

---

### Post by Red_Lion on 2009-08-04
On non patched hp_wmi - work.

Need run under user in xorg (just save, +x, and put in in autostart in gnome/kde/xfce...).

If you rotate screen to tablet mode - this script rotate stilys/eraser (but see - here is no touch - i broken him, so not put in to script by hands) to left-handed and show cellwriter. If you in normal "notebook" mode - normal rotation and autohide cellwriter (in mode change only).

Just run on non patchen hp_wmi - you will see :)

If i not mistake it's you call "magic rotation"?

// Also - i on archlinux :) This script was also tested on 8.10, 9.04

---

### Post by Favux on 2009-08-04
Hi Red_Lion,

You must be using Kubuntu Jaunty (9.04).

I understand you now.  You are using the unpatched HP-WMI and using the "docking event" as the trigger.  Clever.

Unfortunately that won't work for Intrepid (or Hardy) because there is no HP-WMI.
```
$ lsmod
wmi                    15808  0
dock                   18592  1 libata
```
```
~$ modinfo -d wmi
ACPI-WMI Mapping Driver
```
```
$ modinfo -d dock
ACPI Dock Station Driver
```
So there is no "hp-wmi/dock" in "/sys/devices/platform/".  Instead there is "/sys/module/wmi", "/sys/bus/acpi/drivers/wmi", and "/sys/module/dock".  Oh well.

---

### Post by Red_Lion on 2009-08-04
Ohh... About 8.10 - sorry - i think what anover ubuntu user who use this script is on 8.10.

I know what a say now is naive (i don't know can be compiled on 8.10) - but try to compile and install hp_wmi in my attachment.

---

### Post by Favux on 2009-08-04
Hi Red_Lion,

Thank you.  I will take a look at it.  But I think HP-WMI can only be compiled on kernel 2.6.28 (Jaunty) and up.  Not on kernel 2.6.27 (Intrepid) or lower.

---

### Post by Red_Lion on 2009-08-04
No, 2.6.27 have hp_wmi:

[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.27.y.git;a=blob;f=drivers/misc/hp-wmi.c;h=6d407c2a4f91d80e54d5885e741ce436fb21aa31;hb=a8823aefd142d2a9c4b3661bf8712ccd2da1b220](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.27.y.git;a=blob;f=drivers/misc/hp-wmi.c;h=6d407c2a4f91d80e54d5885e741ce436fb21aa31;hb=a8823aefd142d2a9c4b3661bf8712ccd2da1b220)

It's just not included by ubuntu (or you not modprobe it, but it's less real :) )

---

### Post by Favux on 2009-08-04
Hi Red_Lion,

You are correct, I spoke too soon.  From the Makefile "No support for 2.4 series kernels".  Do you know which kernel version this hp-wmi.ko is for?

It compiled fine.  I installed it in "/etc/modules" and it is now present in "lsmod":
```
hp_wmi                 14768  0 
```

However I didn't get the script to work on swiveling yet.

Edit:  Tried a few things.  Still no luck.

---

### Post by Red_Lion on 2009-08-05
ls /sys/devices/platform/hp-wmi/ ?

dmesg | grep -F WMI ?

---

### Post by Favux on 2009-08-05
Hi Red_Lion,

About all I learned is the first 2.6(.27?) HP-WMI was accepted 7/25/08 and the one I'm using 2.6.27 is 9/3/08 with some changes like hotkey_query added.  Ignoring the git identifiers of course.

```
$ ls /sys/devices/platform/hp-wmi/
als  display  dock  driver  hddtemp  modalias  power  rfkill  subsystem  uevent

```
```
$ dmesg | grep -F WMI
[   14.958643] ACPI: WMI: Mapper loaded
[   18.528333] input: HP WMI hotkeys as /devices/virtual/input/input12
```

---

### Post by Red_Lion on 2009-08-05
> **Favux said:**
> Hi Red_Lion,

About all I learned is the first 2.6(.27?) HP-WMI was accepted 7/25/08 and the one I'm using 2.6.27 is 9/3/08 with some changes like hotkey_query added.  Ignoring the git identifiers of course.

```
$ ls /sys/devices/platform/hp-wmi/
als  display  dock  driver  hddtemp  modalias  power  rfkill  subsystem  uevent

```
```
$ dmesg | grep -F WMI
[   14.958643] ACPI: WMI: Mapper loaded
[   18.528333] input: HP WMI hotkeys as /devices/virtual/input/input12
```

/sys/devices/platform/hp-wmi/dock parsing only via hp_wmi. hp_wmi using wmi system what work correctly in you kernel. Try test hp_wmi driver:
```
cat /sys/devices/platform/hp-wmi/dock ; sleep 5s ; cat /sys/devices/platform/hp-wmi/dock
```
on "sleep 5s" rotate screen to tablet.

---

### Post by Favux on 2009-08-05
Hi Red_Lion,

It works!  It works!  I have auto-magic rotation!

automatic rotation + magic rotation = auto-magic rotation

I had a typo in the command line for the script in Sessions (Startup Applications in Jaunty).  I must have looked at it 10 times and kept missing it.  I finally looked at .xsessions-errors again and spotted it.

Thank you!

Edit:  And your test line works.

---

### Post by Red_Lion on 2009-08-05
Good what it work :)

Also i recomend to add second my script to system autostart (/etc/rc.local example - i can't remember what file exec after last init level in ubuntu). Make it background ("&" after script filename).

It's realy give to you working remoute and bezel buttons (only what work in normal mode - Q and DVD) in tablet mode.

---

### Post by Favux on 2009-08-05
Hi Red_Lion,

I meant to ask you about the bezel button script.  Mine work when rotated.  You have the TX2500 correct?  Are you using "fglrx"?  Are you using Compiz?  ATI "fglrx" doesn't work correctly with Compiz when rotated.  Have you run the aticonfig command?  See Appendix 1 here:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)

Do you have a link to the hp-wmi source code and makefile you packaged?

Thanks again.

---

### Post by Red_Lion on 2009-08-05
I not using compiz. Yes - i use fglrx and make xrandr support for rotation via aticonfig.

hp_wmi what i posted - from 2.6.30, makefile crated by me - so i have no link :)

I have tx2500 (tx2650er)

P.S. bezel/remoute button script need only if they making "dead" on tablet mode. It reset controller for activate them.

---

### Post by Favux on 2009-08-05
Hi Red_Lion,

Thank you for the 2.6.30 Makefile, it worked fine on 2.6.27.

OK, now I understand the:
```
echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
```
Several users have reported the bezel buttons dead on rotation.  Updating the bios to the latest version seems to help some of them.  Others noticed a link with the small button at the top of the Synaptic touch pad.  The one that disables it for typing.  If touchpad was turned off they lost their two bezel buttons.  See, starting with post #56, here:  [http://ubuntuforums.org/showthread.php?p=6725304](http://ubuntuforums.org/showthread.php?p=6725304)  It goes on for a page or two.

---

### Post by Favux on 2009-08-06
Hi Red_Lion and everone,

I discovered something sort of interesting.  Either that or I'm doing something wrong.  The blobs of hp-wmi.c from the 2.6.27 and 2.6.30 git trees seem to be identical.  Which I suppose helps explain why your 2.6.30 makefile worked on the 2.6.27 hp-wmi.c Red_Lion.

[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.27.y.git;a=blob_plain;f=drivers/misc/hp-wmi.c;hb=a8823aefd142d2a9c4b3661bf8712ccd2da1b220](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.27.y.git;a=blob_plain;f=drivers/misc/hp-wmi.c;hb=a8823aefd142d2a9c4b3661bf8712ccd2da1b220)

[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.30.y.git;a=blob_plain;f=drivers/misc/hp-wmi.c;hb=a8823aefd142d2a9c4b3661bf8712ccd2da1b220](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.30.y.git;a=blob_plain;f=drivers/misc/hp-wmi.c;hb=a8823aefd142d2a9c4b3661bf8712ccd2da1b220)

The last patches I could find were both submitted on 9/8/08 I think.

If I'm messing up I would appreciate someone explaining what I'm doing wrong.

---

### Post by Red_Lion on 2009-08-06
Yes, it's can be. I say what i take hp_wmi from 2.6.30 tree, but when it will wrote i not say :D My makefile not depend of kernel (on 2.6 tree) - hp_wmi maybe can compile in kernels <2.6.17 - i not test it.

P.S. In our notebook series now only need to make bezel buttons, red light on mute, and understand how in vista switching buttons on remoute (acpi-keyboard). In first - need somebody who know how programming modules under acpi and somebody who can read dsdt source well (i can read, but lot of code not understand). If somebody whant to help - write me to jabber - [email]red_lion@jabber.ru[/email]

---

### Post by Red_Lion on 2009-08-11
Sad news - in dsdt only information about HotStart - not more. Aslo Hotstart(quickstart) will work only in suspend/poweroff mode. Just 2 ways we now have - decompile hp drivers (if need i can give code decompiled, but realy need somebody who can help read them) and search about i8042 controller.

I think what 2 bezel buttons will never work - i cant make all myself, and nobody now can help in this job :(

---

### Post by Rangua on 2009-09-19
hello again :)
so.. anyone noticed that multimedia buttons (and remote control) stop working when you have the screen folded and closed? (tablet-mode)
0.o??
 i've been trying to figure out whether the computer knew when it was folded tablet-mode, but i couldn't find it where the file for the lid one is (i forgot now where that one is too...), so i thought that ubuntu just couldn't.. but now it seems it can :O, so, anyone got this issue?

edit: sorry for repeating the post. i'll read [http://ubuntuforums.org/showthread.php?p=6725304](http://ubuntuforums.org/showthread.php?p=6725304) and comment if i get somewhere...
lastedit: wow! i thought things moved fast on these subject, but i it seems it was all just the beggining! i got autorotation :D thank you thank you thank you thank you all you guys that made this possible!! great work guys!

---

### Post by Favux on 2009-09-20
Hi Rangua,

Hey great!  Glad you have auto-rotation now.  Are you using the script or the applet?

As you can see with the discussion with Groove Therapy and the rest, updating the bios seemed to help with the buttons in tablet mode, at least for some folks.

---

### Post by andre.mella on 2009-10-28
hi 
i just went from windows to ubuntu whit my hp tx 2525nr 
and I'm having problems with my sound card 
so if same body cut help me out it would be grate

---

### Post by Favux on 2009-10-28
Hi andre.mella,

Welcome to Ubuntu Forums!

You didn't mention which version of Ubunu you installed.

You want to add the line:
```
options snd-hda-intel index=0 model=toshiba position_fix=1
```
to the end of the alsa-base.conf file. Which used to be called alsa-base before Jaunty.  Don't worry that it says Toshiba.  To do that in a terminal enter:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add the line to the end (copy and paste). Save and restart.

Hope this helps.

---

### Post by andre.mella on 2009-10-28
thank you for answering so quickly 
i tied but id didn't work
i'm using ubuntu 9.10

---

### Post by Favux on 2009-10-28
Hi andre.mella,

That's too bad.  Since you are using Karmic, maybe something has changed since Jaunty.  Check your mixer and make sure the volume sliders are up, including PCM and also try rebooting a couple of times.  Otherwise we'll have to wait until someone reports success in Karmic.

---

### Post by andre.mella on 2009-10-28
thanks
i will be waiting then

---

### Post by marranzano on 2009-10-29
hi,
just installed karmic.
before going into fixing the dsdt I'm curious to know if i'm the only one not reading the cpu temperature? (i've had this problem with jaunty as well and had to fix the dsdt)

waiting for your comments.
tnx

---

### Post by Favux on 2009-10-29
Hi marranzano,

You can't use a patched DSDT in Karmic.  The kernel dev.s dropped the support for the DSDT kernel patch.  67GTA talks about this on his thread:  [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)  and on a thread he started in the Karmic forum.  I think OpenSuse decided to get the patch working for 2.6.31 and he talks about that too.

You can try adding:
```
acpi_osi="Linux"
```
to the boot options.

---

### Post by marranzano on 2009-10-29
> **Favux said:**
> 

You can try adding:
```
acpi_osi="Linux"
```
to the boot options.

thanks for the info favux, unfortunately no luck with this option... but will look around to see what can be done...

EDIT:
the option works, i did a typo... :)
tnx

---

### Post by marranzano on 2009-10-30
> **marranzano said:**
> ...the option works...
tnx
although showing temperature i doubt it's the right temp:
i have both cpu (AMD Turion 2100) scaled at 525, no particular activity and have a temp ranging in the high 70 degrees...!!! :confused:
is there a way to fix this??
tnx

yes!! and the correct way was to open up the machine and clean it!!

---

### Post by chadmerkert on 2009-10-30
Hey andre.mella,

I am having the same problem. I just did a clean install of Ubuntu 9.10 on my tx2500z and the sound is not working. This is very annoying, because the sound worked fine in 9.04. I will be working to find a solution to this problem, because I really don't want to downgrade to 9.04! 

If someone who is running 9.10 on a tx2500z and has working sound, could you please post your alsa-base.conf so I can compare it to mine. Thanks

---

### Post by tannalv on 2009-10-30
chadmerkert, mine works fine. And here you go.

---

### Post by chadmerkert on 2009-10-30
Hey andre.mella,

I am working on fixing my problem, and I wanted to ask you a few questions about your problem, to see if it is the same problem. Did the sound ever work with Ubuntu 9.10? For example when I boot to the 9.10 Live CD, the sound is working! If possible try booting to the live CD and seeing if you have sound then.

I also have sound after I install Ubuntu 9.10, but something must have broken the sound after I installed it. I am going through installing different programs and drivers again, to see if I can find out what it was that stopped my sound from working.

Thanks

---

### Post by smileykoki on 2009-10-30
hey there!  i'm having the same sound problem on my tx2510us.. i had sound working on ubuntu 9.04, and yesterday i updated to 9.10 directly from update manager, and the sound is gone.. i'll stick around if someone post a solution for this issue.. i don't want to downgrade! D:

sorry for the bad english, i'm from Paraguay, and i'm new around here..

thnx!

---

### Post by Favux on 2009-10-30
Hi everyone,

An off the wall thought.  Check the modules file in /etc/.  See if 'lp' and 'fuse' are in there.  If 'fuse' is missing try adding it and rebooting.

---

### Post by smileykoki on 2009-10-30
hi favux!

i did that, added 'fuse' in /etc/modules, restarted, and nothing happens. :(

---

### Post by Favux on 2009-10-30
Hi smileykoki,

Disappointing but not too surprising.  Someone told me about that 4 or 5 months ago.  I don't know why adding user space files access works but it has for a few.  The other day we had to add wacom for a guy who's setup didn't auto-load the wacom module.  It knocked out sound for him.  When we added fuse to modules sound came back.  All the modules files I've seen had lp already, which is parallel port.  It's worked for one or two others also.  My guess was that maybe something was stopping fuse from auto-loading (like adding wacom).  Maybe not.

---

### Post by andre.mella on 2009-10-30
i never had sound and ubuntu never detected the sound card

---

### Post by andre.mella on 2009-10-31
finally i got sound working 
i just deactivate modem for software in hardware manager
restarted an i had sound

---

### Post by Docaltmed on 2009-10-31
I'm thinking about moving from Jaunty to Karmic. What's the word from the front lines? On the live CD, everything seemed fine, but, well, you know...stuff happens. This is a production machine. Should I do it?

---

### Post by martinjochimsen on 2009-10-31
Hi Docaltmed

I changed (clean install) Thursday from Jaunty to Koala and it has only been positiv. I still had to work a little with the wacom- and rotation-stuff but with galis and Favuxs guides it has been easy.
I have a tx2590oe and now for the first time since 8.04 the sound works out-the-box (haven't tested the mic's yet).
Everything goes more smooth, so either the Ubuntu-gyes has hit the spot this time or I have become more skilled.....! I'll put my money on the Ubuntu-team.
I think you should go for it.
I always make clean installs so that is what I recommend.
And DON'T forget to backup!!! :-D

Martin :-)

---

### Post by chadmerkert on 2009-10-31
I would like to confirm andre.mella's finding. 

I didn't have sound, so I reinstalled 9.10, and the sound works, and the only thing that I did differently was I didn't install the Software Modem driver in Hardware Drivers. 

So if someone else has a problem with sound, check to see if you have Software Modem active in Hardware Drivers, and try disabling it.

Docaltmed,

I did a clean install upgrade from 9.04 to 9.10, and other than doing a bit of tweaking to the touch screen, everything works out of the box!! I have tested the Mic, and all I needed to do was change the settings from Mic 1 to Mic 2 and then adjust the volume of the mic! Suspend works perfectly with no modification, and Compiz Desktop effects works perfectly with the Radeon 3200 now!! (before it would crash X-server when I played a video)

So all in all, Everything is working better than in Jaunty, and I would definitely recommend the upgrade!!!

So far, my only 2 complaints of 9.10 are

1. I use the CPU Frequency monitor on the pannel(I am using gnome not kde)
 and now it asks for the admin password every time I try to change the CPU frequency which is a little annoying!

2. When running on battery, it won't let my CPU speed go above 1.1GHz(50%) even if I try to change it with CPU Frequency Monitor, which is a bit annoying because if you are trying to watch a video or play a game on battery, it won't be the best performance!

I am looking for a solution to my 2 complaints, but have yet to find anything.

---

### Post by Docaltmed on 2009-11-01
> **martinjochimsen said:**
> Hi Docaltmed

I changed (clean install) Thursday from Jaunty to Koala and it has only been positiv. I still had to work a little with the wacom- and rotation-stuff but with galis and Favuxs guides it has been easy.
I have a tx2590oe and now for the first time since 8.04 the sound works out-the-box (haven't tested the mic's yet).
Everything goes more smooth, so either the Ubuntu-gyes has hit the spot this time or I have become more skilled.....! I'll put my money on the Ubuntu-team.
I think you should go for it.
I always make clean installs so that is what I recommend.
And DON'T forget to backup!!! :-D

Martin :-)

Thanks for the advice, Martin. I think I'll take it. Backup first. See you guys on the other side.

Avery

---

### Post by marranzano on 2009-11-02
any clue with the dvd button?

showkey reports 389

sudo /lib/udev/keymap -i input/event5
gives me:
scan code: 0x8E   key code: dvd

unfortunately the
[INDENT]sudo update-rc.d -f hotkey-setup remove
sudo update-rc.d hotkey-setup start 99 6 5 4 3 2 1 .
sudo /etc/init.d/hotkey-setup restart
[/INDENT]trick doesn't work because there's no hotkey-setup...

can anyone help implement it in hal?
tnx

---

### Post by Favux on 2009-11-02
Hi marranzano,

I guess you could work through the "I want to fix my multimedia keys" at the [HAL Quirk Site]("http://hal.freedesktop.org/quirk/").  That may help.

---

### Post by smileykoki on 2009-11-03
> **andre.mella said:**
> finally i got sound working 
i just deactivate modem for software in hardware manager
restarted an i had sound

worked for me! now i have sound again! thnx andre.mella! i will the try microphone now :)

---

### Post by marranzano on 2009-11-03
ok, i'm back...
firstly thank favux, ran into your thread regarding rotation and discovered the use of hp-wmi!!!

i had no luck with the dvd key, hal doesn't seem to make much of a difference.

but most of all i'm struggling with the audio:
everything seems to work (i can confirm that installing the modem software brakes audio) untill i try to use the mic. the mic picks up a lot of noise, which i can do my best to reduce but mainly it picks up from either the speakers or the output resulting in a deadly feedback when talking on skype: i can hear perfectly but the other person hears hisown voice.

anyone has solved this on karmic (this problem didn't exist in jaunty with the same skype version)

tnx

---

### Post by Favux on 2009-11-04
Hi marranzano,

Yes, pretty cool, huh?  MisteR2 and Red_Lion really did us all a solid.

From Ayuthia:
> There are some adjustments needed in alsamixer to get the internal microphone to work. First, you need to go into alsamixer from the Terminal. Once you are in there, press the right arrow until you see Input Source. If you don't see that entry, press tab until you do. Make sure that it is set to Front Mic. Set Front Mic and the Front Mic Boost as high as possible. Play around with the Capture and Digital controls until your voice is clear. Fan noise or the display buzz may get recorded into the sound, but you should be able to get voice to sound clear. Try Capture volume at 65 and Digital at 40. You might be able to adjust it via the volume control in the system tray. KDE and KMix does provide the ability to adjust all the controls. The Line In does work with a microphone plugged it. You need to adjust the Input Source to Line In. It does capture the sound, but may not come in as loud as the internal mic.
Knowing diddly about sound this is the best I can come up with.  For a TX2z.

---

### Post by jubej on 2009-11-12
Hello!

I have read a really god stuff here and i got my tx2520us working really god with ubuntu 8.04. its was a lot of work but worth it. Thanx all for the help.

But now I made a clean install of karmic koala. and everthing works OOB!
caemra, sound, even bluetooth can conect to my headset and i can listen and talk in a few klicks.

But there is one thing Im still having problems with and i dont know what to do.

**The problem:**

my stylus is working, i can write in xournal nad erase with the side button. the "back botton, the one you use in a normal pen to erase just works as a pen"
but the most problematic stuff is that its not calibrated, and thet make my taking notes in the university a nightmare. I have installed wacom-tools and when I use the wacomcpl...it starts but there is nothing on it. Its like it dont recognice that there is a stylus.

Waht can I do to resolve this problem. Im kind of desperate here :).

By the way touch not working at all, maybe its not active?  

thnx. A strugeling student

---

### Post by marranzano on 2009-11-12
> **jubej said:**
> .... my stylus is working, i can write in xournal nad erase with the side button. the "back botton, the one you use in a normal pen to erase just works as a pen"
but the most problematic stuff is that its not calibrated, and thet make my taking notes in the university a nightmare. I have installed wacom-tools and when I use the wacomcpl...it starts but there is nothing on it. Its like it dont recognice that there is a stylus....
had the same issue, this did the trick:
[http://ubuntuforums.org/showpost.php?p=7092941&postcount=102](http://ubuntuforums.org/showpost.php?p=7092941&postcount=102)
;)

---

### Post by OnionMan on 2009-12-11
hi guys,
I have not read all the thread but here are my problems:

I waited for a few kernel updates but nothing is fixed yet.

My sound is cracking a lot. Small sounds like IM sounds are only a crack. Longer sounds like music or video are ok after few seconds, really annoying since it was working on 8.04/8.10/9.04.

Microphone isnt working too :(

My sleep is not working, when i come back from it, no trackpad/keyboard.

I have a TX 2524ca, clean install of 9.10 and my modem driver is not installed.

Anyone can help?

thx

---

### Post by OnionMan on 2009-12-14
:-(

---

### Post by marranzano on 2009-12-14
still need a little help with the dvd key on tx2510us:

I added
```
setkeycodes 0x8e 142
```
to /etc/rc.local
and now the dvd key is working again :)
the only problem is that it works as a duplicate of the (fn f5 key) (sleep)

how do i make it differ from such key?

EDIT: ok, I'll reply to myself since it was kind of stupid question...
I just changed the line to
```
setkeycodes 0x8e 162
```
which is the XF86Eject and all is ok!!

But i still would like to learn a little more:
why is it that the reload key (the low right on the screen used for rotation) is binded to XF86AudioMedia?
also fn+prtsc and fn+sysrq seem to be the same keys, same applies to fn+pause and fn+break?

is it because i have chosen the wrong keyboard layout (the generic pc105) or it's something that someone should check and remap?

tnx again

---

### Post by chadmerkert on 2009-12-17
Hey OnionMan, 

Just wondering, are you using the 32-bit or 64-bit version? I'm not sure why you are having so many problems. I am running Ubuntu 9.10 on a tx2500z and almost everything worked without any problems. The microphone I had to adjust a few settings in the audio settings, but other than that, everything worked fine. If you are not using the 64-bit version, try downloading that. And if you are using Kubuntu, maybe try Ubuntu just to see if the problems are in Ubuntu as well.

Best of luck! :)

---

### Post by duganoneil on 2009-12-21
> **OnionMan said:**
> hi guys,
I have not read all the thread but here are my problems:

I waited for a few kernel updates but nothing is fixed yet.

My sound is cracking a lot. Small sounds like IM sounds are only a crack. Longer sounds like music or video are ok after few seconds, really annoying since it was working on 8.04/8.10/9.04.

Microphone isnt working too :(

My sleep is not working, when i come back from it, no trackpad/keyboard.

I have a TX 2524ca, clean install of 9.10 and my modem driver is not installed.

Anyone can help?

thx

Hello OnionMan,
 I also have microphone problems. My microphone was working fine in intrepid and Jaunty but not in Karmic. I have resorted to USB mics. I don't have a problem with crackling sounds though. I am running 32-bit ubuntu.

 I also had the problem with not waking properly from sleep. To fix it I made a change to boot options in GRUB. I edited /etc/default/grub to have

GRUB_CMDLINE_LINUX_DEFAULT="i8042.reset"

than ran "update-grub" and it worked fine after that.

Other than the microphone, the only lingering Karmic problem for me is that plugging in a USB mouse usually does not work. My external keyboard works fine whether I plug it in for boot or at some random later time. Other USB devices are also fine. However, the mouse works only occasionally. If I restart X many, many times I have some chance it will work. However, most of the time I get no external mouse at all. I have tried multiple mouse models and many solutions from google searches with no luck. Anybody else having this problem on this laptop in Karmic? Worked fine in all previous releases...

Thanks,
Dugan.

---

### Post by aeiluindae on 2010-01-07
I have the microphone and sleep problems as well. I'm gonna try the grub fix suggested. Anybody have any idea why the microphones fail? I've tried the internal mic and the line in. Absolutely nothing, and the line in worked in Jaunty, I'm pretty sure. I don't want to have to buy a usb mic.

---

### Post by Peckham on 2011-03-04
Hello,
       Thanks for this info this was the next thing i was going to try...  another boot loader... thanks for pointing me in the right direction...  somehow i misplaced my kalyway .iso file but am going to try and patch a  leo4all v3 .iso with chameleon boot loader and see what happens there..   I will report here if it worked.


Thanks 
_______
[COLOR=blue][FONT=&quot]http://www.viewguard.com/en-us/[/FONT][/COLOR]

---

### Post by shm on 2011-09-05
Hi all! three years has left, linux-kernel, after 2.6.38, have problems with power management and amd often more voracious then others, so?
I have 90-95 Celsius degrees without any load (cpu overheating)!

Problem in linux/ubuntu? amd? HP build bad laptop?
No!

But,  may be  clogged small radiator in tx2500  (inside)! I have this situation!
after cleaning  i have 54-58 degrees with running firefox, and 75 degree with compiling, using two cpu cores.

I fully disassemble my laptop(and also change thermal grease), but i believe, you may just unscrew keyboard. Unscrew only 4 bolt at bottom(search keyboard pictures) and carefully pick-up keyboard above laptop case, don't disconnect keyboard cord from motherboard!  Next carefully clean your cooler, using vacuum cleaner, using hole in mother board at right top corner.  

My setup (without any magic):

ubuntu 11.04. amd64
cpu frequency policy - conservative

video driver from Xorg Edgers repository
linux-kernel Linux  3.0.0-7-generic

Ati Video card power save settings:

echo "profile" > /sys/class/drm/card0/device/power_method
echo "low" > /sys/class/drm/card0/device/power_profile


I hope my info helps prolong your laptop life.

Sorry for my English.

---

### Post by Favux on 2011-09-05
Hi shm,

Thank you for sharing that.

I've been blowing out my TX2000 fan with canned air.  But if I can access the heat sink to clean it with canned air through the motherboard by just removing the keyboard, I should try that too.

This shows how to disassemble a TX200:  [http://www.insidemylaptop.com/disassemble-hp-pavilion-tx2000-tablet-pc/](http://www.insidemylaptop.com/disassemble-hp-pavilion-tx2000-tablet-pc/)  Are those four screws for the keyboard the ones you are talking about?

By the hole in the "right top corner" on the motherboard do you mean the same place as where the fan and it's vents are, i.e. where the cooling module is?

---

### Post by shm on 2011-09-06
> **Favux said:**
> Hi shm,

Thank you for sharing that.

I've been blowing out my TX2000 fan with canned air.  But if I can access the heat sink to clean it with canned air through the motherboard by just removing the keyboard, I should try that too.

This shows how to disassemble a TX200:  [http://www.insidemylaptop.com/disassemble-hp-pavilion-tx2000-tablet-pc/](http://www.insidemylaptop.com/disassemble-hp-pavilion-tx2000-tablet-pc/)  Are those four screws for the keyboard the ones you are talking about?


Hi Favux!

At this picture, blue circles it is keyboard screws [[IMG]http://img824.imageshack.us/img824/245/tabletpcdisassembly22.jpg[/IMG]](http://imageshack.us/photo/my-images/824/tabletpcdisassembly22.jpg/)

After unscrew four bolts,use knife (or something like this) to pick up keyboard,
it have small ledges on the edge.

> **Favux said:**
> 
By the hole in the "right top corner" on the motherboard do you mean the same place as where the fan and it's vents are, i.e. where the cooling module is?



Yes it is cooler vent, i think if clean through this vent, dust should easily to come out.
[[IMG]http://img801.imageshack.us/img801/8883/tabletpcdisassembly21.jpg[/IMG]](http://imageshack.us/photo/my-images/801/tabletpcdisassembly21.jpg/)

At this picture you can see how the dust is looks like =) 
I had a similar picture.
[[IMG]http://img233.imageshack.us/img233/170/tabletpcdisassembly34.jpg[/IMG]](http://imageshack.us/photo/my-images/233/tabletpcdisassembly34.jpg/)
Also you can try to use ear stick (or any other tiny stick), to hook the dust.

And probably good idea to use compressed gas duster, from out side of radiator, at the same time as  vacuuming.

Good luck!

---

### Post by Favux on 2011-09-06
Wow shm thanks!

I'll add that to my maintainance routine.  :)

---

