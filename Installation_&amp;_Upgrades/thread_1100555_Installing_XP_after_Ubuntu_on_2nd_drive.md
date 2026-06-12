---
title: "Installing XP after Ubuntu on 2nd drive"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by squirrelpants on 2009-03-19
Basically, I have two hard drives, one connected via SATA and one via EIDE. I already have ubuntu installed on the SATA drive and would like to install Windows XP on the EIDE drive and eventually dual boot.

I started installing Windows XP on the EIDE drive, but when the install needs to reboot, grub just automatically loads ubuntu (and thus never finishes the Windows installation). 

Can I just add the EIDE drive that I started installing Windows on to grub, and if so, how would I do that? Alternatively, can I just unplug the SATA drive for the time being, install Windows, and then when it is finished installing add it to grub (and if so, how would I do that)?

Thanks

---

### Post by Therion on 2009-03-19
The easier solution would be to install XP alongside Ubuntu on the one drive and dual-boot from there.  Is it possible to do the whole dual-drive/dual-boot thing with mixed drives? Yes, from a technical standpoint it certainly is; I've done it.  

However, and this is a huge caveat, just because you *can* doesn't mean it's easy or that you *want* to.  Voice of Experience talking here when I tell you it's not worth the hassle.  Seriously.  It's just not.

So... All that being said, see this tutorial for how to install Windows XP alongside your current Ubuntu install so you can do this the (relatively) easy way:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by Mark Phelps on 2009-03-21
> **squirrelpants said:**
> 
Can I just add the EIDE drive that I started installing Windows on to grub, and if so, how would I do that? Alternatively, can I just unplug the SATA drive for the time being, install Windows, and then when it is finished installing add it to grub (and if so, how would I do that)?

Thanks

I have a similar situation, with Windows OSs on one drive and Ubuntu on a different drive, and have it setup so that I boot from an Ubuntu drive and use GRUB to select all of the other OSs.

Don't install GRUB to the Windows drive, just boot from the Ubuntu drive and add a stanza for Windows.

Read the post below and do the second part (Windows is missing ...):

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

---

