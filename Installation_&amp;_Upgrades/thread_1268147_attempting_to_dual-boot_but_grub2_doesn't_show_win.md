---
title: "attempting to dual-boot but grub2 doesn't show windows"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by Geoffzx6r on 2009-09-16
I just installed the alpha 5 of ubuntu 9.10. So far I'm loving it. I'm impressed. It's the first version to install and run great straight out of the box on my notebook.

One problem though. I resized my windows partition to dual-boot and installed 9.10 using the default ext4. Grub doesn't show my windows partition. It's there though and I can mount it in ubuntu just fine. How do I setup grub to boot windows? I would definitely appreciate some help even towards the direction of a howto. 

Here's my fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x408bf227

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       13524   107091822+   7  HPFS/NTFS
/dev/sda3           13525       19457    47656822+   5  Extended
/dev/sda5           13525       19208    45656698+  83  Linux
/dev/sda6           19209       19457     2000061   82  Linux swap / Solaris

```

Also I heard alpha 5 is using grub2 and the config file is grub.cfg. I looked at it and it says not to edit:confused:

---

### Post by Geoffzx6r on 2009-09-16
Well I figured it out guys.

I edited the /boot/grub/grub.cfg file. I added this entry:

```

menuentry "Windows Vista" {
set root=(hd0,2)
chainloader +1
}

```

for anyone searching this as a solution to their problem in the future. Where I typed "windows Vista" title it as the version you're using and under set root=(hd0,2) type in the partition windows is installed. For most people it's going to be: (hd0,1)

:D

---

