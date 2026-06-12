---
title: "sd card not recognized on eeepc 701sd"
date: 2008-12-30
forum: Hardware
---

### Post by handydan918 on 2008-12-30
Just got a eeepc for xmas, and of course felt the urge to purge Xandros...Yuck.

Insstalled eeebuntu and everything just works. Except for the sd card.
I can't find any reference to it anywhere. 

fstab looks like this:
```
daniel@eeepc:/dev/disk$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=6a219c5c-c6c4-49e1-9337-ae1e2587c8d3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=8a460949-22f6-441d-9394-5a67a3341ba0 /home           ext3    relatime        0       2
```

here's fdisk -l:

```
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01f501f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         492     3951958+  83  Linux
/dev/sda2             493         981     3927892+   5  Extended
/dev/sda5             493         981     3927861   83  Linux
```

Last but not least, a titillating tidbit from dmesg:

```
daniel@eeepc:/dev/disk$ dmesg | grep sd
[   11.618575] Driver 'sd' needs updating - please use bus_type 
```

Honest, guys, I've done my due diligence on this one. I've googled half my **** off, posted to the eeebuntu forums, and zip.
Any clues would be appreciated.

---

### Post by Daveth on 2008-12-31
um, odd, as my 701 Hardy under Remix works fine. This post has some pointers, and may help a bit

