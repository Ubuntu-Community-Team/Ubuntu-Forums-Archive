---
title: "Hard Drive Question"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by Mular on 2007-12-10
Hey Guys!

New to linux, and I just want to say thanks for this forum. The help and how tos that are avaiable is simply amazing and helped so much.. Now for my question

I recently bought a 500g Western Gate external Drive right. I have windows installed on my internal 160g and I partitioned my western gate into 3 (400ish gig for storage, 40gig for linux OS, and 10gig for file swap.)

Now my question is this, any negative impact on the drive (life span issues) by having an OS installed on an external drive? Also I read about some problems with ubuntu affecting the life on your hard drive by having it constantly spinning down and up. I read there was a command you can put it to help this, but when I tried it gave me an error. Maybe it has to do with that its on an external drive? Maybe hd0,0 isn't my external drive even though thats the main OS hard drive? Since I am not on a lap top I didn't think I would have to worry about the spinning up and down issues but since its an external I think its doing it alot.

Secondly my dual boot is winxp like I said. I see in windows xp there is an option in device management for an external drive to be on optimise for removal or for performance. I think this removal mode causes my drive to spin up and down tons, so I changed it over to performance (I am hoping that stops it from constantly spinning up and down?) Is there anything in ubuntu like that?

I just don't want to hurt my external drive - I don't plan on taking it anywhere just the price was right.

Thanks guys

---

### Post by Mular on 2007-12-10
Oh I just learned something the spinning down is actually a function of the External Drive.. I guess its a feature in the hard drives firmware, and can't be changed according to Western Digital.. 

So is there anything that I can do in linux about it, I know in windows I can't.. ?

I guess I shouldn't really worry about the lifetime of the drive but the constant spinning down makes me think its going to decrease the lifetime a lot.

My 2 year old internal drive according to smartmonitor is 98 and my like 1month year old My Book is about 100 =/

I think the problem is going to be really bad in linux since my main filesystem is on that but maybe all the process's running will keep it from going into standby?

---

### Post by kgr132 on 2007-12-10
I had a similar problem with a Seagate FreeAgent Drive that would spin down on it's own. It kept causing my Windows VM to crash since the virtual disk was on the external drive. I found this: [COLOR="Blue"][http://alienghic.livejournal.com/382903.html](http://alienghic.livejournal.com/382903.html)[/COLOR] linked in another forum. The short version is to use sdparm to change the drive's default parameters with respect to standby. Here's the code I used. Notice that the Standby timer active and Standby condition timer are zeroed. Obviously, you'll need to replace /dev/sdb with whatever your external drive maps to. For info on sdparm, type *sdparm --help* in a terminal. You can get the sdparm package from the Ubuntu repositories via Synaptic.

```

# sudo sdparm -all /dev/sdb 
    /dev/sdb: Seagate   FreeAgent Go  100F
    Direct access device specific parameters: WP=0  DPOFUA=0
Power condition [po] mode page:
  IDLE        0  [cha: n, def:  0, sav:  0]  Idle timer active
  STANDBY     1  [cha: y, def:  1, sav:  1]  Standby timer active
  ICT         0  [cha: n, def:  0, sav:  0]  Idle condition timer (100 ms)
  SCT       2400  [cha: y, def:2400, sav:2400]  Standby condition timer (100 ms)

# sudo sdparm --clear STANDBY -6 /dev/sdb 
    /dev/sdb: Seagate   FreeAgent Go  100F

# sudo sdparm -all /dev/sdb 
    /dev/sdb: Seagate   FreeAgent Go  100F
    Direct access device specific parameters: WP=0  DPOFUA=0
Power condition [po] mode page:
  IDLE        0  [cha: n, def:  0, sav:  0]  Idle timer active
  STANDBY     0  [cha: n, def:  1, sav:  0]  Standby timer active
  ICT         0  [cha: n, def:  0, sav:  0]  Idle condition timer (100 ms)
  SCT         0  [cha: n, def:2400, sav:  0]  Standby condition timer (100 ms)

# sudo sdparm --save -6 /dev/sdb
    /dev/sdb: Seagate   FreeAgent Go  100F

```

---

### Post by Mular on 2007-12-11
Awesome thanks so much for your help..

I am so grateful for all the help I see on this forum.. I really would never have been able to do anything in linux without this forum lol.. I am having a blast just learning all this stuff ;)

---

### Post by etotheipiplusone on 2008-03-04
So I made the above fix, is there any way you can think of to undo it?  My drive is CONSTANTLY spinning, and say what you will about spinning up then down, I'm not too thrilled about the fact that my drive is spinning 24/7. 

Help?

---

### Post by dunja on 2008-03-07
I would also like to undo the setting.  I've tried:

> sdparm -D -p 0x1a -6 --save /dev/freeagent

..but the drive reverts back to the always-on state upon reboot.  Anybody know how to undo it?

---

### Post by kernalsanders123 on 2008-03-11
Hello all, another relative newbie to linux here. I've learned a lot in the last year, much of it thanks to this terrific forum!

Anyway, getting back on topic, I'm looking at possibly buying a 500GB Seagate Freeagent drive myself, but I don't plan on running programs off of it. At this point it would just be for periodic backups, and larger files that I might not want hogging up my internal drive. I've also read that some external hard drives have problems with linux regarding power saving features. I can't recall any specifics, but something along the lines of what Mular said on the first post.

Since I wouldn't be using it to run programs off of, would this be an issue I shouldn't really worry about? I've also considered going along the route of using an internal hard drive in an external enclosure, but I"m not sure if it would have the same power saving issues, being read as an external drive.

Thanks in advance...

---

### Post by quodlibetor on 2008-05-14
OK, I don't know how to fix the problem that got started in this thread of the constantly spinning hard drive, but I did get tired of not being able to keep mine awake so I wrote a little hacky script to keep mine awake. Script and instructions [at my blog]("http://blog.quodlibetor.com/2008/05/14/my-first-useful-program-ever/"). 

I wrote the instructions both at 3 am and for complete neophytes, so please excuse/comment if they're too verbose. Or for any other reason.

---

