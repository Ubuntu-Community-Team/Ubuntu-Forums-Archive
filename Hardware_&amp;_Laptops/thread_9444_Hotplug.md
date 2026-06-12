---
title: "Hotplug"
date: 2004-12-28
forum: Hardware &amp; Laptops
---

### Post by animalstyle on 2004-12-28
I have an ASUS P4P800 SE motherboard (ICH5).  Everything is working fine except hot plug.  I cannot unplug my mouse and plug it back in.  It does not even seem to recognize my iPod at all, even when i have it plugged in from when i boot.  Anyone had  some similar problems?  What can I try?

---

### Post by animalstyle on 2004-12-29
Just to let you guys know, if you are having any trouble with hot plugging i found that in my motherboard's BIOS (ASUS P4P800SE), after disabling "Legacy USB Support", hotplugging works absolutely perfectly.  I noticed alot of people posting problems with hotplugging, maybe this will help.  Just doin my part.

---

### Post by Bart Van on 2004-12-30
Hm, I also have an ASUS motherboard (A7V8X), and a very similar problem with hotplug, but turning of Legacy USB support in the BIOS didn't help.

My problem is that when during boot I leave my ADSL modem (USB Sagem Fast 800) plugged in, I never get past hotplug... Have to unplug it first and plug it in once the bootup process gets past hotplug. 
I already tried anything I could find in different forums, and used my own imagination (bad idea for a non-geek like me :-) ), but nothing helps.

A shame really, because otherwise I'm very pleased with Ubuntu...

---

### Post by animalstyle on 2004-12-30
Hmm, well im pretty much a newbie myself.  I guess about the only advice I can give you is to keep messin around with things, googling, and searching these forums.  I finallay got this system fully functional, and trust me, it feels good to have a completely free operating system that works.  Its worth the effort IMHOP, so dont give up.

---

### Post by Bart Van on 2004-12-31
Apparently this is a kernel bug, at least, that's wat dmesg says.
This is what I get when booting with my USB ADSL-modem connected (hangs on hotplug, after that I continue with Alt-SysRq-E):

```

dmesg

usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 185
uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:10.0: irq 185, io base 0000d800
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.1(B) -> GSI 21 (level, low) -> IRQ 185
uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:10.1: irq 185, io base 0000d400
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 185
uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
uhci_hcd 0000:00:10.2: irq 185, io base 0000d000
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 1-1: new full speed USB device using address 2
CSLIP: code copyright 1989 Regents of the University of California
PPP generic driver version 2.4.2
[eagle-usb] driver V1.9.9 loaded
[eagle-usb] New USB ADSL device detected, waiting for DSP code...
[eagle-usb] Interface 0 accepted.
[eagle-usb] created proc entry at : /proc/driver/eagle-usb/001-002
usbcore: registered new driver eagle-usb
ACPI: PCI interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 185
ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:10.3: irq 185, pci mem e09cf000
ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
ehci_hcd 0000:00:10.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
usb 1-1: USB disconnect, address 2
[eagle-usb] ADSL device removed
------------[ cut here ]------------
**kernel BUG at mm/slab.c:1544!**
invalid operand: 0000 [#1]
PREEMPT 
Modules linked in: ehci_hcd eagle_usb ppp_async ppp_generic slhc crc_ccitt uhci_hcd usbcore snd_bt87x snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd snd_page_alloc bt878 bttv video_buf i2c_algo_bit v4l2_common btcx_risc i2c_core videodev soundcore b44 mii via_agp agpgart pcspkr rtc analog gameport floppy md dm_mod capability commoncap parport_pc lp parport tsdev evdev ide_cd cdrom mousedev psmouse ext3 jbd ide_generic via82cxxx ide_disk ide_core unix fan thermal processor font vesafb cfbcopyarea cfbimgblt cfbfillrect
CPU:    0
EIP:    0060:[<c0133960>]    Not tainted
EFLAGS: 00010246   (2.6.8.1-4-386) 
EIP is at kmem_cache_destroy+0x1b/0xe0
eax: 00000000   ebx: 00000006   ecx: 00000000   edx: c178fb74
esi: c178f800   edi: 00000000   ebp: def6a400   esp: df0bfe80
ds: 007b   es: 007b   ss: 0068
Process khubd (pid: 2372, threadinfo=df0be000 task=df5ed6f0)
Stack: 00000006 c178f800 def6a400 e0aa9b47 00000000 dec37000 dfbe0a60 00000002 
       00000028 00000002 def6a400 e0a74374 def6a400 0000900f c178f800 dfbe0760 
       e0aa99f1 c178f800 def6a400 dfbe0760 e0abaf00 def6a400 dee1cdc8 e0a6f077 
Call Trace:
 [<e0aa9b47>] eu_disconnect_postfirm+0x135/0x208 [eagle_usb]
 [<e0a74374>] usb_disable_endpoint+0x29/0x61 [usbcore]
 [<e0aa99f1>] eu_disconnect+0x117/0x138 [eagle_usb]
 [<e0a6f077>] usb_unbind_interface+0x31/0x5b [usbcore]
 [<c01d47f9>] device_release_driver+0x40/0x4b
 [<c01d499b>] bus_remove_device+0x39/0x68
 [<c01d3de0>] device_del+0x43/0x67
 [<e0a7445a>] usb_disable_device+0x73/0xe4 [usbcore]
 [<e0a70a64>] usb_disconnect+0x95/0x10c [usbcore]
 [<e0a71457>] hub_port_connect_change+0x5e/0x313 [usbcore]
 [<e0a71930>] hub_events+0x224/0x2da [usbcore]
 [<e0a719e6>] hub_thread+0x0/0xe4 [usbcore]
 [<e0a71a03>] hub_thread+0x1d/0xe4 [usbcore]
 [<c0116ca8>] autoremove_wake_function+0x0/0x3a
 [<c0105e72>] ret_from_fork+0x6/0x14
 [<e0a719e6>] hub_thread+0x0/0xe4 [usbcore]
 [<c0116ca8>] autoremove_wake_function+0x0/0x3a
 [<c01041e1>] kernel_thread_helper+0x5/0xb
Code: 0f 0b 08 06 b2 f4 25 c0 bb 8c a5 34 c0 89 d9 ff 0d 8c a5 34 
 <7>irda_init()
NET: Registered protocol family 23
ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 193
PCI: Setting latency timer of device 0000:00:11.5 to 64
SysRq : Terminate All Tasks
ACPI: Power Button (FF) [PWRF]
NET: Registered protocol family 10
IPv6 over IPv4 tunneling driver

``` 

