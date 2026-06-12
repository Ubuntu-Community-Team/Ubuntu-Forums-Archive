---
title: "ubuntu won't install!"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by rabidog on 2008-12-31
hello,
i'm totally new to ubuntu.  i've been using puppy linux which boots from CD just fine.  however when i put my ubuntu disc in, start the computer and press F12 for setup, i get the start screen with options to: try ubuntu without any change to your computer, install ubuntu, check CD fr defects, test memory, and boot from first hard disk.  when i select any of these and hit enter, i can hear the CD spinning in the drive for about 5 seconds, but nothing happens.  there's currently no operating system installed on the PC and no personal files saved on it.  any ideas?  TIA!

computer is a dell latitude D400. 
external CD drive is a dell model # PD01S. 
the setup screen reads: 
pentium m 2.00 GHz/600MHz
current CPU speed: 2.00 GHz
Level 2 Cache: 2048KB
System memory: 512 MB @ 266 MHz
primary HD: 40gb

---

### Post by lemming465 on 2009-01-01
Can you test the CD on another computer?  It's just barely possible that the CD has burn problems.  However, the 5s of CD activity followed by zilch suggests that the boot process using the BIOS loads the kernel and initrd, but then the ubuntu kernel modules can't talk to the CD drive afterwards.  

Check for BIOS updates from DELL, see if you can tweak BIOS settings (USB) for different compatibility options, try [different kernel boot options]("https://help.ubuntu.com/community/BootOptions"), maybe try ubuntu 9.04beta2 (with a newer kernel).

---

### Post by DGSpeir on 2009-01-01
Try checking the CD for defects.

---

