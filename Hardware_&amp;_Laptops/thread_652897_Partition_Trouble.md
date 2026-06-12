---
title: "Partition Trouble"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by pudpud on 2007-12-29
Hi,

I've been searching around for someone who might have a similar problem on here, but I think this is a rather unique problem, although it may have a somewhat simple solution.

So here's the story:

I have a Dell Laptop, and a portable external HD. Originally, I had the internal HD with XP on it, and I wanted to try out Ubuntu. I tried the Live CD, liked it, and installed the distro on a partition of my external HD. Everything was absolutely fine with that.

After living with the distro for a couple of months I decided I'd actually like to be able to boot my PC with ease without my external HD installed, so I backed up my XP files onto the FAT32 partition of the external HD, wiped my internal drive, and started again. I then reinstalled ubuntu, this time onto half of my internal hard drive. Everything was again fine.

I lived with this for a couple of weeks, before deciding that I'd quite like the 90Gb of my external HD back in FAT32 form, as I keep most of my games on it. (This is my reason for dual boot). I went through the filesystem on the linux partition backed up my files from there, and then went looking for a partition tool in ubuntu. I chose Gparted. I used this to delete the old partitions on my external HD, and extended the FAT32 to cover the whole disk. I let it complete the task, but now when I check the free space, that 90Gb is still missing. I know I probably should have used a Windows partition editor, but there we go. Any suggestions for what I might be able to do/what the problem underlying this is? Is it the remnant filesystem from linux on the disk?

Thanks in advance for any help.

---

