---
title: "Replacing hard drives, wanting to merge four into two"
date: 2019-02-04
forum: Hardware
---

### Post by Keith_Beef on 2019-02-04
After not touching my old and in many ways "main" computer for some months, I booted it up about a week and a half ago to rip some recently bought CDs to keep the music on the NAS. And there, I ran into a problem that had been intermittent, but is now worrying: one of the four Seagate 160GB mechanical hard drives is failing.

These drives are probably around ten years old, and I have decided to replace them.

I've got two brand new 500GB SSDs, and I'm wondering about the "best" method for moving the partitions that are on the four 160GB discs onto the new SSDs.

Is it possible, for example, to connect the SSDs through a USB adapter, use GParted to set up partitions, then use dd to copy from the old drives to the SSDs?

---

### Post by #&amp;thj^% on 2019-02-04
Here is some food for thought: [https://www.makeuseof.com/tag/2-methods-to-clone-your-linux-hard-drive/](https://www.makeuseof.com/tag/2-methods-to-clone-your-linux-hard-drive/)
> Is it possible, for example, to connect the SSDs through a USB adapter,
This how I do it.^^^^^^^^^, Or even a docking bay.
Good Luck

---

### Post by oldfred on 2019-02-04
You cannot use dd as that is an image copy. Or you only get the partition(s) you have on existing drive and cannot reconfigure.
But you can just use cp -a or rsync with various parameters to copy data with ownership & permissions intact. But must have folders mounted and your ownership & permissions set.

Only if installing Windows in the now 35 year old BIOS/MBR configuration should you use MBR(msdos) partitioning.
But to use new gpt, you have to select that first in gparted.

If drive will ever get moved to a new UEFI system and be a boot drive, you may want to include both a bios_grub partition (1 or 2MB unformatted) for BIOS boot and an ESP (FAT32 300 to 600MB) for UEFI boot. 

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by #&amp;thj^% on 2019-02-04
oldfreds suggestions are probally the easiest to follow.
Just to "NOTE ONLY" I use "DCFLDD" a lot with no problems, this came with some hard learned lessons.
```


DCFLDD(1)                        User Commands                       DCFLDD(1)

NAME
       dcfldd - manual page for dcfldd (dcfldd) 1.3.4

SYNOPSIS
       dcfldd [OPTION]...

DESCRIPTION
       Copy a file, converting and formatting according to the options.

       bs=BYTES
              force ibs=BYTES and obs=BYTES

       cbs=BYTES
              convert BYTES bytes at a time

       conv=KEYWORDS
              convert the file as per the comma separated keyword list

       count=BLOCKS
              copy only BLOCKS input blocks

       ibs=BYTES
              read BYTES bytes at a time

       if=FILE
              read from FILE instead of stdin

       obs=BYTES
              write BYTES bytes at a time

       of=FILE
              write to FILE instead of stdout

              NOTE: of=FILE may be used several times to write

              output to multiple files simultaneously

       of:=COMMAND
              exec and write output to process COMMAND

       seek=BLOCKS
              skip BLOCKS obs-sized blocks at start of output

       skip=BLOCKS
              skip BLOCKS ibs-sized blocks at start of input

       pattern=HEX
              use the specified binary pattern as input

       textpattern=TEXT
              use repeating TEXT as input

       errlog=FILE
              send error messages to FILE as well as stderr

       hashwindow=BYTES
              perform a hash on every BYTES amount of data

       hash=NAME
              either md5, sha1, sha256, sha384 or sha512

              default  algorithm  is md5. To select multiple algorithms to run
              simultaneously enter the names in a comma separated list

       hashlog=FILE
              send MD5 hash output to FILE instead of stderr

              if you are using multiple hash algorithms you can send each to a
              seperate  file using the convention ALGORITHMlog=FILE, for exam&#8208;
              ple md5log=FILE1, sha1log=FILE2, etc.

       hashlog:=COMMAND
              exec and write hashlog to process COMMAND

              ALGORITHMlog:=COMMAND also works in the same fashion

       hashconv=[before|after]
              perform the hashing before or after the conversions

       hashformat=FORMAT
              display each hashwindow according to FORMAT

              the hash format mini-language is described below

       totalhashformat=FORMAT
              display the total hash value according to FORMAT

       status=[on|off]
              display a continual status message on stderr

              default state is "on"

       statusinterval=N
              update the status message every N blocks

              default value is 256

       sizeprobe=[if|of]
              determine the size of the input or output file

              for use with status messages. (this option gives you a  percent&#8208;
              age indicator) WARNING: do not use this option against a

              tape device.

       split=BYTES
              write every BYTES amount of data to a new file

              This operation applies to any of=FILE that follows

       splitformat=TEXT
              the file extension format for split operation.

              you  may  use  any number of 'a' or 'n' in any combo the default
              format is "nnn" NOTE: The split  and  splitformat  options  take
              effect

              only  for  output  files specified AFTER these options appear in
              the command line.  Likewise, you may specify these several times
              for for different output files within the same command line. you
              may use as many digits in any combination you would like.  (e.g.
              "anaannnaana" would be valid, but quite insane)

       vf=FILE
              verify that FILE matches the specified input

       verifylog=FILE
              send verify results to FILE instead of stderr

       verifylog:=COMMAND
              exec and write verify results to process COMMAND

       --help display this help and exit

       --version
              output version information and exit

       The structure of of FORMAT may contain any valid text and special vari&#8208;
       ables.  The built-in variables are used the  following  format:  #vari&#8208;
       able_name#  To  pass FORMAT strings to the program from a command line,
       it may be necessary to surround your FORMAT strings with "quotes."  The
       built-in variables are listed below:

       window_start
              The beginning byte offset of the hashwindow

       window_end
              The ending byte offset of the hashwindow

       block_start
              The beginning block (by input blocksize) of the window

       block_end
              The ending block (by input blocksize) of the hash window

       hash   The hash value

       algorithm
              The name of the hash algorithm

   For example, the default FORMAT for hashformat and totalhashformat are:
              hashformat="#window_start# - #window_end#: #hash#" totalhashfor&#8208;
              mat="Total (#algorithm#): #hash#"

   The FORMAT structure accepts the following escape codes:
       \n     Newline

       \t     Tab

       \r     Carriage return

       \\     Insert the '\' character

       ##     Insert the '#' character as text, not a variable

       BLOCKS and BYTES may be followed by the following  multiplicative  suf&#8208;
       fixes:  xM  M,  c  1,  w  2,  b  512,  kD 1000, k 1024, MD 1,000,000, M
       1,048,576, GD 1,000,000,000, G 1,073,741,824, and so on for T, P, E, Z,
       Y.  Each KEYWORD may be:

       ascii  from EBCDIC to ASCII

       ebcdic from ASCII to EBCDIC

       ibm    from ASCII to alternated EBCDIC

       block  pad newline-terminated records with spaces to cbs-size

       unblock
              replace trailing spaces in cbs-size records with newline

       lcase  change upper case to lower case

       notrunc
              do not truncate the output file

       ucase  change lower case to upper case

       swab   swap every pair of input bytes

       noerror
              continue after read errors

       sync   pad  every  input  block  with  NULs to ibs-size; when used with
              block or unblock, pad with spaces rather than NULs

AUTHOR
       Written by: dcfldd by Nicholas Harbour, GNU dd  by  Paul  Rubin,  David
       MacKenzie and Stuart Kemp.

REPORTING BUGS
       Report bugs to <nicholasharbour@yahoo.com>.

COPYRIGHT
       Copyright © 1985-2006 Free Software Foundation, Inc.
       This is free software; see the source for copying conditions.  There is
       NO warranty; not even for MERCHANTABILITY or FITNESS FOR  A  PARTICULAR
       PURPOSE.

SEE ALSO
       The  full  documentation  for dcfldd is maintained as a Texinfo manual.
       If the info and dcfldd programs are properly installed  at  your  site,
       the command

              info dcfldd

       should give you access to the complete manual.

dcfldd (dcfldd) 1.3.4            February 2006                       DCFLDD(1)

```
Admitting "rsysnc" I don't use, just old habits i have become comfortable with.

>  I'm wondering about the "best" method for moving the partitions that are on the four 160GB discs onto the new SSDs.
[B]Replacing 4 x 160gig drives=640 or 320Gigs for the 2 160Gig failing drives
With 2 X 500gigs=1000gigs[/B]
Forgive me if I'm not understanding the request fully. (And correct me if I'm wrong)

