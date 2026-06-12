---
title: "Suspend2Ram on Thinkpad R50e"
date: 2006-05-29
forum: Hardware &amp; Laptops
---

### Post by mula on 2006-05-29
It has been already a quite a long time since I got stuck with this issue. I just can't get suspension working without problems on IBM Thinkpad R50e.

I followed both these instructions:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_R50e#Standby.2C_Sleep_and_Hibernation](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_R50e#Standby.2C_Sleep_and_Hibernation)
[http://www.kaltertee.de/index.php?current=linux](http://www.kaltertee.de/index.php?current=linux)
Neither of them works. Laptop goes successfully into a suspend mode but is unable to wake up.

I looked through the forum but unfortunately, I didn't find any promising replies..
I'm just desperately asking: is there anyone here with a Thinkpad R50e who got suspend2ram working under Breezy/Dapper? If yes, how?

I am not sure if that changes anything but I know that configuration of this laptop varies from country to country. Mine has a *Pentium M *processor with* Intel Extreme Graphics* card.

---

### Post by apastuszak on 2006-05-29
I have a Thinkpad R50 with only 256 MB of memory, and I manage to get the laptop to suspend without issue and it even wakes up without issue.  My problem is that invariably the thing locks up about 2-3 minutes after it wakes up.  My mouse is responsive, but I can't click on anything.  It's like X is completely frozen other than the mouse.  I end up having to power cycle the machine in order to get it to work again.  I had this same issue with Suse 10.0, 10.1 and Fedora Core 5, so I don't think the issue is unique to Ubuntu.

Andy

---

### Post by Nomadadon on 2006-05-30
I have the same issue.  All looks well after it awakes for about 2-5 minutes then i get a considerable number of disk errors:

hda: task_in_intr: status=0x59 {DriveReady SeekComplete DataRequest Error }
hda: task_in_intr: error=0x10 {SectorIdNotFound}, LBAsect=XXXXXXXXXX, sector=xxxxxxxx
ide: failed optcode was: unknown

---

### Post by slimdog360 on 2006-05-31
I had the same issue when I ran the live cd on my R50e. I could turn off the screen and back on again no problems, but when I put it into suspend it stayed there.

---

### Post by mula on 2006-06-01
It seems that it's more a trend than an exception. I wonder where the problem hides...
Hopefully, we'll have a solution soon.

---

