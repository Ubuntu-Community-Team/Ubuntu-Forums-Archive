---
title: "When attempting to install Ubuntu 8.10 on PPC, the DVD ejects.  I am attempting to"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by goldblattster on 2009-03-02
When attempting to install Ubuntu 8.10 alternate on PPC, the DVD ejects.

I am attempting to boot Ubuntu 8.10 PPC on a PowerMac G4, the CD ejects automatically after a few seconds. I desperately want to get Ubuntu 8.10 on my PowerMac, since it helplessly runs 10.2 OS X. I have also tried pressing/holding C after the chime. A few months ago I tried this with the system cds that came with my PowerMac, and those worked. I don't know if anything changed since then. I also tried this with the openSUSE and the same thing happened.

Please Help!
goldblattster:confused:

---

### Post by sgosnell on 2009-03-02
Did you do a md5checksum on the .iso you downloaded?  Did you verify the CD after the burn?  You may have a defective CD.  When the live CD starts, have it check the CD.

---

### Post by goldblattster on 2009-03-02
I did do both, I did it with OPENsuse and the same thing happened, so it would be a fat chance if I messed up both.

---

### Post by sgosnell on 2009-03-02
I don't know then, you may have a defective laptop.  I know nothing about Macs, maybe someone who does will be along.

---

### Post by goldblattster on 2009-03-02
What i'm using isn't a laptop, but many thanks to your help anyway! :P

---

### Post by Neo_The_User on 2009-03-02
Could be something wrong with the BIOS... Try putting in those Mac system CDs or whatever that worked before. That way we could rule out a bad disc being the case. ;)

---

### Post by goldblattster on 2009-03-02
> **Neo_The_User said:**
> Could be something wrong with the BIOS... Try putting in those Mac system CDs or whatever that worked before. That way we could rule out a bad disc being the case. ;)

There is only one problem... I have them at school because I need to fix up the computers there (yes, they run OS9) So i'm going to pick them up when I go there tomorrow.

---

### Post by Neo_The_User on 2009-03-02
pick up the discs or the computers?

---

### Post by goldblattster on 2009-03-03
I tried a 10.4 Disc I have here, and this is what I got.
```
panic (cpu0caller): unable to find driver for this platform (PowerMac 3,1...
```
That goes on forever, and I realize it might be because that disc for my MacBook Pro.
Smack dab in the middle of the screen, it goes:

You need to restart your computer. Hold down the power button for several seconds ore press the restart button.

This disc did not eject.

ALAS, all this might mean I burnt the disc incorrectly. This is the procedure I used to burn the disc.

1. Firefox: go [here]("http://cdimage.ubuntu.com/ports/releases/intrepid/release/") and download the alternative cd iso (my mac has 128 megs ram)
2. Download the iso via Vuze.
3. Burn the iso onto an Imation Forcefield CD-R via Cyberlink DVD Suite (should something else, like maybe InfraRecorder, recommended by Canonical?)
Note: I lost the burn log, otherwise I would attach it.:(
Note: I did not actually do an md5check on the Ubuntu ppc cd, I only did it on the openSUSE cd. I'd like to work on Ubuntu, since it is easy to get software for, and everybody under the sun uses it.

---

### Post by Ledsled7 on 2009-03-14
> **goldblattster said:**
> When attempting to install Ubuntu 8.10 alternate on PPC, the DVD ejects.
...
Please Help!
goldblattster:confused:

Like most threads concerning this question (at least when I was in your predicament), the majority of solutions offered really didn't address the problem, and they were over-complicated.

Elsewhere, I read a forum thread in which a user burnt "at least a dozen" install CDs and DVDs of various Linux distros and was unable to boot from any of them with his particular Mac.  He was being told that his ISOs must have been 'bad' and that he ought to slow down his burn rate, etc.  Balls!

I can't guarantee this will work for you, and I didn't invent it, but this is what got my iMac G3 running on Ubuntu.  *Please read to the end before proceeding to reboot and install.*

1) _Boot into Open Firmware_:  reboot your Mac and depress COMMAND-OPTION-O-F simultaneously immediately after the chime.
2) _Tell the firmware where yaboot is_:  at the prompt, enter ```
boot cd:,\install\yaboot
```
3) Follow the installer's instructions.

P.S.  Verify the path of yaboot on the install disc before you boot to the Open Firmware prompt.

Cheers.

---

### Post by goldblattster on 2009-03-15
Perfect! This works! Thanks a lot!:popcorn:

---

