---
title: "MP-Bios bug 8254 timer not connected to IO-APIC"
date: 2009-01-30
forum: Hardware
---

### Post by don54321 on 2009-01-30
Hello,

I have had a problem booting to Ubuntu 8.1.  Earlier Hardy is fine.  As per below, I have some strange Bios phenomena that is somehow related. I get the following errors booting with 8.1:

MP-Bios bug 8254 timer not connected to IO-APIC followed by a kernel panic.


I have been experimenting, and strangely, if I make "any random change" to my BIOS and save, just prior to booting the CD, It will boot fine.  (I disccovered this while updating the Bios) I can then install, but even a hard drive boot fails unless I do the random Bios change beforehand.  This is not a CD issue.  I believe that this may be a new kernel issue as a debian Dream Linux release candidate has the same bizarre behavior.  I imagine that I can not be the only one experiencing this problem.  My motherboard is a 2007 quality DFI board with NVIDIA GForce chipset.  The processor is an AMD X2 5000+ andI have 2 Gb DDR2 memory.  I would fault DFI except that this board was fine for earlier Ubuntu releases, and I would expect future releases to only improve hardware compatibility.

I am not sure of the best place to post this bug for the good of the larger community, please advise if you have any ideas.

I am also curious what possible effect could the simple act of  changing the bios have on the boot immediately following and ONLY immediately following.  Very very odd.

Don

---

### Post by Jordanwb on 2009-03-04
I'm getting the same error, but I haven't gotten a kernel panic. I found [this](http://www.linuxquestions.org/questions/linux-hardware-18/mp-bios-bug-8254-timer-not-connected-use-noapic-option-to-boot-591891/) which talks a bit about the problem. It says to put "noapic" to your kernel params.

For me in the dmesg it says this:

> [    0.516031] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.516031] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.516031] ..... (found apic 0 pin 0) ...
[    0.556429] ....... works.

For me I guess the reason that the kernel doesn't panic is that it has a workaround. I'm a bit apprehensive to add "noapic" to the params though.

---

