---
title: "Can you decompress this initrd image? File attached"
date: 2008-08-15
forum: General Help
---

### Post by karthikb23 on 2008-08-15
Hi,
I have problems with the new kernel i compiled, using the vanilla kernel for version 2.6.11.

I have tried every suggestion possible, (compile IDE, SCSI though i dont have SCSI devices!, RAID, EXT2, EXT3, NTFS, MSDOS, Reiser FS) and yet my kernel wont boot, saying
"VFS: Unable to mount root on unknown block (0,0)"

The only alternative is to check what else my initrd is booting for the original distro, that i am not doing.

But i am unable to decompres this initrd image (gzip just doesent accept this as a valid file for it, even if i rename it as ".gz". Even cpio does not decompress it Then how t hell is my kernel able to decompress it and mount it??? :mad:)

I have uploaded the file at:

[]("http://rapidshare.com/files/137571545/INITRD.IMG.html")

[http://rapidshare.com/files/137571545/INITRD.IMG.html](http://rapidshare.com/files/137571545/INITRD.IMG.html)

Could you please try decompressing it someway??!!!
Thanks in advance for your help!

Regards!

---

### Post by psusi on 2008-08-15
Your boot loader is not loading an initrd, so the kernel is trying to mount the root filesystem itself, without the aid of an initrd to load drivers and detect hardware and such.  The root filesystem is not configured in the kernel image so it defaults to device 0,0, which does not exist, hence the error.

Run file foo.img to see what the file looks like.  If it is an initramfs, it should look like a gzipped cpio archive.  If it is an old style initrd, it is a romfs image.

---

### Post by karthikb23 on 2008-08-16
Hi psusi.
could you please explain what you mean by run "foo.img"?

Should i just give it execute permission and run it from the shell?

As apart, i tried decompressing the file with gzip, and cpio combo, but am unsuccessful.

These issues are related to an earlier post of mine, to which you had replied (unknown block device (0,0))

Thanks!

---

### Post by karthikb23 on 2008-08-16
and just to add....
root device (0,0) does exist, because when GRUB boots and passes the root parameter to kernel, it displayes the device correctly and the filesystem too.

My old kernel boots just fine off the same GRUB settings, but using an initrd.

---

### Post by psusi on 2008-08-17
No, there is no such thing as device 0,0.  You probably have grub configured to pass the root filesystem identified by UUID, and the kernel itself can not understand what that means; it requires scripts in the initrd to locate the root filesystem by UUID and mount it.

foo.img is whatever the name of your .img file is.  Just type "file foo.img" in the shell.  What did gzip say when you asked it to decompress the file?

---

### Post by karthikb23 on 2008-08-18
GZIP just complains that the file is not a gzip file. I dint try 'file' though. Will try n let u know.

---

### Post by pauper on 2008-08-20
Try:
```
mkdir /tmp/imagefile && cd /tmp/imagefile
gzip -cd /boot/initrd.img-`uname -r` | cpio -imd --quiet
```

[http://www.mjmwired.net/kernel/Documentation/initrd.txt](http://www.mjmwired.net/kernel/Documentation/initrd.txt)

---

### Post by karthikb23 on 2008-08-20
Thanks!
I'll try that n let u know

---

