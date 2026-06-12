---
title: "unknown filesystem 'vfat'"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by andradelipe on 2006-11-02
Hi,

After the last update I can't mount my fat32 partion. 
Searching  the google, seems that my kernel (2.6.17)  doesn't
have the module for vfat. and seems that I have to rebuild the kernel.

I'm not a super-user, just have edgy installed and add new packages and updates from synaptic. 

my /etc/fstab :

[SIZE="1"]/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda1 -- converted during upgrade to edgy
UUID=eac3950c-784d-4b0c-9bd6-02b0531b36da / ext3 nouser,defaults,errors=remount-                                                              ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=cdb362af-550e-41dd-b7bc-558ded80bdae none swap sw 0 0
# /dev/hdb2 -- converted during upgrade to edgy
/dev/hdb2 /media/windows vfat nouser,iocharset=utf8,umask=000,atime,noauto,rw,no                                                              dev,noexec,nosuid 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
[/SIZE]



You can help me?

---

### Post by pay on 2006-11-02
These are the options that you need enabled in your kernel
[http://gentoo-wiki.com/HOWTO_USB_Mass_Storage_Device](http://gentoo-wiki.com/HOWTO_USB_Mass_Storage_Device)
And heres a guide on how to compile the kernel
[http://ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel](http://ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel)

---

### Post by andradelipe on 2006-11-03
So, are you telling me to compile the kernel because the last update comes
without the "vfat" ???

Is true that this is the only option? 

I've tried to compile last night, but I'm a newbie and make a lot of mistakes, like, in that how-to above, ask me to not load nVidia, and my MX 440 doesn't work anymore. My keyboard, also. (br abnt2). I really configure it correctly (sudo dpkg-reconfigure xserver-xorg) but it's not working right.

I'm back in my 2.6.17-10-386, without my files on hdb2 =/

I can change the type of partition without lose my files? like vfat to reiserFS?

This will be a solution that solve this, but will cause another problem, like my mother can't see she's files on ruindows anymore..

so, what can I do?](*,)

---

### Post by taurus on 2006-11-03
Have you at least tried to mount it by hand first to see what's the problem is?  

```

sudo mount -t vfat /dev/hdb2 /media/windows

```

---

### Post by andradelipe on 2006-11-03
Make shure that yes, I've tryed. 

[COLOR="Red"]mount: unknown filesystem type 'vfat'[/COLOR]

That is the problem.

---

### Post by andradelipe on 2006-11-04
> **andradelipe said:**
> Make shure that yes, I've tryed. 

[COLOR="Red"]mount: unknown filesystem type 'vfat'[/COLOR]

That is the problem.



someone?

---

### Post by andradelipe on 2006-11-04
sudo modprobe vfat

FATAL: Error inserting vfat (/lib/modules/2.6.17-10-386/kernel/fs/vfat/vfat.ko): Unknown symbol in module, or unknown parameter (see dmesg)

~$ dmesg | tail
[ 2467.748488] vfat: Unknown symbol fat_search_long
[ 2467.748791] vfat: Unknown symbol fat_attach
[ 2467.748993] vfat: Unknown symbol fat_build_inode
[ 2467.749149] vfat: Unknown symbol fat_fill_super
[ 2467.749314] vfat: Unknown symbol fat_alloc_new_dir
[ 2467.749471] vfat: Unknown symbol fat_notify_change
[ 2467.749627] vfat: Unknown symbol fat_remove_entries
[ 2467.749870] vfat: Unknown symbol fat_add_entries
[ 2467.750027] vfat: Unknown symbol fat_sync_inode
[ 2467.750325] vfat: Unknown symbol fat_detach

---

