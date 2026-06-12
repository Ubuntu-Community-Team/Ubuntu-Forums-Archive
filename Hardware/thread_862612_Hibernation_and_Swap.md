---
title: "Hibernation and Swap"
date: 2008-07-17
forum: Hardware
---

### Post by Zaff on 2008-07-17
Hi I didn't really know where i should post this so feel free to move it anywhere it should.
So I've been trying to have hibernation working on my desktop. And the first thing I got was this message : 
```
not enough free swap
```
So I added more space to my swap partition (which dating to when I first installed Dapper was a weak 512Mb) using Gparted and it's now a little over 3G (I have the space). I did a swapon on the new bigger swap partition and I even rebooted but the system still tells me it's only 512M.
```
 swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda8                               partition       514040  0       -2

```

What else do I need to do ? Can someone tell me how to make it so it'll use the entire 3Gigs as swap ?
Also when going into hibernate and after the "not enought swap" error, it seemed the system restarted but I then got the following repeated over and over until I finally reset my computer : 
```
BUG: soft lockup - CPU#0 stuck for 11s! [compiz.real:6588]
```
Obviously a compiz issue. Anyone ever seen that before ?
Thanks for the help in advance

---

