---
title: "Massive DVD Problems"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by jlacroix on 2005-07-01
I really hope someone can help me with this. It is very discouraging. I am about to just consider Linux not capable of playing Movie DVD's, I hope someone here can prove me wrong, this is very very very annoying.

First off, I followed the unnoficial ubuntu guide to get DVD working. All repositories in that guide are enabled. I downloaded every multimedia package you possibly can, and I downloaded every package with the word DVD in it that referred to playback. Yes, even the CSS package.

Here is a little bit more about the problem and error messages I get (Playing the Garfield DVD):
---
Xine: "The source can't be read. Maybe you don't have enough rights for this or the source doesn't contain data".

Totem-xine: "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

Mplayer: "Mplayer interrupted by signal 11in module decode_audio".

Ogle: Plays for a few seconds, then exits automatically.
---

Also, when trying to play "Are We There Yet" in Totem-xine, I get this nasty error:
```
The audio device is busy. Is another application using it?
```

Please somebody help, my wife uses Ubuntu on her PC and also has these problems, and is about ready to switch back to Windows.

---

### Post by dimec on 2005-07-02
had an almost similar problem here... installed dvd playback using the unofficial guide with xine, mplayer and the codecs installed. 

Errors on playing the 'Casablanca' DVD... Almost the same as above except for totem xine.
______________________________________________________________________________
Xine: "The source can't be read. Maybe you don't have enough rights for this or the source doesn't contain data".

Totem-xine: It plays - just about. There is a big audio lag and no DVD menu.

Mplayer: "Mplayer interrupted by signal 11 in module decode_audio".
______________________________________________________________________________________

well, what to do?... installed the vlc player...
sudo apt-get install vlc
sudo apt-get install vlc-plugin-es
vlc --aout esd
(as in [http://ubuntuforums.org/showthread.php?t=20588](http://ubuntuforums.org/showthread.php?t=20588))

now, the vlc player plays the dvd with all the menus (and sub-titles too), there was a frame drop or jerky vedio, so...
settings - preferences - check advanced on the bottom right - general settings - video - change video output module to 'X11 video output'
this works for me - i have no clue why :)
yes, the xines and mplayer dont work still...:(

now, the vlc player displays the mrl as 'dvd:///dev/hdd' and device name as '/dev/hdd'. (Ctrl + D)
well and when i browse the dvd by rclicking and browse folder the path is shown as '/media/cdrom0'

why is that?
ideas anyone?
this is my first post... so apologies for idiocy in advance :)

---

### Post by jlacroix on 2005-07-02
VLC plays the DVD's but it's slower than dirt, even with the video settings you said above.

I REALLY want to play them under Totem-xine. Is that possible?

---

### Post by phen on 2005-07-03
did you try to enable DMA for your DVD/CD drive? like this:

sudo hdparm -d1 /dev/hdb  (use your cdrom device...)


this should fix your performance problem!

cheers,
kai

---

### Post by dimec on 2005-07-03
was about to suggest that...
but what about the xines and mplayer not able to play dvds?
i have no problem playing dvds now thanks to vlc, though.

---

### Post by jlacroix on 2005-07-03
DMA was enabled, it isn't anymore. When it was enabled, same problem, and now that its not enabled, still, same problem.

I disabled it because enabling DMA caused Ubuntu not to boot 50% of the time.

---

### Post by kanem on 2005-07-03
[QUOTE=dimec]was about to suggest that...
but what about the xines and mplayer not able to play dvds?
i have no problem playing dvds now thanks to vlc, though.[/QUOTE]
Once I had a problem playing a dvd and got the same error message in xine and vlc as the posts above. I knew I could play dvds because other ones worked. But this one just wouldn't play. I thought it must be some new encryption. What is actually was, I think, is that dvdcss somehow did a bad job at unencrypting this particular dvd. And stored what it thought were the correct key in the usual place: /home/user/.dvdcss/movietitle. So whenver I put this movie in it used these faulty keys and wouldn't play. I fixed the problem by just erasing that folder. The next time I tried to play the movie dvdcss got the encryption right.

If this isn't the problem, I would still suspect its something to do with dvdcss

[quote=jlacroix]Also, when trying to play "Are We There Yet" in Totem-xine, I get this nasty error:```
The audio device is busy. Is another application using it?
```[/quote]
Have you enabled the ability to play [multiple sounds at once?](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple+sounds) You don't have to but it's worth it. If you don't you should probably turn off 'Sounds for events' in System->Preferences->Sound. All those beeps will capture your sound card for 10 seconds or so and if you try to do anything else that needs sound within this time it will give you that error.

---

### Post by jlacroix on 2005-07-03
I had already removed the system sounds, however I have not set up my machine to hear multiple sounds at once. I followed the link you posted and rebooted, but I still get:

```
The audio device is unavailable. Please verify if another program already use it.
```

I also removed my .dvdcss folder before I started to play the DVD. I can assure you that I have no other programs open that make sound.

---

### Post by kanem on 2005-07-03
Durn. Those were all of my ideas. Do other sound applications work, like Rhythmbox?

---

### Post by jlacroix on 2005-07-03
Yeah, I am listening to Virgin Free Radio in Rhythmbox right now. ZSNES, Frozen-Bubble, Chromium, XMMS, etc all have sound. Even the new-mail sound in Evolution works fine.

Are there any logs I can provide to help out?

Anyway, here is some more info on what happens.

1. I put the dvd in.

2. I choose XIne, then click on DVD.

3. DVD plays, previews show with full sound.

4. After previews, I get the DVD main menu.

5. I choose play, and the typical warning screen comes up.

6. Then it just stops with the error I showed above.

I tried Star Trek First Contact, and it plays fine all the way up until Picard is speaking to Starfleet, and then out of nowhere, it crases with that error.

Garfield the movie crashes at the main menu.

A Dragonball Z movie I have, with three episodes on it, will play each episode fine independantly, but when switching from one episode to another, it crashes.

The problems are exactly the same with Xine, Ogle and Totem-xine. Mplayer crashes before the DVD is even initialized. The only thing different between Xine, Ogle and Totem-xine is the error message, but the dvd's crash at the same place every time.

Also, my wife's computer also running Hoary has the exact same problems.

---

### Post by dimec on 2005-07-04
what is the terminal output?

dude, i wish i could help you out...
you started out with the same problems as me, but the vlc player works really well for me.

and, yes i would like to know why xine, totem and mplayer refuses to play dvds - not just refuse but crash.

am trawling the net - will post if something comes up.

PS: the audio in vlc player is not too hot either - otherwise sound in my linux box is way better than xp.

PPS: like you my mplayer crashes even before the dvd is initialized...why? why? why?
 ](*,)

---

### Post by Vesperan on 2005-08-07
[QUOTE=kanem]Once I had a problem playing a dvd and got the same error message in xine and vlc as the posts above. I knew I could play dvds because other ones worked. But this one just wouldn't play. I thought it must be some new encryption. What is actually was, I think, is that dvdcss somehow did a bad job at unencrypting this particular dvd. And stored what it thought were the correct key in the usual place: /home/user/.dvdcss/movietitle. So whenver I put this movie in it used these faulty keys and wouldn't play. I fixed the problem by just erasing that folder. The next time I tried to play the movie dvdcss got the encryption right.

If this isn't the problem, I would still suspect its something to do with dvdcss[/quote]

Sorry to drag up an old thread, but you are my hero kanem.

At the next full moon I will sacrifice three virgin maidens and several neighbourhood animals in your honour. I was scratching my head when a DVD that worked fine on Warty stopped working for Hoary (when every other DVD I tried worked fine).

---

