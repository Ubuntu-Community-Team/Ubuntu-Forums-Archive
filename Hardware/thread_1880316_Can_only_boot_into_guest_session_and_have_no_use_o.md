---
title: "Can only boot into guest session and have no use of mouse or keyboard"
date: 2011-11-13
forum: Hardware
---

### Post by Green_Vigo on 2011-11-13
pretty sure i have some hdd problems. started when windows7 just wouldnt boot a few months ago. wiped it and installed ubuntu 11.10. had some weird stuff happen ended in me having to re/.install as wouldn-t boot past that ubuntu generic or ubuntu safey mode. was getting some inframs weird messages.

latest is that when it boots now i can only use touchpad - keyboard and mouse don't work. if i boot from livecd its fine. sometime try and access the hdd and it won-t let me mount it. gives me some message re> superblock. also seen stuff about I/O errors.

have done some reading and have read about some lines to put in terminal to give status - here-s some below. anyone any ideas?

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000effd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968388607   484193280   83  Linux
/dev/sda2       968390654   976771071     4190209    5  Extended
/dev/sda5       968390656   976771071     4190208   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6ad2f3be-68f8-45bd-bf3c-7644413862d8" TYPE="ext4" 
/dev/sda5: UUID="5aa243fc-e435-4adc-b76a-95c79969fc03" TYPE="swap" 
ubuntu@ubuntu:~$ sudo smartctl -t short /dev/sda1
sudo: smartctl: command not found
ubuntu@ubuntu:~$ sudo e2fsck -y -f -v /dev/sda1
e2fsck 1.41.14 (22-Dec-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  186226 inodes used (0.62%)
     431 non-contiguous files (0.2%)
     312 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 152269/169/7
 9936203 blocks used (8.21%)
       0 bad blocks
       5 large files

  119576 regular files
   21455 directories
      57 character device files
      25 block device files
       0 fifos
      10 links
   45102 symbolic links (33687 fast symbolic links)
       2 sockets
--------
  186227 files
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1: clean, 186226/30269440 files, 9936203/121048320 blocks
ubuntu@ubuntu:~$ ls -l /dev/*da*
brw-rw---- 1 root disk 8, 0 2011-11-13 15:23 /dev/sda
brw-rw---- 1 root disk 8, 1 2011-11-13 15:37 /dev/sda1
brw-rw---- 1 root disk 8, 2 2011-11-13 15:23 /dev/sda2
brw-rw---- 1 root disk 8, 5 2011-11-13 15:23 /dev/sda5
ubuntu@ubuntu:~$ 

Checked SMART data and get two warnings. Reallocated Sector Count and Current Pending Sector Count. 649 bad sectors in total it says.

Reallocated SC Values are
Normalized 100
Worst 100
Threshold 50
Value 627 sectors

Current pending sector count values
Normalized 100
Worst 100
Threshold 0
Value 22 sectors

---

### Post by 2F4U on 2011-11-13
Did you look into the log files such as dmesg, /var/log/Xorg.0.log?

---

### Post by Green_Vigo on 2011-11-13
No haven't done that as I'm not sure how to. Pretty new to ubuntu - tried dmesg|tail commands earlier but livecd told me i needed to be root. just tried it again and got this -

ubuntu@ubuntu:~$ dmesg|tail
[  210.528135] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  210.528137] cfg80211: Disabling freq 2484 MHz
[  210.528142] cfg80211: Regulatory domain changed to country: ES
[  210.528144] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  210.528147] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  210.528150] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  210.528153] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  210.528156] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  222.320060] wlan0: no IPv6 routers present
[ 1238.536174] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)



also tried / dmesg|var
No command 'var' found, but there are 19 similar ones
var: command not found
ubuntu@ubuntu:~$ 

and...

dmesg|log
No command 'log' found, did you mean:
 Command 'klog' from package 'openafs-krb5' (universe)
 Command 'klog' from package 'klog' (universe)
 Command 'klog' from package 'openafs-client' (universe)
 Command 'mog' from package 'mazeofgalious' (universe)
 Command 'vlog' from package 'atfs' (universe)
 Command 'logo' from package 'ucblogo' (universe)
 Command 'rlog' from package 'rcs' (universe)
 Command 'plog' from package 'ppp' (main)
 Command 'xlog' from package 'xlog' (universe)
 Command 'iog' from package 'iog' (universe)
 Command 'eog' from package 'eog' (main)
 Command 'flog' from package 'flog' (universe)
log: command not found

Oh, and thanks very much for the reply.

---

### Post by northd_tech on 2011-11-13
> **Green_Vigo said:**
> No haven't done that as I'm not sure how to. Pretty new to ubuntu - tried dmesg|tail commands earlier but livecd told me i needed to be root. just tried it again and got this -

ubuntu@ubuntu:~$ dmesg|tail

One thing about Ubuntu- if you get error messages about root (or sometimes file permissions) you sometimes need to use the command **sudo** (short for **S**uper **U**ser **DO**).  Consequently, the command in this case would be

**sudo dmesg | tail**

I really didn't think that **dmesg** needed SuperUser priveleges though, and it doesn't make any difference either way on my working Ubuntu Lucid Lynx 10.04.3 LTS.

All this sudo business is to protect people from themselves and to prevent them from REALLY screwing up their Ubuntu system(s).

You can read more about all this **sudo**, **gksu**, and **gksudo** business here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Back to your original issue, I noticed this part:

> 186226 inodes used (0.62%)
     431 non-contiguous files **(0.2%)**
     312 non-contiguous directories **(0.2%)**
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 152269/169/7
 9936203 blocks used (8.21%)
       **0 bad blocks**
       5 large filesThat low fragmentation level and NO bad blocks really doesn't look like a bad HDD to me.  Maybe it is just old & tired like my laptop HDD (which is still chugging along), but I've been very careful to back up everything **important** to external USB HDD and to **optical** (CD & DVD) WATERPROOF and NON-MAGNETIC media in duplicate.  I've just been jumping through some hoops trying to read/convert some 10-15 year old CD-R archives that aren't reading too well now- likely because of the 'cheap' media they were originally recorded on.  In fact, I might need to resurrect my old Windows 98 machine to read them on the original CD-RW drive that wrote them- perhaps there is a laser alignment issue or something like that.

I'm wondering if you installed from an iffy/flaky/scratched/bad LiveCD in the first place and something got mangled in your original install.  If that 'problem?' HDD doesn't have any IMPORTANT data on it, you might consider a **low-level format** or extensive disk-wipe (like I always recommend after a Windows virus infection rebuild/recovery).  

Then reinstall whichever Linux you prefer from a KNOWN GOOD LiveCD/DVD.  My most recent LiveDVD Ubuntu install performed a checksum test on the LiveDVD itself before installing (I know because I had attempted to 'insert' some Linux drivers and sourcecode into the .ISO file to 'fill up' the disk before burning and the install WOULD NOT run and exited due to the checksum error from my larger .ISO size).  

It might be better to borrow a KNOWN GOOD LiveCD from a friend who has already installed that same operating system (hopefully more than once) if you can't find a Live CD/DVD with a checksum verification or disk media/data test function.  Some Ubuntu versions will do a "disk media test" or something simialr 

Just beware that disk 'wipe' utilities are like firearms and explosives- THEY ARE INHERENTLY DANGEROUS and require EXTREME CAUTION and attention to detail!!!  This is why I'm not providing any links to disk wipe or low-level format programs in this post (it might get me in trouble on the forum here anyway).  I'm sure you could find at least 3 related tools if you search hard enough though.

---

### Post by Green_Vigo on 2011-11-14
thanks for the reply northd.

hdd not old - only bought the laptop last april. its a toshiba gmx55 something. agree that the two lots of results don't really match up but the behaviour plus the fact that SMART says 648 bad sectors means that's still the way I'm leaning. 

also, this all started when original win7 (that was loaded on machine when i bought it) just stopped booting. would just hang on completely black screen in boot. 

have now re-installed ubuntu - smart still says bad sectors..

---

### Post by northd_tech on 2011-11-14
Hi again GV-

If you're still worried about your 'Winchester' blowing up, I found a highly relevant discussion that even mentions SMART and 'imminent disk failure??' here- read the whole thread though **BEFORE doing** anything, and I'm not quoting any of the code here to stay out of trouble.

**Clean Hard Drive (zero fill)**  
[http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill](http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill)

Be sure to read the parts about various HDD manufacturers' utilities (which might possibly require one of Big Bill's operating systems to run if they aren't bootable .ISO files burned to CD/DVD or USB stick).

Here's your bit of computer archaic comptuter trivia for the evening:

[http://www.webopedia.com/TERM/W/Winchester_disk_drive.html](http://www.webopedia.com/TERM/W/Winchester_disk_drive.html)

As an aside, I really did NOT like the SMART cycle counts on my 3+ year old Western Digital 2500xx HDD when I recently ran some 'rescue' Linux utilities after losing **fstab**, **mtab**, and/or **GRUB2**.  It is running as good or better right now than it has been for months though (I cleaned off a Windows rootkit that had apparently buried itself in my HIBERFIL.SYS hibernate and PAGEFILE.SYS virtual memory Vista files- and that rootkit might be a large portion of the reason those HDD cycle counts are so high).  Interestingly, my GRUB & GRUB2 dual-booting of Ubuntu seems to have prevented this rootkit from mutating into a full-blown virus infection and loss of Windows Vista and/or data.  In fact, my Vista partition was actually working better than my Ubuntu one for about 8 days (I needed to boot from a LiveDVD to access my ext4 Linux partition).

The good news- my old 17-inch laptop has an **empty 2nd** HDD bay (now I just need to find a laptop HDD mounting bracket that is compatible with my old HP and a cheap deal on a good 750GB - 2TB HDD to slip in there so I can keep about 5 different backup Linux operating systems and maybe even FreeBSD! :D )

---

