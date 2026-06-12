---
title: "Triple-boot with 2 HD and Grub not on MBR"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by wklang on 2009-08-02
I have a two HD system with the Windows Xp installed on the first drive and bootable from the MBR.

I would like to install Ubuntu and Windows 7 beta on the second drive and have the booting as follows:

1. when drive 1 is the default boot, I want Windows XP to boot (without Grub playing any part)

2. when drive 2 is the default boot, I want Grub to give me a choice between Ubuntu, Windows XP, and Windows 7.

The reason for this is I cannot - at present - afford to risk not being able to boot Windows XP which contains my finance and research data.  If I somehow screw-up the Ubuntu installation, I want to be able to unplug drive2, restart the computer and have Windows XP come up.

I'm pretty sure this is possible, but I don't consider myself enough of a geek - or enough of a gambler - to try this without advice.

Thanks,

Wes

---

### Post by louieb on 2009-08-02
What kind of drives? internal or external? SATA (slim cable connection to mother board) or PATA  (wide flat ribbon cable to mother board).  

If both are internal and SATA drives. the easiest way to protect XP is to uplug its cable during the Windows 7 and Ubuntu install. Win 7 will want to put its boot loader in XP and Ubuntu will want to alter the drives MBR.  

After the install plug the XP drive back in.  It will be easy to add it to GRUB later. 

It get a bit trickier with a mix PATA/SATA or internal/external drives.

---

### Post by wklang on 2009-08-02
Thanks for the suggestion.   Both of my drives are SATA....and it'd be easy enough to unplug the first drive (with XP) while installing Ubuntu and Windows 7 on the second.

I'm even less of a geek than I thought ! :-)

Wes

---

