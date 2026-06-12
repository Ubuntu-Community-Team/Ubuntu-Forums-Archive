---
title: "cannot boot to xp after loading Ubuntu"
date: 2008-11-15
forum: General Help
---

### Post by vancouverron on 2008-11-15
I wanted to work with Ubuntu 8.04, but before installing it I loaded it from a cd. Since then I cannot boot into XP any longer. The system hangs just after the initial message "loading windows xp". The screen goes blank, and the disk activity light stays on (i.e. the disk seems to be in an endless loop). 

I have a second drive that has XP on it, loaded xp, and looked at the drive that no longer boots. All files are there and accessible. 
Then I downloaded and ran mbrfix. That did not fix it. Still the same blank screen. I wondered how to get to the boot segment while the system was still hanging, when all of a sudden the system re-started on its own, and now loaded xp. 

This leads me to believe that somehow I have managed a dual-boot, but without the option of choosing one or the other system. At this stage I'd like to fix the system so xp boots "normally". Any suggestions short of re-installing xp? 
Here is a copy of the boo.ini file: 

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

---

### Post by caljohnsmith on 2008-11-15
OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"

```
Also, that "Starting up..." error that you got when booting XP is often caused by the file system parameters being corrupt in the XP partition's boot sector, which sometimes happens after resizing the partition. Fortunately you can usually fix it with "testdisk". To use testdisk, first make sure the Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens when you boot XP.

---

### Post by vancouverron on 2008-11-15
Aloha Caljohnsmith, 

First, many thanks indeed for the quick response! Much appreciated. 

Here is the output from the two commands: 

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x442e442d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    97659134    48829536    7  HPFS/NTFS
/dev/sda2        97659135   312576704   107458785    f  W95 Ext'd (LBA)
/dev/sda5        97659198   195318269    48829536    7  HPFS/NTFS
/dev/sda6       195318333   312576704    58629186    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
ubuntu@ubuntu:~$ 


Next step I'll download testdisk and will post results. 

Mahalo!

---

### Post by vancouverron on 2008-11-15
Ok, it seems that the mbr is ok. Here is the output: 

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  6078 254 63   97659072 [System]

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.





[  Quit  ]  [  List  ]  [Rebuild BS][Repair MFT][  Dump  ]
                            Return to Advanced menu

Somehow I suspect that the boot loader or whatever the file is called that follows the mbr is corrupt. Any other suggestions?

Mahalo!

---

### Post by caljohnsmith on 2008-11-15
Well, your boot.ini is pointing to the correct drive and partition, and since you aren't getting a "ntldr missing" error, then you are making it at least as far as the initial booting process; so I'm not sure what is causing your Windows to hang. I think if I were you, I would just boot your Windows Install CD and do a "Windows Repair", which will replace all the fundamental Windows system files while leaving your installed programs and personal files untouched. Good luck and let me know what you decide to do.

---

### Post by vancouverron on 2008-11-15
Well Caljohnsmith, you have done it. After re-booting, the system booted flawlessly to XP. 

THANK YOU VERY MUCH INDEED - awesome, that the problem got fixed THIS fast!!

Thanks again, and have a great day. 

Vancouverron.

---

### Post by vancouverron on 2008-11-15
Aloha Caljohnsmith, 

I also thought that we did not really change anything. However, following your suggestions carefully and step by step obviously did something (good!). 

Thanks again!
Vancouverron

---

