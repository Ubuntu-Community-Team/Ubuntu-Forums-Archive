---
title: "Link creation and kernel compilin error on USB"
date: 2008-11-26
forum: General Help
---

### Post by guedesav on 2008-11-26
Hi,

I have my USB mounted in read-write mode, with me as owner and owner group. I can read and write freely on it, but I'm having problem doing at least two things:

1. creating a link. I can't create a link to a folder, no matter what. When I try "ln -s tmp linktest" on my /media/usb folder, I get:

> 
guedesav@guedesav-desktop:/media/usb$ ln -s tmp/ linktest
ln: criando link simbólico `linktest' to `tmp/': Operação não permitida


That means I have no permission.

2. compiling a kernel. I'm trying to compile a kernel package in the USB, because my HD is already full. But that doesn't matter. The problem is I can't compile it, even as root! Here's the output for "make menuconfig"

> 
guedesav@guedesav-desktop:/media/usb/so/linux-2.6.24.2$ make menuconfig
  HOSTCC  scripts/basic/fixdep
/bin/sh: scripts/basic/fixdep: Permission denied
make[1]: ** [scripts/basic/fixdep] Erro 126
make: ** [scripts_basic] Erro 2


The same happens for "sudo make menuconfig" and "su -c make menuconfig".

My /etc/fstab is clearly set to give me full permission:

> 
/dev/sda1				/media/usb			auto			rw,user,noauto	0				0


and the /media/usb folder is clearly mine, as this command shows:

> 
guedesav@guedesav-desktop:~$ ls -l /media/
total 44
lrwxrwxrwx  1 root     root         6 2007-11-15 08:06 cdrom -> cdrom0
drwxr-xr-x  2 root     root      4096 2007-11-15 08:06 cdrom0
drwxr-xr-x  2 root     root      4096 2008-09-23 19:44 flash
lrwxrwxrwx  1 root     root         7 2007-11-15 08:06 floppy -> floppy0
drwxr-xr-x  2 root     root      4096 2007-11-15 08:06 floppy0
drwxr-xr-x  2 root     root      4096 2008-05-23 17:49 mp3
drwxr-xr-x  2 root     root      4096 2008-05-23 18:00 mp32
drwxr-xr-x  2 root     root      4096 2008-04-29 20:24 sd
drwxr-xr-x 17 guedesav guedesav 16384 2008-11-26 10:24 usb
drwxr-xr-x  2 root     root      4096 2008-05-21 21:41 usb2


And that's it. Can anyone give a help here?

---