---

### Post by C.S.Cameron on 2019-02-04
I use GParted right click copy/paste to copy partitions.

---

### Post by Keith_Beef on 2019-02-09
Thanks for your help, 1Fallen, OldFred and C.S.Cameron.

This is going to be quite a long post... tl;dr version is: used GPartEd copy and paste, and now it looks stuck part way through pasting onto the new drive.



Long version:

Disc replacement

Four existing Seagate 160GB discs

Two new Samsung 500GB discs
The idea is to connect each of the old discs in turn, and copy the partitions to a new disc.

So, removed the old discs.

Connected the first old disc and the first new disc each to a USB adapter.
USB stick containing a bootable Debian is connected to a USB port, and the computer BIOS is configured to boot from USB.

Power on, wait for Debian to boot.

Connect the first old disc and the first new disc, and start GPartEd.

$ lsblk
NAME	MIN:MAJ	RM	SIZE	RO	TYPE 	MOUNTPOINT
[stuff about sda (USB stick with debian)]
sdg		8:96	0	465.8G	0	disk
[stuff about sr0 and sr1, which are optical drives.]

So, it doesn't see the Seagate drive. Neither does GPartEd.

Try a different Seagate drive: 6PT5T9KB. No change.

I don't hear the discs spin up, don't feel any vibration... Maybe they are not getting enough power?
Tried on the USB port on the back of the computer (mainboard port) in the hope that this gets more power... nothing.
Third and fourth discs, the same.

