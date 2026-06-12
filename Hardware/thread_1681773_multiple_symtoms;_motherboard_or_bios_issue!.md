---
title: "multiple symtoms; motherboard or bios issue?!?"
date: 2011-02-04
forum: Hardware
---

### Post by phredbull on 2011-02-04
Reposted from Mint forums:

Hi, I just bought a used HP Compaq nx9110 laptop. I've installed Isadora  XFCE along side WinXP, and both are booting fine. A few problems in Mint  though:
-the Alps trackpad sensitivity is very low, and movement is jittery. I installed gsynaptics-pointing-devices, but no change.
-though  it seems that ALSA is seeing my sound card and loading the drivers,  whenever I try to play audio, it will play a tiny bit, then the program  will stop responding. I've tried cd's, Youtube vids, (the video will  play, but no audio), and streaming flash players. This problem doesn't  occur in WinXP.
-My external usb drive with Isadora Fluxbox won't  boot from bios. (It will boot, fully functional, from my other laptop, a  Compaq Evo N610.) I can mount the partitions from my XFCE install, and  after doing a "update-grub", I can *sometimes*  boot from the internal hd's grub, but the login screen has graphical  glitches, and audio is similarly non-functional. Both installs use the  same 2.6.37 kernel and xorg-edgers PPA.

I have "noapic" in my  boot configurations, to avoid the whole system freezing up, but was  wondering if I need to modify this command to improve sound and trackpad  handling.

According to my research, my sound card, (ATI IXP),  should be well-supported in Linux. XFCE w/Compiz works fine, aside from the trackpad and sound. I've  updated the Phoenix bios to version f.45. The power supply the computer  came with is a replacement; 18.5v, 6.5a, but the specs on the HP website  said max operating voltage is 10a. Not sure if this is a problem; I  couldn't find the specs for the original power supply.

Does this  sound like a bios or motherboard compatibility issue, or a power issue,  processor scheduling, IRQ handling, or something else? Not having sound is a deal-breaker for me, as I intended to use this as a music production machine. Plus, a shaky trackpad is a pretty frustrating user experience. If I can't sort it out, I think I'll have to wipe  Linux from this machine and sell it. Any suggestions?
 [IMG]http://forums.linuxmint.com/images/smilies/icon_sad.gif[/IMG]

edit: I just booted Crunchbang Statler on a USB stick, and audio DOES function, (trackpad still sucks though.) Any ideas why audio in works in this particular distro?

---

### Post by phredbull on 2011-02-07
bump

---

