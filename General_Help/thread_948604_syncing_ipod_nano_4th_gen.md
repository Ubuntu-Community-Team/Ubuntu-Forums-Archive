---
title: "syncing ipod nano 4th gen"
date: 2008-10-15
forum: General Help
---

### Post by weeman7007 on 2008-10-15
I was wondering if it is possible to sync the brand new ipod nano 4th generation with ubuntu? if so, then how please? i am wanting to buy one and wanted to get everything set up ready for when i actually get one.

---

### Post by Sam on 2008-10-15
[http://ipodlinux.org/wiki/Project_Status](http://ipodlinux.org/wiki/Project_Status)

---

### Post by haletd on 2008-10-23
Yes the new ipod nanos will sync with amarok and Rhythmbox.  However, I have yet to get album art to work.  I haven't tryed transfering video yet.  

Sam your post is not helpful, He didn't ask if he could run linux on it.

---

### Post by Het Irv on 2008-10-27
haletd, what version of Amamrok are you using?  I hate to buy some overpriced music player if it won't work.

---

### Post by liam517 on 2008-10-27
hey i'm planning to get a new nano same day as UNUBTU 8.10 is released (3 more days), i'll post back and let ya now how it goes.
thanks for the "Amorak" mention, i dig it interface the most.

---

### Post by liam517 on 2008-10-27
[http://www.linuxforums.org/forum/peripherals-hardware/130653-ipod-nano-4th-gen.html](http://www.linuxforums.org/forum/peripherals-hardware/130653-ipod-nano-4th-gen.html)

first couple of posts are "not working" then further down seems Amorak is the one to go with m:)

---

### Post by motoperpetuo on 2008-10-31
> **haletd said:**
> Yes the new ipod nanos will sync with amarok and Rhythmbox.  However, I have yet to get album art to work.  I haven't tryed transfering video yet.  

Sam your post is not helpful, He didn't ask if he could run linux on it.

i don't know if this will be helpful or not, but this is how i add cover art on my 2nd generation nano in amarok:

1)Start Cover Manager (Tools|Cover Manager).
2)Find the blank icon for the album. Right-click it and choose “Set Custom Cover”
3)Browse to the image for the cover you want to use and select it.
4)Delete the album from your iPod.
5)Add the album to the iPod again and click the Transfer button.

i'd be interested to hear if this works on the 4th geneartion nano, and how the 4th generation nano works on amarok in linux in general. it looks nice, but it seems like i've heard rumors that apple has thrown up some technical roadblocks to getting it to work under linux.

---

### Post by cszikszoy on 2008-11-05
Album Art used to work just fine with my Ipod Classic.  Unfortunately, it was stolen, and now album art wont load on my 4th gen nano.  

Anyone gotten album art on their 4th gen nano yet?

---

### Post by ahbart on 2008-11-13
I had some problems with a ipod nano 4th generation on Ubuntu Intrepid. Amarok, banshee, Rhythmbox, gtkpod, had all problems connecting and syncing. But now I found Floola! This is working native on Linux, not install required. Syncing photo's, music, movies, etc. There is even a connection to amazon, but This one I could not test. because then it crashed. Hopefully this will get beter soon.
Have a look here: [link](http://www.floola.com/modules/wiwimod/index.php?page=WiwiHome)
Bart

---

### Post by Simian Man on 2008-11-13
I use a 4th gen iPod nano with Rhythmbox.  It connects, and transfers music and cover art beautifully out of the box.  The only issue I have is that on the iPod the cover art shows up in the cover flow view, but not when actually listening to a song.

I haven't tried adding pictures or videos, since Rhythmbox doesn't seem to support that.

---

### Post by ahbart on 2008-11-13
@Simian Man, and if you use Rhythmbox, is it possible to use itunes too? or do both need/create another database?

---

### Post by Simian Man on 2008-11-13
> **ahbart said:**
> @Simian Man, and if you use Rhythmbox, is it possible to use itunes too? or do both need/create another database?

I don't know, I haven't tried it.  I *imagine* that iTunes will overwrite any music that is on the iPod but not iTunes - if it accepts it at all.

---

### Post by ahbart on 2008-11-13
Most applications, will use the generation 3 database structure for the ipod. This will work but itunes will 'fix' this. But I do not know what the consequenties are for this. 
If I understand this well Floola uses the 4th generation database.
Bart

---

### Post by dark joev on 2008-12-01
I have been using banshee for syncing music from my laptop to my new 8GB Nano and it seems to work fine except I can't put more than 322 items on it.

---

### Post by zbrox on 2008-12-02
I'm a new iPod Nano 4g user, and all is working well with Banshee 1.4.1 (including artwork and video upload). I tried Floola, but it was a usability mess and it reminded me a lot of a Windows freeware-ad-full software. Also it didn't manage to manage the artwork of the albums.

---

### Post by kernelhaxor on 2008-12-02
> **Sam said:**
> [http://ipodlinux.org/wiki/Project_Status](http://ipodlinux.org/wiki/Project_Status)

ipodlinux is a whole different thing.  It is an open source venture into porting Linux onto the iPod.

---

### Post by ispy on 2009-01-02
I have the same problem you do.

Just got my music synced (I had to connect to Windows once to get it formatted and set up for disk use, but I got my music on with Rhythmbox.)

I'm using Handbrake right now to convert a video file to ipod format.

I'll let you know if it works.

---

### Post by ispy on 2009-01-02
Alright, I managed to get it to work. All you need is the gtkpod-aac package ( sudo apt-get install gtkpod-aac).

From there, I selected the Ipod Nano 3rd gen, 8GB, Silver. It worked.

I was able to sync my copy of The Dark Knight to my ipod. i love it (Btw, I have the 16 gig black nano, so I don't think GTKpod cares which version you select.

---

### Post by Benanov on 2009-04-09
Floola is binary-only...that's not good enough for me. :(

Most of my friends have avoided iPods, but this doesn't help those that have. I'll watch this thread a bit more to see if the situation improves.

---

### Post by mb_webguy on 2009-04-09
I had no problems using gtkpod to load songs, video, and photos on an iPod Nano 4th gen recently.  [Here]("http://wysiwyb.blogspot.com/2009/03/ipods-and-ubuntu-linux-yes-you-can.html")'s an article I wrote about it, which includes links to install other related applications, including one to add album art to mp3s.

---

### Post by Epitaph44 on 2009-04-09
> **Simian Man said:**
> I use a 4th gen iPod nano with Rhythmbox.  It connects, and transfers music and cover art beautifully out of the box.  The only issue I have is that on the iPod the cover art shows up in the cover flow view, but not when actually listening to a song.

I haven't tried adding pictures or videos, since Rhythmbox doesn't seem to support that.

I have the same problem with the album artwork.
I'm using Rhythmbox on Ubuntu.
I also had the same problem using Kubuntu with Amarok and gtkpod.
Is this still unresolved?

---

### Post by RealG187 on 2009-05-17
[I have the 4th gen iPod Nano]("http://ubuntuforums.org/showthread.php?t=1158593") that I won. I can put music on, but I need help with photos, video, and album art. Some tracks have album art, but I think they were from media monkey in Windows.

---

