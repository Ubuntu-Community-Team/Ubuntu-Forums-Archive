---
title: "Unable to start WInXP after installing Ubuntu 9.04"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by Barry79 on 2009-05-10
Hi there,

I have installed Ubuntu 9.04 on my iMac which also has Mac Os X and win XP installed.

My problem is that I cannot start Windows, getting the message -

"Windows cannot start ... missing file <Windows Root>/system32/hal.dll

instead.

When I run fdisk -lu I get the following -

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca0dca0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2   *      409640   755190127   377390244   af  Unknown
/dev/sda3       755190128   910834659    77822266   83  Linux


```However, I believe WinXP is installed in the /dev/sda5 partition.

ls -al sda* within /dev gives me -

```

brw-rw---- 1 root disk 8, 0 2009-05-10 11:45 sda
brw-rw---- 1 root disk 8, 1 2009-05-10 11:45 sda1
brw-rw---- 1 root disk 8, 2 2009-05-10 11:45 sda2
brw-rw---- 1 root disk 8, 3 2009-05-10 09:45 sda3
brw-rw---- 1 root disk 8, 5 2009-05-10 11:45 sda5

```My Windows and Mac Os X partitions appear as mounted disk drives within Ubuntu's "Places" folder.

The boot.ini file there appears as -

```

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn

```and the windows section of my /boot/grub/menu.lst is as follows,

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title           Microsoft Windows XP Professional
rootnoverify    (hd0,4)
chainloader     +1

```Why does sda5 not appear under fdisk?

How might I fix this problem?

Thanks,

Barry

---

### Post by Barry79 on 2009-05-10
Hi again,

I forgot to mention that I also have refit installed. If I click on the windows or ubuntu sybol on startup, it brings me to stage 2 grub prompt where I can chose Ubuntu or XP. 

I have now changed to -

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn

to

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn

which began starting up windows before I got the famous blue screen of death. Which immediately restarted the computer. Now rEDIt is gone...

Any ideas?

Thanks,

Barry.

---

