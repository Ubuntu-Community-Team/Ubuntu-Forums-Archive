---
title: "[SOLVED] &amp;quot;Suspend failed&amp;quot; message...but runs fine?"
date: 2008-06-21
forum: Hardware
---

### Post by Doc Hoss on 2008-06-21
Sometimes when I open the lid for my laptop after having simply closed it (and thus activating suspend), I get a message in the system panel area in a little "speech balloon" of: "Your computer failed to suspend.  See the help file for common problems."  I looked at the help file but can't seem to find anything that would apply to me.  Maybe I just missed it?  Here's a log snippet...

```
Jun 21 02:38:08 XXX-laptop gnome-power-manager: (XXX) Suspending computer because the lid has been closed on ac power
Jun 21 02:38:10 XXX-laptop kernel: [  410.276000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 21 02:38:11 XXX-laptop kernel: [  410.976000] pccard: card ejected from slot 0
Jun 21 02:38:11 XXX-laptop kernel: [  411.276000] ndiswrapper: device wlan0 removed
Jun 21 02:38:11 XXX-laptop kernel: [  411.276000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Jun 21 02:38:11 XXX-laptop kernel: [  411.812000] usbcore: deregistering interface driver ndiswrapper
Jun 21 11:53:02 XXX-laptop gnome-power-manager: (XXX) An unknown error occured code='32' quark='g-exec-error-quark'
Jun 21 11:53:02 XXX-laptop gnome-power-manager: (XXX) Resuming computer
Jun 21 11:53:02 XXX-laptop kernel: [  417.196000] Disabling non-boot CPUs ...
Jun 21 11:53:02 XXX-laptop kernel: [  417.196000] Stopping tasks ... done.
Jun 21 11:53:02 XXX-laptop kernel: [  418.420000] Suspending console(s)
Jun 21 11:53:02 XXX-laptop kernel: [  419.736000] pnp: Device 00:0e disabled.
Jun 21 11:53:02 XXX-laptop kernel: [  419.740000] pnp: Device 00:0d disabled.
Jun 21 11:53:02 XXX-laptop kernel: [  419.784000] ACPI: PCI interrupt for device 0000:00:08.0 disabled
Jun 21 11:53:02 XXX-laptop kernel: [  419.800000] ACPI: PCI interrupt for device 0000:00:07.2 disabled
Jun 21 11:53:02 XXX-laptop gnome-power-manager: (XXX) suspend failed
Jun 21 11:53:02 XXX-laptop kernel: [33696.820000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jun 21 11:53:02 XXX-laptop kernel: [33696.820000] usb usb1: root hub lost power or was reset
Jun 21 11:53:02 XXX-laptop kernel: [33696.836000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Jun 21 11:53:02 XXX-laptop kernel: [33697.388000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jun 21 11:53:02 XXX-laptop kernel: [33697.388000] pnp: Device 00:05 does not support activation.
Jun 21 11:53:02 XXX-laptop kernel: [33697.388000] pnp: Device 00:06 does not support activation.
Jun 21 11:53:02 XXX-laptop kernel: [33697.424000] pnp: Device 00:0d activated.
Jun 21 11:53:02 XXX-laptop kernel: [33697.480000] pnp: Device 00:0e activated.
Jun 21 11:53:02 XXX-laptop kernel: [33701.504000] Restarting tasks ... done.
```

**User names have been changed to protect the innocent.**

---

### Post by brujoand on 2008-09-13
Same problem, even after re-install. SemiHardware related?

---

### Post by IntuitiveNipple on 2008-09-13
Does the PC actually suspend when the lid is closed? Usually the only sign of life will be a power LED that flashes to show it isn't completely powered down.

The log-file extract shows that suspend failed. The reason is probably a driver that can't or won't handle the suspend request.

Post the output of:
```

lspci -nn

lsusb

```
and attach a (compressed) copy of the output of lsmod:
```

lsmod | gzip > lsmod.log.gz

```

---

### Post by brujoand on 2008-09-13
lspci -nn:
> 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:04.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
01:04.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 01)
01:04.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)


lsusb, I dont have anything attached, so nothing.

and, yes it goes to suspend, but for some reason, it "thinks" it failed.

---

### Post by fiddler616 on 2008-09-13
I've gotten the same little bubble on several (I think I'm up to three?) re-installs, yet it always seems to suspend/un-suspend properly, so I haven't really worried about it (until I saw this was the featured thread)

---

