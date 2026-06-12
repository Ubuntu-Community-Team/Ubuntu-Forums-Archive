---
title: "HDD trouble"
date: 2009-05-28
forum: Hardware
---

### Post by iandotcom on 2009-05-28
Hey everyone,

I ran into a bit of a problem with my laptop. Last night, I held the power switch to turn off the laptop, I turned it back on, and Ubuntu started to display errors on the boot screen, and the general performance of the laptop is laggy.

I was able to back up all my files onto another drive, and I've tried formatting everything and reinstalling with a fresh copy of 9.04, but no cigar.

Below is a snippet of what text is spat out on boot from the logs.

```

ata1.00: status: { DRDY ERR }
ata1.00: status: { UNC }

```

It's a little bit more verbose because I'm unsure where I can find the log created on boot, but after a couple of instances of this message, boot continues. I am able to log in, connect to a network, and do other things, but overall performance is very slow. I've ran fsck on a number of occasions, and sometimes I get a clean drive, and some instances I get errors reported back.

I noticed the problem doesn't happen when you install on a single partition, but I'd like to have separate partitions for the OS and the home folders for maintenances sake :)

The hard drive is 200 GB in a Toshiba Satellite L300.

Can anyone give my any guidance?

Thanks a bundle -- Ian.

---

### Post by dargaud on 2009-05-28
Type dmesg in a console to get the boot log.

---

### Post by iandotcom on 2009-05-28
Cheers, heres the full error that appears:

```

[   19.317018] ata1.00: exception Emask 0x0 SAct 0x6ff7f SErr 0x0 action 0x0
[   19.317023] ata1.00: irq_stat 0x40000008
[   19.317032] ata1.00: cmd 60/f0:70:3f:f8:14/02:00:00:00:00/40 tag 14 ncq 385024 in
[   19.317035]          res 41/40:f0:ff:fa:14/00:02:00:00:00/60 Emask 0x409 (media error) <F>
[   19.317041] ata1.00: status: { DRDY ERR }
[   19.317045] ata1.00: error: { UNC }
[   19.318932] ata1.00: configured for UDMA/100
[   19.318959] ata1: EH complete
[   19.319032] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   19.319047] sd 0:0:0:0: [sda] Write Protect is off
[   19.319049] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.319073] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

I can attach a file with the whole dmesg output if needed. Any ideas?

---

### Post by dargaud on 2009-05-28
Off the top of my head (because those messages don't ring a bell), take a look around in your BIOS (press F1, F2 or DEL in quick successsion during boot even if you don't see anything). See if can can enable SMART options, 32 bit transfer and whatever else you see fit. Try a SMART tool (sudo aptitude install smartmontools). You can also try something like the UBCD (Ultimate boot CD) which contains various hard drive diagnostics tools.

---

