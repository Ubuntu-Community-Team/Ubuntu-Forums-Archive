---
title: "utf8 for FAT32 mounted file systems ??"
date: 2008-10-04
forum: General Help
---

### Post by gpsmikey on 2008-10-04
Greetings all -- I have a question -- I have a FAT32 partition that I am mounting from the FSTAB along with the other file systems under Hardy 8.04 Server.  All the indications I have found from reading says it should be mounted with the option "iocharset=utf8", however, when I boot, I get a warning message about using that.  Is this a problem??  Below is the warning message I get at boot time as well as the portion of my FSTAB with the mounts in it:
---------------
boot warning ...
[COLOR="Red"]FAT: utf8 is not a recommended IO charset for FAT filesystems, 
     filesystem will be case sensitive![/COLOR]

From my FSTAB ...


# mikey add ---
#
# sdb1 - 150 gig photo storage partition
/dev/sdb1 /samba/photo ext3 nodev,nosuid 0 2
#
[B]# sdb2 - 100 gig backups partiton - FAT32
/dev/sdb2 /samba/backups vfat iocharset=utf8,umask=000 0 0[/B]
#
# sdb3 - 250 gig /home partition
/dev/sdb3 /home ext3 nodev,nosuid 0 2

---------
Searching the forums and the rest of the Google world does not return a consistant answer as to how a FAT32 partition should be entered into the FSTAB.  

Any enlightenment much appreciated !!  ](*,)

mikey

---

### Post by gpsmikey on 2008-10-05
Well, I see nobody wants to jump on this :-)

From additional searches, it looks like the answer is either "42" or "dr. dr. it hurts when I do this ... then don't do that".  Below are a number of links I found that discuss this problem and it seems there is no "one size fits all" solution for the VFAT filename and iochar set issue.  Anyone interested in reading up on this, check on the links below (note that this is also documented somewhat in the vfat.txt from the kernel docs).

Hopefully this will save someone else some search time - even if there is no clear answer !!

Some interesting discussions on this issue:

Debian bug report discussing this issue:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=443514](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=443514)
[https://launchpad.net/ubuntu/+bug/62321](https://launchpad.net/ubuntu/+bug/62321)

This one discusses the issue in the "How to Mount FatFileSystems"
[http://www.nslu2-linux.org/wiki/HowTo/MountFATFileSystems](http://www.nslu2-linux.org/wiki/HowTo/MountFATFileSystems)

This one concludes that unless you are using funny punctuation/chars
in the file names, it is not needed:
[http://www.linux.net.nz/pipermail/nzlug/2006-August/005606.html](http://www.linux.net.nz/pipermail/nzlug/2006-August/005606.html)

This one thinks it is a bug to have that as a default:
[http://sidux.com/PNphpBB2-viewtopic-t-4787.html](http://sidux.com/PNphpBB2-viewtopic-t-4787.html)

This one discusses the vfat and conversion and concludes that the 
iocharset does NOT make sense and does not work as often expected:
[http://lkml.org/lkml/2006/7/13/63](http://lkml.org/lkml/2006/7/13/63)

See this link for an interesting discussion on why there is no
correct answer ?
[http://linux.derkeiler.com/Mailing-Lists/Kernel/2004-06/4755.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2004-06/4755.html)

This one talks about which charset to use (or not use) and points to
the vfat.txt documentation.
[http://cateee.net/lkddb/web-lkddb/FAT_DEFAULT_IOCHARSET.html](http://cateee.net/lkddb/web-lkddb/FAT_DEFAULT_IOCHARSET.html)

This one discusses this exact issue and points to the vfat.txt and kernel documentation as well as discussing the "shortname" option.
[http://ubuntuforums.org/showthread.php?t=137159](http://ubuntuforums.org/showthread.php?t=137159)


mikey

---

### Post by insane_alien on 2008-10-05
why on earth are you using FAT32? if you don't have to inteface with windows use ext3, if you have to interface with windows use NTFS. 

both of these filesystems are much much better and resistant to failure and corruption.

---

### Post by gpsmikey on 2008-10-05
> **insane_alien said:**
> why on earth are you using FAT32? if you don't have to inteface with windows use ext3, if you have to interface with windows use NTFS. 

both of these filesystems are much much better and resistant to failure and corruption.

Well, yes, both good points, however, I wanted a partition that
could be handled by windows, linux AND my backup software running from a stand alone boot disk (the fat32 partition is on a different drive from the OS that I would be backing up).  After looking at the various tutorials (psycocats etc) this was supposed to be quite simple.  Turns out everybody has a simple answer -- they just don't have the SAME simple answer !!  Time to re-evaluate what I want to do here, but I did want to post the info I found to hopefully help others going down the same path ( /primrose/primrose/primrose ... ) :-)

mikey

---

