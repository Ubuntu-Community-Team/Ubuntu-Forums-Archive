---
title: "Laptop Won't boot!"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by Achetar on 2007-10-05
Oh shoot, I just rebooted and now it refuses to finish booting!

I did a hard shut off and here is where it freezes (taken from recovery mode):

```

natsemi eth0: NatSemi DP8381[56] at 0xc0009000 (0000:00:12.0), 00:0b:cd:7b:19:97, IRQ 10, port TP.
hda: max request size: 128KiB
hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
hda: cache flushes supported
  hda: hda1 hda2 hda3 hda4
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
Uniform CD-ROM driver Revision: 3.20
Done.
Begin: Running /scripts/local-premount ...
kinit: name_to_dev_t(/dev/disk/by-uuid/ec415338-734f-4d8a-9f21-bf49261adf84) = hda4(3,4)
kinit: tring to resume from /dev/disk/by-uuid/ec415338-734f-4d8a-9f21-bf49261adf84
Attempting manual resume
kinit: No resume image, doing normal boot...
Done.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: hda2: orphan cleanup is readonly fs

```

I am typing this on a different computer (running WinXP unfortunately).

I have 2 OSs on my HD on my laptop, WinXP and Ubuntu Feisty. I will boot into Windows then attempt to reboot into Ubuntu to fix the problem.

Also, my ndiswrapper stuff has been having trouble.
Do you think they may be connected? (or just i need to get new ndiswrapper)

EDIT: Just tried booting into Win then back into Ubuntu, same stuff.

---

### Post by louieb on 2007-10-05
J> ust tried booting into Win then back into Ubuntu, same stuff.Did Window boot up normally? 

Can you boot to Ubuntu if you plug the laptop into a wired Ethernet connection?

What I'm wondering about is the health of the hard drive.

---

### Post by Achetar on 2007-10-09
It did boot into Windows Normally. And I was able to get my files off Ubuntu, so I went ahead and reformatted that partition of my HD to Xubuntu (the newest Ubuntu CD i had was 6.10, Xubuntu CD 7.04). It works now. No clue what happened.

---

