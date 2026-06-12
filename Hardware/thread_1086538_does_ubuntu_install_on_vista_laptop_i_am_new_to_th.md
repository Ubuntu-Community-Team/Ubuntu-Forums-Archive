---
title: "does ubuntu install on vista laptop i am new to this"
date: 2009-03-04
forum: Hardware
---

### Post by HANGER18 on 2009-03-04
i am very new to this and need help

---

### Post by albandy on 2009-03-04
It depends on your computer model, but usually it works.
If you want to test it, you can install it in a windows folder.
When you put the ubuntu cd in windows, a installation menu will appear, allowing you to install ubuntu in a windows folder.

---

### Post by HANGER18 on 2009-03-04
ok i downloaded it yesterday... and will this get rid of vista all together

---

### Post by markdavidoff on 2009-03-04
When installing, there are several install modes

you can use a guided install that completely wipes vista(uses the whole drive)
or you can use a guided install that takes 50% of the remaining free space and installs ubuntu on that

otherwise, you can choose the manual partition option
if you do, create a swap partition (generally, double that of the amount of RAM (memory) on your computer is a good amount, and an EXT3 partition with mount point / of any size you want.

Also, the vista bootloader will be replaced by the linux one by default.

This will not prevent you from loading vista, however, but if you want to keep the vista bootloader, you can install it to the partition that has ubuntu on it in the final step of the install by clicking OPTIONS and selecting that partition. You would then need a tool such as EasyBCD to configure the windows bootloader to load ubuntu.

feel free to ask any more questions

---

### Post by HANGER18 on 2009-03-04
ok thanks .... sorry for not knowing a thing about this ... so when i install ubuntu it willl wipe all the windows files

---

### Post by markdavidoff on 2009-03-04
In summary...no it will not...as long as you tell it not to during the install.

You will be presented with the option to use 100% of the drive (wiping everything including windows)
or to use the free space (leaving windows)

---

### Post by ashwinhgtx on 2009-03-04
> **HANGER18 said:**
> ok thanks .... sorry for not knowing a thing about this ... so when i install ubuntu it willl wipe all the windows files

Not always. That will happen only if you decide to format the whole hard drive, get rid of vista thereby, and then install Ubuntu as the sole operating system on your computer.

It is better for you if you try out Ubuntu through Wubi which will install Ubuntu as a sort of program inside windows. You can remove Ubuntu later through Add or Remove Programs option in the Windows Control Panel.

To install through Wubi, make sure you have at least 5GB free on your hardrive. Then insert the Ubuntu CD while you are on Vista. A pop up will ask you how and where you want to install Ubuntu. Select the drive with the free space and continue with the installation. After you reboot you will be presented with an option to boot either into Vista or Ubuntu. Enjoy.

If you want to install Ubuntu alongside Vista you can use the dual boot install. There are many guides on the internet to help you. Just google it. remember to back your data before doing this. And you will not be able to remove Ubuntu using the Add or Remove Programs in Vista as you haven't used Wubi for the install.

The third option is to get rid of Vista completely and install Ubuntu. Thus is recommended only if you are comfortable with Ubuntu and have convinced yourself that you don't need Vista anymore.

Have fun with Ubuntu.:popcorn:

---

