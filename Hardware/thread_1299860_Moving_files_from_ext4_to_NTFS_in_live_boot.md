---
title: "Moving files from ext4 to NTFS in live boot?"
date: 2009-10-24
forum: Hardware
---

### Post by burvowski on 2009-10-24
Hi, so I installed Win 7 on one of my machines to try it out. I was preparing to move some movies and music off my external backup when I realized it's formatted in ext 4 because all my other PCs are running Ubuntu.

Would it be possible to plug in the external, boot into a live session from my 9.04 cd, and then to drag them from the ext4 drive to the NTFS one? If not, is my only other option to backup the external files, reformat it as another disk format, and then to do it?

---

### Post by coffeecat on 2009-10-24
> **burvowski said:**
>  Would it be possible to plug in the external, boot into a live session from my 9.04 cd, and then to drag them from the ext4 drive to the NTFS one?

I don't see why not. Ubuntu 9.04 can read/write both ext4 and NTFS filesystems reliably. The external ext4 drive will be automounted when you plug it in. I presume the NTFS drive is your Win7 C: partition. If it is it should be accessible through the Places menu. The only thing to beware of is that some people (so I've read) have run into some problems writing to a Vista or W7 C: partition. It's not the writing that's the problem - it's that sometimes Windows throws a wobbly for some reason or another. That being said I've got one Vista/Ubuntu machine and one Win7/various Linux distros machine, both with shared NTFS data partitions which show up as D: in Windows. I've never written to either of the C: drives, but both flavours of Windows seem to be happy with files I've written to the data partition(s) with Ubuntu.

With one exception that is. Me-tv in Ubuntu wrote a DVB stream mpeg to the NTFS partition with a very long filename. Windows 7 took exception to this and refused either to rename or delete it. I had to use Ubuntu to rename the file - on an NTFS partition. :roll:

The only other problem you may come across is that you may run into permission problems on the ext4 drive. Depending on the ownership and permissions on your files, you may have to invoke sudo powers to copy them off.

---

