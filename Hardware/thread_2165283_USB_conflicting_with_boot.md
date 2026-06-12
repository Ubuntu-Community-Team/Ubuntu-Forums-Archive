---
title: "USB conflicting with boot"
date: 2013-08-04
forum: Hardware
---

### Post by feardotcom on 2013-08-04
So i have a problem. first i'm running 13.04. Second, it seems to be that my USB devices are causing boot problems. At first i thought it was a HDD issue which it partly was, but i re-installed to another drive that was not failing. When it boots it hangs at a black screen with a flashing dash. If i unplug all of my usb devices the PC will then boot. Sometimes immediately and sometimes after a few seconds. This really has me puzzled and i cant find any information. Any ideas?

---

### Post by VMC on 2013-08-04
Try this and report back with the messages. Boot only without any USB devices attached.

Once booted, Type the following into a terminal
```
tail -f /dev/syslog
``` Then insert the USB device. Wait until the device is fully mounted, then copy/paste back here.

---

### Post by feardotcom on 2013-08-07
Sorry about the late reply.

That kind of wont work because my mouse is usb. I dont have a ps/2 mouse at all anymore.

---

### Post by oldfred on 2013-08-07
Some systems have settings for USB ports to enable USB keyboard & mouse.
Some new systems have Intel NIC setting that seems to cause issues.
And fast boot can cause issue as USB drivers are slow to load. Fast boot may boot system before USB drivers load and you need a full boot to get USB drivers loaded first.

       Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.

---

### Post by VMC on 2013-08-07
> **feardotcom said:**
> So i have a problem. first i'm running 13.04. Second, it seems to be that my USB devices are causing boot problems. At first i thought it was a HDD issue which it partly was, but i re-installed to another drive that was not failing. When it boots it hangs at a black screen with a flashing dash. If i unplug all of my usb devices the PC will then boot. Sometimes immediately and sometimes after a few seconds. This really has me puzzled and i cant find any information. Any ideas?
Interesting idea. I never thought about USB mouse causing issues. I have a USB mouse, but I don't have any issue with booting to a desktop. But I will have to give this some though in the future. What gave you the idea of unplugging your USB mouse?

---

### Post by oldfred on 2013-08-07
Do you still have fastboot still turned on?

 It turns out the loading of USB drivers is somewhat slow. Fastboot with UEFI skips a lot of reinitialization, so you may not see a new device in a USB port.

   [http://mjg59.dreamwidth.org/24869.html](http://mjg59.dreamwidth.org/24869.html)

   > One of the requirements for Windows 8 certified hardware is that it must complete firmware initialisation within a specific amount of time, something that Microsoft refer to as "Fast Boot". Meeting these requirements effectively makes it impossible to initialise USB, and it's likely that certain other things will also be skipped.

---

### Post by feardotcom on 2013-08-07
@VMC

I have a razer deathadder mouse and i kept noticing that the lights on the mouse would either stay lit up when the black with flashing - or sometimes it would go out like the mouse wasn't connected. It's not just my mouse it's also my usb wifi adapter. Sometimes it only takes the mouse to boot, sometimes it only takes the wifi adapter, sometimes, it takes both, and sometimes it boots just fine. Whenever it's disconnected it boots within seconds.

@oldfred

I dont think my mobo supports uefi, or fastboot, But i do have ahci enabled. Also, this is not a Win8 machine. I built my desktop back when win 7 came out.

---

