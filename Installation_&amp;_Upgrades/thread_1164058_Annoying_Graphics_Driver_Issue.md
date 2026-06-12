---
title: "Annoying Graphics Driver Issue"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by airplaneman on 2009-05-19
Alright, well after about 3 different installs of Vista and XP, and having issues with all of them (not graphic driver issues, other things) I've gotten annoyed and decided to switch to Linux. So far, it's been great! A little hard to do some things but that is probably because I'm new to it. I'm using Ubuntu version 9.04.

Now, my problem is I can't seem to install my graphics drivers for my EVGA GTX 260 graphics card. I've looked around and it seems that it 'should' show up in System -> Admin -> Hardware Drivers but it does not. Everywhere I have searched has said to go there and enable them, but it doesn't show up in that list. Can someone help me? Thanks in advance.

EDIT: Also, I would like to partition my hard drive so I can have 1 partition for my programs and OS, and one for my files (Similar to a C:/ and D:/ drive in Windows.) Keep in mind, I do not want to dual boot Windows and Ubuntu.

---

### Post by dstew on 2009-05-19
Go to System --> Administration --> Software Sources. In the Ubuntu Software tab, make sure the Proprietary Drivers box is checked. Then go to the Third Party Software tab and check the box for the partner repository. See the [Ubuntu Repositories documentation]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by airplaneman on 2009-05-19
> **dstew said:**
> Go to System --> Administration --> Software Sources. In the Ubuntu Software tab, make sure the Proprietary Drivers box is checked. Then go to the Third Party Software tab and check the box for the partner repository. See the [Ubuntu Repositories documentation]("https://help.ubuntu.com/community/Repositories/Ubuntu").


Ahh thank you so much!

---

### Post by Vrekk on 2009-05-19
> **airplaneman said:**
> 
EDIT: Also, I would like to partition my hard drive so I can have 1 partition for my programs and OS, and one for my files (Similar to a C:/ and D:/ drive in Windows.) Keep in mind, I do not want to dual boot Windows and Ubuntu.

What you are talking about is basically a seprate /home dirictory.  This keeps ur progams and OS on / and ur personal files on /home.  This is easiest to do while installing, but this link might be able to help u creat a seprate /home without a reinstall.  However, I would recomend backing up anything important, just to be safe. [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by airplaneman on 2009-05-19
> **Vrekk said:**
> What you are talking about is basically a seprate /home dirictory.  This keeps ur progams and OS on / and ur personal files on /home.  This is easiest to do while installing, but this link might be able to help u creat a seprate /home without a reinstall.  However, I would recomend backing up anything important, just to be safe. [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)


Ahh excellent! Thank you. 

Now, anyone know how to install windows programs with Wine? I've installed the newest version of Wine but I can't seem to figure out how to get programs on it, mainly Call of Duty 4 and Photoshop CS4

---

### Post by Vrekk on 2009-05-19
> **airplaneman said:**
> Ahh excellent! Thank you. 

Now, anyone know how to install windows programs with Wine? I've installed the newest version of Wine but I can't seem to figure out how to get programs on it, mainly Call of Duty 4 and Photoshop CS4

You can install apps in wine the same way u would in windows.  You run the installer file the same way you in windows if autorun is disabled.  Right click on the installer and hit Open with Wine. I would check out the app database to make sure your apps run correctly though.  If i remember correctly, COD4 should run fine, BUT PunkBuster wont.  Photoshop might not work though (I have heard stories where it runs great and ones where it wont run at all!).  If it dose not you might want to try out GIMP image editor. I've never used it (nor photoshop) but I've seen what it can do.

Happy Ubuntuing!

---

### Post by airplaneman on 2009-05-19
> **Vrekk said:**
> You can install apps in wine the same way u would in windows.  You run the installer file the same way you in windows if autorun is disabled.  Right click on the installer and hit Open with Wine. I would check out the app database to make sure your apps run correctly though.  If i remember correctly, COD4 should run fine, BUT PunkBuster wont.  Photoshop might not work though (I have heard stories where it runs great and ones where it wont run at all!).  If it dose not you might want to try out GIMP image editor. I've never used it (nor photoshop) but I've seen what it can do.

Happy Ubuntuing!

Well I've installed Win7 on my comp to dual boot with Ubuntu..god damn this OS is terrible but I feel I need to make a slow transition, Linux is so different and takes a lot of time to figure out everything. Thanks for all your help guys!

---

### Post by airplaneman on 2009-05-20
Got Windows 7 up and running and sucessfully dual booting with ubuntu, now, I need some help with the divx web player plugins or whatever for firefox. I've looked around and found lots of threads on it but they either don't work, or I can't understand what they are talking to. If someone could give me some step by step instructions, that'd be fantastic! 

Also, any way to just have ubuntu come up in the boot manager along with my other OS's. I don't like how it has safe mode and memtest options as well.

Thanks again!

---

### Post by dstew on 2009-05-20
If you are referring to the grub boot menu, you can remove the recovery and memory test options by editing the /boot/grub/menu.lst file. To use the graphical editor gedit, open a command line with alt-F2, then```
gksudo gedit /boot/grub/menu.lst
```You can comment out (with a #) or remove the offending menu entries.

Later on, after you get some updates, you will get new kernels. These will be added to the menu. When you want to remove older kernels, do not edit menu.lst. Remove the older kernels using Synaptic (check the older kernels for uninstallation, then Apply). This will remove the menu entries and remove the old kernel files as well, freeing up disk space.

Here is a [nice web page]("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/") that shows you these things.

---

### Post by airplaneman on 2009-05-20
> **dstew said:**
> If you are referring to the grub boot menu, you can remove the recovery and memory test options by editing the /boot/grub/menu.lst file. To use the graphical editor gedit, open a command line with alt-F2, then```
gksudo gedit /boot/grub/menu.lst
```You can comment out (with a #) or remove the offending menu entries.

Later on, after you get some updates, you will get new kernels. These will be added to the menu. When you want to remove older kernels, do not edit menu.lst. Remove the older kernels using Synaptic (check the older kernels for uninstallation, then Apply). This will remove the menu entries and remove the old kernel files as well, freeing up disk space.

Here is a [nice web page]("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/") that shows you these things.

Sweet link man thanks. Showed me exactly what to do. Is there are rep system on these forums? I feel I should give you and some others who helped me some rep if there is.

---

### Post by Vrekk on 2009-05-21
> **airplaneman said:**
> Sweet link man thanks. Showed me exactly what to do. Is there are rep system on these forums? I feel I should give you and some others who helped me some rep if there is.

Sorta, everyone gets beans for posting in the support part of the forums but thats about it.

Btw, it is helpfull to go to Thread Tools and edit you tags to include one saying sloved.  That way the real pro's can help the people who need it

---

