---
title: "Is GParted that awesome?"
date: 2010-10-23
forum: Hardware
---

### Post by Cadeyrn on 2010-10-23
So, I've been copying files of way over 4GB to my FAT32 flash drive without realizing it, and I just realized it. My Linux laptop and my Macbook have both been doing it for a while now, and they've been reading it from each other just fine. I formatted it to FAT32 using GParted, so I'm wondering, does GParted use a special better version of FAT32?

---

### Post by peculiar penguin on 2010-10-23
I don't think so. Make sure your files are still intact - checksum them with md5sum or similar before copying them to the drive and compare after copying them back onto the computer. If you have access to a Windows box, running [H2Testw]("ftp://ftp.heise.de/pub/ct/ctsi/h2testw_1.4.zip") to verify that the flash drive isn't silently eating your data is another option (in the past there were quite a few cases of cheap/counterfeit flash drives having less memory than advertised, with the controller hacked to report a bigger file system).

---

### Post by Cadeyrn on 2010-10-23
Thanks for the tips. It might also be that they're ISO files, and therefor might contain a lot of zeros within the file that allow FAT32 to not freak out over a big size.

---

### Post by Cadeyrn on 2010-10-23
Nope. I just checked my drive, and now, all the 4GB ISOs are 4.29GB and empty on the Mac, and on Linux, they're 4.0GB and missing many files. Thanks for telling me to catch that! I would've had all my full-sized DVDs in storage without real backups!

Incidentally is there an easy way to make Brasero or dvdisaster separate their files into parts, or am I gonna have to do that with some separating program? Also, is there a better burner out there than Brasero? Brasero is extremely robust and I like that, but its GUI leaves a LOT to be desired (slow, no perferences, etc.).

---

### Post by perspectoff on 2010-10-23
> **Cadeyrn said:**
> Nope. I just checked my drive, and now, all the 4GB ISOs are 4.29GB and empty on the Mac, and on Linux, they're 4.0GB and missing many files. Thanks for telling me to catch that! I would've had all my full-sized DVDs in storage without real backups!

Incidentally is there an easy way to make Brasero or dvdisaster separate their files into parts, or am I gonna have to do that with some separating program? Also, is there a better burner out there than Brasero? Brasero is extremely robust and I like that, but its GUI leaves a LOT to be desired (slow, no perferences, etc.).

FAT32 limits files to 2 Gb. I would use a different filesystem if you routinely use > 4 Gb video files. It becomes a PITA to split files into 2 Gb chunks all the time.

---

### Post by Cadeyrn on 2010-10-23
Yeah, I was just about to switch to NTFS. I really wish Mac and Windows could easily read ext...

Anyway, what are the odds of NTFS not being compatible with every computer that I might install games onto? I noticed some Macs magically are and some Macs magically aren't and require NTFS-3G, regardless of the version of OS X or the model of the Mac itself.

But I remember hearing that the newer version of FAT32 can go above 2GB, just not 4GB. Plus I have a bunch of 3.xGB ISOs that have no problems whatsoever living in that drive.

---

### Post by perspectoff on 2010-10-23
> **Cadeyrn said:**
> Yeah, I was just about to switch to NTFS. I really wish Mac and Windows could easily read ext...

Anyway, what are the odds of NTFS not being compatible with every computer that I might install games onto? I noticed some Macs magically are and some Macs magically aren't and require NTFS-3G, regardless of the version of OS X or the model of the Mac itself.

But I remember hearing that the newer version of FAT32 can go above 2GB, just not 4GB. Plus I have a bunch of 3.xGB ISOs that have no problems whatsoever living in that drive.

Yeah, the problem is figuring out which version is on the USB drive. I got so frustrated trying to store large files on my FAT32 (SanDisk) USB drive (and having to split them) that I gave up. It's just too much effort, and so now I'd rather use my own online repository (on my own servers, not public ones) to store stuff.

I'll have to look into the new FAT32 system limitations, though. I hadn't realized FAT32 was still being developed. Wikipedia indicates that 64-bit clusters support up to 4 Gb files max.

