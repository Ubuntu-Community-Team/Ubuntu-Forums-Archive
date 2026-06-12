---
title: "Centrino laptop locks with ATAPI error message"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by NRios on 2005-06-07
Hi there!

I've got a no-name Centrino laptop running Hoary and it locks completely after a seeminly random length of time, running from a couple hours to maybe twelve.

The lockup is total, and there is no further response to keyboard or network; it wont respond to ssh or ping back; it will not shut down with a short push of the power bottom.

With the system recently booted, the last lines in /var/log/kern.log say;

    Jun  7 22:24:48 localhost kernel: speedstep-centrino: invalid ACPI data
    Jun  7 22:24:51 localhost kernel: eth0: no IPv6 routers present

After the system has locked up and then restarted, you can see these lines have been added right before the crash:

    Jun  8 00:02:11 localhost kernel: hdd: irq timeout: status=0xd0 { Busy }
    Jun  8 00:02:11 localhost kernel: hdd: irq timeout: error=0x00
    Jun  8 00:02:41 localhost kernel: hdd: ATAPI reset timed-out, status=0x80
    Jun  8 00:02:46 localhost kernel: ide1: reset: master: error (0x00?)
    Jun  8 00:02:46 localhost kernel: hdd: status timeout: status=0x80 { Busy }
    Jun  8 00:02:46 localhost kernel: hdd: status timeout: error=0x01IllegalLengthIndication
    Jun  8 00:02:46 localhost kernel: hdd: drive not ready for command
    Jun  8 00:03:16 localhost kernel: hdd: ATAPI reset timed-out, status=0x80

And then a new set of messages is appended on reboot, starting with

    Jun  8 00:45:54 localhost kernel: Inspecting /boot/System.map-2.6.10-5-686
    Jun  8 00:45:54 localhost kernel: Loaded 26806 symbols from /boot/System.map-2.6.10-5-686.
    Jun  8 00:45:54 localhost kernel: Symbols match kernel version 2.6.10.

This has happenned time after time, with different time spans between boot and crash. While working, the system seems to run fine, including the ATAPI DVD/CDR combo which reads and writes OK.

I have tried booting with "acpi=off noapic", but the system froze just the same.

Any idea what is this?

Thanx,

-Nacho-

---

### Post by Arthemys on 2005-06-08
One thought is that it doesn't like your hard drive falling asleep on you. (What it appears like to me) Might need to shut off apm too "apm=off" or check your BIOS settings. Do you know if your hard drive is physically good?

---

### Post by NRios on 2005-06-08
Thanks for your suggestion. However, I do not think that's it, because hdd is the CDROM, not the hard disk. Shouldn't it always be asleep?

I'm running now with "acpi=off noapic" and its been going for seven hours. There was a disk in the CDROM, which might make a difference, though. I have to try with ACPI and APIC on AND with a disk in the drive and see if it still crashes.

I will also try with the latest kernel, to see if ACPI support has gotten better.

Any other suggestions?

Thanks,

-Nacho-

---

### Post by s3phiroth on 2006-08-17
Altough this thread is old, i had already searched fot this and never found it. I have exactly the same problem. I've seen some pages and bug reports that describe similar problems but yours is the closest i could ever find, and i have never found a concrete solution. I had this problem in Breezy and still have it in Dapper.

I'll try turning off ACPI as well for the time being.

Oh, and i don't have a centrino based laptop, i have a pentium 4 based laptop .

---

