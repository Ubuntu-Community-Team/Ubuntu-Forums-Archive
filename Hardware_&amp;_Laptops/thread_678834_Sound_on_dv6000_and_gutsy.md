---
title: "Sound on dv6000 and gutsy"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by murra1a on 2008-01-26
Hi all,

I have installed gutsy on a dv6115ca, its a turion x2
I am having a problem with my sound though

First off, to even get it to boot I have to pass "noapic nolapic noacpi nosmp noirqpoll"
that allows me to boot and use things like the SD reader and the USB ports

The sound card is an nVidia MCP51 HDA chip, which from my understanding is supported by the snd_hda_intel module.

this module is loaded at boot, and there are no obvious errors
alsamixer sees a card and allows me to change the volume on it
mplayer, amarok, etc. all see the card and play audio without a problem
but no sound comes out of the speakers

I have no idea how to troubleshoot this does anone have any ideas?
Thanks

---

### Post by fedex1993 on 2008-01-26
okay from what i have read from the wiki page you can run
sudo apt-get install linux-backports-modules
and reboot and it say it should

---

### Post by Kedaeus_Sendre on 2008-02-23
Damnit.. I pressed the "quote" button.. Oh well.

Loaded the backport modules on my dv6000.. corrected the issue.
Thanks 

-Ked

---

### Post by mikael_b on 2008-02-25
when i run "sudo apt-get install linux-backports-modules" it's already installed.. So I reboot but the problem remains, no sound.... Did you have any other suggestions?

---

### Post by jcaveman on 2008-02-26
I've got my DV6119US to boot without any boot options, but failing that try just "noapic irqfixup".  I think you've disabled something critical with the boot parameters.

---

### Post by mikael_b on 2008-02-26
When i installed ubuntu i press F6 and then added to the end of the line;  noapic nolapic

---

### Post by jcaveman on 2008-02-27
You need to add either "irqfixup"  or "irqpoll noirqdebug" to the bootup options.  noapic appears to partially disable the interrupt handling process which means things like sound and usb ports don't work correctly.

---

### Post by Kedaeus_Sendre on 2008-02-29
Hrmm, sound worked fine for a moment after installing the linux-backports-modules however after installing Kernel Linux 2.6.22-14-rt sound has yet again broken. 

 I'll post the results of editing the boot options in a moment.

 --Update--
 
 Rebooting with no extra boot options, noapic, nolapic, irqfixup, or noirqdebug did not work. :o\
Sucks.. Guess i'll revert until I find the answer I need. 

-Ked

---