4 Gb is not big enough, either. Regular DVDs hold 4.4 Gb video files, so I have made almost all my videos 4.4 Gb. That's bigger than 4 Gb. So I would have to downsize all my videos to make them FAT32 compatible even if using 64-bit clusters. That isn't very practical for me.

So USB drives with FAT32 isn't the answer for large file usage. (I use 8 Gb USB drives just for this reason.) 

BTW, GParted has old and new versions. I'm not exactly sure which version is available on the Ubuntu LiveCD, but certainly the new version of GParted is available as its own LiveCD from the GParted website.

---

### Post by coffeecat on 2010-10-23
> **perspectoff said:**
> FAT32 limits files to 2 Gb.

No. The limit in FAT32 is 4 GiB (GiB, not GB) minus 1 byte.

[http://en.wikipedia.org/wiki/Fat32#FAT32](http://en.wikipedia.org/wiki/Fat32#FAT32)

> **Cadeyrn said:**
> I noticed some Macs magically are and some Macs magically aren't and require NTFS-3G, regardless of the version of OS X or the model of the Mac itself.

There's no magic involved. MacOS X since I don't know when has supported NTFS read-only. NTFS write was being developed for Snow Leopard but was not implemented in the release version. To get NTFS write in MacOS you have to install NTFS-3g. I've done so on my Snow Leopard Mac but I find it's much slower than NTFS-3g in Linux (the driver for NTFS in Ubuntu).

---

### Post by CharlesA on 2010-10-23
I thought the file size limit for FAT32 was 4GB, not 2GB?

I think the only thing I have FAT32 on is thumb drives.

EDIT: Thanks coffeecat.

---

### Post by perspectoff on 2010-10-23
> **CharlesA said:**
> I thought the file size limit for FAT32 was 4GB, not 2GB?

I think the only thing I have FAT32 on is thumb drives.

EDIT: Thanks coffeecat.

Right. I'm still using Windows XP on some computers, and there 64-bit clusters aren't supported, so 2 Gb files are the max for FAT32.

---

### Post by CharlesA on 2010-10-23
> **perspectoff said:**
> Right. I'm still using Windows XP on some computers, and there 64-bit clusters aren't supported, so 2 Gb files are the max for FAT32.

I don't understand. How does that work?

---

### Post by Cadeyrn on 2010-10-23
> **coffeecat said:**
> No. The limit in FAT32 is 4 GiB (GiB, not GB) minus 1 byte.

[http://en.wikipedia.org/wiki/Fat32#FAT32](http://en.wikipedia.org/wiki/Fat32#FAT32)



There's no magic involved. MacOS X since I don't know when has supported NTFS read-only. NTFS write was being developed for Snow Leopard but was not implemented in the release version. To get NTFS write in MacOS you have to install NTFS-3g. I've done so on my Snow Leopard Mac but I find it's much slower than NTFS-3g in Linux (the driver for NTFS in Ubuntu).

That much I already knew, but what confuses me is the inconsistency with Mac-NTFS compatibility. Back in late 2006 I bought a Leopard iMac (or maybe it was 10.4, whatever was newest at the time) that could read/write NTFS with its factory-default state before AND after I used BootCamp to install NTFS Winblows XP. Macs I used later could read, but not write, except one ancient PowerPC Mac that couldn't read NTFS or FAT32, but see them in the Disc Utility. This new Macbook I'm using that was mentioned before in the topic, which is Snow Leopard, couldn't even see the disk as a filesystem (Disk Utility said unknown or something like that) until I installed NTFS-3G. So, what gives?

> **CharlesA said:**
> I don't understand. How does that work?

He's saying that Windows XP isn't new or maintained enough to handle the new FAT32, and therefor it assumes FAT32 cannot handle more than 2GB files and so it has a hardcoded limit with copying/moving to FAT32. Just like it has a hardcoded limit that doesn't let it read more than one partition on an external HD. Damn, Windows sucks.

---

### Post by CharlesA on 2010-10-23
So XP doesn't support this "64kb cluster" thing?

---

### Post by perspectoff on 2010-10-23
> **CharlesA said:**
> As far as I know, the 2GB limitation was a limit of FAT16, not FAT32.

That's what has me confused.

Not according to the Wikipedia article. Re-read it.

---

### Post by Cadeyrn on 2010-10-23
Back when XP was new, NTFS wasn't made yet. Or at least it wasn't commonly used yet. At that stage, XP used FAT32, and at that stage, FAT32 could only handle 2GB files. It was a bit after Windows adopted NTFS that FAT32 was upgraded to handle 4GB files, but that new file size limit was never implemented in XP. Therefor, when XP sees a FAT32 drive, it reads it as the old FAT32, before the new size limits, and doesn't let you copy bigger files.

I'm sure FAT16 also started with a smaller limit, but I don't know anything about that.

---

### Post by srs5694 on 2010-10-23
> **Cadeyrn said:**
> I really wish Mac and Windows could easily read ext...

They can, but they need extra drivers. I don't have the links handy; try Googling for them. Also, although I've used such drivers briefly, I've not used them extensively, so I don't know from firsthand experience how reliable they are. Oh, one more caveat: These drivers work with ext2fs and ext3fs, but not with ext4fs. IMHO, that's not a big deal if you plan ahead; ext4fs doesn't offer enough new features or speed improvements for its use to be all that compelling on most typical installations. Even if you do need it, you could set aside a separate ext3fs data transfer partition. That's better from a safety viewpoint, anyhow; it's best not to give Windows, or even OS X, access to a Linux root filesystem.

---

### Post by coffeecat on 2010-10-23
> **Cadeyrn said:**
> That much I already knew, but what confuses me is the inconsistency with Mac-NTFS compatibility. Back in late 2006 I bought a Leopard iMac (or maybe it was 10.4, whatever was newest at the time) that could read/write NTFS with its factory-default state before AND after I used BootCamp to install NTFS Winblows XP. Macs I used later could read, but not write, except one ancient PowerPC Mac that couldn't read NTFS or FAT32, but see them in the Disc Utility. This new Macbook I'm using that was mentioned before in the topic, which is Snow Leopard, couldn't even see the disk as a filesystem (Disk Utility said unknown or something like that) until I installed NTFS-3G. So, what gives?

That is curious. In 2006 I bought a Mac Mini with Tiger (or whichever cat 10.4 was). It could read NTFS but not write. I did an upgrade to Leopard with an Archive and Install and ditto. Then I did a straight upgrade to Snow Leopard (no archive and install Leopard > Snow Leopard) and the OS could still recognise and read NTFS. Until I installed NTFS-3g.

Odd.

---

### Post by CharlesA on 2010-10-23
> **perspectoff said:**
> Not according to the Wikipedia article. Re-read it.

I did. ;)

> **Cadeyrn said:**
> Back when XP was new, NTFS wasn't made yet. Or at least it wasn't commonly used yet. At that stage, XP used FAT32, and at that stage, FAT32 could only handle 2GB files. It was a bit after Windows adopted NTFS that FAT32 was upgraded to handle 4GB files, but that new file size limit was never implemented in XP. Therefor, when XP sees a FAT32 drive, it reads it as the old FAT32, before the new size limits, and doesn't let you copy bigger files.

I'm sure FAT16 also started with a smaller limit, but I don't know anything about that.

Now it makes sense.

Thanks.

---

### Post by Cadeyrn on 2010-10-23
> **srs5694 said:**
> They can, but they need extra drivers. I don't have the links handy; try Googling for them. Also, although I've used such drivers briefly, I've not used them extensively, so I don't know from firsthand experience how reliable they are. Oh, one more caveat: These drivers work with ext2fs and ext3fs, but not with ext4fs. IMHO, that's not a big deal if you plan ahead; ext4fs doesn't offer enough new features or speed improvements for its use to be all that compelling on most typical installations. Even if you do need it, you could set aside a separate ext3fs data transfer partition. That's better from a safety viewpoint, anyhow; it's best not to give Windows, or even OS X, access to a Linux root filesystem.

I already know about and use those drivers. I'm talking about EASILY supported ext. Probably 99% of people who want to check out my drive will be too lazy to bother if they have to install new drivers to read it.

---

### Post by srs5694 on 2010-10-23
> **Cadeyrn said:**
> That much I already knew, but what confuses me is the inconsistency with Mac-NTFS compatibility. Back in late 2006 I bought a Leopard iMac (or maybe it was 10.4, whatever was newest at the time) that could read/write NTFS with its factory-default state before AND after I used BootCamp to install NTFS Winblows XP.

AFAIK, that's not possible; OS X 10.4 and 10.5 did not include read/write NTFS support, even in disabled form. I can think of several possible explanations for your observation. The most likely are that the disk in question was actually FAT or that you'd installed NTFS-3g or some other NTFS read/write driver without realizing it.

> Macs I used later could read, but not write, except one ancient PowerPC Mac that couldn't read NTFS or FAT32, but see them in the Disc Utility.

This is consistent with what I understand, with the possible exception of FAT32 support. I was under the impression that FAT32 was supported from the start in OS X, although I'm not positive of that. I'm not sure when support was added in pre-X versions of Mac OS.

> This new Macbook I'm using that was mentioned before in the topic, which is Snow Leopard, couldn't even see the disk as a filesystem (Disk Utility said unknown or something like that) until I installed NTFS-3G. So, what gives?

One possible explanation is that the partition's type code was set incorrectly, or marked as "hidden," perhaps by a boot loader. It could also be that the filesystem was improperly unmounted, too; perhaps the regular OS X driver is conservative about mounting such filesystems, but NTFS-3g is more willing to take chances. (That's highly speculative on my part, though.)

