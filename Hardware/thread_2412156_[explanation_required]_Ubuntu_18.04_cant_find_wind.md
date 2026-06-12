---
title: "[explanation required] Ubuntu 18.04 cant find windows 7 on a second drive"
date: 2019-02-08
forum: Hardware
---

### Post by teron281 on 2019-02-08
I kind of have the same Problem as described in this thread: [https://ubuntuforums.org/showthread.php?t=2197080](https://ubuntuforums.org/showthread.php?t=2197080).

Basically: I had windows 7 installed on two RAID 0 discs (via pci-e RAID Controller) and later installed Ubuntu as a second operating system onto a different SSD. After installing Ubuntu i was no longer able to boot into windows. After a quick google search i configured 
grub 2 (via the Ubuntu recovery mode) and it even found the windows 7 boot partition.

 I tried to boot it and ... it failed: Status: 0xc0000034, Info: "The Windows Boot Configuration Data file is missing the required information".
Next i tried using the Boot-Repair tool ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) but got an Error saying that i installed Ubuntu in Legacy mode and should reinstall in UEFI mode, which i did.

Now i have Windows in BIOS mode (according to the aforementioned thread), my Ubuntu is in UEFI mode but i should convert it back into legacy mode. I can see the windows "System-Reserved" partition in the file browser in Ubuntu. It even contains the "Boot" folder and the missing "BCD" file and some files called "BCD.LOG", which i cant open. Also the Boot-Repair tool did not help.

Output of "sudo update-grub":
```
 Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.18.0-15-generic
Found initrd image: /boot/initrd.img-4.18.0-15-generic
Found linux image: /boot/vmlinuz-4.18.0-10-generic
Found initrd image: /boot/initrd.img-4.18.0-10-generic
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
Adding boot menu entry for EFI firmware configuration
done

```


output of "sudo parted -l":
```
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name  Flags
 1      1049kB  150GB  150GB   ext4
 2      150GB   150GB  99,6MB  fat32              boot, esp


Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs


Model: ATA WDC WD30EZRZ-00G (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      17,4kB  1066kB  1049kB               LDM metadata partition
 2      1066kB  134MB   133MB                Microsoft reserved partition  msftres
 3      134MB   3001GB  3000GB               LDM data partition


Model: ATA MARVELL Raid VD (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32,3kB  1049kB  1016kB  primary
 2      1049kB  106MB   105MB   primary  ntfs         boot
 3      106MB   231GB   231GB   primary  ntfs
 4      231GB   500GB   269GB   primary  ntfs


```
(Windows Boot partion installed on "ATA MARVELL Raid VD (scsi)"  /  "/dev/sdd: 500GB")


One more thing: 
I tried booting directly into windows by selecting the RAID disc as a boot overwrite from my motherboard bios, but only got a blinking cursor.


My questions:

Why did installing Ubuntu in "legacy mode" the first time, on a completely different drive, affect my ability to boot in to windows 7 ?

When in Ubuntu UEFI mode, why does Grub 2 not detect the "boot" partition of windows even when it flagged as such by the "sudo parted -l" command ?

Why does it mater if i have windows installed in "BIOS mode" and Ubuntu installed in "UEFI mode" ?

and finally:

Is there a way to fix the issue from within Ubuntu because i no longer have the windows 7 install-CD(/stick)?

Any help is greatly appreciated and please excuse my post if it is to drawn out, i´m new here ^^.

---

### Post by dmnur on 2019-02-08
> Why did installing Ubuntu in "legacy mode" the first time, on a  completely different drive, affect my ability to boot in to windows 7 ?
It's probably about the boot priority. BIOS is probably now booting by default from the drive where Ubuntu is installed. To override this, check the info e.g. [here]("https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB").

> When in Ubuntu UEFI mode, why does Grub 2 not detect the "boot" partition of windows even when it flagged as such by the "sudo parted -l" command ?
Not really sure about this, could you please run these commands and show the output?
```

sudo grub-mkdevicemap
sudo grub-probe -v -d /dev/sdd2

```

> Why does it mater if i have windows installed in "BIOS mode" and Ubuntu installed in "UEFI mode" ?
Actually it's better if boot modes of both systems match. Windows is in BIOS mode (Windows 7 actually can't do *real* UEFI boot), so Ubuntu should be too.

