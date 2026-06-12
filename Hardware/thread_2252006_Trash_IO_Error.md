---
title: "Trash I/O Error"
date: 2014-11-08
forum: Hardware
---

### Post by mj-advincula on 2014-11-08
So, I don't know what happened and I'm pretty sure I haven't done anything. I was just watching a video, paused it because it was dinner time, when I came back and pressed play, I get "File cannot be read" errors at VLC. When I rebooted the whole thing and remounted the external HDD, I get some message box that says that the Trash cannot be accessed. Thunar says that there are 0 items on the hard drive.

From the terminal, though, I used ls -a and get this: ```
ls: cannot access .Trash-1000: Input/output error
```

Before that, I tried to use check on GParted but I don't seem to have gotten any favorable results out of it. I can't see the error message though because the thing just freezes up, GParted.  I can, however, access files almost normally. As long as I can type in the address, it seems. It appears, it's the base that I can't access.

Before all this happened, I noticed that Thunar would freeze up whenever I tried to access it while this externall HDD is mounted. I put it down to the slowness of this machine. After all, it's an old IBM 140p. And that maybe there are just too many files in the Trash already.

How do I fix this problem, please? Can this even be fixed? I've been Googling and I've not been getting good results.

---

### Post by MJae on 2014-11-11
Really, no one knows what can be done about this?

Update:

So, I used someone else's computer and found something new about the external hard drive: While there seems to be no bad sectors (gparted just skipped through that part) the problems seems to be something about multiple references to several clusters.

This is what I got from gparted:
> GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize

 Libparted 2.3
  [TABLE]
[TR]
 [TD="colspan: 2"] **Check and repair file system (ntfs) on /dev/sdb1**  00:12:41    ( ERROR ) [/TD]
 [/TR]
 [TR]
 [TD]    [/TD]
 [TD] [TABLE]
 [TR]
 [TD="colspan: 2"] calibrate /dev/sdb1  00:00:00    ( SUCCESS ) [/TD]
 [/TR]
 [TR]
 [TD]    [/TD]
 [TD] [TABLE]
 [TR]
 [TD="colspan: 2"] [I]path: /dev/sdb1
start: 2048
end: 1953523119
size: 1953521072 (931.51 GiB)[/I] [/TD]
 [/TR]
 [/TABLE]
 [/TD]
 [/TR]
 [/TABLE]
 [TABLE]
 [TR]
 [TD="colspan: 2"] check file system on /dev/sdb1 for errors and (if possible) fix them  00:12:41    ( ERROR ) [/TD]
 [/TR]
 [TR]
 [TD]    [/TD]
 [TD] [TABLE]
 [TR]
 [TD="colspan: 2"] ***ntfsresize -i -f -v /dev/sdb1*** [/TD]
 [/TR]
 [TR]
  [TD] 
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]


Although, as I write this, gparted is still all frozen up.

---

