---
title: "Making WinXP boot from third HDD"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by 73ckn797 on 2009-05-25
Here is the deal.

I had Windows XP installed on an IDE 250Gib drive and it was (hd0) in the physical boot order.  Through some confusion trying to install Fedora 10, the drive was corrupted and I lost the Windows XP installation. Since I do not use XP much anymore I wanted that first drive to be Ubuntu, which it now is (9.04 64bit ext4). I installed Windows on a third (SATA2) drive connection.

```
/dev/sda1: UUID="a6ad6af7-c6f3-40de-b7da-4de6e4a4f851" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="2a6f6ef3-b03e-4a52-97e0-9594fbc29574" 
/dev/sdb1: UUID="058C68677FD1D240" LABEL="SATA2" TYPE="ntfs" 
/dev/sdc1: UUID="3cb9d90a-ebd9-4bb7-832d-550e9f870042" TYPE="ext4" 
/dev/sdc5: UUID="da68f9b7-7e11-4286-addc-15f7ee0ec08c" TYPE="ext3"
```It shows as being sdb/hd1 though the physical order in BIOS is the third drive.

I have tried editing grub to be (hd1) and also using map entry. I have tried all other options of changing drive designations in grub.

I am getting "bootmgr missing" messages when trying to boot. This is probably due to Windows wanting the priority.

Using the WinXP disk in recovery mode to "fixmbr" or "fixboot" it warns that I will overwrite the MBR and could lose the first drive. It may only be a simple thing as boot with SGD and "fixing grub". I am hesitant at this point to do that since the message also states that I could destroy that installation (something to that effect).

Any suggestions to avoid having to reinstall Ubuntu or go through explaining to MS why I am activating WINXP again, two days in a row?  I have a legit copy of WinXP

The sda1 is a 32 bit 9.04 install on 160GiB SATA1 drive, sdb is Windows XP on SATA2, sdc is 9,04 64 bit ext4 on IDE Master.

BIOS boot order is sdc, sda & sdb.

I do have another 160Gib drive that I could install and remove the IDE 250Gib drive completely. I would then move the Windows drive to the SATA1 position which I believe would solve the problem.

Any ideas/solutions besides what I mention here?

My "menu.lst" is:
```
title        Ubuntu 9.04 64bit Ext3, kernel 2.6.28-11-generic
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a6ad6af7-c6f3-40de-b7da-4de6e4a4f851 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot

title        Ubuntu 9.04 64bit Ext3, kernel 2.6.28-11-generic (recovery mode)
root        (hd2,0) 
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a6ad6af7-c6f3-40de-b7da-4de6e4a4f851 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot

title        Ubuntu 9.04, memtest86+ 
kernel        /boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Ubuntu 9.04 64bit ext4, kernel 2.6.28-11-generic
root        (hd0,0)
uuid        3cb9d90a-ebd9-4bb7-832d-550e9f870042
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3cb9d90a-ebd9-4bb7-832d-550e9f870042 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04 64bit ext4, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,0)
uuid        3cb9d90a-ebd9-4bb7-832d-550e9f870042
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3cb9d90a-ebd9-4bb7-832d-550e9f870042 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3cb9d90a-ebd9-4bb7-832d-550e9f870042
kernel        /boot/memtest86+.bin
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1

title        Microsoft Windows XP Home Edition
root        (hd1,0)
chainloader    +1
```

---

### Post by 73ckn797 on 2009-05-27
Bump

---

### Post by confused57 on 2009-05-27
One of these entries "should" work:
```
title              Windows XP
root               (hd1,0)
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

```
title              Windows XP
root               (hd2,0)
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader        +1
```

This is assuming XP is on the first partition of the drive.  If on the 2nd partition, then "root (hd1,1)" or
"root (hd2,1)", etc.

---

### Post by presence1960 on 2009-05-27
sometimes BIOS and GRUB see the order of drives differently. Go with GRUB's order. Windows is on sdb1 and Ubuntu is on sdc which is booting first. I would try this in menu.lst for windows

```
title        Microsoft Windows XP Home Edition
root        (hd1,0)
map         (hd2) (hd1)
map         (hd1) (hd2)
chainloader    +1
```

Good Luck, I know this can get aggravating.

---

### Post by 73ckn797 on 2009-05-28
> **presence1960 said:**
> sometimes BIOS and GRUB see the order of drives differently. Go with GRUB's order. Windows is on sdb1 and Ubuntu is on sdc which is booting first. I would try this in menu.lst for windows

```
title        Microsoft Windows XP Home Edition
root        (hd1,0)
map         (hd2) (hd1)
map         (hd1) (hd2)
chainloader    +1
```Good Luck, I know this can get aggravating.


Tried all of that. I discovered the brand new hard drive is failing.  The "bootmgr is missing" message led me the check the drive and it returned bad sectors. Have not had the drive installed 3 days. Back to Micro Center to exchange and try again.

Thanks.

---

### Post by presence1960 on 2009-05-28
> **73ckn797 said:**
> Tried all of that. I discovered the brand new hard drive is failing.  The "bootmgr is missing" message led me the check the drive and it returned bad sectors. Have not had the drive installed 3 days. Back to Micro Center to exchange and try again.

Thanks.

well that will explain it. At least you can exchange it and not shell out anymore money. Glad you found out what the problem is.

---

### Post by 73ckn797 on 2009-05-28
> **presence1960 said:**
> well that will explain it. At least you can exchange it and not shell out anymore money. Glad you found out what the problem is.

I actually am thinking that I will not reload Windows on the desktop since it gets used so little anymore. I still have it installed on my laptop dual booting with 9.04. The few time I have to have it I will fire up the laptop.

---

### Post by presence1960 on 2009-05-28
I hear you! I have a small Windows partition for 2 aggravating reasons. First is work, they made it clear no open office-something about formatting not 100% from Open Office to MS Office. The second is Verizon. When I needed a service call for my DSL they would not work on a Linux box. They require a Windows install. But I only boot into it like once per month. What a waste heh?

---

### Post by 73ckn797 on 2009-05-28
> **presence1960 said:**
> I hear you! I have a small Windows partition for 2 aggravating reasons. First is work, they made it clear no open office-something about formatting not 100% from Open Office to MS Office. The second is Verizon. When I needed a service call for my DSL they would not work on a Linux box. They require a Windows install. But I only boot into it like once per month. What a waste heh?

I know what you mean. I could keep using Windows for several reasons but the differences between Ubuntu and Windows is not of such a great necessity to want to do that. I do have one site for my work that will only allow me to upload photos using IE. I have installed "User Agent Switcher" in Firefox but have not tried it on that site yet. The next chance I get I will.

I would like to be able to download some podcasts but have not really looked much into how to accomplish that in Ubuntu. What little I have looked at suggests that Rhythmbox, if given an address, could allow me to do that. Any suggestions you may have will be appreciated.

NOTE to others: this is my thread and I will change the topic as I want (GRIN).

---