> Is there a way to fix the issue from within Ubuntu because i no longer have the windows 7 install-CD(/stick)?
Yes, but for that we need to find out why exactly GRUB is failing to find Windows boot partitions.

---

### Post by teron281 on 2019-02-09
"sudo grub-probe -v -d /dev/sdd2" output:



```
grub-probe: info: adding `hd0' -> `/dev/sda' from device.map.
grub-probe: info: adding `hd1' -> `/dev/sdb' from device.map.
grub-probe: info: adding `hd2' -> `/dev/sdc' from device.map.
grub-probe: info: adding `hd3' -> `/dev/sdd' from device.map.
grub-probe: info: /dev/sdd2 is present.
grub-probe: info: Looking for /dev/sdd2.
grub-probe: info: /dev/sdd is a parent of /dev/sdd2.
grub-probe: info: /dev/sdd2 starts from 206848.
grub-probe: info: opening the device hd3.
grub-probe: info: drive = 3.
grub-probe: info: the size of hd3 is 976466432.
grub-probe: info: drive = 3.
grub-probe: info: the size of hd3 is 976466432.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: Found array LEO-PC-Dg0.
error: invalid volume.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Partition 0 starts from 63.
grub-probe: info: Partition 1 starts from 2048.
grub-probe: info: Partition 2 starts from 206848.
grub-probe: info: /dev/sdd2 is present.
grub-probe: info: Looking for /dev/sdd2.
grub-probe: info: /dev/sdd is a parent of /dev/sdd2.
grub-probe: info: /dev/sdd2 starts from 206848.
grub-probe: info: opening the device hd3.
grub-probe: info: drive = 3.
grub-probe: info: the size of hd3 is 976466432.
grub-probe: info: drive = 3.
grub-probe: info: the size of hd3 is 976466432.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: Found array LEO-PC-Dg0.
error: invalid volume.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Partition 0 starts from 63.
grub-probe: info: Partition 1 starts from 2048.
grub-probe: info: Partition 2 starts from 206848.
grub-probe: info: /dev/sdd2 is present.
grub-probe: info: Looking for /dev/sdd2.
grub-probe: info: /dev/sdd is a parent of /dev/sdd2.
grub-probe: info: /dev/sdd2 starts from 206848.
grub-probe: info: opening the device hd3.
grub-probe: info: drive = 3.
grub-probe: info: the size of hd3 is 976466432.
grub-probe: info: drive = 3.
grub-probe: info: the size of hd3 is 976466432.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: Found array LEO-PC-Dg0.
error: invalid volume.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd3.
grub-probe: info: Scanning for mdraid1x devices on disk hd3.
grub-probe: info: Scanning for mdraid09 devices on disk hd3.
grub-probe: info: Scanning for mdraid09_be devices on disk hd3.
grub-probe: info: Scanning for dmraid_nv devices on disk hd3.
grub-probe: info: Scanning for ldm devices on disk hd3.
grub-probe: info: scanning hd3 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd3.
grub-probe: info: no LVM signature found.
grub-probe: info: Partition 0 starts from 63.
grub-probe: info: Partition 1 starts from 2048.
grub-probe: info: Partition 2 starts from 206848.
grub-probe: info: opening hd3,msdos3.
grub-probe: info: drive = 3.
grub-probe: info: the size of hd3 is 976466432.
ntfs


```


"sudo grub-mkdevicemap" did not result in an output.


Thanks for the quick reply ^^

EDIT: The "error: Invalid Volume" line really appears multiple times in the output i did not copy it multiple times

---

### Post by dmnur on 2019-02-09
> **teron281 said:**
> ```

grub-probe: info: scanning hd3 for LDM.
grub-probe: info: Found array LEO-PC-Dg0.
error: invalid volume.

```

Strange. GRUB thinks that your **/dev/sdd** contains LDM (Logical Disk Manager), which is (roughly) Windows' *software* RAID, but you use *hardware* RAID for this disk.

What this command shows?
```
sudo fdisk -l /dev/sdd
```

---

### Post by teron281 on 2019-02-09
"sudo fdisk -l /dev/sdd" returns:

```
Disk /dev/sdd: 465,6 GiB, 499950813184 bytes, 976466432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x16d1e6b2

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdd1              63      2047      1985 992,5K 42 SFS
/dev/sdd2  *         2048    206847    204800   100M 42 SFS
/dev/sdd3          206848 450562047 450355200 214,8G 42 SFS
/dev/sdd4       450562048 976464383 525902336 250,8G 42 SFS


