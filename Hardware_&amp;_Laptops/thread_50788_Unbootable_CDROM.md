---
title: "Unbootable CDROM"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by Paul Bramscher on 2005-07-21
I installed Ubuntu on a new development workstation here at work, and had some problems with the onboard Intel (Marvel/Yukon) NIC.  Disabled it, used a spare Intel Pro 1000MT NIC they had lying around and Ubuntu was happy.

Liked it so much that I decided to install Ubuntu on a spare box I have at home.  It's a PIII 800 MHz, Abit BE6-II motherboard, 512 MB RAM.  The problem is that however I fiddle the BIOS (CDROM-HD-FLOPPY) I cannot get the CD-ROM to boot.  I don't blame Ubuntu for this: I think it's the crappy Highpoint chipset and the way it detects CD-ROM hardware (outside of normal BIOS).

So my question -- if you're still reading this -- can anyone recommend a floppy boot solution?  I hope to boot to floppy, have it load the CD-ROM drivers, then install Ubuntu from CD at that point.  Thanks for any tips!

Paul Bramscher

---

### Post by Paul Bramscher on 2005-07-22
I can answer my own question.  What I did was to download Smart Boot Manager ([http://btmgr.webframe.org/)](http://btmgr.webframe.org/)).  Worked like a charm, I was able to boot to CD-ROM with it, install Ubuntu and get up and running without any further issues.

---

### Post by damonw5 on 2005-07-22
[QUOTE=Paul Bramscher]I can answer my own question.  What I did was to download Smart Boot Manager ([http://btmgr.webframe.org/)](http://btmgr.webframe.org/)).  Worked like a charm, I was able to boot to CD-ROM with it, install Ubuntu and get up and running without any further issues.[/QUOTE]
 Glad to hear it! I was reading your first post and I was about to recommend SBM... but then I saw your second post!

Don't you love it when you can solve your own problems? :)

---

### Post by andlinux21 on 2005-07-22
I used SBM  and installed Ubuntu on my old 200Mhz Pentium box but when i reboot it stops at grub and that is it... ](*,)

---

