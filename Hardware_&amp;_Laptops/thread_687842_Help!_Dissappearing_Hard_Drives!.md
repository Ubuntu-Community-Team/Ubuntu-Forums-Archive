---
title: "Help! Dissappearing Hard Drives!"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by kira. on 2008-02-04
For some reason, I rebooted to Ubuntu from Windows XP, and my Windows hard drives were no longer there. Any ideas?

-unhappy Ubuntu user:(

---

### Post by taurus on 2008-02-04
What do you mean your window partition is no longer there?  Maybe you need to mount it before you can access it.  Open a terminal and post the outputs of these commands here.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by kira. on 2008-02-04
the thing is, it was mounted before, but now it isn't anymore, anyways, i'll try that code..
by the way, what does it do? @_@

thx

---

### Post by kira. on 2008-02-04
Oh, and how do you open a terminal? >_<
ima noob... >_<

thx

---

### Post by jken146 on 2008-02-04
Applications  ->  Accessories  ->  Terminal

---

### Post by taurus on 2008-02-04
Applications -> Accessories -> Terminal

Sounds to me like you didn't shutdown windows cleanly so it won't mount without the force option.  So, boot back into windows again and this time, shut it down instead of using the hibernation or sleep mode.

---

### Post by kira. on 2008-02-04
BAM! I just did those code things, and my drives still haven't done anything, what now?

---

### Post by kira. on 2008-02-04
OOOh, kk, thanks, but does this mean i shouldn't have written those codes O_O????

---

### Post by kira. on 2008-02-04
what do they do, anyhow?

---

### Post by taurus on 2008-02-04
Can you at least, BAM, post the outputs of those commands?

---

### Post by taurus on 2008-02-04
> **kira. said:**
> OOOh, kk, thanks, but does this mean i shouldn't have written those codes O_O????

There are nothing wrong with those codes.  They won't mess up your system or anything like that.  And if you think I provide you with some bogus codes, then don't run them and ask others first.

---

### Post by kira. on 2008-02-04
of course! ;)

sean@sean-desktop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10ab10aa

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3433    27575541    7  HPFS/NTFS
/dev/hda2            3434        4798    10964362+  83  Linux
/dev/hda3            4799        4865      538177+   5  Extended
/dev/hda5            4799        4865      538146   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x052761f2

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        2551    20482875    f  W95 Ext'd (LBA)
/dev/hdb2            2552       24321   174867525    7  HPFS/NTFS
sean@sean-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=90a9be3f-0264-4afc-97cc-7c2c5687f231 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=99f956a5-4437-476d-ae2d-df4ee1c0be54 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hda1   /media/hda1   ntfs-3g   defaults   0   0
/dev/hdb2   /media/hdb2   ntfs-3g   defaults   0   0
sean@sean-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              11G  3.9G  6.2G  39% /
varrun                506M  216K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  112K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
sean@sean-desktop:~$ 

Like so?

---

### Post by taurus on 2008-02-04
I bet you if you run this command at a terminal, you will get a warning message that you didn't shut down your windows cleanly and you would have two options:  boot into windows again and shut it down cleanly or use the force option to mount it.

```
sudo mount -t ntfs-3g /dev/hda1 /media/hda1
```

If you want to use the force option, then run

```
sudo mount -t ntfs-3g /dev/hda1 /media/hda1 -o force
```

---

### Post by kira. on 2008-02-04
* I'm sorry:(, i didn't mean to offend you or anything:(, i was only asking if what i did was right, if something had happend, i would in no way hold you accountable, and thanks for your help, it was greatly appreciated!

---

### Post by kira. on 2008-02-04
+ thanks for the extra codes, you're quite knowledgable:)

---

### Post by kira. on 2008-02-04
what would happen if i chose to force mount the drives?

---

### Post by taurus on 2008-02-04
> **kira. said:**
> what would happen if i chose to force mount the drives?

Nothing would happen, as far as I know.  Again, if you don't feel safe using the force option, I would strongly recommend you reboot into windows and shut it down cleanly this time.  Then, everything should be rosy again.

---

### Post by kira. on 2008-02-04
and also, just to clarify, the prompt says "external drives", but it's my internal drives that aren't showing up

---

