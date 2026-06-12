---
title: "A few issues with Sony NWZ A818"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by mlkv on 2007-12-26
Hi all, Santa just got me a Sony NWZ A818 for Christmas, but I'm having a few issues while using it with Ubuntu.

1) Even though all the MP3s are correctly tagged with their cover arts (something I did using EasyTAG), I can't see any in my player when I browse the library or play some music.

2) Most of the artists and albums names are uncorrect, for example "Burial" became "Burial <-loads of space-> G", or "Converge" became "Converge <-loads of spaces-> 2", which is annoying because makes the text scroll even when it shouldn't.

3) This might not be an issue in fact, but it looks strange to me so I'll add it: when I unmount or eject the device, I got returned with the usual "now is safe to remove bla bla" but on my Sony's screen I can see the "Connecting" message. However, when I unplug its USB cable it starts building the library and everything goes fine. Well, unless this is the reason why it messes up with MP3 tags!

Has anybody of you encountered the same issue? Any help would be greatly appreciated! :)

---

### Post by Daniel15 on 2007-12-27
> 1) Even though all the MP3s are correctly tagged with their cover arts (something I did using EasyTAG), I can't see any in my player when I browse the library or play some music.
I'm encountering the [same problem with album (cover) art on my NWZ-S616F](http://ubuntuforums.org/showthread.php?t=651031), it displays properly when I use Amarok, but doesn't display on the MP3 player.

> 3) This might not be an issue in fact, but it looks strange to me so I'll add it: when I unmount or eject the device, I got returned with the usual "now is safe to remove bla bla" but on my Sony's screen I can see the "Connecting" message. However, when I unplug its USB cable it starts building the library and everything goes fine. 
Similar to me. Right after I unmount it, I get:
> Cannot unmount volume

Cannot unmount the volume 'WALKMAN'.
Cannot remove directory.

But then it seems to unmount fine anyways. And same as you, "Connecting" remains on the screen.

---

### Post by mlkv on 2007-12-27
A quick update: I tried to move tracks with latest Windows Media Player on Windows XP and everything went ok. Tags are not messed and the cover art displays properly.

I've also tried to encode video in MP4 and send one to the player, and this time it worked properly. The video shows and sounds perfect, and the name is correct. I haven't tried creating a preview image but I don't care to be honest, videos are going to come and go pretty fast on my player. Just be careful that you need to change a few packet names on Gutsy, compared to what was written in the original HOWTO (just search for "nwz" on here and you'll find it).

---

