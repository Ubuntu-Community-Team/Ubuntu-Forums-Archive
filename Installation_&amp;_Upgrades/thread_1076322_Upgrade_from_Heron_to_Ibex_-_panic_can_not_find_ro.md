---
title: "Upgrade from Heron to Ibex - panic can not find root"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by vuroth on 2009-02-21
MAYBE I did this to myself.

Set up the upgrade to run overnight.  This morning, it got to the reboot part, and seemed to lockup in etc/rc.local.  So I pressed my power button, and it seemed to continue.

However, on reboot, the new entry can not find the root task.

I'm downloading the Ibex install CD.  I'm hoping that I'll be able to run it, and recover my install.

Any advice or well wishes would be appreciated.

---

### Post by ajgreeny on 2009-02-21
I've never done an online upgrade of distro, so can't help there, but you should use the live CD downloaded together with a usb drive to make sure you have all your /home folder backed up before doing anything too drastic.  If you have a separate /home partition you will find life a lot easier, particularly if you do not already have a backup of all your own files and configs from /home, so think about doing that if you end up reinstalling the system.

---

### Post by vuroth on 2009-02-21
Thanks.  I *think* /home was seperate, but we'll find out soon enough.  :)

---

### Post by vuroth on 2009-02-21
Uhh.  This is not looking good.  Confusing.

When I try to install from live CD, it does not see any of my existing partitions, including the windoze one I'm running from now.  However, when I explore the file system on live CD, I can still see my home drive.

The (lilo? EDIT:  grub) commands at boot for the new install seem to look similar to the previous ones, however, they're missing the initrd commands.  Intended, or not?

I do NOT want to reformat the whole HD.

---

### Post by vuroth on 2009-02-21
Ok Windows Vista sees:

Its own C, D and F volumes
A 64GB partition
A 2.7 GB partition
A 2.5 GB partition

There's also an 80MB unallocated part.

gPartEd/Ubuntu install don't seem to see any of them.

Think I'll play with LiveCD some more.  Maybe there's something on that side I'm missing.

V

---

### Post by vuroth on 2009-02-21
Exact error indication:
> 
Starting up ...
(0.884092) Kernel Panic - not synching: VFS: Unable to mount root fs on unknown-block(0,0)

Extended, from recovery:
> Cannot open root device "UUID=blah" or unknown-bloc(0,0)
Pleaes append a correct "root=" boot option; here are the available partitions:
Kernel Panic - not synching: VFS: Unable to mount root fs on unknown-block(0,0)

---

### Post by vuroth on 2009-02-21
Could be relatedt to [http://ubuntuforums.org/showthread.php?t=944444&highlight=Kernel+Panic+synching%3A+VFS]("http://ubuntuforums.org/showthread.php?t=944444&highlight=Kernel+Panic+synching%3A+VFS")

Partitions ARE ext3.  Doesn't explain why I can't see them during an install.

---

### Post by vuroth on 2009-02-21
I guess I shout note that, if I use recovery from a previous version, fdisk seems to see the partitions ok.

---

### Post by vuroth on 2009-02-21
It would seem that the Dell (Inspiron 1720) partitions were the issue.  Unfortunately, I broke my windoze boot somehow fixing the partitions.

I also lost my previous linux install, in its entirety.

Think I'll make sure I have a separate /home partition next time.  In the meantime, this upgrade from Heron to Ibex was very much not worth the trouble.  :(

V

---

