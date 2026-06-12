---
title: "Vista Ubuntu LOADED, XP fail"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by Jeahavee on 2009-07-01
:rolleyes: I know I know Install xp first then Vista ten Linux BUT that's not how computers (laptops) come sometimes. I have a HP Pavilion Dv6 1030us I got Vista 64bit home pre on it. I partitioned 3 spaces I managed to install ubuntu no problems at all. BUT XP 64bit was fail. I got a blue screen that said unable to boot. :lolflag: I don't remember what it said I just turned away. Now I need xp because my old computer hdd has important information on it and I need to read'em. Vista can't read it. I haven't figured out how to do it on ubuntu. So any of the solution to my multi problems would be nice. NOTE the most important thing is to find a way for me to read my hdd. I have a usb to ide/sata adapter. ](*,)HELP and [-o< thank you in advance.

---

### Post by LepeKaname on 2009-07-01
You should be able to access you HDD from Ubuntu using ntfs-3g:

Edit your /etc/fstab:

> /dev/sda  /media/disk  ntfs-3g defaults,locale=en_US.UTF-8 0   0

Adjust accordingly.

---

### Post by Jeahavee on 2009-07-02
Typed that but it said "bash: /dev/sda/media/disk: Not a directory" and "bash: /dev/sda/media/disk: No such file or directory" when I changed the letters ntfs to usb. . I guess I need to know where this USB drive would be. I only have 4 usb ports. Not sure what other information you would need from me.

---

### Post by LepeKaname on 2009-07-02
Be aware that there is a space between:

"/dev/sda"  and "/media/disk"

```
/dev/sda /media/disk
        ^
       here
```

> when I changed the letters ntfs to usb

You should not change ntfs for usb in "ntfs-3g" because it is the driver's name to access disks formatted with NTFS. 

So the drive you are trying to read is USB? in that case, you don't need to edit your /etc/fstab. Ubuntu does it automatically... Try to connect it first go to the Menu: Places -> Computer. It should be there. If it is not, post here the output of the command: 

```
dmesg | tail -n 50
```

Just about 1 min. after connecting your device.

---

### Post by Jeahavee on 2009-07-02
Cool okay found it. NOW I can't read it.

Name: USB Drive (I can't rename it)
Type: unknown
Location: computer:///
Volume: unknown
Accessed: unknown
Modified: unknown

Try to open and try to open with file reader.

---

### Post by Jeahavee on 2009-07-04
Well found this nice code and this should be helpful to me and others helping me. Still unable to look up my 320 or 80gb hdd via USB.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf9bc167

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25597   205605880    7  HPFS/NTFS
/dev/sda2           25597       31441    46941184    7  HPFS/NTFS
/dev/sda3           31442       37285    46941930    5  Extended
/dev/sda4           37286       38913    13075456    7  HPFS/NTFS
/dev/sda5           31442       37040    44973936   83  Linux
/dev/sda6           37041       37285     1967931   82  Linux swap / Solaris

ALSO I can't seem to look up my "Documents and Settings" in my windows portition. I know how to get there but can't open it.

---

