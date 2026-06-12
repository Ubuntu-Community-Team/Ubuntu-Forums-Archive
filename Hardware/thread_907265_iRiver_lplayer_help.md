---
title: "iRiver lplayer help"
date: 2008-09-01
forum: Hardware
---

### Post by devosion on 2008-09-01
I purchased myself an iRiver lplayer about a month ago and so far it has worked well with ubuntu. I've had to use UMC in favor of MTP, and format the drive as fat32 but so far its proven to work admirably.

Today I have run into a problem as I have attempted to sort the files on my lplayer. For some reason the lplayer is not reading files alphabetically, and it seems that my attempts at renaming my music files based on a scheme does not work because it doesn't read them based upon this scheme (01_filename - 0x_filename). Instead it is reading my files based upon a scheme I do not know. The case it is reading my 06_filename first and then randomly reading them. Thus I am unable to play the files as they would be played on the cd. 

This isnt so much an ubuntu question as it is a question as if anybody knows the method the lplayer reads the files. Im somewhat at a deadend with this conundrum so either a little bit of help or a point in the right direction will suffice. 

Thanks!

---

### Post by happyisland on 2008-10-14
I know what you mean, and I feel your pain. The seemingly semi-random sorting that the player does is one of my biggest criticisms of this device. If you ever do get a handle on how it decides to sort files please let me know!

---

### Post by ajcham on 2008-10-18
For reasons which are completely beyond me, the lplayer sorts tracks in the order in which they were added to the player.  If you copy an entire folder over they can come out in pretty much any order.

The workaround I've used is to copy the individual tracks, instead of the folder containing them.  It should be okay to select all the tracks, then drag the first one over.  (This works for me in Konqueror, although I've heard that Nautilus might not be as useful here.)  If that's no good then try copying the tracks one at a time - A PITA I know, but until a firmware update sorts this out I don't think there's much else you can do.

---

### Post by MattressVon on 2008-12-14
If I'm not mistaken, editing the ID3 tags in easytag seemed to fix my sorting problem. Make sure to tie all tags together with the same artist, track number set, album, and genre and you should be fine. I upgraded the firmware, so this may be why it works this way for me.

---

### Post by Kshegzyaj on 2008-12-31
Guys, I also purchased a Lplayer as my christmas present, and I got it yesterday (I had to order it they didnt' have it in stock). By the way, I found [this post](http://lostwebsite.wordpress.com/2008/12/18/iriver-lplayer-in-linux/) on a blog, saying that we can use rsync.

```
rsync --verbose --recursive --times -whole-file --delay-updates --modify-window=1 /home/me/temporaryfolder/Music /media/Lplayer/
```
(I'm using a temporary folder instead of /home/me/Music because the Lplayer only has 8Gb and my Music folder is bigger, then I can choose which track put on my Lplayer, and then just copy the new Music folder with rsync)

It took me nearly 1 hour to copy 4,6Gb (847 tracks within 111 albums within 91 artists, if the number of files changes the speed instead of the filesize...I don't really know...)
I did as well for my video clips.

It's a long time to wait, but the Lplayer is full after 2 or 3 hours of charge, so...

---