SATA discs are meant to be hot-swappable, so I take the old disc and connect it to the cables in the computer. I hear it spin up and it appears in lsblk and in GPartEd as /dev/sdf with two partitions.

OK, sdf and sdg are visible... try using GPartEd to copy partitions...
But which type of partition table? Try gtp.
Make a partition table (gpt type), copy partitions:
	/dev/sdf1 to /dev/sdg1 (251.0 MiB)
	/dev/sdf2 to /dev/sdg2 (148.8 GiB)

This leaves 316.71 GiB unallocated.

GParted starts preparing the disc, copies /dev/sdf1  successfully.

It does en e2fsck on /dev/sdf2 and begins copying, but gets stuck while in e2image -ra -p /dev/sdf2 /dev/sdg2.

The interface to GpartEd seems hung. Looking at dmesg reveals some problems.

```
# dmesg | tail -n50
[ 4917.759687] Buffer I/O error on dev sdf2, logical block 1960004, async page read
[ 4917.759689] Buffer I/O error on dev sdf2, logical block 1960005, async page read
[ 4917.759691] Buffer I/O error on dev sdf2, logical block 1960006, async page read
[ 4917.759693] Buffer I/O error on dev sdf2, logical block 1960007, async page read
[ 4917.759699] Buffer I/O error on dev sdf2, logical block 1960000, async page read
[ 4917.759701] Buffer I/O error on dev sdf2, logical block 1960001, async page read
[ 4923.168312] buffer_io_error: 6902 callbacks suppressed
[ 4923.168314] Buffer I/O error on dev sdf2, logical block 1963456, async page read
[ 4923.168319] Buffer I/O error on dev sdf2, logical block 1963457, async page read
[ 4923.168321] Buffer I/O error on dev sdf2, logical block 1963458, async page read
[ 4923.168323] Buffer I/O error on dev sdf2, logical block 1963459, async page read
[ 4923.168325] Buffer I/O error on dev sdf2, logical block 1963460, async page read
[ 4923.168326] Buffer I/O error on dev sdf2, logical block 1963461, async page read
[ 4923.168328] Buffer I/O error on dev sdf2, logical block 1963462, async page read
[ 4923.168330] Buffer I/O error on dev sdf2, logical block 1963463, async page read
[ 4923.168336] Buffer I/O error on dev sdf2, logical block 1963456, async page read
[ 4923.168338] Buffer I/O error on dev sdf2, logical block 1963457, async page read
[ 4928.579893] buffer_io_error: 6934 callbacks suppressed
[ 4928.579895] Buffer I/O error on dev sdf2, logical block 1966928, async page read
[ 4928.579899] Buffer I/O error on dev sdf2, logical block 1966929, async page read
[ 4928.579901] Buffer I/O error on dev sdf2, logical block 1966930, async page read
[ 4928.579903] Buffer I/O error on dev sdf2, logical block 1966931, async page read
[ 4928.579905] Buffer I/O error on dev sdf2, logical block 1966932, async page read
[ 4928.579907] Buffer I/O error on dev sdf2, logical block 1966933, async page read
[ 4928.579909] Buffer I/O error on dev sdf2, logical block 1966934, async page read
[ 4928.579911] Buffer I/O error on dev sdf2, logical block 1966935, async page read
[ 4928.579917] Buffer I/O error on dev sdf2, logical block 1966928, async page read
[ 4928.579919] Buffer I/O error on dev sdf2, logical block 1966929, async page read
[ 4934.111219] buffer_io_error: 6934 callbacks suppressed
[ 4934.111222] Buffer I/O error on dev sdf2, logical block 1970400, async page read
[ 4934.111233] Buffer I/O error on dev sdf2, logical block 1970401, async page read
[ 4934.111235] Buffer I/O error on dev sdf2, logical block 1970402, async page read
[ 4934.111238] Buffer I/O error on dev sdf2, logical block 1970403, async page read
[ 4934.111240] Buffer I/O error on dev sdf2, logical block 1970404, async page read
[ 4934.111242] Buffer I/O error on dev sdf2, logical block 1970405, async page read
[ 4934.111245] Buffer I/O error on dev sdf2, logical block 1970406, async page read
[ 4934.111247] Buffer I/O error on dev sdf2, logical block 1970407, async page read
[ 4934.111257] Buffer I/O error on dev sdf2, logical block 1970400, async page read
[ 4934.111259] Buffer I/O error on dev sdf2, logical block 1970401, async page read
[ 4939.516797] buffer_io_error: 6918 callbacks suppressed
[ 4939.516800] Buffer I/O error on dev sdf2, logical block 1973864, async page read
[ 4939.516805] Buffer I/O error on dev sdf2, logical block 1973865, async page read
[ 4939.516807] Buffer I/O error on dev sdf2, logical block 1973866, async page read
[ 4939.516809] Buffer I/O error on dev sdf2, logical block 1973867, async page read
[ 4939.516811] Buffer I/O error on dev sdf2, logical block 1973868, async page read
[ 4939.516813] Buffer I/O error on dev sdf2, logical block 1973869, async page read
[ 4939.516815] Buffer I/O error on dev sdf2, logical block 1973870, async page read
[ 4939.516817] Buffer I/O error on dev sdf2, logical block 1973871, async page read
[ 4939.516823] Buffer I/O error on dev sdf2, logical block 1973864, async page read
[ 4939.516825] Buffer I/O error on dev sdf2, logical block 1973865, async page read
```

