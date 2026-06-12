---
title: "dm-cache creation errors under dmsetup"
date: 2014-10-20
forum: Hardware
---

### Post by WinEunuchs2Unix on 2014-10-20
Using the Dell instructions from December 2013 found here: [http://en.community.dell.com/techcenter/extras/m/white_papers/20438199](http://en.community.dell.com/techcenter/extras/m/white_papers/20438199)

a cache meta file and cache block file were setup on /dev/sdb1 which is 11GB of a 30GB SSD.  The other "invisible" 19GB of the SSD are an Intel RST RAID 0 used for Intel SRT caching under Windows and supported by Firmware/Hardware Hybrid.

The only deviation from the instructions is a new 100GB partition was NOT created but rather an existing partition /dev/sda5 (about 250GB ext4 format--most of it empty) was used.  Also note that partion /dev/sda5 is mounted because that is where the system boots.

The following error message was encountered when trying to marry the origin device (sda5) to the caching block and caching meta data:

```

[FONT=arial]rick@Dell:~$ sudo dmsetup create dmcache0 --table "0 420388672 cache /dev/cache/meta /dev/cache/block /dev/sda5 512 1 writeback default 0"[/FONT]
[FONT=arial][sudo] password for rick: [/FONT]
[FONT=arial]device-mapper: reload ioctl on dmcache0 failed: Device or resource busy[/FONT]
[FONT=arial]Command failed[/FONT]
[FONT=arial]rick@Dell:~$ [/FONT]

```

It's very important to get caching working (either in dmcache, flashcache, lvmcache, enhanceio or bcahce) because the i7 is painfully slow compared to Windows 7.  For example 45 seconds to boot versus 14 seconds.  15 seconds to load goggle chromium versus 2 or 3 seconds to load Google Chrome on Windows.

Could dmraid which is automatically supported in the kernel using ddf and imsm be slowing things down on the RAID side?  Note that with Intel RAID accelerated or decelerated under Windows doesn't seem to impact speed in ubuntu 14.04.1 Kernel 3.17.1, 3.16.3, 3.13.32, 3.13.36(?).  Decelerated HDD (ie not being cached) within Windows only slows Windows down to Linux speeds.

Best-guesstimate are 10 million laptops like this Dell Inspiron 17R 7720 SE circa 2012 (including other high-end ones built afterwards).  Intel, Dell and Ubuntu should ALL like to see this working.

Sadly the 7 y/o old Toshiba L-300 Centrino Dual Core @ 2Ghz and 4GB RAM boots faster than the Dell with 3.2Ghz 8 Virtual Cores and 8GB RAM.

Any and all comments are welcome.  What feels like hundreds of sites / messages have already been googled over the last month and a hundred more is no problem to the tenacious.

---

### Post by WinEunuchs2Unix on 2014-10-26
Still on-going research here--not to be construed as a *bump*. Inserted two lines of code (in bold) within /usr/share/initramfs-tools/init for better readability and correct random "done" message:

```

maybe_break premount
[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/init-premount"
run_scripts /scripts/init-premount
[ "$quiet" != "y" ] && log_end_msg


maybe_break mount
log_begin_msg "Mounting root file system"
**_log_msg "\n"**
. /scripts/${BOOT}
parse_numeric ${ROOT}
maybe_break mountroot
mountroot
**log_begin_msg "End Mounting root file system"**
log_end_msg


maybe_break bottom
[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/init-bottom"
run_scripts /scripts/init-bottom
[ "$quiet" != "y" ] && log_end_msg

```

Without the inserted lines the boot messages are confusing because local-top, local-premount and local-bottom scripts get jumbled inside the two inserted lines.

The "quiet" variable is not tested because "log_begin_msg" calls "_log_msg" which checks "quiet" variable.

To see the messages at human readable speeds tips other people's tips on kernel option were used:

"noquiet nosplash noresume loglevel=3".

---

### Post by WinEunuchs2Unix on 2014-10-28
It appears from: [https://swrveengineering.wordpress.com/2014/10/14/how-we-increased-our-ec2-event-throughput-by-50-for-free/](https://swrveengineering.wordpress.com/2014/10/14/how-we-increased-our-ec2-event-throughput-by-50-for-free/) that Enhance-IO is faster and easier than dm-cache.

I know that mdadm is preferred to dmraid by Intel but I don't see them coming out with an accelerate button in Linux.

I know that LVM2 cache is preferred to dm-cache in the future but the future has yet to arrive.

Here: [https://wiki.archlinux.org/index.php/EnhanceIO](https://wiki.archlinux.org/index.php/EnhanceIO) they say Enhance IO might not be supported anymore but the last support 5 months ago is better than dm-cache support years ago.  I appreciate dmraid, dmsetup and dm-cache are rolled into the kernel but there are little real world examples (that my good, bad or ugly google skills have) found.

I think EnhanceIO might be a lot easier at this given juncture.

google chromium is taking about 25 seconds to restore in Kernel 3.17.1 but only takes 2 to 3 seconds in Windows 7 with Intel Smart Response Technology (SRT) active under Intel Rapid Start Technology (RST).  SSD caching of the HDD really does work in the real world.  Additionally the ArchWiki link above include instructions for booting off the cache, if you figure out where mkinitcpio is, so that is very promising under enhanceio too.

---

### Post by WinEunuchs2Unix on 2014-10-29
Well THAT was an exciting trip.  Couldn't download enhanceio from github because my user id didn't match ssh.  Manually downloaded but then it wouldn't compile because of Kernel 3.17 change for wait_on_bit_lock and control table becoming a structure.  Had to type in a bunch of c-code.

Used dkms to compile according to instructions here: [http://sindzinski.de/content/enhanceio-ssd-caching-ubuntu-1304](http://sindzinski.de/content/enhanceio-ssd-caching-ubuntu-1304)

dkms means you won't have to recompile manually with each kernel update.

Google chromium loads in 2 to 3 seconds instead of 15 to 25 seconds (depends on how many tabs are being restored from last session). Performance is just like Intel RST under Windows with added benefit of statistics in enhanceio that intel doesn't provide in the console software (I hear it is available in the command line but I don't have that program installed).

Unlike bcache you don't have to reformat your create new partition types for your data.  Unlike flashcache, lvm and dm-cache, enhanceio works on mounted partitions.  Also unlike dmraid, dmsetup, dm-cache, enhanceio is persistent and deadly simple.

I went with write through performance because there are some myths / bug reports floating around about write-back caching.

After a month of research, I'm almost there.  The next step is to cache the boot up process.  Life is good again :)

Marking as [solved]

---

