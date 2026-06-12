---
title: "Can't install 22.04 on Lenovo Thinkpad T460"
date: 2022-08-22
forum: Hardware
---

### Post by marcsiepman on 2022-08-22
Hi,

I'd like to upgrade to the latest version, but I keep on running into the same problem: the system keeps rebooting after a few seconds. 

At first, I thought it was my HD, so I installed a new disk to no avail.

Then I figured it was the software, so I tried Kubuntu instead of Mate. Same result. 

Now I'm starting to think my laptop is not compatible (Lenovo Thinkpad T460 from 2016, 16GB RAM, i5 dual processor), but I rather hope to be wrong.

I've never understood boot sectors and GRUB. Before I start experimenting with Boot-Repair: is that the place to start? Or is there something else I can do? 

Thanks for any tips!

Marc

---

### Post by oldfred on 2022-08-22
Did you update UEFI? If not you should, but update often resets many settings back to defaults.
You then have to redo the settings in UEFI you need to change to install Ubuntu. My Asus motherboard had 7 settings to redo. Most only need a couple.

 Lenovo T460S unable to update firmware fwupdate disabled boot order lock
[https://ubuntuforums.org/showthread.php?t=2455027](https://ubuntuforums.org/showthread.php?t=2455027)
[https://tothepoles.co.uk/2017/11/16/lenovo-t470p-ubuntu-16-04-install-notes/](https://tothepoles.co.uk/2017/11/16/lenovo-t470p-ubuntu-16-04-install-notes/)

If UEFI settings are good, lets see details:
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

