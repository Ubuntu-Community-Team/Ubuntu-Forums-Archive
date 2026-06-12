---
title: "Hardware problem - but what?"
date: 2014-07-19
forum: Hardware
---

### Post by Carl H on 2014-07-19
I'm having some issues with my current desktop machine booting up. It either gets as far as the Ubuntu logo, and then freezes with the keyboard LEDs flashing, or it reboots before it gets to that point, or occasionally I get a screen of output for a second before it goes blank and freezes. The output appears to end with 'Waiting for /dev to be populated', something about dbus, and then 'kernel panic'.

This has been happening for about a week or so and after a few power cycles it would eventually boot up. But this morning it won't boot at all, I just get one of the scenarios described above. 

I'm dual booting Ubuntu14.04 and Mint16 and the same happens with either. I initially thought that my recent and somewhat problematic installation of 14.04 might have updated Grub with duff settings but I've checked that by trying a couple of Live CDs and got the same result, so I've concluded that the problem is the machine itself. 

But what could cause such symptoms?

---

### Post by kc1di on 2014-07-19
Hi Carl H ,

I'm just guessing here , You didn't give much information to go on.
But it's most likely a video card problem.  and you need the correct driver for your card. 
can you boot to either one in compatibility mode.  or recovery mode?
if you can get to a terminal type the following and list the output here and we will try to help you find the problem. 
```
lspci
```
and also the out put of ```
lsmod
```  would be helpful.

if you can't get to the terminal , give us as much information on your system as possible, make, model video card in use etc.

---

### Post by Carl H on 2014-07-19
I can't boot to anything. Neither of the installed distros, or any Linux live CD or rescue CD. 

The video card is an ATI 6530D and both distros have the correct drivers installed, and were working fine until last week.

---

### Post by kc1di on 2014-07-19
if you can't run a live cd I suspect you have deeper problems than just a O.S /software problem,

Check for Hard drive failure, Ram intermittent or failed.
Processor failure.  Bios corrupted or failed.

Is this a dual boot if so does windows boot correctly?

Give as many details as possible.

---

### Post by Carl H on 2014-07-19
It does not dual boot Windows. 

A hardware problem is what I suspect. I'm hoping to isolate the faulty component and then replace it. 

How do I check the hard drive, RAM, etc?   The machine seems fine until it gets to a specific point in the Linux boot sequence.

---

### Post by kc1di on 2014-07-19
you can try to run the memory test , it would be better to let it run all day or night. that will tell you if your have bad ram or not. 

Try downloading a copy of system rescue disk, [found here]("http://www.sysresccd.org/SystemRescueCd_Homepage").
it has some tools to check out the H.D. and partition on your machine.

---

### Post by tgalati4 on 2014-07-19
Check the power supply voltages in BIOS or with a volt meter.  If your 5VDC or 12VDC values are low, then that would cause boot problems.

---

### Post by a-mani-cms on 2014-07-19
Your kernel may be corrupted?

can you boot in rescue mode? with older kernels?

---

### Post by Yellow Pasque on 2014-07-19
If memtest checks out, I would reset the CMOS and try a verified good LiveUSB/CD. If it was still kernel panicking, I would go into BIOS and disable as many extra hardware components as possible (like the audio codec, NIC, firewire controllers, etc.). If that allows booting, reenable components one-by-one until you find the culprit.

> **a-mani-cms said:**
> Your kernel may be corrupted?

If the system does it with different LiveCD's, that is not the issue.

---

### Post by Carl H on 2014-07-21
I put a different hard drive in and did a fresh install. It worked fine. 

I then put the original hard drive into an older box and installed Mint 16.  After about an hour..... "kernel panic - not syncing"

Therefore, it looks like the hard drive has some problems. Maybe several weeks of Ubuntu14.04 not shutting down and having to be killed on the power has meant that the disk has repeatedly not been spun down properly and that has taken it's toll. 

Is the disk scrap or can anything be done with it?

---

### Post by WinEunuchs2Unix on 2014-07-21
run "fsck" on the disk.

---

### Post by gordintoronto on 2014-07-22
There is a program called Disks, Disk Utility, or something along those lines. (The name varies from distro to distro.) It will display the SMART data for your hard drive. If there are a lot of reallocated sectors (more than 200) then you should copy what you can from the drive, then smash it with a hammer or run DBAN on it, then put it in the trash.)

---

### Post by Carl H on 2014-07-25
Gnome Disk Utility mentioned some minor problems, but a total reformat of it and everything seems okay (although I haven't reinstalled Ubuntu, I've gone back to Mint). 


Thanks for the replies and advice.

---

