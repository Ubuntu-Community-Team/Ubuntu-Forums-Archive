---
title: "Booting up problems"
date: 2009-01-16
forum: Hardware
---

### Post by maka on 2009-01-16
Hey community,

I've been with ubuntu for awhile, and on my laptop, I always have a problem with hanging when it boots up.

During the splash screen with the progress bar, it begins hanging there (when there is a mini bar that slides back and forth if you know what i mean).  When it hangs, my caps lock begins to blink and ctrl+alt+delete won't work.  I have to kill it by holding power.

It happens very often when i start my machine up, often having to do it multiple times before it actually boots into my gnome.

Anyways, I'm wondering if anyone has issues like this?

I am using a Toshiba notebook (Toshiba Satellite M105-S3041 14.1" Widescreen Laptop (Intel Core Solo Processor T1350, 512 MB RAM)

I've searched around and tried editing my grub file with new options that these threads suggest, but to no avail.


Any ideas?  Probably a kernel problem? TIA

---

### Post by taurus on 2009-01-16
Edit /boot/grub/menu.lst and remove the **quiet splash** at the end of the entry for kernel.  Now, you would get the text printout of the screen when you boot and if it hangs, you would know which process that causes it.

---

### Post by maka on 2009-01-16
Ah, that's just what I needed.  Thanks for the tip.  I'll give this a try when I am off work.

---

### Post by maka on 2009-01-19
time to report back.

as you suggestd, i turned off the quiet and splash.

When it hanged this time around booting up, it seems it was stuck on:

"Starting Samba daemons"

This line did not receive the "OK" on the right of it and just hung there...

What does this mean?

TIA again

---

### Post by sully101 on 2009-01-19
Samba is the daemon that lets you connect to windows networks. You can disable it in System Services and see if that makes a difference.

---

### Post by maka on 2009-01-20
> **sully101 said:**
> Samba is the daemon that lets you connect to windows networks. You can disable it in System Services and see if that makes a difference.

thanks sully.  I did that.  Now another problem caused it to hang at bootup.  THis is the one that has been causing the caps lock to blink (the other one didnt).  There's a lot of lines, but i'll start typing where it looks like is having a problem...

~~~
[    3.081484] ohci1394: fw-host0: OHCI-1394 1.1 (PCI) IRQ=[17] MMIO=[d0007000-d00077ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.184003] Marking TSC unstable due to TSC halts in idle
[    3.184276] scsi0 : ata_piix
[    3.184691] scsi1 : ata_piix
[    3.186026] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    3.186087] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
/init: line 191: root_missing: not found
Done.
/init: line 191: root_missing: not found
/init: line 191: root_missing: not found
/init: line 191: root_missing: not found
/init: line 191: get_fstype: not found
Begin: Running /scripts/local-premount ...
[    3.285250] init[1] segfault at 0 ip 000e68a2 sp bf958fec error 4 in sh[8048000+e8000]
[    3.286304] Kernel panic - not syncing: Attempted to kill init!


Now, can any one decipher what this means?  I'm sure this has been the root of my booting problems.  TIA!  P.S. I also want to note that I've had Ubuntu for a number of years now (complete reinstall at every new final release), and this hang which causes the kernel panic with caps lock blinking has been happening throughout them.  I'm thankful it's intermittent ;-)

---

### Post by sully101 on 2009-01-21
Sorry I really cant tell what this is about. I would start to wonder if it is hardware related as the symptoms are intermittent. Do they happen when the laptop is hot? Have you done a memory test from the live cd lately? Do you have smart enabled on your hard drive? Have a look at smartmontools and smart-notifier.

I hope someone else with more experience in this area will be able to help. Or start another thread with the errors from your last post. Good luck :)

---

### Post by maka on 2009-01-22
> **sully101 said:**
> Sorry I really cant tell what this is about. I would start to wonder if it is hardware related as the symptoms are intermittent. Do they happen when the laptop is hot? Have you done a memory test from the live cd lately? Do you have smart enabled on your hard drive? Have a look at smartmontools and smart-notifier.

I hope someone else with more experience in this area will be able to help. Or start another thread with the errors from your last post. Good luck :)

Thanks Sully.  Actually, it happens more when the system is cold.  I noticed it starts more often than not after I've used it recently and shutted it down to start it back up.  But on a cold boot, it runs into this problem.  Also ran memtester for a couple of hours on this and had multiple passes... so I don't think it's the ram.  What could it be?

---

### Post by sully101 on 2009-01-23
> **maka said:**
> Thanks Sully.  Actually, it happens more when the system is cold.  I noticed it starts more often than not after I've used it recently and shutted it down to start it back up.  But on a cold boot, it runs into this problem.  Also ran memtester for a couple of hours on this and had multiple passes... so I don't think it's the ram.  What could it be?

Just a stab in the dark then. It could be that your hard drive is not getting enough time to spin up. Sometimes there is a setting in the bios to lenghten it to a couple of seconds. But I would still recomend smartmontools that I mentioned earleir.

---

