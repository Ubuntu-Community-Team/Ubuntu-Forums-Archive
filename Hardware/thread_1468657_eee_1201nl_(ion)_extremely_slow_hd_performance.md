---
title: "eee 1201nl (ion): extremely slow hd performance"
date: 2010-05-01
forum: Hardware
---

### Post by g.st on 2010-05-01
don't get me wrong i'm perfectly aware that the hitachi 160gb drive here is inherently slow, but it seems that in lucid lynx the drive performance is far worse than in windows.

e.g.:
-  here i'm getting apparently only 10MB/sec max "bandwidth" copying files from external usb drives while in the same situation windows goes at least 2x
- you might suspect something about usb instead but no: copying few large files from one partition to the other have initially 1.1MB/sec throughput and after a while it drops to a "whopping" 0.6MB/sec.
- if i benchmark it in windows with hdtune i can get way higher bandwith (i don't even remember, over 40MB/sec anyway)

hdparm output seems ok to my eyes (nothing fishy, almost everything already set for best performance, AAM turned off, like in windows)

what's happening here?

does the nforce/ION chipset need some kind of special tuning to behave normally under linux?

i'm quite confortable with unicies, there's no problem for me to fiddle with it, let me know what i could check.

tyia :)

---

### Post by P4man on 2010-05-01
is this ubuntu 10.04 ? If so, go to system > adminstration > disk utility. Select your drive > benchmark. Lets see what that gives and find out if its a hardware/driver issue or a filesystem problem

---

### Post by g.st on 2010-05-01
thanks for the prompt reply :)

read only: 
minimum 20.4 maximum 64.9 average 49.2
avg access time: 18.5 ms

seems "normal"; why so slow (or: being reported as slow) with both nautilus copying and grsync? :confused:

maybe i should redo the same operation under windows and measure the actual time difference if any....

---

### Post by P4man on 2010-05-01
should be easy to spot the difference between 0.6 MB/s and anywhere near 60MB/s. Just copy a 100 or 600mb file (iso or something). Write caching might pollute the result though (and keep in mind it cant read and write from the same drive), so while doing that, have iotop running in a terminal. Install it from synaptic (or sudo apt-get install iotop).

I do suspect those numbers are correct though. Im just at a loss as to what causes them.

---

### Post by g.st on 2010-05-02
aaand yes, i get the same results when spying on the processes with iotop, if i copy a file on the same hd. 

moreover:

if i dump the data cat-ing it into /dev/null is blazingly fast (it seems to reach the benchmarked bandwidth) either reading from the ext4 and the ntfs partition - but i don't know if it counts.

similar test: writing a file on the disk reading from /dev/zero. i get 
- for ext4,  an apparently varying speed between 100 and 300 MB/s, i don't know that sounds pretty decent for a netbook use.
- for ntfs, a much slower 10MB/s performance.

in the end, apparently the problem i got was mainly because of 

- rather slow big-file writing performance with ntfs
- rather slow same-drive copying: 
  i get 1-1.6 MB/s speed reading and writing to ext4; this   
  surprises me, i was expecting much better performance since 
  the pc has 2GB of ram to use as cache (it could read the entire 
  file content in the "cache" and write it back). also, i can't 
  hear the hd head seek that much.


still something sounds wierd, i'm not entirely convinced. if i can i'll repost with more tests done.

for the meantime, thank you a lot.

---

### Post by P4man on 2010-05-02
writing to ntfs can be painfully slow at times (from linux). It also eats up a lot of cpu cycles. Have a look in top and see if its not your cpu bottlenecking you while writing to ntfs.

---

