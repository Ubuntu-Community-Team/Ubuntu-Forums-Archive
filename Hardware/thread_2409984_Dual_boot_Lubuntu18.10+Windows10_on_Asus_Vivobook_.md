---
title: "Dual boot: Lubuntu18.10+Windows10 on Asus Vivobook E203"
date: 2019-01-09
forum: Hardware
---

### Post by ubtnk on 2019-01-09
Now it's time to say goodbye to my 12 year-old Compaq Presario V3000 notebook and buy new notebooks.

I'm interested in either 'Asus Vivobook E203NAH with 500 Gb HDD' or 'Asus Vivobook E203MA with 64 Gb eMMC Flash Storage'. 

Is it difficult to install Lubuntu 18.10 after pre-installed Windows 10 Home for dual boot in such Asus notebook?

For it will be a new notebook with 4 Gb RAM, can you please tell me which Ubuntu family I should install?

---

### Post by mikasu on 2019-01-09
Take something with a big amount a storage... 500GB should be fine. I did that with Ubuntu 18.04.1, you actually need to install Windows 10 first on a dual boot with both OS on the same drive, it's because of how Windows wants to be installed... It is recommended to do your partitions yourself ("something else") as it's usually more secure for both OS' integrity. I could walk you through, I always install Ubuntu with manual partitioning. Just read a bit on Internet about what was other user's experience installing Ubuntu on the device you're looking for.

---

### Post by ubtnk on 2019-01-11
> **mikasu said:**
> Take something with a big amount a storage... 500GB should be fine. I did that with Ubuntu 18.04.1, you actually need to install Windows 10 first on a dual boot with both OS on the same drive, it's because of how Windows wants to be installed... It is recommended to do your partitions yourself ("something else") as it's usually more secure for both OS' integrity. I could walk you through, I always install Ubuntu with manual partitioning. Just read a bit on Internet about what was other user's experience installing Ubuntu on the device you're looking for.

[https://github.com/canonical-websites/tutorials.ubuntu.com/issues/689](https://github.com/canonical-websites/tutorials.ubuntu.com/issues/689)

Having read from this, I have no dare to follow from a lot of suggestion. Can you please explain to me how to install step by step?

---

### Post by oldfred on 2019-01-11
Each vendor or configuration may need different boot parameters. 
Like nVidia video cards/chips normally need nomodeset boot parameter.

See link in my signature for general UEFI install instructions.

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)  & 
[https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi](https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi)
UEFI install,windows 8 with Something Else screen shots, similar for newer versions of Ubuntu
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

### Post by mikasu on 2019-01-11
I expect the Windows to be pre-installed so do the classic setup then go in the disk manager and shrink the size of your C: Drive to the amount of storage you wan to give to Ubuntu. Then you need to get an iso of Ubuntu and burn it on a usb drive (using rufus for example). Expect UEFI for recent hardware. Olfred provided you very useful infos so I will only give you my knowledge about the partition sizing. You want to use that unallocated partition that you created on Windows to do that, while on the Ubuntu setup. So you choose "something else" when you get to the screen asking you how you want to install Ubuntu. Then, you select the empty partition and click the "+" to make partitions, select a partition and do "-" to delete it. Everything is sized in megabytes (1024MB = 1GB, ig you know that), you want a root partition (ext4 with mount point "/") from 20GB to 25GB or more to your likings, I personally feel that 22GB is good. Then you want a "swap" partition, this one will be sized depending on the amount of ram, with 4GB, it's often recommended to use a 4 to 8GB swap partition, depending on your use. For 8GB, depending on your use, you can size your swap equal to the amount of ram or you can turn it down a little to about 6GB. More than 8GB is really on your type of use. I have 16GB of ram, for example, and my swap is 6GB(actually about 5.9-ish GB) just to feel safe but it's never used. Then you want to do your "/home", this will use the rest of your free space, it's a ext4 file system, mount point is "/home". That partition is recommended to be able to easily reinstall the OS while not loosing your user data. Finally, select the Windows Boot Manager as boot partition. Then it will all be just about boot order in the BIOS.

If you want to make a simpler installation, do the swap first, then use all the remaining space for the root partition, if there are no "/home" in your partitions, the OS will put it in the root partition. Note that you might lose your data when you reinstall your OS or upgrade it through a reinstallation process instead of a distro upgrade.

That said, you should have all the infos that you need to setup your dual boot :D

(to be noted, what I wrote here is how I install Ubuntu manually and it's how I recommend to do it from personal experience. Some of the recommendations also comes from things that I read online when setting up my dual boot. What Olfred provided gives very good informations and the setup that is shown in one of the links is also good. I just find that for general basic-ish use, the setup I suggested is fine and gives more space for the user. Though if you plan on installing very large softwares on the root of the system, more space than what I suggested would be a good idea.)

---

