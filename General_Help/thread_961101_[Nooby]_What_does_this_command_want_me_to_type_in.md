---
title: "[Nooby] What does this command want me to type in?"
date: 2008-10-28
forum: General Help
---

### Post by Dayo6 on 2008-10-28
OK OK, so I got fuseiso, and I want to mount my back up copy of Freedom Fighters.  There is a .mds and .mdf file in the folder freedom fighters, so it looks like this

owner/downloads/freedom fighters/freedomfighter.md(s/f)

The readme included in the fuse iso said this:

> Usage:
    
    fuseiso [<options>] <image_file> <mountpoint> [<FUSE library options>]
    
mounts image, while fusermount shipped with FUSE library can be used to unmount:

    fusermount -u <mountpoint>

fuseiso options are:

    -p              Maintain mountpoint. Create it if it does not exists on start, delete it on exit.
    -n              Do NOT maintain ~/.mtab.fuseiso . This file have format of /etc/mtab and normally stores information about currently mounted iso images.
    -c iocharset    Specify iocharset to use. Joliet filesystem store filenames in unicode and to show them properly they need to be converted to local charset. Default charset is a current locale charset.
    
fuseiso supports plain ISO images (created by mkisofs for example), BIN and NRG images 
containing ISO9660 filesystem. Along with standard ISO9660 filesystem it support some common extensions: 

Joliet              Common in windows world. Allow long filenames stored in unicode.
RockRidge           Common in unix world. Allow long filenames, deep directories, symbolic links and permission bits to be stored.
zisofs              Compressed filesystem, drastically increases capasity of standard CDROM.

In fact i found what CCD (CloneCD) .IMG files along with .MDF (Alcohol 120%) images 
can be mounted without problems because their format looks exactly as .BIN image file format. 
So currently fuseiso supports disk images with following extensions: 

.iso
.img
.bin
.mdf
.nrg

Although, BIN images support have now major limitation -- fuseiso does not handle .CUE files in any way 
and thus can work only with first track of the BIN image. I don`t know if this is important 
to support .CUE files properly. Please email me if you need it. Support for other types of media  
descriptors like .ccd and .mds looks more difficult task because no one know it`s format.

How do I mount FF?

Thanx

---

### Post by alienprdkt on 2008-10-28
I believe its saying:

#fusermount -u /some.iso /path_to_where_you_want_to_mount

but may have to add it to your /etc/fstab or /etc/mtab if doesn't work

---

### Post by pofigster on 2008-10-28
First- do you have a mount-point set up?  I use /media/iso for mounting disc images.

If you don't, type ```
sudo mkdir /media/iso
``` or something like that to make your mountpoint.

Then type:

```
fuseiso /home/owner/downloads/freedom\ fighters/freedomfighter.mdf /media/iso
```

Of course, if the path to the .mdf file is different, you should change it so that it's correct.  Also, if you have a different mount-point, you should change that as well.

I'm going to go ahead and qualify this by saying I've never used fuseiso - i use gmount-iso and convert all my image files to .iso

---

### Post by Dayo6 on 2008-10-28
> **pofigster said:**
> First- do you have a mount-point set up?  I use /media/iso for mounting disc images.

If you don't, type ```
sudo mkdir /media/iso
``` or something like that to make your mountpoint.

Then type:

```
fuseiso /home/owner/downloads/freedom\ fighters/freedomfighter.mdf /media/iso
```

Of course, if the path to the .mdf file is different, you should change it so that it's correct.  Also, if you have a different mount-point, you should change that as well.

I'm going to go ahead and qualify this by saying I've never used fuseiso - i use gmount-iso and convert all my image files to .iso

OK I got gmount-iso, which seems much easier.  But what program do you use to convert your mdfs?

Thanks

---

### Post by soro2005 on 2008-10-28
> **Dayo6 said:**
> OK I got gmount-iso, which seems much easier.  But what program do you use to convert your mdfs?

Thanks

You can use mdf2iso (repository/commandline), like so:
```
mdf2iso input.mdf
```
When it tells you that the mdf is already in iso format, I've had luck just running it through cat like this:

```
cat input.mdf > output.iso
```

One would normally assume that just changing the extension does the same, but for some reason which I did not investigate this does not seem to be the case. Don't forget the > in the middle. If you do, the output will be printed into the terminal. Stop that with ctrl+c and reset your terminal with
```
reset
```
By the way: If you have .mdf, md0, md1 ... mdn, you can combine them by daisy chaining them like this:
```
cat input.mdf input.md0 input.md1 ... input.mdn > output.iso
```

---

