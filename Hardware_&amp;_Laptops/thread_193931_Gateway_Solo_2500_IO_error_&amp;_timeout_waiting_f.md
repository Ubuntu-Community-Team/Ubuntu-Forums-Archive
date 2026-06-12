---
title: "Gateway Solo 2500 I/O error &amp; timeout waiting for DMA"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by jer2eydevil88 on 2006-06-10
I am trying to install Ubuntu on my buddies laptop.

Its an old box and he just wants to use it as a wireless email/chat for his Mom.

When booting off the Dapper CD in normal boot it would just go black after outputting some errors.  Now I booted in graphics safe mode and I get the following on the screen.

hdc: timeout waiting for DMA
hdc: drive not ready for command 
 >>> Repeated this 8 times with different numbers in front of the text
Buffer I/O error on device hdc, logical block 357296
 >>> Repeated this another 8 times

So then anyone know how I can fix this?  I know its not the CD drive because I installed XP, 2000 and 98 on it already before deciding he would be better off with Linux.

He has only got 128mb of ram so if anyone has advice for tweaking it then feel free to toss that in here.

---

### Post by pincushionman on 2006-06-12
jer2eydevil88, I believe that this can be easily fixed.  I have had the same problem with a 'Future Power' brand computer.  The computer had a Celeron processor, and the IDE interface uses an SiS5513 IDE controller.  If you search online for SiS5513 you'll find many questions about it's DMA compatiblity.  I'm not sure DMA is automatically turned on in Windows without their driver (others with more experience, please correct me on this).

You can verify you have this chipset by opening a terminal or console and typing:
[FONT="Fixedsys"]sudo lspci[/FONT]
If you want more verbose info, type this:
[FONT="Fixedsys"]sudo lspci -vv[/FONT]
You will find it listed under IDE interface: blah blah controller (rev 02)

To fix this, boot from CD, go to more options, and add [FONT="Fixedsys"]nodma[/FONT] after the two dashes.  It worked for me.  It may be possible to re-enable the DMA after you install Ubuntu.

---

