---
title: "hard drive issues"
date: 2009-02-22
forum: Hardware
---

### Post by belfasttim on 2009-02-22
Hi-- I'm hoping a hardware guru can help me track down what's going wrong with my desktop machine.

I have a desktop with an ASUS M2n-SLI motherboard with AMD Phenom 9850 quad core chip, 8GB RAM, and two 500 GB Seagate SATA hard drives. One of the drives functions as the /home directory, the other is the boot and OS drive, and is also used for backups of the home drive.

It's running Ubuntu 8.1 64bit, and pretty much since install (when I built the machine new) it's been acting very strangely. Often on boot I'll get Grub errors, usually error 16, and once in a while I get bad sector disk errors. I've also seen "inconsistent filesystem" errors on boot. In the logs I often find I/O errors, at which point the machine will lock up. Sometimes Ubuntu boots fine, but the home directory is inaccessible which means settings don't load.

The strange thing is that a reboot almost always solves the problems, and it'll run fine for days, at which point the errors come back. I updated the bios, and have tried several settings in the bios thinking that maybe these settings were the issue, with no resolution. 

It seems likely that a drive is bad, and I've been using the smartmontools package to try and catch any errors-- but the tests always come back passed, and there's nothing in the smartctl logs that seem to be troublesome. When Ubuntu runs the disk check at startup it never reports any errors either. The other odd thing (that makes me think it may be motherboard/bios/sata related) is that I've tried using one disk or the other alone, and I still get errors-- and I doubt both disks could be bad.

Any help most appreciated-- I am happy to post logs or run diagnostics, just tell me what you need. 

Thanks

---

### Post by belfasttim on 2009-02-28
I thought I'd add a little more info since no one has responded-- 

the usual pattern is I'll be working fine for hours (or days) and something goes a little haywire (most recently, konsole would crash whenever I tried to do an ls command). When I restarted X, as it tried to shutdown I got a bunch of errors saying end_request: I/O error, dev sdb, sector XXXX
end_request: I/O error, dev sdb, sector XXXX
end_request: I/O error, dev sdb, sector XXXX
end_request: I/O error, dev sdb, sector XXXX

When I restart, I'll get a 
ATA6: comreset failed (errno: -16)
ATA6: comreset failed (errno: -16)
ATA6: comreset failed (errno: -16)
ATA6: comreset failed giving up

and sometimes after GRUB tried to load it'll give an Error 16, inconsistent filesystem

Any ideas?

---

### Post by tgalati4 on 2009-02-28
What specific model drives and what does hddtemp say?

Sometimes new drives need breaking in before use.

Post output of:

sudo badblocks /dev/sda1
sudo badblocks /dev/sdb1

---

### Post by belfasttim on 2009-03-01
Hi tgaliti4-- drives are Seagate 500GB Serial ATA HD 7200/32MB/SATA-3G, manufacturer's part # ST3500320AS SY

I ran both commands you posted, and they printed nothing-- so I ran with the -o flag, and the output file was empty. I can try again on verbose if that makes a difference.

hddtemp is reading 27C.

---

### Post by mrwoody on 2009-03-01
Hi!

I also have a lot of problems with my hdd. It is connected through USb using a hdd enclosure (which has a fan), but it only lasted few months. 
It seems that testdisk gives me hundreds of errors like this one:

file_read(5,1,buffer,334939269(20849/1/22)) read err: Input/output error

Does it mean that the hdd is dead? 

**Thanks!**

---

### Post by belfasttim on 2009-03-01
> **belfasttim said:**
> Hi tgaliti4-- drives are Seagate 500GB Serial ATA HD 7200/32MB/SATA-3G, manufacturer's part # ST3500320AS SY

I ran both commands you posted, and they printed nothing-- so I ran with the -o flag, and the output file was empty. I can try again on verbose if that makes a difference.

hddtemp is reading 27C.

Update-- just finished running badblock with -ov, and both drives reported 0 bad blocks.

---

### Post by belfasttim on 2009-03-01
Any other ideas or tests I ought to run?

Thanks

---

### Post by tgalati4 on 2009-03-01
Your drives may be OK, but your power supply may be the issue.  Use a volt meter to measure the power from the Yellow and Black leads in a spare drive power connector.  Any dips below 12 volts DC could mean that your 8 Gigs of memory and Quad Core Monster CPU are sucking up the power.  You probably need 750 to 1000 watt PSU.

Although not convenient for your setup, try running with one drive alone for a while.

