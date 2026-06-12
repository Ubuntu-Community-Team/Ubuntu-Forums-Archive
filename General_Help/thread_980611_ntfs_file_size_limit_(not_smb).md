---
title: "ntfs file size limit? (not smb)"
date: 2008-11-13
forum: General Help
---

### Post by daximus on 2008-11-13
Pardon me if this is the wrong forum section... didn't see a perfect spot for filesystem posts.

I'm mounting an NTFS partition in Hardy.  Every way I've gone about it I seem to have a 2GB file size limit (files larger than 2GB just show as 2GB)

I've done a fair bit of reading the last couple of hours and haven't found anything that says this limit exists.  ulimit shows 'unlimited' for file size.  I've mounted through nautilus (auto), manually with -t ntfs, and with -t ntfs-3g.  'mount' always shows the volume with type 'fuseblk' no matter which type option I use.  I have tried -o lfs, and that gets ignored (guess that doesn't work with fuse?).

Any ideas?

edit:  might be worth mentioning this is i386 ubuntu, so 32bit.

---

### Post by TeXtonyx on 2008-11-13
There is a 2GB file size limit when fat32 partitions are involved.

---

### Post by daximus on 2008-11-13
There is no fat32 involved here.

---

### Post by daximus on 2008-11-13
bump

---

### Post by TeXtonyx on 2008-11-13
I became interested in your problem. I found this post,

" Re: File size capped at 1.7 G?
Quote:
/dev/sdb2 ext3 5044188 3127252 1660700 66% /
That is your /root partition and you only have 1.66G available"

My idea is to check and see if any of your partitions are 2GB.

"2) increase the root filesystem size to be more than the file 
size limit"

You weren't getting any responses so I tried the any port in a
storm approach to troubleshooting ideas; I mean possible but I'm
not claiming plausible. Both of these quotes are about areas I
don't know about, so I'm offering them in case they ring a bell.

---

### Post by daximus on 2008-11-13
I appreciate the effort... it doesn't apply, though.   Root filesystem is 40GB, about 27 free.

Thanks for looking.

---

### Post by jimv on 2008-11-13
Does it show the same file size in Nautilus and the terminal?

---

### Post by daximus on 2008-11-13
> **jimv said:**
> Does it show the same file size in Nautilus and the terminal?
Nautilus reports "2.0GB"
ls -l reports 2147457361

so... yes.

---

### Post by unutbu on 2008-11-13
According to [http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS)
the max file size is 2^64 bytes - 1 KB.

What happens when you type
```

ls -l file
cat file file > file2
ls -l file2
```

---

### Post by jimv on 2008-11-13
I've got nothing.  If it's NTFS, I doubt that you'll ever have a file in near future (or even the distant future) that would be too big.  It's probably some odd bug with NTFS-3g reporting the size wrong.

I'd test to see if I have the same issue, but I converted my NTFS drive to EXT3 awhile ago.

---

### Post by daximus on 2008-11-13
> **unutbu said:**
> According to [http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS)
the max file size is 2^64 bytes - 1 KB.

What happens when you type
```

ls -l file
cat file file > file2
ls -l file2
```

I get the same, new file is 2GB.

@jimv: I figured as much as well, but it's also rendering the file unusable.

I supposed there's still an outside shot the file actually is corrupt, but that would be quite a coincidence that it broke in a way to report exactly 2GB size.

---

### Post by jimv on 2008-11-13
I suppose you could try downloading a large file...like the Debian DVD ISO (4.4 gigs).

Here's the link:

[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-dvd/debian-40r5-i386-DVD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-dvd/debian-40r5-i386-DVD-1.iso)

Or you could use VirtualBox to make a >2 gig hard disk image file....that would be the quicker method (vs downloading a 4 gig file).

---

### Post by y@w on 2008-11-13
According to this, there shouldn't be any limit.. 
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

Does it have compression turned on? I did find this: [http://www.pcreview.co.uk/forums/thread-363364.php](http://www.pcreview.co.uk/forums/thread-363364.php)

---

### Post by y@w on 2008-11-13
Hmm.. post got dup'd :)

---

### Post by daximus on 2008-11-13
No compression, no encryption.   Though that bit about the root folder is interesting.  That was much smaller than the file I'm dealing with, though.

---

