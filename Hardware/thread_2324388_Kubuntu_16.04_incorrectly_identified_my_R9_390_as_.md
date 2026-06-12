---
title: "Kubuntu 16.04 incorrectly identified my R9 390 as a 290."
date: 2016-05-13
forum: Hardware
---

### Post by silverbullet007 on 2016-05-13
First off I know these chipsets are supposed to be similar, but I worry that when I try the new amdgpu drivers coming out that since the OS does not correctly identify my card that they might not either.  Anyway have this before?  Any clue what I can do?

THanks

---

### Post by silverbullet007 on 2016-05-13
Should I try using the bios file with this?
[https://www.techpowerup.com/vgabios/175728/gigabyte-r9390-8192-150605](https://www.techpowerup.com/vgabios/175728/gigabyte-r9390-8192-150605)

---

### Post by QIII on 2016-05-13
I would suspect that the identification is a matter of the relatively recent release of the Grenada-based 390s versus the Hawaii-based 290s.  (They are very similar, but the 390 is not just a rebrand.)

A bigger concern for you at the moment is that AMDGPU will not work with the R9 290s or 390s, which use GCN 1.1 architecture.  It will only work presently with the Volcanic Islands chipsets using GCN 1.2 architecture:  Tonga and Fiji.

There is experimental support right now for GCN 1.1 architecture, but to use it you'll have to roll your own kernel.  We'll have to wait until the end of Summer to see if AMD includs GCN 1.1 (and maybe 1.0) chipsets.

---

### Post by silverbullet007 on 2016-05-13
I found some reference to that elsewhere but did not want to take it at face value.  I mean why leave out the 390 since it's so new?  So Qlll is the only option I have left to run with 'radeon' driver with it's rather craptastic performance?

---

### Post by QIII on 2016-05-13
For right now, the Radeon driver is it in 16.04.  You can go back to, say, 14.04 of course.

Rumor (only rumor) has it that as the development of AMDGPU goes on, GCN 1.1 will be supported by the time the 4.7 kernel arrives.  But I can't confirm that.

But I can tell you that the R9 380X I bought for testing runs brilliantly on AMDGPU (once I figured out where all the KDE5 setting are).  Almost as good as fglrx, but without the nice interface and fine adjustments.  AMDGPU Pro should be very nice.

---

### Post by Yellow Pasque on 2016-05-13
As for the original question, lspci might shed some light:
```
sudo update-pciids
lspci -nn | grep -i vga
```

---

### Post by silverbullet007 on 2016-05-13
Temujin, That's actually how I discovered the name mis-match.

My initial project was to setup linux and virtualize my Win10 gamer.  I lucked into a nice video card, then a mobo/cpu upgrade and thought 'What the hell'.  But I've had quirkiness with the pci-passthrough in QEMU/KVM so that projects kinda halted.  So now I wondered what kind of perf I could get natively in Kubuntu.

---

### Post by silverbullet007 on 2016-05-13
And thanks QIII.. is there an eta or a time frame for 4.7?

Nevermind.. I found it.

---

### Post by Yellow Pasque on 2016-05-13
Solved?

---

### Post by silverbullet007 on 2016-05-13
Possibly.. the rig is at home so I won;t know until later tonight.

---

### Post by silverbullet007 on 2016-05-16
sudo update-pciids
lspci -nn | grep -i vga

Actually still showed my card as a 290.  Not sure what the deal is however I decided to toss WIn10 on the second SSD for now, until 4.7 hits the shelves or until AMDGPU supports me card.

---

### Post by silverbullet007 on 2016-05-16
I am going to try kernel 4.6 and see if anything changes.

---

