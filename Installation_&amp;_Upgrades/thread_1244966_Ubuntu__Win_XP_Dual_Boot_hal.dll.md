---
title: "Ubuntu / Win XP Dual Boot: hal.dll"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by pnotequalsnp on 2009-08-20
I am having problems getting my computer to dual boot Ubuntu and Windows XP (missing hall.dll).
I installed Windows XP, then Ubuntu 9.04.

Here's my "boot.ini file.  
```
[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional 1"

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional 2" 

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional 3" 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional 4"
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional 5" 
multi(0)disk(0)rdisk(0)partition(6)\WINDOWS="Microsoft Windows XP Professional 6" 

```

As you can see, I have tried various configurations to say the least. 
I have also tried:
```
[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional"


```

Now in parted I see:
```
(parted) print                                                            
Model: ATA WDC WD1500AHFD-0 (scsi)
Disk /dev/sda: 150GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  77.0GB  77.0GB  extended                    
 5      64.5kB  73.8GB  73.8GB  logical   ext3              
 6      73.8GB  77.0GB  3183MB  logical   linux-swap        
 3      77.0GB  150GB   73.0GB  primary   ntfs         boot

```
So I assume that my Windows XP install is on Number 3.
Since Linux is 0-based and Windows is 1-based, I assume that it should be 4 in the boot.ini file.

None of this has  worked.  I have also tried replacing the hal.dll file from my Windows XP isntall disk.

Thanks for your help in advance.

---

### Post by rcayea on 2009-08-20
Try this link. 

[http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)

 or 

[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)


Let me know if neither help. 

Good luck,
Randy

---

### Post by pnotequalsnp on 2009-08-20
> **rcayea said:**
> Try this link. 

[http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)

 or 

[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)


Let me know if neither help. 

Good luck,
Randy

Thanks, I tried those links, including system recovery, and replacing the files.  Could someone look at my partition set-up and tell me if my boot.ini is correct?

---

