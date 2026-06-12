---
title: "Using LZMA compression for squashfs"
date: 2008-07-22
forum: General Help
---

### Post by jedi453 on 2008-07-22
Hi, I've finally learned how to build liveCDs thanks to the following guides:
[http://ubuntuforums.org/showthread.php?t=736861](http://ubuntuforums.org/showthread.php?t=736861)
[https://help.ubuntu.com/community/Li...ionFromScratch]("http://ubuntuforums.org/showthread.php?t=688872&page=12")
[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

I've found that all of them use mksquashfs for compressed filesystems, which is great for fitting extra on a cd, but it would probably be much better (compression ratio) if the kernel could read the lzma squashfs filesystems that mksquashfs can produce. I've found a site that tells how to make this possible with it's prebuilt kernel image: [http://www.squashfs-lzma.org/](http://www.squashfs-lzma.org/)
however it doesn't have nearly the hardware support that ubuntu natively has. Is there any way to use the ubuntu kernel and patch it to support lzma compression?

I've tried using the lzma-source package from the ubuntu repository, however I'm unsure what to do next. I found a site that claims this can be done with m-a build lzma, but I followed the instructions to no avail. Here's the site: [https://answers.launchpad.net/ubuntu/+source/squashfs/+question/34199](https://answers.launchpad.net/ubuntu/+source/squashfs/+question/34199)

If anyone has experience with patching or updating the kernel for support with lzma compressed squashfs files, help would be greatly appriciated. 

Thanks

---

### Post by DagMan on 2008-07-25
I'm myself wondering if the squashfs-tools package doesn't by default use lzma.  I was just looking at man mksquashfs and it looks like you have to explicity say --nolzma if you don't want to use it, if I understand correctly.  
It seems to be part of the mksquasfs command, and I'm presuming that the lzma package was pulled in when I did apt-get install squashfs-tools because I can't imagine what else would have pulled it in unless it was part of the initial install.
If you learn otherwise, please post it because I'm also looking to use heavier compression if I can.

---

### Post by jedi453 on 2008-07-26
> **DagMan said:**
> I'm myself wondering if the squashfs-tools package doesn't by default use lzma.  I was just looking at man mksquashfs and it looks like you have to explicity say --nolzma if you don't want to use it, if I understand correctly.  
It seems to be part of the mksquasfs command, and I'm presuming that the lzma package was pulled in when I did apt-get install squashfs-tools because I can't imagine what else would have pulled it in unless it was part of the initial install.
If you learn otherwise, please post it because I'm also looking to use heavier compression if I can.
I saw the same this before, however I'm not sure it uses squashfs by default. When I use the "-nolzma" option I get the same file size as without it. Strangely enough I still get the same filesize with the "-lzma" option. Yet when I use the "-lzma" option instead of "-nolzma" the kernel can't boot the livecd and I get dropped into busybox. So I believe that not only does mksquashfs not use lzma by default, it doesn't use it at all. Can anyone second this, or correct it? If I'm right how does one use lzma compression with squashfs?

---

### Post by jedi453 on 2008-09-12
I've finally found a way to get a working kernel using a process similar to that described here ([http://www.beyondlogic.org/nb5/squashfs_lzma.htm](http://www.beyondlogic.org/nb5/squashfs_lzma.htm)). I end up with a kernel capable of booting. I haven't been able to test if squashfs works or not yet however. My next question is how do I add hardware support to the kernel. I want to get the hardware support of ubuntu, but all to custom build kernel has for support is matched by that of the official squashfs-lzma kernel.

In short I'm asking, does anyone know how to add the wireless card support ubuntu has to a custom or prebuilt kernel?

Thanks,

jedi453

---

### Post by bbala2020 on 2010-08-09
It seems from kernel 2.6.30, squashfs and lzma are supported but I dont find any howtos to use without patching a self kernel. Also I would like to know how to use squashfs with fuse? Only root being able to mount squash images makes it not suitable for using squash as backup.

---