The disc had been making some click-clack whirr-whirr noises, but is 
now just quetly spinning.

# fdisk -l /dev/sdf
fdisk: cannot open /dev/sdf: No such file or directory
# smartctl -c /dev/sdf
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.9.0-8-amd64] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

Smartctl open device: /dev/sdf failed: No such device

It looks like /dev/sdf has simply disappeared from the system.


# ps -edf | grep parted
user      1939     1  0 12:29 tty2     00:00:00 /bin/sh /usr/bin/gparted-pkexec
root      1940  1939  0 12:29 tty2     00:00:00 /bin/sh /usr/sbin/gparted
root      1992  1940  0 12:29 tty2     00:00:00 /bin/sh /usr/lib/udisks2/udisks2-inhibit /usr/sbin/gpartedbin
root      1997  1992 34 12:29 tty2     00:30:34 /usr/sbin/gpartedbin
root      3433  3234  0 13:59 pts/1    00:00:00 grep parted
# ps -edf | grep e2image
root      3159  1997  0 13:17 tty2     00:00:11 e2image -ra -p /dev/sdf2 /dev/sdg2
root      3435  3234  0 13:59 pts/1    00:00:00 grep e2image

Looking again at dmesg, after leaving the computer alone for an hour and a half, I see:

```
# dmesg | tail
[14638.887404] Buffer I/O error on dev sdf2, logical block 5020088, async page read
[14638.887410] Buffer I/O error on dev sdf2, logical block 5020089, async page read
[14638.887412] Buffer I/O error on dev sdf2, logical block 5020090, async page read
[14638.887414] Buffer I/O error on dev sdf2, logical block 5020091, async page read
[14638.887416] Buffer I/O error on dev sdf2, logical block 5020092, async page read
[14638.887418] Buffer I/O error on dev sdf2, logical block 5020093, async page read
[14638.887419] Buffer I/O error on dev sdf2, logical block 5020094, async page read
[14638.887421] Buffer I/O error on dev sdf2, logical block 5020095, async page read
[14638.887427] Buffer I/O error on dev sdf2, logical block 5020088, async page read
[14638.887429] Buffer I/O error on dev sdf2, logical block 5020089, async page read
```

Earlier, those messages referred to logical block 1973865, and now up to 5020089... Does this mean that the computer is advancing through the logical blocks, trying to read them, and giving up after a certain number of tries?

Edit to add: dmesg now tells me:
[21639.548799] Buffer I/O error on dev sdf2, logical block 6624713, async page read

And I've even seen a little bit of reaction from GpartEd; though it's difficult to read (like the text has been written twice to the canvas, slightly shifted):
e2image: Input/output error reading block 563775

I wonder what till happen...

---

### Post by oldfred on 2019-02-09
With gpt you can only copy data, not partitions.
Gpt has primary partition table, backup partition table & each partition with GUIDs that must match. So if you attempt to copy a partition you will not have the match on GUIDs.
Better to just create partitions & rsync or cp data to new partition.

Often USB ports do not have enough power to spin up HDDs. I had same issue where my adapter cable would not work on a HDD, but worked with a SSD.

---

