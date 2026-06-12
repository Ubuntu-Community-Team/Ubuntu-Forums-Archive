---
title: "Mounting Windows Mobile as USB mass storage drive"
date: 2008-05-22
forum: Hardware
---

### Post by Endolith on 2008-05-22
I have a file on my Windows Mobile phone that it refuses to delete, probably because of a question mark in the filename.  (I don't know how I got it on there with a question mark in the first place.)  I'd also just like to be able to navigate my phone's file system like I can do with ActiveSync in Windows.

So I downloaded [WM5torage]("http://freewareppc.com/communication/wm5torage.shtml") and it seems to work.  I can see a bunch of devices:

```
lrwxrwxrwx 1 root root  9 2008-05-21 22:57 usb-WM5torag_WIZA200_CB7BF6B3A735B5C8AD010EDD36021DF896FB8BF2-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 2008-05-21 22:57 usb-WM5torag_WIZA200_CB7BF6B3A735B5C8AD010EDD36021DF896FB8BF2-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-05-21 22:57 usb-WM5torag_WIZA200_CB7BF6B3A735B5C8AD010EDD36021DF896FB8BF2-0:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-05-21 22:57 usb-WM5torag_WIZA200_CB7BF6B3A735B5C8AD010EDD36021DF896FB8BF2-0:0-part3 -> ../../sdb3

```

If I use cat (or less or xxd), I can see strings in these "files" like "MSFLSH50" and "Windows^@^@^@^@ Mobile PC", so it's obviously accessing the phone's memory, but when I try to mount these, it doesn't work, and doesn't seem to give me any errors, either.  Is there a way to discover partitions/file systems, and mount them, or are these not recognizable file systems in the first place?  Could I use a raw byte editor to overwrite just the question mark character with something normal?

Gnome Partition Editor shows 3 partitions, all of them "unknown".  First two are 3.06 MiB, third is 50.75 MiB.

---

