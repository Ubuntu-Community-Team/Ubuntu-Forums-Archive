---
title: "Suspend causes laptop not to boot grub after reboot/shutdown"
date: 2010-11-13
forum: Hardware
---

### Post by DarkCanis on 2010-11-13
This is a Toshiba Satellite T215D-S1150 running Ubuntu 10.04 x64 and dual boot with Windows 7.  

So far what happens is if I suspend the laptop Ubuntu, if I shutdown the machine it no longer is able to boot from the hard drive, ie it doesn't detect a bootable partiton and moves onto PXE and other boot methods. 

Suspend and Hibernate work well in Ubuntu the main problem occurs should I shutdown the system after performing a Suspend.
Suspending from Windows does not cause problems with grub. 

So far as a workaround what I have been doing is using a Live CD and then using cfdisk to access the partition table and make a small change then write.

Most likely the boot flag is being affected but I am not certain.  After I make the change I do not have to do this again unless I accidentally suspend.  Hibernate works with no issues in Ubuntu.

Right now the laptop is running 1.50 update of the BIOS.  

Has anyone seen this before?

---

### Post by ajgreeny on 2010-11-13
I don't understand what you mean by comments about when you shutdown after a suspend.

Do you mean that you can suspend ubuntu and then come out of suspend with no problem, but then a subsequent full shutdown causes these problems?  Please let's have more detail of the sequence of events to make it clearer.

---

### Post by DarkCanis on 2010-11-13
1. Suspend Ubuntu works well
2. Resume Ubuntu works well
3. Shutdown OS/Reboot OS
4. Power On Laptop
5. Laptop does not boot a hard drive grub is not presented. Goes through other boot options
6. Boot from LiveCD
7. Edit partition table, write, reboot
8. Laptop boots normally.

It will continue to boot normally unless I perform a suspend/resume from Ubuntu. Hibernating does not cause this issue.

---

### Post by thomas-r-robbins on 2010-12-14
I am running Ubuntu 10.10 and am having the same problem. However, I have found that if I boot the LiveCD (via USB) and restart, I can then boot from the hard drive.

---

### Post by thomas-r-robbins on 2010-12-24
I downgraded to (legacy) grub 0.97-29ubuntu60 and still have the same problem.

---

