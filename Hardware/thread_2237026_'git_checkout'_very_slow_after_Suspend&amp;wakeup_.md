---
title: "'git checkout' very slow after Suspend&amp;wakeup on SSD disk"
date: 2014-07-30
forum: Hardware
---

### Post by Peter Vojtek on 2014-07-30
hello,

I updated this post as I gathered more info. 
the original subject " 'git checkout' very slow after Suspend&wakeup on SSD disk"   should be renamed to "write to SSD disk slow after suspend & wakeup", however it does not seem to be possible to rename the thread name in ubuntu forums.

So the point is following:
When I make a fresh boot on my notebook to Ubuntu, SSD writing speed is normal:
 dd if=/dev/zero of=speed_test bs=10M count=10
104857600 bytes (105 MB) copied, 0,549743 s, 191 MB/s

Then I enter sleep and wakeup.

After then the SSD write speed drops badly:
dd if=/dev/zero of=speed_test bs=10M count=10
104857600 bytes (105 MB) copied, 108,623 s, 965 kB/s
 
I can confirm via iotop that no other app is influencing the dd-based test.

OS: ubuntu 14.04 
Linux 3.13.0-24-generic #47-Ubuntu SMP i686 i686 i686 GNU/Linux
notebook dell E7440
hard drive: SAMSUNG SSD PM841 mSATA 256GB

---

### Post by Peter Vojtek on 2014-08-05
I also tried following approach, but no improvement:
[http://superuser.com/a/623808](http://superuser.com/a/623808)

---

### Post by sillyxone on 2014-10-24
Not sure if this is relevant, but I also experienced the same problem lately with the same drive on the same e7440. At first I thought it's due to suspend/wakeup, but I eventually running into slowness after a long period of use without suspend/resume. I found what works is to drop the filesystem cache as it got built up overtime and reached its max. Just try this command and see if it will work for you:

sync; echo 3 | sudo tee /proc/sys/vm/drop_caches

I still don't have an explanation, this is my first SDD drive so I can't tell if it's this particular drive. Basically I now have to drop the caches once in a while or the SSD will become slow. I've also tried other things (e.g. fstrim, date=writeback, ...) that don't seem to have any effect.

---

### Post by Peter Vojtek on 2014-10-28
sillyxone, thanks for feedback.
I confirm your approach works for me.
I also confirm the slowness occurs without suspend/wakeup - all I need to do is to I remove the notebook from docking station and then plug it back to docking station.

---

### Post by sillyxone on 2014-10-31
just found that external HDD got affected too, then stumbled across this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta-lts-trusty/+bug/1333294](https://bugs.launchpad.net/ubuntu/+source/linux-meta-lts-trusty/+bug/1333294)

So, it's well known and has been reported. According to a comment in the bug report, "echo 1" (dropping just the page cache) is probably good enough instead of "echo 3". I'm testing out different drivers for 64-bit Ubuntu as Darktable keeps showing me the skull, perhaps this is another reason for me to make the jump.

---