A quick google on ST3500320AS brings up numerous issues: firmware, sudden failures, and Seagate's quality control.

@mrwoody:  Yes, portable drives don't get the cooling or power they need to run properly so drives do tend to fail quicker.  If it fell over or was kicked during an impromptu soccer match, then it may have crashed.  You may be able to recover with:

sudo fsck -cc /dev/sda1      (the -cc switch marks the badblocks and tries to move the data to better locations.)  I wouldn't rely on the drive for critical operations.

---

### Post by belfasttim on 2009-03-01
> **tgalati4 said:**
> Your drives may be OK, but your power supply may be the issue.  Use a volt meter to measure the power from the Yellow and Black leads in a spare drive power connector.  Any dips below 12 volts DC could mean that your 8 Gigs of memory and Quad Core Monster CPU are sucking up the power.  You probably need 750 to 1000 watt PSU.

Although not convenient for your setup, try running with one drive alone for a while.

A quick google on ST3500320AS brings up numerous issues: firmware, sudden failures, and Seagate's quality control.

Thanks tgaliti4-- I have my meter hooked up and ran through a couple power up/shutdown cycles, and it seems to be solidly 12V+. However, I'll try a 
"cold" startup and see if that's a factor.

I will also check with Seagate and see if there's anything they can tell me.

In dmesg, it looks like the drives are running at 1.5GB/s rather than the 3GB/s that the mobo and drives are rated for. Is there any obvious reason for this?

```
[    4.256025] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.264496] ata6.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    4.264499] ata6.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    4.280477] ata6.00: configured for UDMA/133
```

---

### Post by tgalati4 on 2009-03-02
The SATA link speed is not important.  Physical drive limitations will slow transfers to 77 MB/sec or 0.616 Gbits/sec.  So you are running at more than twice that.

Make sure your drives are screwed in tight.  7200 rpm can cause vibrations which can lead to read errors.

Try one drive and see if you can get 3 Gbits/sec.

sudo  hdparm -tT /dev/sda1

---

### Post by belfasttim on 2009-03-05
> **tgalati4 said:**
> The SATA link speed is not important.  Physical drive limitations will slow transfers to 77 MB/sec or 0.616 Gbits/sec.  So you are running at more than twice that.

Make sure your drives are screwed in tight.  7200 rpm can cause vibrations which can lead to read errors.

Try one drive and see if you can get 3 Gbits/sec.

sudo  hdparm -tT /dev/sda1

Hi tgaliti-- thanks for the tips. I have a case that has the clamp-style drive mounts, not screws, and they seem secure. I tried the hdparm command and got ~3GB/sec on cached reads, 97MB/sec on buffered.

I also went ahead and copied all the partitions from the drive that had been giving most errors, /dev/sdb, which was also the boot drive.

I spent most of the day on this, copying and resizing partitions and resetting GRUB and the boot options, and I had high hopes that maybe sdb was just a bad drive. 

I left the machine running for a while after successfully booting and shutting down a few times to make sure it was all working, and had totally disconnected sdb. To my great disappointment, I tried to reply to an email and the application locked up. I hit control-alt-F1 to see if I could learn anything from the command line, and there was my old friend, a long string of I/O Error: /dev/sda etc. etc.

Very frustrating-- I know it's possible both drives are bad, but all tests have said the drives are fine and the power is fine. Can it be that there's an issue reading/writing to SATA drives in certain circumstances, or that perhaps my BIOS/motherboard is disagreeing with the drives?

Any help or further data I can provide, please let me know.

---

### Post by tgalati4 on 2009-03-06
If you were a PC builder, you wouldn't sell this combination to a customer.

97 MB/sec is faster than 77 MB/sec that I get from my Western Digital Raptors.  You have verified that you are getting 3 Gbits/sec through the SATA bus.

Since you are using 64-bit Ubuntu, I have sometimes experience strange behavior using it.  I would burn a disk of Hardy 32-bit and boot from it.  See how reliable your system is running from the Live CD.  If you get several days of uptime without I/O errors then I would wipe the machine and install 32-bit on a small (10 -20 GB) partition and boot off of that and run it for several days.  

You need to isolate hardware from software and 32-bit Hardy is relatively stable.  It's possible there is some problem with 64-bit, the AMD multi-core processor, and the ASUS motherboard.

This is what we call an *edge* case.

---

### Post by belfasttim on 2009-03-06
Thanks for all your help tgaliti!

---

