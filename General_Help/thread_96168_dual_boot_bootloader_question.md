---
title: "dual boot bootloader question"
date: 2005-11-28
forum: General Help
---

### Post by Latem on 2005-11-28
Hello, if I want to install Kubuntu on a second HD, and my primary HD has Windows XP on it already. Is it possible to do this and keep the windows bootloader thing (NTLOADER); and have 2 choices in it: Windows XP and Kubuntu.  Or will I have to install GRUB and use it?  I just really don't want to risk anything to lose my windows  install.  I've never done dual boot before in any shape or form.

Thanks,

Latem

---

### Post by aysiu on 2005-11-28
Installing Grub does not lose your Windows install. It loses your Windows boot loader, which can be restored if you have a Windows installation disk (you won't have to reinstall Windows--you just go to recovery mode and type "fixmbr").

It's complicated (especially for someone new to Linux) to use Windows' boot loader to dual boot, as it won't recognize Linux, so you'll have to do all sorts of electronic backflips to get it working.

It's simple to use Grub, as it will almost always automatically add Windows to the boot menu.

By the way, if this is your first dual boot, I'd highly recommend [this site](http://users.bigpond.net.au/hermanzone/) for instructions.

---

### Post by Latem on 2005-11-28
Thanks for the reply.  I was aware of fixmbr, but I always thought that that would mess up my existing Windows install.  I didnt think it can recognize and bring back the Windows install. 

Yes, I should just trust the Kubuntu installer and that it should detect the other hd and os fine, and add it to GRUB menu as appropriate.  I just thought there was no way to get back Windows in the unlikely chance that someting somehow went wrong.  But if fixmbr will do it than I have a back up plan.  So might as well use GRUB.

Thanks for the link, I am sure it will be useful.  I always had seperate Windows and Linux boxes. The only thing I find myself doing in windows is play Counter Strike, and end up using my (worse) Linux box for everyhing else.  so might as well have dual boot on the good machine.  
Thanks

Latem

---

### Post by guice on 2005-11-28
GRUB recongizes Windows with zero problems. Heck, it even recongized an old XP install and 4 Kubuntu (2 k7 and 2 defaut) images on an old external drive I accidentally had connected during my install a bit ago.

---

### Post by infoseeker on 2005-11-30
I had a problem installing Kubuntu the first time (I had a read error on the CD I burnt :( ) which crashed the install process, but also corrupted my WinXP mbr. 'fixmbr' did not repair it. What did repair it eventually was a boot with a Gentoo live CD which I fortunately had, used 'cfdisk' which I used to deselect the NTFS drive as a boot drive. I then again used the 'fixmbr' app on the WinXP install disk which this time DID successfully repair the mbr and I could then get back to WinXP.  I then burnt another Kubuntu disk from the Kubuntu iso, deleted the non-NTFS partitions with WinXP, and started the installation again....this time successfully :)

---

