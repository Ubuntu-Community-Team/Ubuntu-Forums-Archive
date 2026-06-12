---
title: "Complex multi-boot advice"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by kev51773 on 2009-11-02
Hi all,

I'm about to reinstall my main office PC and I want to try something a bit different. For years I've been booting single/multiple linux distros with a single Windows (XP or Vista)

What I'm trying to set up now is a single large drive with Ubuntu (and probably some other linuxes) and every version of Windows since XP (including 32/64 bit and basic/premium/business/pro K/KN Various service pack levels etc etc)

I haven't finished the list yet but I guess this is easily over 50 versions of windows plus I may want to add some windows server versions as well.

I'd like all of the Windows version to believe that they are installed on the C Drive and not see the partitions of the other OS's.

I can't use VM's as I need the full performance. I only have space for 1x2TB harddrive as the rest of the PC is filled with a SAS array.

Any thoughts on where to start or if this is even possible?

---

### Post by oldfred on 2009-11-02
You will have issues with trying to have more than 3 windows installs in one hard drive as windows just about requires a primary partition and you can only have 4 primary but if you want more than 4 you convert one primary to an extended and install logical partitions.

Herman had some info on a work around for windows but I do not remember where on his site. Also Vista and Win Seven seem to work from an extended partition if you have a windows in a primary as they combine the boots into the primary and chainload into the extended.

More info:

chainboot 145 systems
[http://www.justlinux.com/forum/showt...282#post861282]("http://www.justlinux.com/forum/showthread.php?p=861282#post861282")

Herman on multibooting and lots of other info:
[http://members.iinet.net.au/~herman5...rub_Partition_]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_")

---