[http://www.linuxforums.org/forum/linux-laptops/120303-eeepc-sd-card-mounted-home.html](http://www.linuxforums.org/forum/linux-laptops/120303-eeepc-sd-card-mounted-home.html)

Happy New year.

---

### Post by cmay on 2008-12-31
thanks for bringing this up. i have the exact same model and installed crunch bang linux in it. everything works out of the box other than the sd card on mine. (even that no one seems to believe me but it just does not :( )

---

### Post by handydan918 on 2008-12-31
> **Daveth said:**
> um, odd, as my 701 Hardy under Remix works fine. This post has some pointers, and may help a bit

[http://www.linuxforums.org/forum/linux-laptops/120303-eeepc-sd-card-mounted-home.html](http://www.linuxforums.org/forum/linux-laptops/120303-eeepc-sd-card-mounted-home.html)

Happy New year.

Thanks for the reply. It seems that the issue in the link you provided was about mounting a filesystem on an sd card at /home. my issue is that, as far as I can tell, the hardware simply does not see it at all. You can't mount what doesn't exist...
Any of you kernel gurus got a clue?

---

### Post by handydan918 on 2008-12-31
> **cmay said:**
> thanks for bringing this up. i have the exact same model and installed crunch bang linux in it. everything works out of the box other than the sd card on mine. (even that no one seems to believe me but it just does not :( )

How about comparing your fstab to mine, and grep your dmesg for a  similar error? Sure would be nice to have more than one person singing this song...

---

### Post by cmay on 2008-12-31
yes good idea, i just need around 30 minuttes. :)

---

### Post by cmay on 2008-12-31
here is my fstab from my asus EeePC 701sd ,  all new i got 14 days ago and installed crunch bang linux in it the exact same day i got it.
[php]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=69034d92-3e9f-4c61-800b-c0d110e9da58 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=443f5e84-af43-45d4-a537-2d3d4dfa75b9 none            swap    sw              0       0
[/php]

---

### Post by handydan918 on 2008-12-31
@ cmay:
Looks different than mine, but not in any way that might be related to sdb1...
Surprised to see you using a swap partition. 

How about grepping your dmesg for that sd related error?

Sorta like ```
dmesg | grep -i sd
```

---

### Post by cmay on 2009-01-01
here it is. (exactly dmesg | grep -i sd > error.txt) i had a little trouble finding the '>' on the keyboard.  the reason i use swap is because the installer failed everytime i tried not to use swap. even i would liked to have avoided it. but it runs great as it is ohter than the sd card. 
[PHP][    0.000000] ACPI: RSDP 000FBE60, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1F780000, 0034 (r1 A M I  OEMRSDT   8000830 MSFT       97)
[    0.000000] ACPI: DSDT 1F780400, 5E11 (r1  A1027 A1027042       42 INTL 20051117)
[    0.035009] ACPI: Checking initramfs for custom DSDT
[    0.806096] ACPI: EC: Look up EC in DSDT
[    5.492411] ata2.00: ATA-5: ASUS-PHISON SSD, TST2.04P, max UDMA/66
[    5.500578] scsi 1:0:0:0: Direct-Access     ATA      ASUS-PHISON SSD  TST2 PQ: 0 ANSI: 5
[    6.030421] Driver 'sd' needs updating - please use bus_type methods
[    6.030610] sd 1:0:0:0: [sda] 15761088 512-byte hardware sectors (8070 MB)
[    6.030646] sd 1:0:0:0: [sda] Write Protect is off
[    6.030652] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.030706] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    6.030863] sd 1:0:0:0: [sda] 15761088 512-byte hardware sectors (8070 MB)
[    6.030895] sd 1:0:0:0: [sda] Write Protect is off
[    6.030900] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.030954] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    6.030963]  sda: sda1 sda2 < sda5 >
[    6.034795] sd 1:0:0:0: [sda] Attached SCSI disk
[   20.246387] Adding 385520k swap on /dev/sda5.  Priority:-1 extents:1 across:385520k
[   20.290013] EXT3 FS on sda1, internal journal
[   21.087945] type=1505 audit(1230826119.492:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3851[/PHP]

---

### Post by Old_Grey_Wolf on 2009-01-01
Is this your problem? [http://forum.eeebuntu.org/viewtopic.php?f=3&t=539&p=2987&reeedirected=yes](http://forum.eeebuntu.org/viewtopic.php?f=3&t=539&p=2987&reeedirected=yes)

Looking at what was posted above, it doesn't look like it will help.

Edit: I googled on "Driver 'sd' needs updating - please use bus_type methods" with quotes. It appears to be a Kernel bug that doesn't affect anything.

---

### Post by handydan918 on 2009-01-01
> **Old_Gray_Wolf said:**
> Is this your problem? [http://forum.eeebuntu.org/viewtopic.php?f=3&t=539&p=2987&reeedirected=yes](http://forum.eeebuntu.org/viewtopic.php?f=3&t=539&p=2987&reeedirected=yes)

Looking at what was posted above, it doesn't look like it will help.

Edit: I googled on "Driver 'sd' needs updating - please use bus_type methods" with quotes. It appears to be a Kernel bug that doesn't affect anything.

Yeah, I googled that, too, with similar results. I just can't believe that with all these eeepcs out there floating around this has never become an issue before!  

I only have 8G of space on this little thing, so I'd really like to have hte sd card available, too. 

Anyone?

@ cmay. 
Your dmesg error 
```
6.030421] Driver 'sd' needs updating - please use bus_type methods

``` Is just what I got. Seems like the only info out there is, as greywolf said, tending toward the conclusion that this is inconsequential. I just don't know if I believe in coincidences like that or not.

---

### Post by handydan918 on 2009-01-01
> **Old_Gray_Wolf said:**
> Is this your problem? [http://forum.eeebuntu.org/viewtopic.php?f=3&t=539&p=2987&reeedirected=yes](http://forum.eeebuntu.org/viewtopic.php?f=3&t=539&p=2987&reeedirected=yes)

Looking at what was posted above, it doesn't look like it will help.

Edit: I googled on "Driver 'sd' needs updating - please use bus_type methods" with quotes. It appears to be a Kernel bug that doesn't affect anything.

I have actually posted on the eeebuntu forums, and I ahd already found that post you linked to. I inspected my fstab, and even though it didn't appear to have any references to cdrom in it, I went ahead and rant the eeebuntu fixit script, just in case there was an undocumented effect that might help. 
No dice.

Thanks for looking, though.

---

### Post by Old_Grey_Wolf on 2009-01-01
I looked for any help I could find. 

I don't know what to say. My wife's EeePC is working just fine. 

I hope you are able to solve your problem.

---

### Post by Ripose on 2009-01-02
From what I've found you should check your linux distro release date since there may be issues with ASUS that did not make it into the linux kernel.

Wikipedia  ASUS 701SD ( a little info there).

Did you upgrade your BIOS before removing XANDROS?

Did you search the ASUS eeepc forum?

What color is your 701? Are you holding your tongue the right way? LOL

Have a great New Year people! :D

---

### Post by handydan918 on 2009-01-02
> **Ripose said:**
> From what I've found you should check your linux distro release date since there may be issues with ASUS that did not make it into the linux kernel.

It's eeebuntu 8.10, so it's unlikely to be out of date yet. It's also running the array.org kernel, and it works great other thhan this..> 

Wikipedia  ASUS 701SD ( a little info there).

Aye, VERY little.> 

Did you upgrade your BIOS before removing XANDROS? no. I wasn't looking for trouble. Xandros was recognizing it OK...so I wouldn't have made the leap to "Ah-ha! I need to update my bios, since everything seems to be working!"

;-)
>  

Did you search the ASUS eeepc forum?

Yeah, and  even found a few similar posts, none of which were answered, or which I had already tried. I posted there, too. No ack.> 

What color is your 701? Black, but my 501s are blue.... > Are you holding your tongue the right way? LOLDoh! That was it! moved my tongue to the other side and the sd card just showed up! Now if a mod can mark this thread as "Stupid"....LOL indeed!

---

### Post by Old_Grey_Wolf on 2009-01-02
Can the Partition Editor see the SD card?

---

### Post by handydan918 on 2009-01-02
> **Old_Gray_Wolf said:**
> Can the Partition Editor see the SD card?

No. Neither does fdisk -l.
I was hoping some kernel genius would have an idea for some obscure command line trick or module to load or...

I can't find any trace of the sd card in any of the usual places.

---

### Post by handydan918 on 2009-01-04
This is not a bump.












:P

---

### Post by handydan918 on 2009-01-07
Now THIS is a bump.

---

