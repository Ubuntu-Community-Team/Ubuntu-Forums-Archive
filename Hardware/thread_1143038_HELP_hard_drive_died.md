---
title: "HELP hard drive died"
date: 2009-04-29
forum: Hardware
---

### Post by Macrosystems on 2009-04-29
After restarting in XP (I dual boot), I get an error saying hal.dll is missing or corrupt. I tried to fix this using the recovery cd. Chkdsk reported unrecoverable errors, so I ran fixboot which only screwed the drive up more. Now I don't even get the grub boot menu, just NTLDR is missing. I checked the drive on another machine and it only shows a three mb partition with a strange bootex file when it's a 320gb drive. I just to recover my files and reformat. Any ideas what the problem is? Any way to get the files from my ubuntu partition off? Sorry if this is too windows related, I'm desperate...

---

### Post by coffeecat on 2009-04-29
You could boot up with a live CD and install testdisk to the live session - it's only about 1.5 MB. Before you do, search the forums because I believe there are some useful howtos and tutorials for testdisk. If you can't restore lost partitions, you might be able to find and copy data files with PhotoRec. In case you're having to post from another OS and haven't got a way to look in Synaptic, this is what is says about testdisk:

> TestDisk checks the partition and boot sectors of your disks.
 It is very useful in recovering lost partitions.
 It works with :
 * DOS/Windows FAT12, FAT16 and FAT32
 * NTFS ( Windows NT/2K/XP )
 * Linux Ext2 and Ext3
 * BeFS ( BeOS )
 * BSD disklabel ( FreeBSD/OpenBSD/NetBSD )
 * CramFS (Compressed File System)
 * HFS and HFS+, Hierarchical File System
 * JFS, IBM's Journaled File System
 * Linux Raid
 * Linux Swap (versions 1 and 2)
 * LVM and LVM2, Linux Logical Volume Manager
 * Netware NSS
 * ReiserFS 3.5 and 3.6
 * Sun Solaris i386 disklabel
 * UFS and UFS2 (Sun/BSD/...)
 * XFS, SGI's Journaled File System
 .
 PhotoRec is file data recovery software designed to recover
 lost pictures from digital camera memory or even Hard Disks.
 It has been extended to search also for non audio/video headers.
 It searchs for
 * Sun/NeXT audio data (.au)
 * RIFF audio/video (.avi/.wav)
 * BMP bitmap (.bmp)
 * bzip2 compressed data (.bz2)
 * Source code written in C (.c)
 * Canon Raw picture (.crw)
 * Canon catalog (.ctg)
 * FAT subdirectory
 * Microsoft Office Document (.doc)
 * Nikon dsc (.dsc)
 * HTML page (.html)
 * JPEG picture (.jpg)
 * MOV video (.mov)
 * MP3 audio (MPEG ADTS, layer III, v1) (.mp3)
 * Moving Picture Experts Group video (.mpg)
 * Minolta Raw picture (.mrw)
 * Olympus Raw Format picture (.orf)
 * Portable Document Format (.pdf)
 * Perl script (.pl)
 * Portable Network Graphics (.png)
 * Raw Fujifilm picture (.raf)
 * Contax picture (.raw)
 * Rollei picture (.rdc)
 * Rich Text Format (.rtf)
 * Shell script (.sh)
 * Tar archive (.tar )
 * Tag Image File Format (.tiff)
 * Microsoft ASF (.wma)
 * Sigma/Foveon X3 raw picture (.x3f)
 * zip archive (.zip)

Canonical does not provide updates for testdisk. Some updates may be provided by the Ubuntu community.

---

### Post by Macrosystems on 2009-04-29
Thanks for suggesting testdisk. It found the old ubuntu and windows partitions. Two problems though. When I enter p to list the ntfs windows partition I get a seg fault and it exits. And I can view the ext3 ubuntu partition; however, I can't seem to recover the files. How do you copy / rescue them? Thanks again.

---

### Post by coffeecat on 2009-04-29
You need photorec which comes with testdisk. Have a look at post #2 on this thread:

[http://ubuntuforums.org/showthread.php?t=1142358](http://ubuntuforums.org/showthread.php?t=1142358)

And the link that poster provides:

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

In your situation, running live from a CD, you'd have to plug an external drive in to write the recovered files to.

---

