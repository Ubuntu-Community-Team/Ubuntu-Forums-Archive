---
title: "Motherboard compatibility matrix for Ubuntu Hoary and AMD64"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by Bob Owen on 2005-03-22
Has Ubuntu published a hardware compatibility matrix showing which AMD64 mobos have been tested with Hoary and are fully functional?  I want to build a 64 bit system but don't want to end up with a lemon.  I have read other forum entries on other member's problems with various types of mobos and would like to avoid these problems if possible.  Thanks in advance for your replies.

---

### Post by MaX on 2005-03-23
[QUOTE=Bob Owen]Has Ubuntu published a hardware compatibility matrix showing which AMD64 mobos have been tested with Hoary and are fully functional?  I want to build a 64 bit system but don't want to end up with a lemon.  I have read other forum entries on other member's problems with various types of mobos and would like to avoid these problems if possible.  Thanks in advance for your replies.[/QUOTE]
 I know the MSI K8N Neo Platinum nForce3 250Gb works with Ubuntu, my father runs it.

---

### Post by Bob Owen on 2005-03-23
Many thanks.  Can dad confirm that all hardware was detected successfully?  Does the SATA work?  What chip and graphics card is he using?  Any other problems or things to avoid?  Thanks again.

---

### Post by neville_lobo on 2005-03-23
Buy anything that does not have an SIS chipset. I'm having major problems enabling DMA on my Asus K8S-Mx. Also, the onboard graphics chip is not well supported (SIS760). Plus the onboard LAN (SIS190) is not at all supported. Same problems in Warty, Hoary and even with the SimplyMepis Live CD.

See here for more info:
[http://www.ubuntuforums.org/showthread.php?t=16242&highlight=sis](http://www.ubuntuforums.org/showthread.php?t=16242&highlight=sis)

Neville

---

### Post by MaX on 2005-04-12
[QUOTE=Bob Owen]Many thanks.  Can dad confirm that all hardware was detected successfully?  Does the SATA work?  What chip and graphics card is he using?  Any other problems or things to avoid?  Thanks again.[/QUOTE]
 He runs only on a SATA disk and it works so... his Geforce 6600 had problems until the right drivers showed up in hoary other than that it runs fine.

---

### Post by Pipette Monkey on 2005-04-12
I have a system with a soltek SL-K8AN2E-GR NFORCE3 250 RT Mobo.  Everything works fine except for getting my USB flash drive to work, fedora core 3 had the same problem.  It's got to be something with the board itself because the same drive automount on another system wth fedora and an ASUS mobo

---

### Post by rpseng on 2005-09-24
[QUOTE=neville_lobo]Buy anything that does not have an SIS chipset. I'm having major problems enabling DMA on my Asus K8S-Mx. Also, the onboard graphics chip is not well supported (SIS760). Plus the onboard LAN (SIS190) is not at all supported. Same problems in Warty, Hoary and even with the SimplyMepis Live CD.

See here for more info:
[http://www.ubuntuforums.org/showthread.php?t=16242&highlight=sis](http://www.ubuntuforums.org/showthread.php?t=16242&highlight=sis)

Neville[/QUOTE]


Hi Neville,

I have a K8S-MX, you can use the onboard LAN SIS190 with the driver from [http://www.sis.com/download](http://www.sis.com/download). You just need to compile it as a module to get it working, I can post further information here if you want.

I already posted a messege to the ubuntu developers in order to add this driver to the installation cd.

Cheers.

---

### Post by higgins on 2006-03-21
rpseng

I have the LAN SIS190.

You mentioned you need to compile it as a module with the driver from [http://www.sis.com/download](http://www.sis.com/download). 

Can someone shed some light on this process?

Tim

---

