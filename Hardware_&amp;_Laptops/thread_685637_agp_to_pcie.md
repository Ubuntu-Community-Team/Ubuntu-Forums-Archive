---
title: "agp to pcie"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by MooseMuffin on 2008-02-02
Hi everyone.  I have both agp and pcie slots on my motherboard, and I just replaced my agp card with a new pcie one.  Ubuntu didn't seem to like this however, and now I get no video when I boot up.

I figured my xorg.conf was still looking for the agp card, so I booted into recovery mode and had it generate a new xorg.conf, but this hasn't seemed to help.  Both the old and new card were nvidia, so I don't think the driver needs to change.  What else should I try?

---

### Post by Yellow Pasque on 2008-02-02
What kind of nvidia cards are we talking about here? THere are a few different nvidia drivers for different ages of cards.

Assuming they use the same driver, the other thing I would suggest is making sure the BusID is correct. When you're at a terminal, run:
```
sudo update-pciids
lspci | grep VGA
```
Then you should make a BusID line in your xorg.conf's Device section that uses the three numbers at the beginning of that line. The formatting is different, so I'll show my system for example:
```
dan@harvest:/$ lspci | grep VGA
**01:05.0** VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
```
```
Section "Device"
        Identifier      "Generic Video Card"
        **Busid           "PCI:1:5:0"**
        Driver          "radeonhd"
EndSection
```

---

### Post by MooseMuffin on 2008-02-02
Thanks for the reply.

The old card was an agp 7800gs.  The new card is a 8800gt.  I think those are both new enough to be using the same driver.

The lspci command came back with 01:00.0, and my xorg.conf shows PCI:1:0:0, which I think means its correct.

What settings is this 'recovery mode' using that enables it to give me video, while the normal bootup can't?

---

### Post by Yellow Pasque on 2008-02-02
I'm guessing recovery mode is using the generic VESA driver.
Try this to make sure your xorg.conf is set right:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by MooseMuffin on 2008-02-02
Hmm ok.  I have the vesa driver working now, which is great.  Neither the nvidia nor the nv driver seem to work however.  Is the 8800 series not supported?  If I go into the device manager I see:

vendor:  nVidia corporation
product:  Unknown (0x0611)

---

### Post by MooseMuffin on 2008-02-02
Nevermind.  Envy seems to have done the trick.  I didn't know the 8800gt wasn't supported by the repository drivers.

---

