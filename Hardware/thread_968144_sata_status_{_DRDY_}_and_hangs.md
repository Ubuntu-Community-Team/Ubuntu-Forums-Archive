---
title: "sata status { DRDY } and hangs"
date: 2008-11-02
forum: Hardware
---

### Post by graylion on 2008-11-02
Hi guys

ever since i installed Intrepid on my box I am getting:

Nov  1 03:27:48 lionscage kernel: [ 2611.762897] ata5.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Nov  1 03:27:48 lionscage kernel: [ 2611.762915] ata5.01: cmd a0/00:00:00:08:00/00:00:00:00:00/b0 tag 0 pio 16392 in
Nov  1 03:27:48 lionscage kernel: [ 2611.762916]          cdb 4a 01 00 00 10 00 00 00  08 00 00 00 00 00 00 00
Nov  1 03:27:48 lionscage kernel: [ 2611.762917]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Nov  1 03:27:48 lionscage kernel: [ 2611.762920] ata5.01: status: { DRDY }
Nov  1 03:27:48 lionscage kernel: [ 2611.762945] ata5: soft resetting link
Nov  1 03:27:48 lionscage kernel: [ 2611.961369] ata5.00: configured for UDMA/33
Nov  1 03:27:48 lionscage kernel: [ 2611.976423] ata5.01: configured for UDMA/33
Nov  1 03:27:48 lionscage kernel: [ 2611.976444] ata5: EH complete

together with regular hangs of the system

any idea?

---

### Post by quackking on 2008-11-22
I have the same problem, and I am very disappointed that there seems to be no action at all from the Ubuntu folks on this. 

I have an AMD Athlon64 Dual Core mobo  (Gigabyte K8 Triton GA-K8U-939) with an optical DVD. There is an Nvidia 6200LE card installed, and the SATA BIOS boot message identifies it as a VIA VT8237 Series SATA settings utility version V4.90. There are two WDC 250GB SATA drives attached to the motherboard.

Running 2.6.27-7 (Nov 4) I get the DRDY hang within an hour or so of booting (which makes the machine unusable.) The 'freeze' happens randomly - sometimes it is ATA1, sometimes 3, etc. 

Running Intrepid with the 2.6.22-14 kernel, it works fine (that is, I never get the DRDY -- Frozen bug. Of course I have other compatibility problems with this kernel.)

I've tried adding 

all_generic_IDE floppy=off IRQPOLL  hpet=disable 

to the kernel argument line, and I have set my BIOS to RAID. Absolutely no effect. None of these do anything. This problem is definitely something that entered the Ubuntu kernel after 2.6.22-14.

There must be fifty threads with various versions of this same problem, and NOBODY HAS COME UP WITH A FIX.

HELP HELP HELP!!!!

---

### Post by Yezinki on 2008-11-22
Personally never liked Via Chipset mobos.

Try Via Forums for assistance.

Regards,

Yezinki.

---

### Post by quackking on 2008-11-22
The issue is really why does the 2.6.22 kernel work while newer versions  fail. Obviously this is a kernel, not a chipset, problem. You could also say 'why not use Mandriva, it doesn't have this problem' (true, by my test, btw.) 

Somebody on the kernel team would probably love to identify and fix this IN THE Ubuntu-distributed KERNEL. Suggesting that hundreds of thousands of VIA chipset mobos get shoved into a landfill someplace is not helpful.

---

### Post by Yezinki on 2008-11-22
2.6.22 kernel is compatible with the chipset whilst the newer one isn't.

Regards,

Yezinki.

---

### Post by quackking on 2008-11-22
Yes, you are restating the problem, which is that there is a bug in the kernel. 

It is the kernel's job to support hardware, and in particular, popular chipsets are generally not orphaned. I suspect this is not a policy move by Linus ('Hey, dudes, I hate VIA, so let's blow off their SATA support' sounds like a phrase he DID NOT utter.)

In other words, this is a bug that can be fixed. If the kernel supports ancient 486 legacy hardware (it does, I use it on a bunch of odd, old stuff) then it can include some sort of support for the VIA SATA implementation.

Also I  don't think that this problem is confined to VIA, since it seems that users of other mobos also have reported DRDY - frozen. Nor is it completely true that 2.6.27 'does not support' VIA, since I have installed Mandriva 2009.0 on this same box and their kernel (2.6.27.4-x) does not exhibit the buggy behavior. It is an Ubuntu problem.

OT: Just wondering - you say 'you don't like' VIA. Why? Feel free to reply with a PM to this part of the post.

---

### Post by Yezinki on 2008-11-23
Via Chipsets are buggy, poorly designed  architecture, substandard......I buy Via when Im broke!

Regards,

Yezinki.

---

