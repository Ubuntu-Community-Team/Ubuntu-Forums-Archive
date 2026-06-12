---
title: "Having trouble syncing sony ericsson"
date: 2006-05-24
forum: Hardware &amp; Laptops
---

### Post by Piggah on 2006-05-24
Hey everyone... This may be a simple problem, I'm not sure. 

The problem I'm having is that when I try to copy a file over to my phone, just using Konqueror since that's all that will work, I'm now getting an error that I can't copy the file because it's a read-only filesystem. I'm set as the owner and have read/write priveleges, so I'm not sure what's going on. 

I was just able to send files over to it yesterday, but after transferring files to it using its software on windows, I'm now getting this error. I've used it with Ubuntu after doing this before, so I'm a bit confused. 

It is properly mounted and I can browse the files and even take files off of it fine. 

So I'm trying to figure out how I can get it so I can get it so I can write to the filesystem on the phone again. I'm really just using it like a usb drive. But the model is a Sony Ericsson W600i if it does help any. 

Any ideas?

Thanks :)

---

### Post by zhoux on 2006-05-24
I dunno if this would help, but Linux cannot write to NTFS disks.  Maybe that's the problem? :-k

---

### Post by Piggah on 2006-05-25
I'm thinking it is, but then I was able to write to it before. So I'm really confused there.

Somehow I need to format it so I can write to it using Linux.. I just don't know how.

Thanks.

---

### Post by zhoux on 2006-05-25
[QUOTE=Piggah]I'm thinking it is, but then I was able to write to it before. So I'm really confused there.

Somehow I need to format it so I can write to it using Linux.. I just don't know how.

Thanks.[/QUOTE]

if you want to format or partition it, you can try gparted

sudo apt-get install gparted, if found it very effective and easy to use.

Hope that helps.

As for the problem with writing to it before, i think the windows software might've reformatted the disk to NTFS, although i'm not sure.

---

### Post by zhoux on 2006-05-25
By the way, Windows can't read ext2 or ext3 format.  You have to find a software on the web that allows windows to do that.  As of right now, i can't think of the name.

---

### Post by Aetherius on 2006-11-18
explore2fs

[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

---

