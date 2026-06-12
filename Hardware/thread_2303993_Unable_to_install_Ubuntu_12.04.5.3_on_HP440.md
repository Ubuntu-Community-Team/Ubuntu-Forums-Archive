---
title: "Unable to install Ubuntu 12.04.5.3 on HP440"
date: 2015-11-23
forum: Hardware
---

### Post by Tajammul_Rafique on 2015-11-23
I am trying to install Ubuntu 12.04.5.3 (Security Onion) on HP 440 Desktop, which is listed as an approved hardware for Ubuntu v 12.04.5. But I having a hard time installing it. I get to install the OS but on reboot I get an error "Boot Device Not found" "Hard Disk - (3F0).

I have four, 4 terabyte hard drivers in it and I built a raid 5 with mdadm, I also tried as single drive without raid but had no luck.

Can someone please help? Thanks

---

### Post by yancek on 2015-11-23
If you just let the installer use the defaults on a system such as yours with no current operating system on it, then the installer should work and put the bootloader where it belongs.  Are you using UEFI or MBR to boot?  I don't use RAID so I'm not sure how that would affect anything.  As a starting point, boot the Ubuntu installer and from a terminal run this command and post the output here:  sudo parted -l(Lower Case Letter L in the command)  That should at least give basic drive/partition information.

---

### Post by Tajammul_Rafique on 2015-11-23
I read lot of on this topic, but don't know how to switch between to two[COLOR=#000000]

"Are you using UEFI or MBR to boot"

Here is the result Parted.

[/COLOR][COLOR=#000000][FONT=garamond]securityonion@securityonion:~$ sudo parted -l[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Model: ATA ST4000NM0033-9ZM (scsi)[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Disk /dev/sda: 4001GB[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Sector size (logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Partition Table: gpt[/FONT][/COLOR]

[COLOR=#000000][FONT=garamond]Number  Start   End     Size    File system     Name  Flags[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond] 1      1049kB  2097kB  1049kB                        bios_grub[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond] 2      2097kB  3967GB  3967GB  ext4[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond] 3      3967GB  4001GB  34.3GB  linux-swap(v1)[/FONT][/COLOR]


[COLOR=#000000][FONT=garamond]Model: ATA ST4000NM0033-9ZM (scsi)[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Disk /dev/sdb: 4001GB[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Sector size (logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Partition Table: gpt[/FONT][/COLOR]

[COLOR=#000000][FONT=garamond]Number  Start   End     Size    File system  Name  Flags[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond] 1      1049kB  4001GB  4001GB  ext2[/FONT][/COLOR]


[COLOR=#000000][FONT=garamond]Model: ATA ST4000NM0033-9ZM (scsi)[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Disk /dev/sdc: 4001GB[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Sector size (logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Partition Table: gpt[/FONT][/COLOR]

[COLOR=#000000][FONT=garamond]Number  Start   End     Size    File system  Name  Flags[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond] 1      1049kB  4001GB  4001GB  ext2[/FONT][/COLOR]


[COLOR=#000000][FONT=garamond]Model: ATA ST4000NM0033-9ZM (scsi)[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Disk /dev/sdd: 4001GB[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Sector size (logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Partition Table: gpt[/FONT][/COLOR]

[COLOR=#000000][FONT=garamond]Number  Start   End     Size    File system  Name  Flags[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond] 1      1049kB  4001GB  4001GB  ext2[/FONT][/COLOR]


[COLOR=#000000][FONT=garamond]Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]has been opened read-only.[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Error: /dev/sr0: unrecognised disk label                                  [/FONT][/COLOR]

[COLOR=#000000][FONT=garamond]securityonion@securityonion:~$ [/FONT][/COLOR]

---

### Post by yancek on 2015-11-23
Your output from parted shows you are using GPT partitioning so you should have installed the Grub bootloader to the MBR, this would be /dev/sda under the 'Device for bootloader installation' and is the default.  You need to have it set in your BIOS, enter setup immediately on boot and look for something like Legacy boot or CSM.  Making this change varies with manufacturer and you should be able to get some info if you got some type of documentation or manual with the computer or by going to the HP site below to search for the manual for your particular system.  If that doesn't help, go to the second link below and use the Ubuntu installation medium to download and run the boot repair script.  Select the option to Create Bootinfo Summary and post the output here.

[http://h20566.www2.hp.com/portal/site/hpsc/public/psi/manualsResults?sp4ts.oid=5359410&ac.admitted=1448303149301.1123376534.199480143](http://h20566.www2.hp.com/portal/site/hpsc/public/psi/manualsResults?sp4ts.oid=5359410&ac.admitted=1448303149301.1123376534.199480143)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Tajammul_Rafique on 2015-11-23
In BIOS I moved the HardDisk on the top for Legacy Boot.

Here is the result from Boot Repair

[COLOR=#000000][FONT=garamond]Boot successfully repaired.[/FONT][/COLOR]

[COLOR=#000000][FONT=garamond]Please write on a paper the following URL:[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]http://paste.ubuntu.com/13479706/[/FONT][/COLOR]


[COLOR=#000000][FONT=garamond]In case you still experience boot problem, indicate this URL to:[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]boot.repair@gmail.com or to your favorite support forum.[/FONT][/COLOR]

[COLOR=#000000][FONT=garamond]You can now reboot your computer.[/FONT][/COLOR]
[COLOR=#000000][FONT=garamond]Please do not forget to make your BIOS boot on sda (4001GB) disk![/FONT][/COLOR]
[COLOR=#000000][FONT=garamond][/FONT][/COLOR]
[COLOR=#000000][FONT=garamond] [/FONT][/COLOR]

---

