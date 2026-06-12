---
title: "Can't boot with Thinkpad T22"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by Araj on 2007-02-28
I can't get Ubuntu to boot from the CD. Trying to preview/install on a trusty old IBM T22 Thinkpad (currently running XP)

The CD does start to load Ubuntu, but never makes it to actually show the desktop. I get the CD menu, the logo with the progress bar, lots of toing-and-froing from the CD drive, the odd message or two, mostly too fast to read, and then the system hangs. 

One message I did manage to read was something about detecting an IBM laptop and not being able to load a module in case the EEPROM was corrupted.

I have tried 6.10 and 6.06, even tried reburning the downloaded ISOs again in case of errors.

---

### Post by Lonestar on 2007-02-28
Arja:

I have a Thinkpad T21 which is very similar to the T22.  I had all kinds of problems installing Ubuntu, I got it installed (somehow).  Then it worked for a while, but eventually my laptop quite working.  In the meantime, I bought a new hard drive and when trying to install Ubuntu on the new hard drive ran into the very same problem you did. 

I tried EVERY suggestion on this forum and nothing worked, the CD would not install, the self-booting GParted CD would not run either.  I would just get a blinking cursor at loading the Linux Kernel.

BUT, after a lot of searching I found on a small entry on the Internet that said that either Linux does not like the 1050 Mini PCI adapter (used in the T20, T21 and T22) or that it went bad.  In any case, the author said, remove the Mini PCI adapter daughter card and try to run Linux again (you have nothing to loose, if it doesn't work, put it back!).  A manual to explain how to remove the card (it is quick and easy) can be downloaded from IBM here [ftp://ftp.software.ibm.com/pc/pccbbs/mobiles_pdf/62p9631.pdf]("ftp://ftp.software.ibm.com/pc/pccbbs/mobiles_pdf/62p9631.pdf")

All I can tell you is, with the Mini PCI adapter removed, Ubuntu worked with no special settings and boots up every time!  NOTE: this does mean is you will have to get a PCMCIA Ethernet card to take the place of the removed adapter, I bought one for $14 that works great.

Good luck, I hope this helps you and everyone with this problem on a Thinkpad.

---

### Post by Araj on 2007-03-01
Thanks Lonestar

I also finally managed to get it up and running - on attempt 7, installing in "safe graphics" mode. 

However, judging by what you said this may just be luck and I could have problems in the future booting up - so I'll bear the info about the mini PCI adapter in mind for emergencies.

---

### Post by lassegs on 2007-03-05
Any news on this one Araj? Is it still working?

LGS

---

### Post by fitz_ryan on 2007-03-21
I've been using my T22 successfully with 6.10.

I had similiar issues where the install and livecd would just hang.  After some investigation, I was led to the alternate install cd.  It worked fine.  I also had to edit xorg.conf according to [http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21)

---

### Post by EventHorizon on 2007-04-02
Hello there,

> **Araj said:**
> I can't get Ubuntu to boot from the CD. Trying to preview/install on a trusty old IBM T22 Thinkpad (currently running XP)

The CD does start to load Ubuntu, but never makes it to actually show the desktop. I get the CD menu, the logo with the progress bar, lots of toing-and-froing from the CD drive, the odd message or two, mostly too fast to read, and then the system hangs. 

One message I did manage to read was something about detecting an IBM laptop and not being able to load a module in case the EEPROM was corrupted.

I have tried 6.10 and 6.06, even tried reburning the downloaded ISOs again in case of errors.

I am trying to install kubuntu from an iso on my T22 laptop and I'm experiencing the same problem as Araj.

This same laptop is currently running Mandake 10.1 but I want to do a fresh kubuntu install .

Does anyone have any pointers for a resolution that doesn't involve **removing** hardware?

- Simon

---

### Post by harryc on 2007-04-06
Thanks Lonestar

I had all kinds of install and boot problems on my T-21 until I removed the Mini PCI adapter. It's been working like a charm on Edgy for a day now. Hopefully that was the end of the boot problems. I run PCMCIA wireless anyway, so no great loss. Of interest also is that this was not just an Ubuntu problem. I also had major boot problems with OpenSUSE and Mepis.

---

### Post by aristotlewilde on 2007-06-17
I just picked up one of these laptops and plan to run Ubuntu on it.  What is the function of this Mini PCI card? Do I lose anything by removing it?

---

### Post by harryc on 2007-06-17
On a T2x Thinkpad, the MiniPCI card provides Ethernet and Modem capabilities. It's a combo card.

---

### Post by Wattos on 2007-06-17
have you tried using the alternative cd to install ubuntu? it works for my laptop where the live cd fails (its an Asus tho)

---

### Post by hansisland on 2007-10-10
> **Lonestar said:**
> Arja:

BUT, after a lot of searching I found on a small entry on the Internet that said that either Linux does not like the 1050 Mini PCI adapter (used in the T20, T21 and T22) or that it went bad.  In any case, the author said, remove the Mini PCI adapter daughter card and try to run Linux again (you have nothing to loose, if it doesn't work, put it back!).  .

Thanks for this! This probably saved me a whole weekend of swearing at this T22. 

I physically removed the ethernet/modem minicard from the back of the T22 and set the PCI setting in the BIOS to 'Automatic' and within minutes Ubuntu7.04 was installing happily. 

I now just need to find a way of getting connected to my home network (wifi or wired)....  But that shouldnt be too harrd.

---

