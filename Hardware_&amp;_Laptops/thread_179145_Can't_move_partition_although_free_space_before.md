---
title: "Can't move partition although free space before"
date: 2006-05-19
forum: Hardware &amp; Laptops
---

### Post by Bazon on 2006-05-19
Hello!

I have 1.6GB free space before my systempartition, hda3:
[[img]http://img129.imageshack.us/img129/9459/screenshotgparted7yu.th.png[/img]](http://img129.imageshack.us/img129/9459/screenshotgparted7yu.png)

I'd like to move my systempartition this 1.6GB to the left and increase my home partition hda4 with that.

The problem is:

I'm not able to resize/move hda3 to the left, the free space before just isn't recognized!:
[[img]http://img124.imageshack.us/img124/8527/screenshotresizedevhda33rl.th.png[/img]](http://img124.imageshack.us/img124/8527/screenshotresizedevhda33rl.png)

I tried with gparted and the Breezy Live-CD (as seen in Screenshots) and as well with qparted on Knoppix, both have the same problem.

Any ideas?

What can I make to use this free space without greating a new partition??

Thanks,
Bazon

---

### Post by Sef on 2006-05-19
You can't add to a partition at the beginning, only the end.

---

### Post by Bazon on 2006-05-19
Thanks, that explains everything...

...so it's going to be a mighty reinstall + backup + playback session to use this space.... :x :wink:

(I need a lot of space on my home partition for kaffeine DVB-T timeshift recording which doesn't work on the vfat partition for strange reasons...)

---

### Post by comer on 2008-07-09
I google partition manager find some freeware bellow:

paragon  [http://www.paragon-software.com](http://www.paragon-software.com)
I have not used,no comment!

easeus partition manager 
I download from brother soft 
[http://www.brothersoft.com/easeus-partition-manager-51814.html](http://www.brothersoft.com/easeus-partition-manager-51814.html)

It worked OK, but failed when i tried to  merge partition. so i have to allocated the free space to another partition. Partition magic may merge two partitions which will cost you $69.95

cute partition manager
[http://www.giveawayoftheday.com/freeware/partition_download.shtml](http://www.giveawayoftheday.com/freeware/partition_download.shtml)

---

