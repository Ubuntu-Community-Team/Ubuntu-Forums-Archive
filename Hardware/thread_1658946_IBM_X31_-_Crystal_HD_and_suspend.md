---
title: "IBM X31 - Crystal HD and suspend"
date: 2011-01-03
forum: Hardware
---

### Post by Issssy on 2011-01-03
I have an X31 running 10.10 and love it.

1) Coming back from suspend fails; need to reboot. Anyone have a pointer to a fix? (I see a few bugs posted for this)

2) Has anyone successfully installed the Broadcom Crystal HD mini PCI card on a X31 or similar? I was thinking of pulling the internal PCI Wifi card, replacing it with a Broadcom 12 or 15 series HD card, and using a PCMCIA wifi card instead. Anyone tried it?

---

### Post by Vincent_Lin on 2011-01-03
Hi,

I have an x31 and with 10.10 installed.  However, I have exactly the same problem you have - sending this x31 to suspend(by closing the lid) and it would not wake up at all.  

Actually, I have had this problem since 9.10 (or even earlier) that I have always suspected hardware failure or something.  The installation of 10.10 sortof confirmed my guessing.

But reading your post, hummm.  Could it really be something to tweak about to bring this functionality back?  For all x31's?  

Well, I don't have the solution.  Maybe someone can chime in and give some pointer - as you said.

Vincent

---

### Post by Issssy on 2011-01-04
The following worked for me for suspend on an x31 running 10.10, found here:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_Thinkpad_X31](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_Thinkpad_X31)

"For the suspend/hibernate problems, modify /etc/default/grub, add 'nomodeset' to GRUB_CMDLINE_LINUX_DEFAULT"  i.e. GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

Make sure you regenerate the grub config as it tells you.


hmmm... wonder if I can get the included CF slot to work? Anyone have this working on theirs?

b

---

### Post by Vincent_Lin on 2011-01-04
Thanks.  I was about to write about that.  

My CF card reader has been working since I first put ubuntu on it, and is still working.

Vincent

---

### Post by Issssy on 2011-01-04
Vincent,

If you insert a CF card, do you get a desk top icon like a USB stick, or does it just create a mount point directory under /media?

b

---

### Post by Vincent_Lin on 2011-01-06
I think it actually pops an icon on desktop.  Will try it tonight.

Vincent

---

### Post by Issssy on 2011-02-02
Well, my CF issue is due to trying to use a SD to CF adapter.... the X31 slot doesn't like it.
A true CF card works fine.

---

### Post by Issssy on 2011-02-07
Well, never one to refrain from highlighting my own errors, and rather than confuse anyone if they stumble on this thread later, Crystal HD is mini-PCIe, and the Wifi slot in the X31 in Mini-PCI --  completely socket incompatible. It went into the empty mini-PCIe slot on my HP mini 110 instead, and works very well with XBMC.

One tidbit, the D-Link WNA-2330 PCMCIA wifi/G card is fully compatible with the madwifi drivers if you do want to use the mini-PCI slot on the X31 for something else--  but there isn't much available other than wifi cards and small drives.

---

