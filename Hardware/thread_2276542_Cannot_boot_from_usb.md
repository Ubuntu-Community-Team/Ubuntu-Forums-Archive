---
title: "Cannot boot from usb"
date: 2015-05-03
forum: Hardware
---

### Post by Alxl on 2015-05-03
On my Asus laptop I have dual boot - Win 8 and Ubuntu 15.04. Both have been recently installed.
Both allow booting. 
But booting from USB is very inconsistent - mostly the USB is not recognized in BIOS accessed in Windows and Ubuntu. My stick with YUMI is not recognized as a bootable media. Neither is a stick with Boot Repair. But a stick with Ubuntu 15.04.iso is recognized at times.

I think that it may have to do with booting in Legacy or UEFI but don't know about these things and don't know how to change these.

Help would be appreciated.

---

### Post by sudodus on 2015-05-03
It is more tricky to boot and install, when UEFI is involved. But it is possible in most computers. Ubuntu 64-bit iso files are made such that DVDs and USB drives can boot both in UEFI and BIOS (CSM) mode. There are many tutorials, wiki pages and help pages that might help you get more reliable results, for example the following links,

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295").

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by Alxl on 2015-05-03
Thanks[**[COLOR=#C61919][B] sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021") for the links.

---

### Post by Alxl on 2015-05-03
One link recommended Chainloading with The 40_custom method

Did ' sudo gedit /etc/grub.d/40_custom ' and it added a partition to the boot options:

unfortunately it did not work and gave various options to edit.

I don't understand what any of these mean but would very much like to try to follow recommendations

[ATTACH=CONFIG]261740[/ATTACH]

[ATTACH=CONFIG]261741[/ATTACH]

---

### Post by sudodus on 2015-05-03
You can use the command line

```
sudo nano /etc/grub.d/40_custom
```

but for a GUI editor (any GUI program) you should use gksudo or gksu

```
gksudo gedit /etc/grub.d/40_custom
```

to avoid problems with permissions later on.

In order to know what to enter, when editing the grub menu, we have to know more about your system, and what you want to achieve with chainloading.

Please enter the output of the following commands

```
sudo parted -l
```
and
```
df
```

and describe what you have in each partition.

---

### Post by Alxl on 2015-05-03
~$ sudo parted -l```

Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 
Number  Start   End    Size    File system     Name                          Flags
 1      1049kB  316MB  315MB   ntfs            Basic data partition          hidden, diag
 2      316MB   420MB  105MB   fat32           EFI system partition          boot, esp
 3      420MB   555MB  134MB                   Microsoft reserved partition  msftres
 4      555MB   355GB  354GB   ntfs            Basic data partition          msftdata
 7      355GB   362GB  7233MB  fat32                                         msftdata
 6      362GB   493GB  131GB   ext4
 5      493GB   500GB  7169MB  linux-swap(v1)
First 4 are Win8
7 for some storage
5 & 6 Ubuntu 15.04
```

:~$ df```

Filesystem     1K-blocks     Used Available Use% Mounted on
udev             1954028        0   1954028   0% /dev
tmpfs             393036     6136    386900   2% /run
/dev/sda6      125509492 86366456  32744472  73% /
tmpfs            1965168      160   1965008   1% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            1965168        0   1965168   0% /sys/fs/cgroup
/dev/sda2          98304    28091     70213  29% /boot/efi
cgmfs                100        0       100   0% /run/cgmanager/fs
tmpfs             393036       48    392988   1% /run/user/1000
```



Actually, all I want is to be able to plug in a USB with a iso Linux and boot. Right now a live USB is not recognized at boot time.  
But I used Ubuntu 15.04 iso to install Ubuntu - so at the time it was recognized.

Thanks  sudodus

---

### Post by sudodus on 2015-05-04
> **Alxl said:**
> ... But a stick with Ubuntu 15.04.iso is recognized at times ...

How did you create the stick with Ubuntu 15.04.iso? With which tool?

> **Alxl said:**
> ~$ sudo parted -l```

Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: [COLOR=#ff0000]gpt[/COLOR]
Disk Flags: 
Number  Start   End    Size    File system     Name                          Flags
 1      1049kB  316MB  315MB   ntfs            Basic data partition          hidden, diag
[COLOR=#ff0000] 2      316MB   420MB  105MB   fat32           EFI system partition          boot, esp[/COLOR]
 3      420MB   555MB  134MB                   Microsoft reserved partition  msftres
 4      555MB   355GB  354GB   ntfs            Basic data partition          msftdata
 7      355GB   362GB  7233MB  fat32                                         msftdata
 6      362GB   493GB  131GB   ext4
 5      493GB   500GB  7169MB  linux-swap(v1)
First 4 are Win8
7 for some storage
5 & 6 Ubuntu 15.04
```

:~$ df```

Filesystem     1K-blocks     Used Available Use% Mounted on
udev             1954028        0   1954028   0% /dev
tmpfs             393036     6136    386900   2% /run
[COLOR=#ff0000]/dev/sda6      125509492 86366456  32744472  73% /[/COLOR]
tmpfs            1965168      160   1965008   1% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            1965168        0   1965168   0% /sys/fs/cgroup
[COLOR=#ff0000]/dev/sda2          98304    28091     70213  29% /boot/efi[/COLOR]
cgmfs                100        0       100   0% /run/cgmanager/fs
tmpfs             393036       48    392988   1% /run/user/1000
```

Actually, all I want is to be able to plug in a USB with a iso Linux and boot. Right now a live USB is not recognized at boot time.  
But I used Ubuntu 15.04 iso to install Ubuntu - so at the time it was recognized.

Thanks  sudodus

You are running in UEFI mode and your root partition is** /dev/sda6**.

If you have no other drive connected, the pendrive will be recognized as the second drive in the grub menu. This means that 'External drive on (hd1) ...' should be correct. The first drive is (hd0). What happens if you just select the line and press Enter instead of pressing 'e' to edit it?

I have used this method in several computers and know that it works well in BIOS mode in order to chainload a pendrive or other external drive. I'll check in UEFI mode and come back ...

---

### Post by sudodus on 2015-05-04
No, I'm sorry. I tested the 40_custom method, and I did ***not*** manage make it work in UEFI mode. I have changed the information in the help page

[https://help.ubuntu.com/community/In...n/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

to make it clear, that it works only in BIOS mode.

---

### Post by Alxl on 2015-05-05
Boot allows to add a new boot option.
Here are the pics.  I want to boot a live USB    /dev/sdb1
What do I enter for Name? File System? Path?
Thanks

---

### Post by sudodus on 2015-05-05
I must admit, that I don't know what to enter into that edit box. I hope someone with experience of the same UEFI system can help you. The UEFI systems in my family's computers have other menu systems, and the connected USB device is found and selected automatically.

---

### Post by Alxl on 2015-06-09
Actually the problem was solved by setting “Lunch CSM” to Enabled   and "Secure Boot Control" to Disabled (both in BIOS).
Laptop now boots from any live USB or CD.
Thanks

---

### Post by sudodus on 2015-06-10
Congratulations and thank for sharing your solution :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

