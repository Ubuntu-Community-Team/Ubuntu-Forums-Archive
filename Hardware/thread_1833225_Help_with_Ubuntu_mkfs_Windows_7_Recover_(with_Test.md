---
title: "Help with Ubuntu mkfs Windows 7 Recover (with Testdisk)"
date: 2011-08-25
forum: Hardware
---

### Post by noobuntu80 on 2011-08-25
Hi Guys,

So I tried to be super techy and recover laptop data via [these instructions]("http://geekyprojects.com/storage/how-to-recover-data-even-when-hard-drive-is-damaged/comment-page-3/#comment-30268")  and ended up accidentally using the mkfs.ext3 command on /dev/sda which is my Windows 7 primary hard drive.  I realized this 3 seconds into entering the command and shutoff the PC.

I am hoping I can still recover my data - I have the ubuntu 11.04 rescue cd with test disk.  

Here is what sudo cat /proc/partitions shows:


7      0       207984 loop0
8     0   976762584 sda
8     1          40129 sda1
8     2     11102208 sda2
8     3    965617664 sda3


I ran a quick and deep testdisk analyse which I have:

1 P FAT16 >32M    0       1   1         4   254  60      80259 [DellUtility]
2 P HPFS - NFTS    5      25  21  1387    66   23    22204416 [Recovery]
3 * HPFS - NFTS   1387  66 24   121601  25  24 1931235328 [OS]

When I hit 'P' on [OS] it shows:

No file found. filesystem seems damaged


At this point I don't want to guess and try to fix things and then make everything worse.  

Right now when I boot the PC it just comes to a black screen with a blinking cursor.

Should I:

[LIST]
[*]run testdisk deep scan again?
[*]Use windows 7 recovery disk?
[*]Purchase getdataback nfts?
[*]Something else?
[/LIST]

This is a dell studio xps with Windows 7 64.  Thank you for your help!

---

### Post by Basher101 on 2011-08-25
First try to boot a live cd and try to copy as many files as possible to an external HDD (or alot of DVDs, whatever media you have) and then reinstall everything completeley. If you cant copy it then you're out of luck..

---

### Post by coffeecat on 2011-08-25
I think this is the important bit:

> **noobuntu80 said:**
> 
No file found. filesystem seems damaged

It sounds as though the NTFS filesystem has been partly overwritten and the ext3 filesystem only partly created, not that the ext3 filesystem would have been any use because it would have no record of your data.

Testdisk is unlikely to recover the partition because the filesystem is too damaged. However, with testdisk comes photorec which you can use to recover files of certain types:

> PhotoRec is file data recovery software designed to recover
 lost pictures from digital camera memory or even Hard Disks.
 It has been extended to search also for non audio/video headers.
 It searchs for following files and is able to undelete them :
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

Have a look here:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Scroll down past the testdisk instructions to where it describes how to use photorec. You should be able to rescue many of your files but be warned. It will try to rescue everything it finds and you will end up with probably tens of thousands of files with seemingly arbitrary filenames. Sorting through that lot will be tedious.

There are also some alternatives to photorec described in that link.

---

### Post by noobuntu80 on 2011-08-25
Great thanks for your help!

I think I'll follow what you suggested, it sounds like what I feared was true - can't fix the boot / mbr / partition (whatever is wrong) and just boot back normally.

Time to get to work

---

