---
title: "Two Questions"
date: 2009-07-23
forum: Hardware
---

### Post by MrChezedoodle on 2009-07-23
Hi,

Two quick questions.  I have an old Dell Dimension 4550 that was my dad's. It was running windows and he got hit with a bad virus.  I got most of his documents off by mounting the drive in a live cd and copying them to an external harddrive, but i missed a few.  Now, windows won't even boot in safe mode.  When i try mounting the drive, the folder that i mount it to is empty but it says that only 40 gig's are free out of a 120 gig hard drive.  can someone help me see my files again?


and the second question... I was planing on installing ubuntu on the machine, but the wireless card isn't seen.  how would i go about installing the drivers for the wireless card?  


thanks 

Steve

---

### Post by nixscripter on 2009-07-29
First question: go get a linux recovery CD, and see if it can reconstruct the volume. Here is a fine example:

[http://www.livecdlist.com/fccu-gnulinux-forensic-boot-cd](http://www.livecdlist.com/fccu-gnulinux-forensic-boot-cd)

Second question, it depends on what kind of card it is. Boot from a live CD and run in a terminal: ```
lshw -C network
``` And post the output. (Please use [code] tags around it to make it look nice.)

---

