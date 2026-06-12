---
title: "ntfs-3g on Linux VERSUS ext2ifs on Windows"
date: 2008-07-25
forum: General Help
---

### Post by LoganK on 2008-07-25
Got a brand-new XPS M1530...fantastic hardware, horrible software (AKA Vista). After cleaning up the hidden recovery partition, Vista started BSOD-ing all over the place, continually getting corrupt disk notifications requiring chkdsk, etc.; finally broke down and formatted the whole disk and re-installed Vista. Guess what? Vista's STILL crashing faster than a Nascar race. Whatever; I'm done with Vista.

I want to install XP on the machine now, dual-booted with Linux (BTW, this whole time Linux was dual-booting on the machine and never once encountered a problem...obviously Vista needs some euthanasia). Ultimately, though, I want XP and Ubuntu to share a data partition. Here's my question: **which is better, ntfs-3g or ext2ifs?** I can format the data partition as NTFS and use Ubuntu's rather good ntfs-3g support to read/write to it, or I can format it as ext3 and install ext2ifs on Windows to read/write to it. Yes, I've considered a neutral FAT32 filesystem, but I've read that apparently FAT32 will require defragging (more often than NTFS or ext3), not to mention its 4GB filesize limit that, although not a problem for me now (I don't have any 4GB+ files), may become an issue in a few years with HD content proliferating.

So can anyone offer up some advice on which solution to go with? Or if I should consider (more strongly) FAT32? Anything will help!

---

### Post by nowhere@cox.net on 2008-07-25
Not that this is any help but I am in the same position. I just came up with a spare 160GB SATA notebook drive and jammed it in my ultrabay slot to house music, videos etc I want available in Ubuntu and Vista (only cuz I need to use itunes with the new iphone right now). 

SO! I too would like to see the results of this poll and also know if there are choices for the ext3 driver for Vista or is there only one? If more than one, which one is best?

Thanks for asking this!

---

### Post by prshah on 2008-07-25
Absolutely _not_ FAT32; there's a 32Gb size limit if you create it in XP (no such limit if you do it with some other partitioning software), and the 4Gb file limit is astonishingly easy to encounter; tried creating a DVD image? Especially one with ECC RS02 adding as done by DVDisaster?

Since it's an internal hard drive and (i suspect) you will not be using XP much, I'd say go ext3 + ext2/3 ifs in Windows.

For external, I'd (reluctantly) vote for ntfs; since you'd probably expect to use it elsewhere and obviously can't go on installing ext2/3 ifs everywhere you go.

btw, make the ext2/3 ifs driver use read-only access; a nice little windows virus could probably play havoc with ubuntu's data. (probably)

---

### Post by Nepherte on 2008-07-25
It depends on what you want to use the most:
1. If you think you'll use linux more, then I suggest you'd take ext2. It has the advantage it doesn't fragment unless the whole disk is full. The downside of ext2ifs is that I just don't like windows having full access to the / directory. It avoids the whole idea of permission based security in linux.

2. If you intend on installing windows apps on the disk, use ntfs.

Note: Have you considered it might be a hardware issue? If you did a clean windows install and you get chkdsk problems, you're hard disk might be dying. Being it a brand new laptop doesn't change the fact that it might be defect.

My preference goes to ext2 + ext2ifs

---

### Post by LoganK on 2008-07-25
@Nepherte: I won't give it full access to the / directory; the partition would probably only house the /home partition (and then I'd re-map all the "My Crap" folders in XP to that partition) so that they can share just data, not OS/program files. Regarding the Vista thing, yeah, I considered a hardware issue, but I really don't wanna face the fact of having to send it in for repairs since it's brand-new and I'm leaving in 3 weeks for college.

One of my other possibilities is have no shared partition between them and only have a small partition for XP...I really only wanna use it for games and to sync my iPod (which I can do by having it reference the ext3 read-only mounted Ubuntu partition)...any other thoughts from the community? Consensus seems ext3 so far!

---

### Post by Nepherte on 2008-07-26
To check your hard disk, you could look at the S.M.A.R.T status of it. Here's how you can do it: [http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu](http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu)

---

### Post by LoganK on 2008-07-26
Due to a bunch of other stuff, right now I've just got XP on the box but as soon as Linux is back on (or if I boot into a Live-CD) I'll check out the S.M.A.R.T. status; thanks!

---

