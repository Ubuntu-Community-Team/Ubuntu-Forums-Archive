---
title: "No DVD play back"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by Sp@z on 2005-12-08
HI all  I am a new user of Linux Ubuntu 5.10 (New to linux period actually) and It seems the only problem I am truley having is DVD playback. Totem just throws the error of "Are you trying to play an encrytped DVD without libdvdcss? I have this installed.

MPlayer loads and when starting a movie loads nothing into the screen and then freezes. A reboot is the only way to get rid of it.

Ogle and OKle read the dvd through the copyright messages from the Government and then just crashes.

CD audio is choppy and skippy.

I have tried to enable DMA but I do believe it won't load since this DVD player is pretty old and doesn't support it. 

Any Ideas?  My signature has my system specs and if not I will post them again.

TIA

---

### Post by HighPlainsDrifter on 2005-12-08
It is very possible that the lack of DMA is causing problems. It certainly will cause playback to be choppy. For Totem, do you have gstreamer0.8-dvd installed?

---

### Post by antidrugue on 2005-12-11
See my post here:

[http://www.linuxforums.org/forum/topic-61547.html](http://www.linuxforums.org/forum/topic-61547.html)

It's everything you need to do.

---

### Post by jml on 2005-12-12
I agree with the suggestions posted so far.  In addition to installing libdvdcss2, you whould also download the w32codecs.  Reboot your system and see how things work.  If you still have choppy playback, try a different player.  I don't know why it should make a difference, but I have had a lot a trouble getting Totem to work on my system.  I'd suggest downloading xine-ui.  I find that this works more reliably than Totem.  I also noted that when I try to play movies on one of my older systems with very modest graphics capabilities, I get choppy playback when I play the movie full screen.  If I shrink the window a bit, playback and sound seem smoother.  Just my two cents worth.  Hope it helps.

Joe

---

### Post by RevNomad on 2005-12-13
I'm going to keep this thread alive.  Simply because it is a major problem.  

I had (K)Ubuntu working fine until I upgraded to 5.10.  Granted I screwed everything up so much I had to reformat and reinstall.  However everything is in place; the libdvdcss, the codec's and everything else a novice like me can find reading this forum.  Still no luck.  

I've tried Totem (bleh never had worked for me) and Kaffine (worked fine before the reinstall).

I'd love some help.

NTP

---

### Post by GrumpyBob on 2005-12-14
I have followed the installation guide for Xine-Gstreamer, and find that while some DVDs play just fine, some throw an error about encryption.  I find I can play these DVDs if I start xine using sudo. 

Robert

---

### Post by Sp@z on 2005-12-14
Yeah I can get my DVD's to play but they are real jumpy. My dvd rom does not support DMA and I have another thread about it and am waiting for a reply to how to make it THINK it has DMA. LOL Outsmarting a computer is a beautiful thing!

---

### Post by kingsidy on 2005-12-15
First you have to make sure you have libdvdcss2 installed. 
Second make sure that DMA is enabled
One quick suggestion is if you are using totem, make sure to install 'totem-xine'. It works much better with dvds. You also have VLC which is one of my favorites.

---

### Post by antidrugue on 2005-12-15
For any kind of video/dvd playback, nothing beats MPlayer.

Making MPlayer works the way you want is not necessarely a simple task. It involves many commands that can seem complex at first.

Once you get to know it, Totem, Xine, VLC just seem impotent and non-functionnal compare to MPlayer.

So, head towards multiverse and grab mplayer-586

```

sudo apt-get install mplayer-586

```

...your /etc/apt/sources.list must be configured accordingly.

Then you must configure properly the file /home/yourself/.mplayer/config

All your problems will then disappear.

But of course you still have to install libdvdread, libdvdcss and get DMA to work properly. Which is quite easy if you follow this:
[http://www.linuxforums.org/forum/topic-61547.html]("http://www.linuxforums.org/forum/topic-61547.html")

Good luck!

---

### Post by Sp@z on 2005-12-15
Thanx for all the replies folks. I have followed the instructions throughout this thread and many others on how to get this to work properly.

I have followed this thread [https://wiki.ubuntu.com/DMA?highlight=%28dma%29](https://wiki.ubuntu.com/DMA?highlight=%28dma%29) as well and was successful in getting these options installed and completed and it has only helped a little bit. The DMA is enabled all codecs and libs are installed. This is THE EXACT same problem I had with WinXP pro on my laptop. And WHY I installed linux. I have completly formated my laptop (My Choice) and restored it to it's original state of Windows 98SE and DVD playback is perfect. I guess I will keep with dual booting win98SE and Ubuntu. 

Thank you for all your help and it is time to move to the next issue and try to resolve this one at a later date. Before I get frustrated and go crawling back to Bill Gates and Windows full time.

---

### Post by Sp@z on 2005-12-15
Thank you I have followed that as well. Still no worky for me.

---

### Post by jml on 2005-12-15
Sp@z, there is one other possiblity.  You are using a Sony Vio, a very good computer.  But Sony is also a huge provider of multimedia content, and has gotten itself in a bit of trouble recently by distributing music cd's with a rather invasive form of digital rights management.  Its possible, (pure speculation on my part, I have no proof,) that Sony has incorporated some form of hardware/firmware based DRM which may prevent successful playback of encrypted DVD's.  I know that I've read a little about the whole topic of Microsoft working with hardware vendors to incorporate DRM technology in multimedia/home entertainment PC's.  The designs discussed would have a very negative impact on Linux users.  Does anyone on this forum have any insight, or thoughts on this?  I'm not trying to start a witch hunt, just "thinking out loud.

Joe

---

