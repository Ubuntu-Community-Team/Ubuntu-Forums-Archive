---
title: "Partition Help Needed - Booting across multiple hdds"
date: 2008-10-15
forum: General Help
---

### Post by tj.milligan on 2008-10-15
Upgrading my computer, which presently is a dual boot off a single hdd:

CURRENT

*Boot hdd* (279.46 formatted GB)

```
/dev/sda1	ntfs		/media/winxp	160.00 GB	(boot)
/dev/sda2	extended			119.46 GB
  /dev/sda5	linux-swap			1.00 GB
  /dev/sda6	ext3		/home		106.45 GB
  /dev/sda7	ext3		/		12.00 GB
```

*Secondary hdd for audio, video & photo partitions (not shown).*

For the upgrade (I'm going to fresh install all OSes), I want to boot Vista 32-bit and XP 32-bit off one hdd, and Ubuntu 8.10 off the other. **Is the following possible:**

*Boot hdd* (279.46 formatted GB)

```
/dev/sda1	ntfs		/media/vista32	160.00 GB	(boot)
/dev/sda2	ntfs		/media/xp32	119.46 GB
```

*Secondary hdd* (465.76 formatted GB)

```
/dev/sdb1	extended			100.00 GB
  /dev/sdb5	linux-swap			1.00 GB
  /dev/sdb6	ext3		/home		87.00 GB
  /dev/sdb7	ext3		/		12.00 GB
/dev/sdb2	extended			345.76 GB
  /dev/sdb9	ext3		/media/photos	25.00 GB
  /dev/sdb10	ntfs		/media/video	220.76 GB
  /dev/sdb11	fat32		/media/audio	100.00 GB
```

Again, Is it possible to boot across more than one hdd, like above? I'm installing xp32, then vista32, then ubuntu 8.10. I want to know that this is possible before installation :) Thanks in advance.

---

### Post by jerome1232 on 2008-10-15
I see no problems with that partitioning scheme.

---

### Post by tj.milligan on 2008-10-15
> **jerome1232 said:**
> I see no problems with that partitioning scheme.

Great... I'll cross my fingers and attempt this later in the week then. Thanks.

---

### Post by tj.milligan on 2008-10-15
How do I set up grub?

Since I'm installing xp first, then vista on the same hdd (sda), this will install the vista boot loader, allowing me to select xp or vista. Then I'm installing ubuntu on the next hdd (sdb), which will prompt me to install grub. Where do I tell the ubuntu installer to install grub to?

---

### Post by jerome1232 on 2008-10-15
I would just let it default to the MBR, it should pick up both XP and Vista. My guess is GRUB chainloads the ntldr anyways which will give the option of Vista/Xp.

[COLOR="Red"]***BUT***[/COLOR] I don't have experience with triple booting 2 Microsoft OS's and 1 Linux OS, have only done it with all Linux OS's, which worked just fine (Ubuntu detected OpenSuse, Debian, and itself)

---

### Post by caljohnsmith on 2008-10-15
When you have more than one HDD, I think it is important to understand the following because it will save you lots of headaches in the long run:

Grub, the boot loader for Ubuntu, will by default install to the MBR (Master Boot Record) of drive (hd0) (otherwise known as /dev/sda) which in most cases is your internal HDD. The thing to keep in mind is that Grub actually lives in two places:
[LIST=1]
[*]In the MBR of the HDD so you can boot it on start up.
[*]Grub also has files necessary to boot which reside in the /boot/grub folder in your Ubuntu install.
[/LIST]
So if you install Grub to the MBR of your internal HDD, it will look for its boot files on the external HDD in the Ubuntu /boot/grub directory. That will work just fine as long as nothing happens to your external HDD; but if you disconnect your external HDD, or if anything happens to it, you won't be able to boot any of your OSes including Windows, because Grub won't be able to access its necessary boot files on the external drive. Also, if you uninstall Ubuntu, you will have to use a Windows Install/Recovery CD to replace Grub in the MBR of the internal drive with a Windows MBR to get Windows to boot again. If that is acceptable to you, then you don't need to do anything special about Grub when you install Ubuntu.

But personally what I would recommend is setting your BIOS to boot the external drive on start up instead of your internal drive, and then you can install Grub to the MBR of the external drive; that leaves your internal HDD completely untouched, so if anything happens to your external drive (including if you decide to uninstall Ubuntu), you will still be able to boot Windows on your internal drive. Also note that you can easily add an entry in your Grub menu so that you can boot Windows on your internal drive, so you don't need to change your BIOS just to boot the internal Windows drive. I think this scenario is more ideal than what I described above where Grub is installed to the MBR of your internal drive.

If you want to do this, all you have to do is change your BIOS boot order so that your external drive boots first, and then when you go through the Ubuntu installer, at the final installation step click on the "advanced" button, and tell Grub to install to /dev/sdb or whichever is your external drive. If you aren't sure which is your external drive, you can open a terminal (applications > accessories > terminal) and do:
```
sudo fdisk -lu
```
And that will show all your drives. I know all this may seem a bit much, but in the long run it can save you a lot of headaches if you understand some of these concepts up front, so you can make the best choices. If you have any questions, let me know. :)

---

### Post by WWSmith36 on 2008-10-15
There you two important thing that you should consider before installing.  First is the way the Windows handles it dual boot.  When the second windows OS is installed it does not contain the required files for booting.  The booting is handled by the first windows installation.  The problem with this is that if the first windows installation is damaged, you will not be able to boot the second on either.

I recommend that you install all your OS´s so that they are completely independent of each other.

The Grub Page is a good reference, since it is quite long search for these references **More than one Windows on the same disk** and **Windows operating system entries**
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Here is another page which might be useful.  It describes how to keep the Windows OS independent from each other.
[http://www.goodells.net/multiboot/index.htm](http://www.goodells.net/multiboot/index.htm)

You may wish to disregard all of this information if you would like.  There is really no right or wrong way of doing it.  This is method is the preferred **techno-geek-computer-guru** configuration.

Hope it helps

---

