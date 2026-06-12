---
title: "ATI propriatary driver locks screen during boot."
date: 2011-03-13
forum: Hardware
---

### Post by redprosumers on 2011-03-13
I am in the similar ati situation. My screen locks during boot. How do i get around it and fix driver to original open source.

Thanks 
redprosumers

---

### Post by redprosumers on 2011-03-13
I know the ATI proprietary driver issue has been addressed. How ever it does not state what they did to get past a locked screen at boot up and how to fix the driver taking it back to open source. I am obviously new to ubuntu and linux. I have a dual boot system with ubuntu 10.10 and windows 7 as secondary. 

Thanks, redprosumers

---

### Post by howefield on 2011-03-14
Threads merged.

---

### Post by coffeecat on 2011-03-14
Which ATI graphics chipset do you have?

Since you can't get to the GUI, you'll have to uninstall the proprietary driver from the command line. See here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

You don't need to troubleshoot. Simply go to "Problem:  Need to fully remove -fglrx and reinstall -ati from scratch".

You are new to the forum but you don't say how much experience of Ubuntu you have. You'll need to boot to a virtual terminal or into recovery mode with networking to run that lot. With recovery mode you have full root privileges so you won't need sudo. If you don't understand those last two sentences, post back and someone should be able to help you.

---

