---
title: "Ubuntu+Vista on two separate HDs...some problems"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by Quaffit on 2009-08-12
Hi all,

about a week ago I installed Ubuntu on my second HD. Before I installed it, I removed my first HD with Vista from my computer on it to make sure I won't accidentally ruin my Vista installation. I did not install Grub because I wanted to boot from either HD via the F12 boot menu on my Acer laptop. This worked fine. However I discovered the following:

- when booting Vista after I previously ran Ubuntu, Vist had checkdisk running every time, saying there were errors on the drive.

A friend recommended me to install a bootloader because there is an incompatibility problem between Vista and Linux regarding the way both OS startup. Well so I wanted to install Acronis bootloader because I trusted it, and this now ruined my Vista partition because it never recognised Vista so it wants to boot Ubuntu and since I did not install Grub it halts on booting. Fortunately I can boot Ubuntu via the F12 menue.

My Vista drive is still accessible in Ubuntu so I'm currently copying my files to an extern HD before I will do a clean reinstallation of Vista.

However, there are still questions I did not find an answer for, that's why I now ask you:

1) I want to remove my second HD with Ubuntu on it before I will install Vista on the first HD. This because I'll have to install Vista from my recovery DVD's. I have no regular Vista installation DVD because I got my Vista preinstalled on my Acer Aspire 8930G laptop and I'm not sure if the recovery DVD will allow me to choose the partition I want to install Vista at. The only options the recovery menue offers after booting from DVD is to do a factory clean install, or to restore from backup, but the latter option is grayed out, so only a factory clean install is possible.

2) Can I activate Grub after installing Vista so I can choose to boot either Ubuntu or Vista? I noticed there is a recovery option in the Ubuntu bootup menue. I tried this once to see what it offers and as far as I remember there is an option to install Grub. Can I trust this? Won't it ruin my configuration? I'm sorry for the dumb questions but I'm still new to Ubuntu and after my experiences with bootloaders, past and recent, I never trust them.

3) Do I really need Grub on a dual-OS-system? I ask because Vista let checkdisk run every time after I previously ran Ubuntu, but this might also have happened because my Vista installation wasn't healthy anymore. In fact I was so sick of all the trouble Vista makes even if using it just normally, that's why I tried Ubuntu and I'm really happy with Ubuntu. I'm using KDE4 with it and it's great. I still have a problem of my new Canon printer not yet working with it but I'm sure I can solve that also. In the future I want to use Vista only for games, blue-ray disc playing and some programs no Linux alternative exists for, like the software of my Canon camera.

Any help with my questions regarding dual-OS would be highly appreciated.

best wishes

Quaffit

---

### Post by Mark Phelps on 2009-08-12
Others may recommend something different, but I run a similar setup and will recommend what works for me ...

You're right that the recovery media will completely replace your Vista install. So, disconnect any other drives and do the recovery.

Then, disconnect your Vista drive, and connect your Ubuntu drive, booting from it.  I'm presuming it won't boot since GRUB is not installed, so install GRUB from the LiveCD to that drive.

Then, reconnect your Vista drive, but still boot from the Ubuntu drive and manually add a boot stanza to the menu.lst file for Vista.

This way, your Vista installation remains untouched, meaning, that the MBR of your Vista drive is not overwritten by installing GRUB.

---

### Post by Quaffit on 2009-08-12
Mark,

many thanks for your quick reply....

> **Mark Phelps said:**
> 
Then, disconnect your Vista drive, and connect your Ubuntu drive, booting from it.  I'm presuming it won't boot since GRUB is not installed, so install GRUB from the LiveCD to that drive.

Actually my Ubuntu drive, which is my second HD, is bootable even without Grubs installed. There is an option in the menu that appears when booting Ubuntu (not a bootloader menu), offering to boot in recovery mode. Then one may choose among other options to install Grub. I guess this will work.

> 
Then, reconnect your Vista drive, but still boot from the Ubuntu drive and manually add a boot stanza to the menu.lst file for Vista.
Is this the correct command for it?: 
sudo gedit /boot/grub/menu.lst

> 
This way, your Vista installation remains untouched, meaning, that the MBR of your Vista drive is not overwritten by installing GRUB.So I hope Grub will keep my Ubuntu drive also alive ;o). I'm currently backing up my data from the Windows drive and will tell you about success or failure of my new configuration as soon as I installed Vista again.

best wishes

Gaston Graf (Quaffit)

---

### Post by Mark Phelps on 2009-08-13
> **Quaffit said:**
> Actually my Ubuntu drive, which is my second HD, is bootable even without Grubs installed. 
Is this true even if it's the only drive connected? Ubuntu can't boot by itself; it must be supplied a boot loader -- typically GRUB or LILO. Still, I'm guessing that if you CAN boot directly from your Ubuntu drive, you really do have GRUB installed.

> Is this the correct command for it?: 
sudo gedit /boot/grub/menu.lst Change it to "gksudo gedit ...", but otherwise, OK.

---

