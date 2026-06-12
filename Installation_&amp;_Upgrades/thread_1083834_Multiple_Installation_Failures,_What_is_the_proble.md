---
title: "Multiple Installation Failures, What is the problem here?"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by GeistDev on 2009-03-01
Hello everyone, I am in bit of a confusing state and hopefully someone here can point me in the right direction.  I have tried to install several different flavors of ubuntu with no luck.

The disks are not defective, as they have worked on other peoples machines.

OK, so here are the versions I have tried:

Ubuntu 8.04.1
nUbuntu 8.12
Kubuntu 8.10
Kubuntu 8.10 ALTERNATE
Xubuntu 8.10 ALTERNATE

All of these installs act like the are going to work but all fail at and display roughly the same message:  AN INSTALLATION STEP FAILED, STEP THAT FAILED:  INSTALLING SELECTED HARDWARE.

Curious.

Here are the system specs on which I am trying to install on:

Dell Dimension 2400
2.4 GHz Intel Pentium 4
256mb DDR SDRAM, 333 MHz

Before attempting these installs this machine was running XP HOME pretty smooth and fast.


Any input is appreciated, thanks!

---

### Post by GeistDev on 2009-03-01
I also did the RAM test on the Xubuntu 8.10 ALT disk, and everything passed.

I'm clueless.

---

### Post by GeistDev on 2009-03-02
Ooooh really? 

Thanks, I'll give that a shot!


LOL, just kidding obviously, but really, does noone have any input?

---

### Post by avtolle on 2009-03-02
An observation; just because the disk(s) worked on other machines, this is not necessarily an assurance that they will work on yours. Example (from my own experience): earlier release (7.10, IIRC) burned to CD-RW; worked, installed correctly on another computer; didn't work at all on mine. Same iso (md5sum checked out, etc., before burning) then burned on a CD-R at slow speed (4x) worked on my machine AND the other one. 

The 256 mb RAM might have been an issue with the Live (Desktop) CDs you tried; IIRC, to use the Live CD graphical installer, there is a minimum system requirement of 384 mb RAM. As to the alternates: both should have installed (assuming no other issues) with the RAM on your system, especially the Xubuntu 8.10 Alternate.

How old is your computer? It may be you need to use a boot option or two to get it installed, if more than 10 years old especially.

---

### Post by avtolle on 2009-03-02
See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) for a general discussion of boot options, how to use the same on installation and post-installation to boot.

---

### Post by avtolle on 2009-03-02
Did a quick Google search on your computer and Ubuntu. One thing that kept popping up (and I don't know if this applies to you) was that there was a "new" driver for USB released a few years ago that needed to be installed from Dell's site under XP (in your case), and that seemed to resolve some of the problems users were having. Other "fixes" included increasing the RAM.

As your recurring error message has mention of hardware problems, I'm wondering if the "driver" is really a BIOS upgrade that needs to be downloaded and installed. Good luck.

---

### Post by Roob on 2009-03-02
You could try changing the SATA mode from IDE to RAID, if your BIOS lists that option, see [here]("http://ubuntuforums.org/showpost.php?p=4783244&postcount=5"). If you're setting up a dual boot machine there is a chance that your machine won't boot into XP after this, which would be easily repaired by changing it back (see follow-up to linked message). I'm a newby to Linux/Ubuntu myself, and I'm having problems installing Xubuntu, so don't expect to much of my suggestion. I would give it a try though...

---

### Post by GeistDev on 2009-03-02
> Did a quick Google search on your computer and Ubuntu. One thing that kept popping up (and I don't know if this applies to you) was that there was a "new" driver for USB released a few years ago that needed to be installed from Dell's site under XP (in your case), and that seemed to resolve some of the problems users were having. Other "fixes" included increasing the RAM.

As your recurring error message has mention of hardware problems, I'm wondering if the "driver" is really a BIOS upgrade that needs to be downloaded and installed. Good luck.



I am sorry, I don't know why I typed HARDWARE earlier, the step it fails on is Select and Install Software. Gets almost ALL the way done on the Alternate disk and fails around 80-something percent.

I installed XP real quick and went to the Dell site for drivers, but did not see anything relating to a USB driver.

I plan to not dual boot this system, but run strictly Ubuntu (preferably, Kubuntu).

I did however download and install all the recomended drivers from Dell's website, and tried to install the KUBUNTU alternate one more time.

(which just finished succesfully)

So, one of those drivers must have done the trick.

I thank you all.

---

