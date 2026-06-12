---
title: "lubuntu hardware problem on compaq 2510p"
date: 2016-10-28
forum: Hardware
---

### Post by troqnec on 2016-10-28
Hi friend's, I have a new lubuntu 16.10 and I have some hardware problem...when the system is booting I have a massage like "dev/sda1: clean, 157778/5900160 files, 1312543/23903232 blocks" or something like that. When I start software & updates and click on additional drivers I see that I have a unknown devise and I pick a "using processor microcode firmware for intel CPUs from intel microcode (proprietary)" option. I search in other forum's and found that may be is a old intel graphic driver but ...when I try:
```
aptitude search xserver-xorg-video-intel
i A xserver-xorg-video-intel        - X.Org X server -- Intel i8xx, i9xx display
p   xserver-xorg-video-intel-dbg    - X.Org X server -- Intel i8xx, i9xx display
```
and I think that my video driver is working ok...sorry for my english ...please help with that dev/sda1 clean..problem

---

### Post by wgilthorpe on 2016-10-28
This should not be a problem.  /dev is your device folder.  /dev/sda is the first hard drive that was found on boot.  /dev/sda1 is the first partition on the first hard drive.  "/dev/sda1:clean" means that on boot the filesystem on this partition was checked and found to be clean.  This is not an error.  

As to the additional drivers, the processor microcode is code used for the CPU.  You can choose to use the generic Linux code or the Intel proprietary code.  In my experience, I have not noticed a difference in performance YMMV.

---