```

---

### Post by dmnur on 2019-02-09
ID 42 is the dynamic extended partition marker, used by LDM. And the partition table makes me think that yes, this is an LDM disk.
Well, bad news: GRUB does not really support LDM. But you could try to trick it by writing your custom configuration.

**IMPORTANT!** Chainloading won't work with GRUB running in UEFI mode, this technique requires BIOS. So you will probably need to reinstall Ubuntu in BIOS mode, I'm sorry.

Add this to the end of **/etc/grub.d/40_custom**:
```

menuentry "Windows" {
    insmod part_msdos
    insmod chain
    set root=(hd3,msdos2)
    drivemap -s (hd0) ${root}
    chainloader +1
}

```

Then run **sudo update-grub**, reboot and select **Windows** in the GRUB menu.

This is how Windows itself is booting, so should work.

---

### Post by oldfred on 2019-02-09
Generally even with Windows better not to use SFS/LDM/dynamic partitions. Some Windows tools do not work with dynamic partitioning.
It used to be that Linux drivers would not even see dynamic partitions. Now they seem them, but do not fully support them.

       [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
    
UEFI and BIOS/CSM/Legacy are not compatible. They write system info differently onto hard drive for the operating system to use.
You then can only dual boot from UEFI boot menu, not from grub.
Microsoft has required vendors to install Windows in UEFI boot mode since Windows 8 released in 2012. So all new hardware is UEFI. But many large corporations still used BIOS/Legacy boot and wanted backwards compatibility, so CSM is available. For an individual installing Windows how you choose to boot install media UEFI or BIOS is then how it installs, that is for both Windows & Ubuntu.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

And Windows 8 or 10 uses fast start up which sets the hibernation flag. Then the Linux NTFS driver will not see the NTFS partition and grub will not boot it. Fast start up must be off.

---

### Post by teron281 on 2019-02-13
I'm sorry i haven't posted anything i am in the middle of exam season :/.  I will update the thread as soon as i tried the solutions ^^.

---

### Post by yancek on 2019-02-13
> Chainloading won't work with GRUB running in UEFI mode

It does because Grub doesn't boot windows, it only points to the partition sector where the windows boot files should reside and 'chainloads'.  The old "chainloader +1" will not work as it needs to point to the correct file on the EFI partition.  Current chainload entry for EFI would be similar to below:

> chainloader /EFI/Microsoft/Boot/bootmgfw.efi

---

### Post by teron281 on 2019-02-20
@[**[COLOR=#000000]dmnur[/COLOR]**]("https://ubuntuforums.org/member.php?u=2117249") i reinstalled Ubuntu in legacy mode and added the code to the "40_custom" file, but when i select the "Windows"option in the grub menu i get an error: "no such partition". 
Also i noticed Grub thinks the boot partition of window is on the "/dev/sdd1" partition and not on ".../sdd2"

Edit: So i checked out the "grub.cfg" file and it had a win7 entry: ```
menuentry 'Windows 7 (on /dev/sdd1)' --class windows --class os $menuentry_id_option 'osprober-chain-6E1AE7F51AE7B7EB' {
    insmod part_msdos
    insmod ntfs
    set root='hd3,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos2 --hint-efi=hd3,msdos2 --hint-baremetal=ahci3,msdos2  6E1AE7F51AE7B7EB
    else
      search --no-floppy --fs-uuid --set=root 6E1AE7F51AE7B7EB
    fi
    parttool ${root} hidden-
    chainloader +1
}
```

---

### Post by dmnur on 2019-02-20
> **teron281 said:**
> Windows 7 (on /dev/sdd1)

This was added automatically by **update-grub** using **os-prober**. No idea why it's **/dev/sdd1** (4th drive, 1st partition) in the menu entry name, but **hd3,msdos2** within the entry (GRUB counts drives from 0 and partitions from 1, so it's 4th drive, 2nd partition).
Did you select this entry or the one named just **Windows**? Try both.

Also would be nice to see the output of this command:
```
sudo blkid
```

You can also try changing the entry I've provided earlier like this:
```

menuentry "Windows" {
    insmod part_msdos
    insmod chain
    drivemap -s (hd0) (hd3)
    chainloader (hd0,msdos2)+1
}

```

**drivemap** is not well documented, so I might have got it wrong that time.

---