I updated hotplug to the latest version (debian testing), but already got the same message with the standard ubuntu hotplug.

I also tried boot parameters noapic nolapic acpi=off nosmp (in different combinations), no change...

I've run out of ideas, think I need help from an expert...

(PS Should I file this as a bug in Bugzilla?)

---

### Post by Bart Van on 2004-12-31
Well, I seem to have solved the problem - I got it working on 2 consecutive startups...

It seems that the eagle-usb-2.0.0 driver for my ADSL-modem (USB Sagem Fast 800) causes the problem. I did ```
cd /etc/init.d
sudo chmod a-x eagle-usb
``` to disable this service at startup, and now everything works perfectly. The message "eagle-usb already started" (or something similar) passes a few times, but the boot-process goes on nicely.

After that, in Gnome, I start (and sometimes restart) my internet connection with ```
sudo stopadsl
sudo eaglectrl -w
sudo startadsl -s
```

One more happy Ubuntu-user  :D

---

### Post by Bart Van on 2004-12-31
OK, seem to have solved the problem, apparently it is related to the eagle-usb-driver for my USB ADSL-modem (Sagem Fast 800).

I removed the eagle-usb packages I installed previously ```
sudo apt-get remove --purge eagle-usb*
``` and installed [eagle-usb-2.0.0.tar.bz2](http://baud123.free.fr/eagle-usb/eagle-usb-2.0.0/eagle-usb-2.0.0.tar.bz2)  **manually** (see [eagle-usb.org](http://www.eagle-usb.org/) for more info).

(For this I also installed linux-headers-2.6.8.1-4-386 and gcc using Synaptic, to be complete).

The hotplug version I use is 0.0.20040329-16, got it from the [debian repositories](http://packages.debian.org/testing/admin/hotplug). At eagle-usb.org [they said](http://forum.eagle-usb.org/viewtopic.php?t=2889&highlight=hotplug+woody) that the woody versions of hotplug don't work...

Anyway, one happy Ubuntu-user more :D

---

### Post by animalstyle on 2004-12-31
Good job.  You should probably file a bug report though, so maybe they can fix it in case someone runs into the same problem you did.  Good luck with your workin' system, its easy to spend too much time with it  :mrgreen:

---

