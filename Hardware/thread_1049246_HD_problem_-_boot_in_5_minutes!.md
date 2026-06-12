---
title: "HD problem - boot in 5 minutes!"
date: 2009-01-24
forum: Hardware
---

### Post by GhostBunnies on 2009-01-24
Hello,

I've recently bought an HP Compaq 6715s laptop, here are some specs:

[LIST]
[*]AMD Sempron 3800+
[*]ATI Radeon XPress 1250 (X1250)
[*]2 GB. RAM
[*]80 GB. HD 5400 rpm SMART SATA
[/LIST]

I've finally succeeded to install Ubuntu 8.10 with "noacpi noapic nolapic".

But now, the system is really slooow.

It takes almost 5 minutes to boot.

It gets stuck here:

```
Boot from (hd0,0) ext3 480db1ea-76f0-49e4-b3f9-8efd0bd7b124
Starting up ...
Loading, please wait ...

```

Then, once the system is running I tested the HD:

```
sudo hdparm -t /dev/sda

/dev/sda:
Timing buffered disk reads: 10 MB in 3.12 seconds = 3.20 MB/sec
```

This is quite problematic.

Does anyone have a clue about how to fix this?

I really need some help - thanks a lot!

---

### Post by GhostBunnies on 2009-01-24
No ideas? :(

---

### Post by toocer on 2009-01-30
Hi

to the boot kernel add nohz=off it works for me. I got a HP 6715s that works perfectly with Ubuntu, (writing from it now) But without the nohz=off in the kernel boot then the computer is realy slow.

And a second tip is to search the forum. this question has been asked before.


```
/dev/sda:
 Timing buffered disk reads:  150 MB in  3.03 seconds =  49.46 MB/sec
```

---

