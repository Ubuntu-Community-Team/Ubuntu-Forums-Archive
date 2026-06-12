---
title: "How to activate LFS support in Hardy i386 (32bit)"
date: 2008-10-22
forum: General Help
---

### Post by remi_2 on 2008-10-22
Hello, 

How can I enable LFS in ubuntu 8.04? 

on my hardy desktop install (32 bit) I can't create or manipulate files larger than 2Gb.

I've googled for LFS (large file support) and saw that it was supported by linux > 2.4 and that ext3 had full support for it. 

ulimit says there are no limits set for filesize.

On the other hand, I have no problems handling bigger files on a 8.04 64bit system.

thanks for any useful input,

best regards

---

### Post by geirha on 2008-10-22
The file size limit on ext3 should be 2TiB if I remember correctly. Are you transferring files via samba by any chance? There's an issue with shared folders on FAT filesystems that limit the filesize to 2GiB (even though FAT32 support filesizes upto 4GiB).

---

### Post by remi_2 on 2008-10-22
Hi!
I'm not using samba, it is an ASCII file created by one of my programs (a log of some sort). The file is written incrementally, and is capped at 2Gb by the filesystem, whereas it should be 7Gb in the end.

---

### Post by geirha on 2008-10-22
Odd. Can't be the program that has the limit can it? Try making a 4GiB file with dd
```
dd if=/dev/zero of=testfile bs=4096 count=$((2**20))
``` and see if it stops at 2GiB there too.

---

### Post by remi_2 on 2008-10-22
Thanks for helping me!

I've tried the command and it worked, a 4.3 gigs file was created, and I could rename it using mv.

So it looks like there is a problem with the program that creates the file.

Are there special functions to use in C/C++ to handle files past the 2Gb size limit? I'm just using the stdio functions to open/write/read files. 
The same software compiled in Hardy x86_64 works just fine with 7Gb files :(

Thanks again!

---

### Post by geirha on 2008-10-22
I wasn't aware of such a limit myself. I did a little test myself, and fwrite won't write more than 2GiB for me either. 

I found this after a bit of googling though: [http://www.suse.de/~aj/linux_lfs.html](http://www.suse.de/~aj/linux_lfs.html)

So a "#define _FILE_OFFSET_BITS 64" fixes things.

---

### Post by remi_2 on 2008-10-23
Thank you, it saved me a lot of time, I'll try that solution, it 'm sure it will work.

---

