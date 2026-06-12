---
title: "aclocal problem....i switched to ubuntu to avoid dependcy issues :("
date: 2005-12-03
forum: General Help
---

### Post by magomago on 2005-12-03
I can't figure this one out.  I wanted to install CCD2ISO so i could mount ff8 b/c i had a desire to play it again.  

Anyways i went to install CCD2ISO (which i found by gooling) but it said i need aclocal-1.6 so i googled more.  I saw i needed automake-1.96 well trying to install that I hit MORE dependency issues

so i said screw it and did an apt-cache search aclocal and just started installing all that I Saw

I went back to CCD2ISO to and ran ./configure and then make

but it STILL gave me the same problem

anyone know how to fix this?  I just want to compile it :( so i can convert it to an iso

on the other hand, the cd image is actually a .img file with a corressponding .cue/.ccd  is there anyway to wor with that?

---

### Post by dafl00 on 2005-12-03
```

mount -o loop -t [image format] [image file].img /place/where/you/want/to/mount

```

-or-

add a repository that contains a binary of that program.. 
[http://www.rarewares.org/debian-info-allpackages.html]("http://www.rarewares.org/debian-info-allpackages.html")
looks like they have it

---

### Post by magomago on 2005-12-03
it works for .img files also?!?! w00t :D

---

### Post by ryan76 on 2006-06-17
What's the image format for .img files? I tried img

---

### Post by ryan76 on 2006-06-24
Anyone? This from the mount man page:

t vfstype
    The argument following the -t is used to indicate the file system type. The file system types which are currently supported include: adfs, affs, autofs, cifs, coda, coherent, cramfs, debugfs, devpts, efs, ext, ext2, ext3, hfs, hpfs, iso9660, jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc, qnx4, ramfs, reiserfs, romfs, smbfs, sysv, tmpfs, udf, ufs, umsdos, usbfs, vfat, xenix, xfs, xiafs.

I'm using the command above,
mount -o loop -t [image format] [image file].img /place/where/you/want/to/mount

I'm also guessing where I want to mount the file, /mnt/ISO?

---

### Post by keithjr on 2006-06-24
[QUOTE=ryan76]Anyone? This from the mount man page:

t vfstype
    The argument following the -t is used to indicate the file system type. The file system types which are currently supported include: adfs, affs, autofs, cifs, coda, coherent, cramfs, debugfs, devpts, efs, ext, ext2, ext3, hfs, hpfs, iso9660, jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc, qnx4, ramfs, reiserfs, romfs, smbfs, sysv, tmpfs, udf, ufs, umsdos, usbfs, vfat, xenix, xfs, xiafs.

I'm using the command above,
mount -o loop -t [image format] [image file].img /place/where/you/want/to/mount

I'm also guessing where I want to mount the file, /mnt/ISO?[/QUOTE]


I'm having a similar problem, I cannot get my img file to mount properly.  If I leave out the -t option, it complains that I must select a filesystem.  If I try iso9660, I get this error:

```
mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


Man, uphill battles never end...  wish I had an answer for you or I.

---