BTW, Snow Leopard does include read/write NTFS support, but it's disabled by default. People who have enabled it often report that it sometimes damages NTFS volumes; no doubt that's why this support was disabled by default.

---

### Post by Cadeyrn on 2010-10-23
I'm glad to hear that Apple has almost reached great stock NTFS support, so nobody will have to download NTFS-3g and then worry about its not-perfect system (extremely slow or damaging the drive).

If that damn filesystem had case-sensitive journaling, it would be the ideal storage system!

---

### Post by coffeecat on 2010-10-23
> **Cadeyrn said:**
> If that damn filesystem had case-sensitive journaling, it would be the ideal storage system!

And if there were adequate tools in Linux to repair the journal so that you didn't have to rely on Windows, and if it wasn't so prone to fragmentation, and if there was a way to support Unix permissions, and if it allowed characters in filenames that are supported in Unix/Linux.....

then....

.... we might have a filesystem that comes halfway to being ideal under domestic  conditions only.

:p

---

### Post by Cadeyrn on 2010-10-23
Well, that's pretty picky. Those other things would be nice, but if I just had some case-sensitivity I'd be happy.

But, now that I think about it, having no CHKDSK in Linux is one of the biggest PITAs ever. ntfsfix doesn't get the job done... but that's what Hiren's BootCD is for!

