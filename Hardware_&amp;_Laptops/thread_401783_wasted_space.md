---
title: "wasted space?"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by acfreema on 2007-04-05
i'm confused with my partition sizes (all problems stem from ext3) and the amount that i am permitted to use.
my boot partition is 10.1gb with 2.8gb free and only 2.3 of that is available - 7.3 used?
/files partition is 25.7gb with 4gb free and only 2.7 is available - 21.7 used... what?
can someone explain this to me?  is there a way to get back that space?  i'm kind of hurting for space on my laptop periodically; i feel like i fill up the drive way too fast (now i know why!?)

---

### Post by mssever on 2007-04-05
> **acfreema said:**
> i'm confused with my partition sizes (all problems stem from ext3) and the amount that i am permitted to use.
my boot partition is 10.1gb with 2.8gb free and only 2.3 of that is available - 7.3 used?
/files partition is 25.7gb with 4gb free and only 2.7 is available - 21.7 used... what?
can someone explain this to me?  is there a way to get back that space?  i'm kind of hurting for space on my laptop periodically; i feel like i fill up the drive way too fast (now i know why!?)
Your /boot partition is huge. My /boot is only 41 MB, only 22MB of which is in use. Look in /boot to see if there's anything not related to the kernel and grub. For reference, here's what's in my /boot: ```
~:$ ls /boot
abi-2.6.17-11-386     grub/                     lost+found/               System.map-2.6.20.4
config-2.6.17-11-386  initrd.img-2.6.17-11-386  memtest86+.bin            vmlinuz-2.6.17-11-386
config-2.6.20.4       initrd.img-2.6.20.4       System.map-2.6.17-11-386  vmlinuz-2.6.20.4
``` If you've got other junk there, it shouldn't be there.

For your /files partition, that's a non-standard directory, so everything in there is stuff that you put there. Ubuntu won't automatically put anything in /files. (Of course, you could have stuff symlinked to /files, which could be a mess to sort out. But, those symlinks only exist if you created them yourself.)

---

### Post by jjordan on 2007-04-05
Have you tried emptying the trash?

-j

---

### Post by ben.s on 2007-04-05
Post the results of 'df -h'.

---

### Post by acfreema on 2007-04-23
i'm sorry it took me so long ot respond, i must not have my preferences set to inform me of new posts...
anyway, the partition that contains my actual install of ubuntu (/dev/hda1) is 10gb, my swap (/dev/hda2) is 512mb and my misc (/dev/hda3) is where i keep things that i may want around for more than one reinstall ;)
i spoke with one of my friends who has been using linux for... 12 years (?), and he mentioned that to the best of his understanding, the ext2/3 formatting would automatically reserve a percentage of the partition for os use, just in case you stopped paying attention to how much crud you accumulated and then the os would lack the space to fulfill its tasks.  enter the sad face of defeat... :-(
anyway, i read someplace that the reiserfs seemed marginally faster than ext3, and being a laptop, i need as much hd speed as i can get.  i decided to try formatting my /dev/hda1 to reiserfs and then reinstalled.  lo and behold.... a full 10.1gb between the used and available space!  sweet!  reiserfs ftw!
maybe the /files partition was reduced because i hadn't emtied that trash (which i just discovered yesterday, i never thought to look in the "file" menu), but i find that irrelevant; because my / partition's trash was emptied every time i deleted stuff totaling more than 100mb

because you asked...
```
 ls /boot
abi-2.6.17-10-generic         initrd.img-2.6.17-11-generic
abi-2.6.17-11-generic         memtest86+.bin
config-2.6.17-10-generic      System.map-2.6.17-10-generic
config-2.6.17-11-generic      System.map-2.6.17-11-generic
grub                          vmlinuz-2.6.17-10-generic
initrd.img-2.6.17-10-generic  vmlinuz-2.6.17-11-generic
```

```
df -h /boot
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              11G  9.9G  399M  97% /
```

```
df -h /files
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              27G   18G  9.1G  67% /files
```

---

