---
title: "No audio (in firefox or VLC) after Jaunty upgrade"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Nathan Otis on 2009-04-25
Greetings all.

My upgrade from 8.10 went off without a hitch, but upon starting anew in 9.04, I have no sound in firefox. I have tried Youtube, and playing mp3 from my own site.

I am also not hearing sound when playing avi files in VLC (or movie player for that matter).

I do have sound when listening to mp3 in audacious.

I have tried a couple of the fixes I've seen for sound issues after the 9.04 upgrade (including setting up Pulse Audio and removing Pulse Audio in favor of esound), but I haven't reached a solution.

---

### Post by _sleeper on 2009-04-25
i, too, face the same problem.

---

### Post by brian.takita on 2009-04-25
I also am having the same problems. This **** is getting old :-(

---

### Post by Zondi on 2009-04-25
Hi, I had a similar problem where I was unable to play any sound however including MP3s. It fixed easily after I found advice in another thread to change all the settings in System>Sound to OSS. This might work for you too.

---

### Post by Nathan Otis on 2009-04-25
System>Preferences>Sound is now set to OSS. I have sound in VLC now after some fiddling. MP3 still works in audacious, but I have no sound in Firefox. I imagine that could be a flash issue (?). I'll start working on that now.

Check that. I'm back to no sound in VLC. I opened it up again to see what settings I was using and I have no audio.

---

### Post by lincsdavid on 2009-04-25
I had the same problem. The following fixed it:

```
sudo apt-get install asoundconf-gtk alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extras

```

(Copy and paste into terminal)

Hope this helps.

---

### Post by noushii on 2009-04-26
Nope, it's not working. 

This upgrade is a pure nightmare, fixing bugs since hours now.

Edit: Anyone else with alsa issues?

---

### Post by noushii on 2009-04-26
Fix'd. 

Had to reinstall adobe-flashplugin ...

---

### Post by Nathan Otis on 2009-04-26
> **lincsdavid said:**
> I had the same problem. The following fixed it:

```
sudo apt-get install asoundconf-gtk alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extras

```


lincsdavid,

I had already made those changes. No help for me. I tried reinstalling the adobe-flashplugin as well, to no effect.

I think I'm going to try a clean install today since nothing else is working. Maybe I'll just roll back to 8.10.

---

### Post by Nathan Otis on 2009-04-26
Interesting... I go to the grub menu and there are no other options besides 9.04. I know I haven't cleared out the older kernals for a while. There should be other options.

Guess it's a clean install for me. Maybe I'll dual boot XP for a while.

---

### Post by spegru on 2009-04-26
I had this problem and just reinstelled flashplayer with new version from Adobe website.
Works ok now

---

### Post by kama-rupa on 2009-04-27
I'm having similar problems. I did a fresh install of 9.04 and immediately noticed the flash bug - I've seen it, or something similar before and just assumed it would get fixed with an update because 9.04 is so new, but then I realised there was more to it than just a flash issue. At first, I had sound with flash, but the video would stop playing after a few seconds and the sound would continue. Then it didn't work at all. Then the computer started making a rapid clicking sound of varying pitches. This all happened without me trying to fix it - just installing various software since I lost it all with the fresh install. Nothing strange - Ubuntu studio, vlc, amarok, etc. 

I realised later that the bug was not just in flash - amarok for instance, wouldn't play a single track - ran through them like there was nothing there. VlC plays video, but with no sound or with the clicking sounds. This is when I decided to try to find a fix - I've tried everything I can find on the net (and I've done quite a bit of searching) and nothing works. 

At one point, it seemed like it was fixed - I got sound out of flash and amarok, but only for a few minutes before it just became the annoying clicking sound. On trying to resolve this, I've ended up with no sound whatsoever unless I uncheck "PCM" in volume control and that only makes an unending clicking sound. Nothing is muted. I've reinstalled pulse. I've followed every guide I can find (lots) I've fiddled with all the settings. 

Very annoying, especially since I didn't have any problem like this in 8.10. I did have a problem like this in Hardy, though, which, after searching for answers for days, I gave up and resolved it with a fresh install. I really hope I don't have to do that with 9.04.

---

### Post by spegru on 2009-04-28
This sounds like a sound problem, not a flash or VLC problem.
Are you running KDE (you have Amarok)?

If so it may be worth looking under system settings and checking out multimedia and lloking at sound devices and backends to see whether phonon is really using the appropriate system.

Even if you are not using Kubuntu, the fact that you have Amarok could still mean that there is enough KDE4 stuff in there to have the same effect. You can also install the system settings applet under gnome which should give you access.

---

### Post by caveman59330 on 2009-04-28
I am having the same problem and after tons of fiddling and researching on the internet am able to get sound while playing music but cannot get sound if I go to Youtube or anything like that.This really sucks I hope someone finds a working solution cause I am about ready to go to a older version of Ubuntu that works.My experience with Jaunty hasn't been great at all.I had really high hopes for Jaunty and I feel let down.

---

### Post by Will Hanley on 2009-04-28
I tried various things, and finally reinstalling the flash plugin worked.

How to (because I seem not to know even the most basic functions, and I imagine others are in the same boat):
a) System>Administration>Synaptic Package Manager
b) type "flashplugin" in the Quick search box
c) right click the box for "flashplugin-nonfree"
d) select "Mark for Reinstallation"
e) do the same for "flashplugin-installer" (not sure if this is necessary, but I did it)
f) click Apply
g) wait for it to finish
h) audio should now work (maybe you'll need to restart first)

---

### Post by Nathan Otis on 2009-04-28
> **Nathan Otis said:**
> Interesting... I go to the grub menu and there are no other options besides 9.04. I know I haven't cleared out the older kernals for a while. There should be other options.

Guess it's a clean install for me. Maybe I'll dual boot XP for a while.

Hey all... Wanted to let you know the result. I installed XP and partitioned the drive for dual booting during that process. Then installed Jaunty. Both OSes work fine now. The sound issue seems to have been with flash and in a clean install of Jaunty was very easy to fix.

Thanks to all.

---

### Post by adm1968 on 2009-04-28
> **kama-rupa said:**
> I'm having similar problems. I did a fresh install of 9.04 and immediately noticed the flash bug - I've seen it, or something similar before and just assumed it would get fixed with an update because 9.04 is so new, but then I realised there was more to it than just a flash issue. At first, I had sound with flash, but the video would stop playing after a few seconds and the sound would continue. Then it didn't work at all. Then the computer started making a rapid clicking sound of varying pitches. This all happened without me trying to fix it - just installing various software since I lost it all with the fresh install. Nothing strange - Ubuntu studio, vlc, amarok, etc. 

I realised later that the bug was not just in flash - amarok for instance, wouldn't play a single track - ran through them like there was nothing there. VlC plays video, but with no sound or with the clicking sounds. This is when I decided to try to find a fix - I've tried everything I can find on the net (and I've done quite a bit of searching) and nothing works. 

At one point, it seemed like it was fixed - I got sound out of flash and amarok, but only for a few minutes before it just became the annoying clicking sound. On trying to resolve this, I've ended up with no sound whatsoever unless I uncheck "PCM" in volume control and that only makes an unending clicking sound. Nothing is muted. I've reinstalled pulse. I've followed every guide I can find (lots) I've fiddled with all the settings. 

Very annoying, especially since I didn't have any problem like this in 8.10. I did have a problem like this in Hardy, though, which, after searching for answers for days, I gave up and resolved it with a fresh install. I really hope I don't have to do that with 9.04.

[FONT="Georgia"]No sound here either!
At first I noticed the bug with Amarok ONLY
Now there is simply NO sound whatsoever

Any ideas???[/FONT]

---

### Post by kerryhall on 2009-04-28
This may or may not be helpful to anyone:

I upgraded to Jaunty from Hardy. I had no sound in Firefox, but sound in all other programs I tried. I installed adobe-flashplugin and restarted Firefox, and now I have sound. Not sure what plugin I was using before. Perhaps that plugin got broken with the upgrade?

---

### Post by XetrovNocilis on 2009-04-30
Add me to the list.  It sure looked like a conflict between flash and Jaunty.  I purged the flashplugin, installed and had nothing.  Stopped all sound apps, purged flash and rebooted.  Installed the flashplugin and suddenly, it works again.  Checked it on a few sites, few different uses and it looks like that did it.

Started up Amarok, listened to some music for a while.  Now sound through flash doesn't work anymore.

Quit Amarok, and the flash sound works again.  Looks to be general problem with the mixer(?not sure what controls the sound channels) only allowing one sound source in the system.  Once that source has captured the audio device no other sounds can be played until the source process is killed.

No idea how to fix this though, but it is a start I hope.  I'll keep looking and if I find something I'll be sure to post back.  This is highly annoying.

XN

---

### Post by bitf on 2009-04-30
I had a similar problem, running recovery mode fixed it.

---

### Post by max.bellicini on 2009-05-01
I had the same problem, but upgrading to Adobe FlashPlayer 10 fixed the "no sound in Firefox" problem.

Hoping it can help..

Massimo

---

### Post by bardiax on 2009-05-07
WoW .  :)
Fixed (No sound in VLC , firefox) (Kubuntu 9.04 Jaunty)

```
sudo apt-get remove libpulsecore9 pulseaudio pulseaudio-esound-compat pulseaudio-module-hal pulseaudio-module-x11 
```

---

### Post by mrdak on 2009-05-07
YO Bardiax....................... That works.....  and will probably work for the majority of us.\
Thanks

---

### Post by mescaleeto on 2009-05-08
removing pulseaudio worked for me as well

---

### Post by rth88 on 2009-05-11
Newbie here... this problem was/ is killing me. I was testing vlc and noticed that some movies would play sound and some wouldn't. avi wouldn't, mkv would. So I i tried playing them with gxine. It flashed that sound was not available. So I try the windows method of the "end process". Ended the pulseaudio process. Frickin worked. Go figure. Now sound is played. Why won't the process shut down properly?

---

### Post by nbayiha on 2009-05-12
bardiax Thanks for your advice it did help me a lot. And for sure will help a lot of people out there . I did follow you instruction after that i change back my sound preference to alsa and it work as a charm.
Thank to you i didn't had to do a clean instalation :D

---

### Post by AnalogWeapon on 2009-05-17
Just an update on this. I was having the same problem after the upgrade (No audio in firefox). Not sure if it will work for everyone but going to Synaptec Package Manager and reinstalling all of the firefox packages did the trick for me. That might have included adobe-flashplugin through a metapackage; not sure. But itworked for me, so I thought I'd mention it.  :)

---

### Post by roameo on 2009-06-10
bardiax you total legend. that worked a charm!

---

### Post by andy_foley on 2009-07-24
I had dreadful problems trying to get sound in Firefox. I even uninstalled Firefox and installed Epiphany (a good simple little browser by the way) but I still couldn't get sound in the browser, such as from YouTube. I'm using Jaunty 9.04 (my 1st ever Linux installation) with 2 sound cards: the system's own Intel 82801 and my own installed C-Media CMI8738. With some tinkering I could get VLC, MoviePlayer, Audacity etc all playing audio fine, but still not the browser.

I must have tried almost every fix on every forum, fiddling with PulseAudio, ALSA and OSS. After trying all the installs and un-installs in the forums, this is the one that worked for me, with good explanations as to how Pulse Audio works:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

It's so good I've printed it off to keep with my Ubuntu manual!

The only extra thing I had to do was go into System>Prefernces>PuleAudio Preferences, and on the Simultaneous Output tab click the box to enable output on all cards. For some reason without this enabled I lost the browser sound again. This does mean I have sound playing from both cards, but I've cabled one card to the computer speakers and one to my TV/Hi-Fi system - one for work, one for parties, which suites me!

It was interesting to read that the flash plugin libflashsupport, given as a Firefox / flash fix in many forums, does NOT work and should be removed if you have it installed!

The link has fixes for Hardy and Intrepid as well as Jaunty.

Good luck! :)

---

### Post by kama-rupa on 2009-10-18
I went at this for about a week before giving up. Fiddling with ALSA/Pulse changed the problem but did not fix. I tried every possible combination. I searched every forum and tried every solution and still nothing. Tried clean install of flash and nothing. Since I have a desktop that runs 9.04 fine and never had a problem I concluded that the issue had to be the new version and compatibility issues with my hardware that hadn't been addressed yet. After days of headache I reinstalled 8.10 and haven't had a problem since. Also, too afraid to try 9.04 again.

---

