---
title: "How to make harddisk with ontrack work with ubuntu?"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by anwarlorenzo on 2007-08-19
Hi! I formatted my primary drive so that I can be windows free and I installed ubuntu but I have a big problem.

I can't get my secondary harddisk (with all my movies and music files) to work. I discovered that It has OnTrackDM6 because I installed onntrack because my pc was really old back then.

I added "hdb=remap63" to my /boot/grub/menu.lst but it didn't work.

It still displays:

```
 Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     8217243   54  OnTrackDM6
```

whenever I do "fdisk -l"

also whenever I try to mount it says:
```

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I also tried ntfs-3g but it still won't mount.

I really hope you guys could help me because I don't want to go back to windows.

Thanks in advance! :)

---

### Post by dmizer on 2007-08-19
[http://ramses.smeyers.be/varia/OnTrackDM6/](http://ramses.smeyers.be/varia/OnTrackDM6/)

almost there ... mount as fat16.

---

### Post by anwarlorenzo on 2007-08-19
Thanks dmizer for the reply! How do I mount as fat 16?
I tried "mount -t fat16 /dev/sdb1 /media/windows" But it didn't work.

p.s.
The drive is formatted as ntfs.
So to clear things up it's a 160gb NTFS hddisk with ontrack.

---

### Post by pbcartwright on 2007-08-19
you might try booting a knoppix LiveCD, it might recognoze it...

---

### Post by dmizer on 2007-08-19
okay ... according to the link i gave you, you'll need to add:
```
sdb1=remap63
```
to your kernel.

to do this, turn off your computer.

turn it back on, and watch for grub line to say "hit esc to enter boot menu" (there will be a 3 or 4 second counter at this point).  hit <esc> while grub is loading so it shows the grub menu. 

if the boot progress indicator splash appears, you've missed the <esc> chance.  shut it down and try again.  it's right after the bios posts.

once you're in the grub menu, there may be more than one kernel listed, make sure the most recent kernel is highlighted (very top of the list).  after selecting the kernel, hit the leter 'e' for "edit".

this will show you the kernel menu.  now highlight the line that looks similar to this: kernel          /boot/vmlinuz-2.6.20-16-generic ...

select 'e' again to edit this line, and add "sdb1=remap63" (no quotes) to the end.  make sure there is a space in front of sdb1=remap63.

hit <enter>
then type 'b'

this will boot your machine with the sdb1=remap63 option enabled.  this will only work once.  the edit will not be perminant.  so if your machine won't boot like this, simply reboot and all should be well.

you may be able to mount your drive as ntfs after doing the above.

are you able to mount any other ntfs partitions or drives?

---

