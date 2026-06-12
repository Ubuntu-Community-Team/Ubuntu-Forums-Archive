---
title: "Drive with Ubuntu on it &quot;not accessible&quot;"
date: 2008-10-27
forum: General Help
---

### Post by lesliek on 2008-10-27
I installed Ubuntu with Wubi. I was invited to use drive I, said to have 43GB free. A 15GB installation was suggested. I followed those suggestions. The installation process appeared to work normally. I was invited to reboot. I did. I could boot into Windows, but not Ubuntu.

I tried to look at drive I in Windows. I got the following message:

" I:\ is not accessible. The request could not be performed because of an I/O device error."

Drive I has important data on it, leaving aside Ubuntu.

What do I try now?

Thanks for reading this.



EDIT: I've kept trying on my own. Also on my machine already is an old Fedora distribution. It treats Windows drive I as /dev/sda1 and would usually mount it at /media/usbdisk1. When I booted up in Fedora, it didn't mount /dev/sda1. I tried to do it manually. I got the following message:

"mount: /dev/sda1: can't read superblock".

I'm not really sure what the superblock is, but Wubi seems to have altered it in some way.

---

### Post by ago on 2008-10-28
Wubi, on the windows side, only writes a few files inside the target folder. That is a normal windows I/O operation.

On the linux side those files (and only those files) get processed, but it does not look like you reached that point at all. 

It might be that it is a hardware problem.

---

### Post by lesliek on 2008-10-29
Thanks for your reply, ago.

After my last edit above, I ran testdisk on /dev/sda1 and was told that I now had an invalid bootsector. I had 544 bytes per sector, rather than the required 512.

A hardware problem seems unlikely, because the drive to which Wubi wrote Ubuntu is a logical one only. The other logical drive on the physical drive, /dev/sda2, continues to operate as normal.

Wubi seems to me to be the obvious cause of the problem.

I was able, with testdisk, to copy some of the files from /dev/sda1 to another physical drive. Some of those were afterwards readable, most not.

Since I'm writing this on a laptop running Ubuntu installed by Wubi, I know that Wubi does work. I guess I was just unlucky.

---

### Post by ago on 2008-10-29
Well you can look at the code if you do not trust me, there is nothing in wubi that writes or even reads the boot sector. It's as simple as that.

---

