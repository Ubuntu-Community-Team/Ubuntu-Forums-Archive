---
title: "external usb harddrive speeds"
date: 2008-07-18
forum: Hardware
---

### Post by psykotrol on 2008-07-18
After formatting my computer and reinstalling ubuntu 8.04 and all its updates, I have extremely poor speeds on my western digital usb drive. Before reinstalling Ubuntu and reformatting the external drive as well, it worked fine and moderately fast, in the 20 mb/s range, using NTFS (external). Now after reinstalling ubuntu and formatting the external to ext3, Im getting speeds in the range of 50-100 kb/s.

hdparm shows fine speeds, but actually copying files to my main drives, I get about 150 kb/s tops.

heres what I get for hdparm

```
Timing cached reads:   2230 MB in  2.00 seconds = 1114.74 MB/sec
Timing buffered disk reads:   14 MB in  3.27 seconds =   4.28 MB/sec

```

I dont get anywhere near those speeds, so what in the world is my problem? My read/write speeds are so horrible, that sometimes music files freeze when being played from the external. Last time I had ubuntu 8.04 right when it came out, and installed all the updates as they came out, now I installed all of them at once. Is there some issue there? After unmounting and remounting it, I still have the problem. I have no clue what to do! It was working fine up until I installed the updates...

edit: actually, it seems like individual files go a bit faster, around the 400 kb/s range, and copying directories with files is in the 50-100 kb/s range.

edit: hmmm.. it seems like certain files go faster than others. Is my drive corrupting the data or something? Because I was able to copy a Pink Floyd album in a second or so, and others are somewhat sporadic with how they copy. I copy half of a Bob Marley album at about 3 mb/s, then itll freeze and go down to about 700 kb/s... anybody have an idea?

---

### Post by Dark_Stang on 2008-07-18
Lets test a few things out to see if we can narrow it down any. Try copying files over through terminal and see how fast that goes.

I tend to get 20+ mb/s going to externals.

---

### Post by psykotrol on 2008-07-18
alright, I try to copy a Hendrix directory of about 600 mb to my Desktop, it does something, doesnt show how fast, but the directory shows up on my desktop, and half of the processor gets used.

edit: used verbose to see whats going on, and it goes through a bunch, gets hung up on one for a few seconds, or sometimes up to a minute or few.

right now its hung up on something, so I played the song(s) in XMMS, and it plays perfectly fine. no audible scratches or skipping...

is there anyway to show the speed and/or timestamps?

command I used was

```
cp -Rv "Jimi Hendrix" /home/user/Desktop
```

---

### Post by Dark_Stang on 2008-07-19
There isn't a way that I know of to show speed in command line, I'd just time it both ways and figure out the speed that way. And to be honest, if it's slow through command line and through nautilus, it sounds like you may have a failing hard drive. See if the manufacturer of your external hard drive has some diagnostic tools that you can use to test it.

---

