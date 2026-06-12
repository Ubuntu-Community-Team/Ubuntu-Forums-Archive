---
title: "Cant Install Karmic grub2 wont install"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by sinim on 2009-11-11
Tried doing a fresh install of Ubuntu 9.10 which led an error message stating grub2 boot loader could not be installed to target. After checking the irc chat we concluded that my two HDDs could be confusing the installer causing it to not install. I followed a few links to disable one drive and installing still to no avail. In the end I tried installing Jaunty which installed yet gave me yet another error of grub error 18 this was followed by a message that stated there were some apic problems and a raid problem. My drives are not Raid yet when I tried to install the Karmic live CD /dev/wrapper/ was the only drive available for use. Does anyone have any ideas on installing this. It seems there is some bios problem but I am not sure. I am not worried about lost information, I just want a fresh clean install of karmic. 
I have an asus mb along with 2 SATA drives 250 gb a piece

---

### Post by frodon on 2009-11-11
Before re-installingf you can try to just reinstall GRUB2, instructions can be found there:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by arkhala on 2009-11-11
If your drives show up as being in RAID when you think they shouldn't, have you used your BIOS' RAID in the past? If so, try re-enabling your BIOS' RAID options, then manually delete the RAID array from your BIOS' RAID menu.. Then disable BIOS' RAID options again.. That fixed that little problem for me.

If you are trying to install w/ software RAID and GRUB is giving you problems not wanting to install, choose "Continue without installing GRUB" - let the install finish, then when it's done, select "Go Back" instead of "Continue & Reboot." Then select to install GRUB again.... this worked for me. (though now I have [this]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/396564/") bug - seems mostly harmless, though, as everything boots up fine)

---

