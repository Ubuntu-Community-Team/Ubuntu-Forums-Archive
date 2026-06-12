---
title: "Constant HDD activity"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by robth on 2006-01-31
I've just installed Ubuntu 5.10 on my Toshiba M70-148 laptop. Currently I'm having constant, never ending HDD activity. The led keeps burning from the moment Ubuntu starts running.

Of couse I've read other threads regarding this topic but most threads talk about hdd beeps/scratching sounds but my hdd is not doing that. It's pure that it won't stop running.

During the install I let Ubuntu create a ext3 partition; I've already mounted it as ext2 to be sure it isn't a journalling problem. But when it's mounted as ext2 the hdd activity also *never* stops; not even for a second.

This is driving me kind of mad, the battery life is short also probably because of the constant activity.

Does anyone know a solution for this? And can you please tell me more about ACPI and stuff, to ensure a long battery life.

PS. I've got laptop-mode installed and when I run:
sudo laptop-mode start
cat /proc/sys/vm/laptop_mode reports 5; but still the HDD activity doesn't stop.

Running top revaels 96.7% idle; load average: 0.25, 0.21, 0.13.

I just don't know what to do now. Ow yeah, when I do a shutdown the HDD makes a stange noise as if it suddenly stops...

Thanks,
Rob

---

### Post by frodon on 2006-02-01
This guide may help you to check if it's an ext3 related problem : [http://www.ubuntuforums.org/showthread.php?t=107856](http://www.ubuntuforums.org/showthread.php?t=107856)

---

### Post by robth on 2006-02-07
OK, I fixed the problem. It seems there was a bug in libata causing the led to burn all the time; it is fixed in kernel 2.6.14.

Since I have some more problems I decided to give the latest stable kernel a shot and so I compiled 2.6.15.3 and now it works!

Thanks for the help though! :mrgreen:

---

### Post by bshephard on 2008-03-14
I seem to be having a similar problem but with a brand new install of gutsy with a few extra apps installed but I have managed to narrow the cause down to Myth TV as it stops when i uninstall it

I'm using a lenovo 3000 N100 laptop with a 120gb sata hdd

I haven't been able to see what happens after I run Myth TV for the first time as my Myth TV back end is on another machine on my network which had to be moved after the room it was in flooded 
I will test this as soon as i can get my plumbing sorted and put the room back together and post the results

If anyone has any ideas I'd be glad to hear them

Ben

---

### Post by wild_oscar on 2008-03-18
> **bshephard said:**
> I seem to be having a similar problem but with a brand new install of gutsy with a few extra apps installed but I have managed to narrow the cause down to Myth TV as it stops when i uninstall it

I'm using a lenovo 3000 N100 laptop with a 120gb sata hdd

I haven't been able to see what happens after I run Myth TV for the first time as my Myth TV back end is on another machine on my network which had to be moved after the room it was in flooded 
I will test this as soon as i can get my plumbing sorted and put the room back together and post the results

If anyone has any ideas I'd be glad to hear them

Ben

Thanks, Ben! The constant hdd activity was driving me nuts, I've just realized it was due to mythtv!

---

