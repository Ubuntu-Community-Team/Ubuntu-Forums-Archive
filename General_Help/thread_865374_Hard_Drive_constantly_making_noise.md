---
title: "Hard Drive constantly making noise"
date: 2008-07-20
forum: General Help
---

### Post by grebarton on 2008-07-20
I have a brand new install of Ubuntu 8.04 and I have just added all the home based files, pics and music I usual need.

Apart from a few basic programs installed in the usual way nothing has changed.

However even though I am doing nothing with the computer actively and the Ram is only 10% used as is the processor the hard drive is constantly making a ticking noise as though something is being read.

Any ideas how I can calm the hard drive down and stop it annoying me?

Thanks

---

### Post by louieb on 2008-07-20
I've seen tracker cause the hard drive to spin when its indexing. Seem to remember seeing  other programs mentioned as the cause. Can't remember just what. Do a forum search on hard drive noise and see what other came up with. It's just a stop this program and see what happens type of fix.

---

### Post by songshu on 2008-07-20
a ticking hard drive?????

one tip.
backup now!!

---

### Post by grebarton on 2008-07-20
well no not exactly ticking but you know when you can hear it writing or reading in little bit, its like that almost constantly.

The hard drive is fairly new and its my second like it and have always been reliable before and this has never happened in either linux mint or fedora before which makes it weirder.

---

### Post by Vivaldi Gloria on 2008-07-20
Install

```
sudo apt-get install smartmontools
```

Then check the health status of your disk

```
sudo smartctl -H /dev/sda
```

Hope that you get the result "PASSED".

See 

```
man smartctl
```

for more info.

EDIT: This is a desktop hard disk, right?

---

### Post by agfa on 2008-09-26
I had the same probleme and i was dicided to reinstalling , so i played all for one.

Open a terminal and type "top" you eill then see the processes that are using the processor, and gess what it was   mythtv that was using 0.0 to 0.5% of the processor.For me it was process 6017 so i opened another terminal and type "sudo kill 6017" then type the password and presto my HDD stopped ticking, and i did not have to reinstall because i deinstall mythtv.

Good luck!!

---

