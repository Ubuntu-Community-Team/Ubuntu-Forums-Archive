---
title: "Switching from GRUB to LILO or NTLDR"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by ironstoneh on 2009-04-26
G'day all.

I didn't know whether to post this in this forum, General Help or Hardware and Laptops. This seemed most appropriate.

I have a Clevo M57U laptop on which I need to dual-boot Ubuntu (8.1) and XP. However, the Clevo has a know issue with GRUB - it makes the DVD-RW device invisible to Windows. The only know solutions are to boot using LILO or NTLDR.

So, for NTLDR, I have dd'd the first 512B of my Ubuntu /boot partition to the Win C:\ directory, and configured the boot.ini to pick it up, but it just hangs on a blank screen: my guess is because GRUB is in the MBR; this sounds a but like catch 22 to me, because a) I don't know how to move GRUB out of the MBR and into the /boot partition, and b) if I get it wrong, I'll need to fix the MBR.

For LILO, I have configured the lilo.conf file. When I tried to install LILO to the MBR, it for some reason installed NTLDR there - which, as I've said, doesn't work.

It seems such a simple thing, why is it so difficult? All I need is to ensure that booting Windows doesn involve GRUB at any point.

Can anyone help me out? Please?

Edwin

---

