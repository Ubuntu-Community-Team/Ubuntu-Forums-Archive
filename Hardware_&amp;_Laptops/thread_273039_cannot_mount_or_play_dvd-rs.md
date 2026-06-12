---
title: "cannot mount or play dvd-rs"
date: 2006-10-07
forum: Hardware &amp; Laptops
---

### Post by gfxcoder on 2006-10-07
i cannot for the life of me get a burned dvd to mount or play.  it will play store-bought movies just fine, at first.  when i put in a burned dvd, it does nothing.  if i try to mount it a console, it hangs.  if i try putting back in a store-bought dvd, it acts as though there isn't a disc in the drive, until i reboot. kaffeine comes back with "the source can't be read.  maybe you don't have enough rights for this, or source doesn't contain data (e.g.: no disc in drive).  (encrypted or faulty dvd)"... except i can mount it in console and see all the contents! ](*,)  and cds work just fine, no problem!

i have 6.06.

here's my fstab:
proc /proc proc defaults 0 0
/dev/hda1 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/dvd auto users,atime,auto,ro,dev,exec,suid 0 0
/dev/hdb1 /media/windows ntfs defaults,uid=1000,gid=1000,auto,rw,users 0 0
/dev/hdd /media/cdrom0 auto user,atime,noauto,ro,dev,exec,suid 0 0

---

### Post by accludetuner on 2007-04-08
same issue here.  I've been looking and will post back if I find a fix.  I've found that occassionally, by editing fstab and saving it and re-mounting with  sudo mount -a will *sometimes* recognize the DVD and play it.  It seems weird, but sometimes putting the previous DVD back in and manually ejecting it through totem or gxine will then correct it.  It seems more like the issue has to do with the previous DVD not un-mounting properly, than the new DVD not mounting right.

and here's my fstab:


/dev/sda1               ext3    defaults,errors=remount-ro 0       1
/dev/sda2              ext3    defaults        0       0
/dev/sdb3    ext3    defaults        0       0
/dev/sdb1 ext3    defaults        0       0
/dev/sda4 none            swap    sw              0       0
/dev/hdc 	/media/cdrom0 	auto 	user,noauto 	0 	0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1   /media/hda1   vfat    iocharset=utf8,umask=000  0    0
/dev/hdb1   /media/hdb1   vfat    iocharset=utf8,umask=000  0    0
/dev/sdc1   /media/sdc1   vfat    iocharset=utf8,umask=000  0    0

---

### Post by accludetuner on 2007-04-08
also thought I would add that mine is PC tower not a laptop.

Also, I watched 3 movies back-to-back with zero issues.  2 store bought, 1 burned.  I've had nothing but issues since then and I didn't make any changes.

It won't recognize DVD format at all (data or movie).  It will read CD's and even burn CD's, but does not acknowledge DVD's at all.  Drive works fine in another machine so I know it's good.  

I don't understand why it just stopped working with no changes.  I've tried all of the workarounds on this forum and others and still nothing.  Gives the error "Mount: no medium found" as if there is no disc.


Still looking but any help would be appreciated.

---