### Post by IntuitiveNipple on 2008-09-13
> **GrimmVarg said:**
> and, yes it goes to suspend, but for some reason, it "thinks" it failed.
Now you confirm it, the log extract does just-about show the same thing although it would be useful to see reports for the five seconds or so leading up to the suspend.

Could you do a test? Remove the existing /var/log/kern.log and then do a suspend with a fresh log-file. Let the PC remain suspended for *exactly* ten minutes (this is so the time-stamps are clearly different *and* any resume clock randomness can be seen) and then resume it. Give it a couple of minutes to settle down then attach a (compressed) copy of /var/log/kern.log to a reply here so we can see the full sequence.

It appears to be reported by others in [Launchpad bug #89983 Feisty reports suspend failed after resuming from suspend](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/89983)

---

### Post by brujoand on 2008-09-13
well, i removed the kernel.log, and suspended, waited 10 minutes. But now, 4minutes after i came back from suspend, there is no krenel.log file.

Did i mess up somewere?

---

### Post by IntuitiveNipple on 2008-09-13
> **GrimmVarg said:**
> well, i removed the kernel.log, and suspended, waited 10 minutes. But now, 4minutes after i came back from suspend, there is no krenel.log file.

Did i mess up somewere?
Um no, probably I did. I was pretty sure sysklogd would recreate the file automatically but it looks like my memory of doing it previously is wrong. It needs an empty file recreating and sysklogd restarting:
```

sudo rm /var/log/kern.log
sudo touch /var/log/kern.log
sudo /etc/init.d/sysklogd restart

```
If you check the file permissions after that they should look like this:
```

ls -l /var/log/kern.log

-rw-r--r-- 1 syslog adm 0 2008-09-13 13:20 /var/log/kern.log

```

---

### Post by brujoand on 2008-09-13
Ok, so i touched it and all is well. did a suspend like last time, and here is the kernel.log:

---

### Post by IntuitiveNipple on 2008-09-13
That is a good log-file. Everything I expected to see; nothing unexpected.

Did Gnome still report a failed suspend?

---

### Post by brujoand on 2008-09-13
nope, not this time.. I'll try to repost after the next time it "fails", thanx

---

### Post by IntuitiveNipple on 2008-09-13
> **GrimmVarg said:**
> nope, not this time.. I'll try to repost after the next time it "fails", thanx
That's "Sod's Law" in operation - when you want it to fail it doesn't :p

---

### Post by brujoand on 2008-09-15
Ok, so in breake between lecturehours today I brought my laptop up from suspend, BEEEEP!!! I got peoples attention allright :P

I attached the kernel.log and dmesg just in case that helps. The wakeup was done at 11:00.

Hope this helps

Anders

---

### Post by IntuitiveNipple on 2008-09-17
It was suspended at 19:18 the evening before, and resumed at 11:00 ?

The log files seem to confirm a good suspend/resume cycle. There are no clues regarding reporting a failed suspend.

Did gnome-power-management report a failed suspend?

Does the "BEEEEP" indicate it made some kind of unexpected noise? If so, did that happen on previous occasions?

---

### Post by brujoand on 2008-09-17
> **IntuitiveNipple said:**
> It was suspended at 19:18 the evening before, and resumed at 11:00 ?

Correct

> **IntuitiveNipple said:**
> 
Did gnome-power-management report a failed suspend?


Yupp

> **IntuitiveNipple said:**
> 
Does the "BEEEEP" indicate it made some kind of unexpected noise? If so, did that happen on previous occasions?

The beep comes whenever the report of failed suspend comes. And I am pretty confident that this only happens when th ecomputer has been in suspend over a long period, say 5-6 hours.

This is really stating to bug me, since the only obvious error, is the report of a failed suspend. I guess will just have to wait and pray for a fix in 8.10, since this error is reported in launchpad.
But thanks four your help InNipp!

Anders

---

### Post by IntuitiveNipple on 2008-09-18
A recent release to hardy-proposed may fix the issue for you:

[Suspends that are longer than 6 hours will inexplicably claim to fail, but not really fail](https://bugs.edge.launchpad.net/ubuntu/+bug/242713)

The [package publishing information](https://launchpad.net/ubuntu/+source/gnome-power-manager)

---

### Post by Doc Hoss on 2009-01-10
Just checking in on this thread...hadn't looked at it in a while.  I think this must have been fixed by an update (probably the one mentioned by IntuitiveNipple...awesome ID by the way), so unless anyone comes back with strong objections, I'll mark this one solved!

Thanks very much for all your help, all who contributed.

---

