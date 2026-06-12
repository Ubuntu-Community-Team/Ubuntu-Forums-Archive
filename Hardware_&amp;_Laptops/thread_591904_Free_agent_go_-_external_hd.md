---
title: "Free agent go - external hd"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by 18nikko on 2007-10-25
Hi,
I just bought a Seagate FreeAgent Go external usb 2.0  hard drive. My first instinct was to try
the good ole "plug and pray", plugged it in and no go, the drive is not recognized. I did my usual
searches on google and found a couple of threads addressing the issue. The main problem is it comes formated as ntfs. I have installed ntfs-3g and ntfs-config, and configured it to write to external drives, but no go. when I plug in the drive is not mounted. I can force it to mount  
using 
sudo mkdir /media/sdg1
sudo mount -t ntfs-3g /dev/sdg1 /media/sdg1 -O defaults,force umask=0

but the forcing part makes me very uncomfortable, and it doesn't spring up a cute little icon when I plug it in. Some posts have suggested reformatting to fat32 or ext3, I would like to use it as is out of the box. I switch computers a lot between xp,  ubuntu, and fedora at work and home. Incidentally it is recognized without problems on fedora 7, and I am using ubuntu gutsy at home.

Now provided I can get it to automount when I plug it in there seems to be another problem with this disk have an auto spindown "feature". There are two solutions I have found to this and I am curious as to which is the preferred solution. The first is from 
 [http://ubuntuforums.org/showthread.php?t=494673](http://ubuntuforums.org/showthread.php?t=494673)
which says to write a new udev rule that calls a script that will allow restarting. This seems like a hack, is there a more elegant way? the other solution at
[http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent](http://www.nslu2-linux.org/wiki/FAQ/DealWithAutoSpinDownOnSeagateFreeAgent)
requires installing sdparm and using 
 sudo sdparm --clear STANDBY -6 /dev/sdg

I am not sure if this needs to be done once, or every time it spins down. Also it is not clear how to automate this.

SO does anyone have a clear solution how to get this sucker working properly? or am I better off reformatting to fat32 and just implementing the 'allow restart' hack. Thanks for bearing with my long post.

Nicholas

---

### Post by 18nikko on 2007-10-27
Bumping this back up.
Even pointers to something I might have missed is helpful

---

### Post by alanpotpot on 2007-12-02
I also have the same problem with seagate's hibernate/sleep/spindown feature. I need to unmount it then remount it. The weird thing is the fat32 partition in that same drive works ok. The ext3 partition is the only one having problems.

---

### Post by Dan Tull on 2007-12-04
I found a way around this which seems to be persisting.  It unfortunately (for now) requires use of the software that comes with the drive, which requires having a way to boot into Windows for a bit.  

However, I think after reading this list that the allow-restart option might actually be a better solution if there was less troublesome way of setting it.  I've bookmarked that to revisit at some point, but for now my drive seems to be behaving now (though it never spins down -- I'm not sure how I feel about that part).

[http://ubuntuforums.org/showthread.php?p=3889580#post3889580](http://ubuntuforums.org/showthread.php?p=3889580#post3889580)

DT

---

