---
title: "Amarok 2 error after upgrade to Jaunty 9.04"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by iption on 2009-05-15
After I upgraded my ubuntu to Jaunty, a lot of errors sprung up. Amarok starts, normally playlist loads, collection ok, everything ok, but when I press play nothing happens. I try to press it a couple of times more, then i get an amarok notification saying: "Too many errors encountered in playlist. Playback has stopped." I tried reinstalling amarok but nothing changed.

Other things that are not working in Jaunty are Macromedia Flash although I have it installed (and tried reinstalling), and my global shortcuts I set up in metacity.

So please some help on this.

---

### Post by Lord Delirium on 2009-05-16
I had the same problem ("Too many errors encountered in playlist. Playback has stopped.", nothing plays) with Amarok 2.0.2 using Ubuntu 9.10. It was corrected when I installed this (using synaptic package manager):

libxine1-ffmpeg

Before doing this I also installed "phonon-backend-xine", may be it is also needed (not sure).
If does not work, try to remove "phonon-backend-gstreamer" (will also uninstall amarok) and reinstall "photon-backend-xine" and "amarok". Then reboot. This worked for me.

Hope it helps.
Lord Delirium

---

### Post by weremichael on 2009-05-18
> **Lord Delirium said:**
> ...

Before doing this I also installed "phonon-backend-xine", may be it is also needed (not sure).
...

Hope it helps.
Lord Delirium

That's what fixed it for me. Thanks for sharing the knowledge.

-Michael

---

### Post by barahonachrism on 2009-06-09
Not needed remove "phonon-backend-gstreamer",  You can install "phonon-backend-xine" anyway, and amarok works fine.

---

### Post by H4rold on 2009-06-10
> **Lord Delirium said:**
> I had the same problem ("Too many errors encountered in playlist. Playback has stopped.", nothing plays) with Amarok 2.0.2 using Ubuntu 9.10. It was corrected when I installed this (using synaptic package manager):

libxine1-ffmpeg

Before doing this I also installed "phonon-backend-xine", may be it is also needed (not sure).
If does not work, try to remove "phonon-backend-gstreamer" (will also uninstall amarok) and reinstall "photon-backend-xine" and "amarok". Then reboot. This worked for me.

Hope it helps.
Lord Delirium
The libxine1-ffmpeg solved it for me, thanks !

---

### Post by stormzen on 2009-06-14
> **H4rold said:**
> The libxine1-ffmpeg solved it for me, thanks !
I just upgraded to Jaunty from Intrepid yesterday.  I was pleased to see sound mostly working (as I'd had no end of troubles with Intrepid), however, Amarok didn't seem to know how to play music anymore.  I discovered that I was now running 2.02 ( I think ), and visited #ubuntu and #amarok to figure out how to get it working.  I was told to upgrade to 2.1 by this method: [http://www.kubuntu.org/news/amarok-2.1](http://www.kubuntu.org/news/amarok-2.1) .  ( I was told that I could actually see my sound settings with 2.1, which proved to be an accurate statement. )

After upgrading, it crashed the first time it ran, but just the once.  However, the files still wouldn't play.  I played around with the sound settings ( configure:playback:sound system configure ) and found that it tested just fine against my card, however, setting that card for all the settings had no effect.

I saw this thread, and uninstalled phonon-backed-gstreamer, but it did not uninstall amarok when I did so, so I just left it uninstalled, and played with the sound configuration again.  I noticed that PulseAudio and Esound both also tested successfully, so I switched to Esound, and then found that I could the music...

---

### Post by chiques on 2009-06-18
This worked for me! Thanks!

---

### Post by Raynman37 on 2009-06-19
Worked for me as well, thanks!

---

### Post by Nytehawq on 2009-06-20
Installing phonon-backend-xine did the trick for me!  Thanks for the tip.

---

### Post by Bart B on 2009-06-24
I had to uninstall phonon-backend-gstreamer

---

### Post by B0rat on 2009-06-27
Installing phonon-backend-xine did the trick for me! Thank you posting this... pity it can't work "out of the box"  :S

---

### Post by filipejps on 2009-07-04
Installing phonon-backend-xine did the trick for me also

---

### Post by mallidi.harish on 2009-08-03
Thanks for the solution. It really solved my problem.

---

### Post by dark0dave on 2009-09-17
Thanks dude! It works perfectly

---

### Post by kunalgautam on 2009-10-18
> **H4rold said:**
> The libxine1-ffmpeg solved it for me, thanks !
Yup same here it solved mine problem too :) 

Thanks to all :) :guitar:

---

### Post by andromeda786 on 2009-10-28
Installing **phonon-backend-xine** and then **libxine1-ffmpeg** worked for me.

---

### Post by Jesua on 2009-11-09
> **Lord Delirium said:**
> 

Before doing this I also installed "phonon-backend-xine", may be it is also needed (not sure).


Worked... thanks... :lolflag:

---

### Post by TheBishopsBane on 2010-01-28
I seem to be having the same problem here. I've just installed Amarok for Ubuntu 9.10 Karmic Koala (Gnome). Amarok works for some MP3s, but not all. Here's what I know/what I've tried:

[LIST]
[*]Certain files play fine, with others skipping to the next track immediately
[*]After 10 or so errored-out songs in a row, I get the "Too many errors encountered in playlist, playback stopped" error, and the tracks halt.
[*]The songs which work seem to be related (though I can't tell why), as whole albums will either work completely, or not at all.
[*]Judging from the file properties, all the files seem to have the same codec "*MPEG 1 Audio, Layer 3 (MP3)*"
[*]The issue doesn't seem to have anything to do with bitrate (ie, some 128kbps files work, some don't. Same with higher and lower bitrates)
[*]I've installed/re-installed/updated **all** of the following (several times): *phonon-backend-xine, libxine1-ffmpeg, amarok* using both Synaptic and the command line.
[*]I've uninstalled *phonon-backend-gstreamer*
[*]All the affected files play fine in Songbird.
[/LIST]
I'd really like to use Amarok over Songbird, but I'm at my wits end as to how to solve this problem. Any one have any ideas?

---

