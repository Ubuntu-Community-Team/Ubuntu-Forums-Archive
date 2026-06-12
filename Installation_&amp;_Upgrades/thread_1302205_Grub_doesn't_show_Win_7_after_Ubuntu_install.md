---
title: "Grub doesn't show Win 7 after Ubuntu install"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by slugicide on 2009-10-26
Thanks in advance.
I upgraded my Vista partition to Win 7. I knew that would wipe out the grub-thing and so had instructions written down on how to repair it. The Hardy disc I had around, when used, would hang forever at the "find /boot/grub/stage1" part of the solution. So, I tried the Karmic disc. That said grub didn't exist. Sooo, I noticed that I had a copy of supergrub. I followed all of its instructions in verbose mode, only to end up with a completely unusable laptop. Like, I got a "no operating system" error. So, I reinstalled Karmic over the old ext4 partition and can log into this fresh install, but I can't figure out how to tell grub where Win 7 is and to let me choose which to boot into. 

I would greatly appreciate any help.

---

### Post by slugicide on 2009-10-27
Bumpity bump.  Any help?

---

### Post by Mark Phelps on 2009-10-27
Karmic and Hardy versions use completely different GRUBs -- so it's not surprising that the Karmic disk wouldn't work.

What version is the Ubuntu that is installed, 8.04?

Boot from a liveCD and run "sudo fdisk -lu" (that's a lowercase L) in a terminal and post the results back here.

---

### Post by slugicide on 2009-10-27
Thanks. The Ubuntu vesion I'm working with is Karmic Koala.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00059366

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    81915434    40956693+   6  FAT16
/dev/sda2        81915435   696321359   307202962+   b  W95 FAT32
/dev/sda3   *   696321360   941617844   122648242+  83  Linux
/dev/sda4       941617845   976768064    17575110   82  Linux swap / Solaris

---

### Post by oldfred on 2009-10-27
When I installed alpha it did not have the os-prober. I should be there now.

Even still, the latest Karmic Alpha needs some help to find other os.
sudo apt-get install os-prober
sudo os-prober
sudo update-grub2

That should find windows if it works. Why is your Win 7 showing FAT32?

---

### Post by slugicide on 2009-10-27
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

The FAT 32 is just a media partition. sda1 is Win7.

---

### Post by oldfred on 2009-10-27
You can add a file 30_os-prober in /etc/grub.d, make it executable, and run update-grub2

Windows 7 entry 

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set [COLOR=DarkRed]yourUUID[/COLOR]
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

```

---

### Post by slugicide on 2009-10-27
I'm confused by the "yourUUID" part of that. Is that part of the file, or am I supposed to add the UUID of the partition? Because I can't find a UUID for that partition. The linux partition and the media partition, yes, but that first partition, the Windows one, no.

---

### Post by oldfred on 2009-10-27
blkid does should show a uuid.  I am also wondering why fdisk is saying the partition is fat16 for an old Vista and now Win7 partition. It should be NTFS. This maybe a partition problem. Did windows boot after you installed it?

I also saw a  chainboot entry for XP that left the entire search line with the UUID out. You could try that. Just set root and the chainboot lines. And if it is not a NTFS partition the ismod NTFS will not work.

Looks like lots of issues, and I do not know why.

---

### Post by slugicide on 2009-10-27
I used Disk Utility to change the partition from FAT16 to NTFS. Now I get

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00059366

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    81915434    40956693+   7  HPFS/NTFS
/dev/sda2        81915435   696321359   307202962+   b  W95 FAT32
/dev/sda3   *   696321360   941617844   122648242+  83  Linux
/dev/sda4       941617845   976768064    17575110   82  Linux swap / Solaris
```I'm a bit confused about making a 30_os-prober file in /etc/grub.d because there is already a file with that name there.

---

### Post by oldfred on 2009-10-27
I do not know if changing the partition type has made any difference to windows or not i.e. will it still boot? How did it get to be FAT16 that goes back to dos days? You may still have to repair the windows with repair console.

I do not have my grub2 partition mounted to see the files, but you need to add the entry to one of the grub entries. see below:

see # 6 for examples of adding entries to be incorporated into grub.cfg:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

looks like [COLOR=DarkRed]40_custom or any variety of names to add entries in order.
[/COLOR]

---

### Post by cwsnyder on 2009-10-28
Your Vista and Win7 should have shown up as **2**, yes 2, different partitions.  A Vista Loader partition (usually marked as NTLDR) to boot from which would be FAT16 or FAT32 and a program/data partition which should be NTFS.  I think you changed the wrong partition.

You will have to get GRUB to point to the NTLDR partition to boot.

---

### Post by oldfred on 2009-10-28
You now have two boot partitions flagged, which will not work. Remove the boot flag from the linux partition, it is not required. Only windows requires the boot flag but it must be on the partition you have your bootable windows. If you have both Vista and Win7 the boot has been combined into one partition.

I am now lost on your system configuration. Please run this script that will document how your system boots and what boot files are where:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by slugicide on 2009-10-28
I reinstalled last night (since it was a fresh install I was trying to fix), so I'm going to mark this thread solved. Thanks for all your help!!

---