Google that, by the way. Best boot software EVER.

Heh, honestly, I think Apple adopting ext, letting Linux use the iPod for free, and using open-source, and all that ridiculous crap is more likely than NTFS becoming that awesome. That, or a better filesystem replacing NTFS as the default tri-compatible filesystem.

---

### Post by coffeecat on 2010-10-23
> **Cadeyrn said:**
> Well, that's pretty picky.

True - I was having fun. But the last point I made is certainly valid. There was a thread a few days ago from someone who had several hundred files that they wanted to copy to a Windows using friend. Every one had filename characters disallowed in NTFS. Oops.

> **Cadeyrn said:**
> That, or a better filesystem replacing NTFS as the default tri-compatible filesystem.

Yes, it's being developed. It's going to be called the flying-pigs FS. :wink:

---

### Post by Cadeyrn on 2010-10-23
The only problem I had with NTFS and its annoying character limits was STALKER mods. Russian filenames. It was awful. I had to copy the files back and forth using Linux, and let the NTFS drive change them to ????? so that they would work with the mods. That's what I had to do to make it stop crashing!

Hmmm... Well, Apple is never willing to bend to be compatible more than they have to, so perhaps the solution is to make Windows adopt HFS+? It is a pretty good filesystem...

Ooh! Or, we wait a few years for Windows to finally die.

---

