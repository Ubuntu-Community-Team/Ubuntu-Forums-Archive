---
title: "[SOLVED] 1280x1024 ATI Rage 128 Pro not working"
date: 2008-10-14
forum: General Help
---

### Post by Spaceman9 on 2008-10-14
I have an ATI All-In-Wonder 128 Pro video card with 32Mgs of ram. It was made in 2000. The highest resolution I can go to is 1152x864. I'm using Ubuntu 8.04. The system is up to date.

Is there any driver for Ubuntu that will let me do 1280x1024? I can do 1280x1024 with Mandriva and OpenSUSE. Is there some special driver in Mandriva and OpenSUSE that isn't available for Ubuntu? Thankx for any help.

---

### Post by overdrank on 2008-10-14
> **Spaceman9 said:**
> I have an ATI All-In-Wonder 128 Pro video card with 32Mgs of ram. It was made in 2000. The highest resolution I can go to is 1152x864. I'm using Ubuntu 8.04. The system is up to date.

Is there any driver for Ubuntu that will let me do 1280x1024? I can do 1280x1024 with Mandriva and OpenSUSE. Is there some special driver in Mandriva and OpenSUSE that isn't available for Ubuntu? Thankx for any help.
Hi and have you tried the command using the alt, F2 keys and enter ```
gksu displayconfig-gtk
``` and adjust there.

---

### Post by tgalati4 on 2008-10-15
Try 16-bit color.

---

### Post by Spaceman9 on 2008-10-15
overdrank I tried that command and tried different settings for ATI cards and now the highest res is 640x480. I don't know how to get it back to the settings it had before. HELP! lol


> **tgalati4 said:**
> Try 16-bit color.

Before everything went bonkers I tried 16 bit color but I still couldn't go to a higher res.

---

### Post by tgalati4 on 2008-10-15
sudo dpkg-reconfigure xserver-xorg

Log into SLED and print out your /etc/X11/xorg.conf file.  Compare this with what you have in Ubuntu.

---

### Post by Spaceman9 on 2008-10-15
> **tgalati4 said:**
> sudo dpkg-reconfigure xorg-xserver

Log into SLED and print out your /etc/X11/xorg.conf file.  Compare this with what you have in Ubuntu.

This is what I got with the command.
bruce@bruce-desktop:~$ sudo dpkg-reconfigure xorg-xserver
[sudo] password for bruce: 
Package `xorg-xserver' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xorg-xserver is not installed
bruce@bruce-desktop:~$ SLED
bash: SLED: command not found
bruce@bruce-desktop:~$ 

What is SLED? I tried to run it but it's not running. What if I just rewrite the xorg.conf file with xorg.conf.1 file?

---

### Post by tgalati4 on 2008-10-15
My error.  SLED is a nickname for SUSE Linux Enterprise Edition. Look at the config files in Opensuse.

Try xserver-xorg.

---

### Post by Spaceman9 on 2008-10-15
> **tgalati4 said:**
> My error.  SLED is a nickname for SUSE Linux Enterprise Edition. Look at the config files in Opensuse.

Try xserver-xorg.


This is what I got. Do I need to install something else?

bruce@bruce-desktop:~$ xserver-xorg
bash: xserver-xorg: command not found
bruce@bruce-desktop:~$

---

### Post by Spaceman9 on 2008-10-15
I got the res back to where it was before by using a command from this page [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)

The command is in the xorg.conf file. The command is 

sudo dpkg-reconfigure -phigh xserver-xorg

I copy and pasted that command into a terminal and it over wrote the xorg.conf file. Then I rebooted my computer and the res is back to what it was after I installed Ubuntu.

I don't think I can do the higher res until I buy a newer video card. I don't understand why Mandriva and OpenSUSE can do 1280x1024 with my video card, but Ubuntu can't. I'm sure there's a good reason though. I like Mandriva, but notice I'm using Ubuntu. I can live with Ubuntu. I can't live with Mandriva and OpenSUSE.

Thankx for the help guys.

---

### Post by Spaceman9 on 2008-10-15
This is really weird. I installed Envy and had it try to automatically install the drivers for my ATI card. It failed. So, I used the Manual Install option. Envy installed everything? I don't know for sure but it downloaded all the packages and I tried to configure my card and monitor but the best resolution I could get was 800x600.

I rebooted and had Envy uninstall everything it had installed. I rebooted. I was able to set the res and monitor at that point to 1280x1024. Then I rebooted again. Gnome booted into the 1280x1024 res. 

Why could I not get anything better than 800x600 with the drivers from Envy after I installed them? I don't know. Why could I set the res at 1280x1024 after I used Envy to uninstall the drivers it installed? I don't know.

It's all working now so I'm happy, my monitor is happy and as my buddy The Bard would say &#8220;All's well that ends well.&#8221;

---

