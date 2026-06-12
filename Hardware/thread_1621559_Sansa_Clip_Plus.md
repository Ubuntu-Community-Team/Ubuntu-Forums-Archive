---
title: "Sansa Clip Plus"
date: 2010-11-14
forum: Hardware
---

### Post by bumder on 2010-11-14
Hi,

Its coming up to Christmas, and I'm looking at getting an mp3 player that I can use for running/cycling. Don't really want to go the route of Apple like everyone else does.

The Sansa Clip has caught my eye, as it looks small, cheap and cheerful, plus I can upgrade its memory in the future!

Also, I believe it can be Rockboxed, adding things like album art and games (possibly)

Has anyone got one, and know if they play nicely with Ubuntu 10.04?

(also, would you recommend Rockbox, or just keep the standard menu?)

Cheers

:guitar:

---

### Post by bumder on 2010-11-18
Is everyone an Iphone chimp nowadays then? 

:(

---

### Post by kliffs on 2010-11-18
As far as I know The Sansa Clip will work fine with Ubuntu. Yes I would reccomend Rythmbox. If you use windows as well I have heard there can be problems of windows not seeing music put on by linux and vice versa but otherwise...

---

### Post by cascade9 on 2010-11-20
Sansa Clip (and clip + etc) should work just fine with ubuntu, if fact they should work with just abotu any OS with USB support. 

I wouldnt run rockbox on a sansa clip myself. I'd doubt that you'd get album art support even with rockbox, the sceen looks way to small (if you really, really want album art get an iRiver E100.....be warned, album art only works with MP3s, not ogg vorbis or flac)

> **bumder said:**
> Don't really want to go the route of Apple like everyone else does.

Not everyone...theres more than a few people (like me) who avoid apple because they dont support decent open source codecs. Comon, apple, would it be so hard to add .flac and proper .ogg vorbis support? Ohh, thats right, apple dont want any competition for ALAC and AAC. They also try way to hard to lock people into using iTunes (bleugh!) etc. 

To apple, I, and many others, say "No, thank you Mr. Jobs" ;)

---

### Post by bumder on 2010-11-20
Just ordered a Sansa Clip+ 8Gb for £38.99 from Amazon UK, and with a 32Gb microSD card in the future (when they are cheaper), will give me 40Gb for my entire collection!

Think I will avoid Rockbox, as although an interesting idea to open up old devices, it will bring little benefit to me (and a chance of bricking it!)

Guess you are right on the album art issue, would not really work with the piddly screen!

Apple do make sexy products, but they are way overpriced, and every man and his dog has one (iphones).
They are starting to become very Microsoft-like :(

---

### Post by cascade9 on 2010-11-20
Since (AFAIK) the sansa clip will play .ogg vorbis and .flac, all that rockbox would give you is replaygain (which most people dont use), support for lossless codecs that are in many ways inferiour for portable media players (like .ape, .wv, .shn etc) and some closed lossy codecs that are best avoided anyway IMO (like .mp4 AAC)

---

### Post by ieShae5d on 2012-01-05
[QUOTE]> **kliffs said:**
> As far as I know The Sansa Clip will work fine with Ubuntu. Yes I would reccomend Rythmbox. If you use windows as well I have heard there can be problems of windows not seeing music put on by linux and vice versa but otherwise...
 
@kliffs Yes, this is true. At first, I couldn't get the Sansa Clip+ to be recognized in Joli OS (based on Ubuntu 10.04). I had to switch to MSC mode in the device's settings to get Joli to recognize the device. However, when in Joli OS, I still couldn't see the .mp3 files I had uploaded to the Sansa Clip+ through Windows 7. I'm still seeking an answer as to how to see the music files. I can only see the directories, which appear to be empty in Joli OS.
 
The post seen [here]("http://www.linuxine.com/story/sansa-m250-trouble") describes my very same issue.
 
I may have to try the "solution" outlined in the documentation found [here]("http://help.ubuntu.com/community/SansaClip?action=print"). It's for the Sansa Clip and not for the Clip+, explicitly, but it might still work. It's worth a shot.
 
I may also need to try updating the firmware, available [here]("http://forums.sandisk.com/t5/Clip-Clip/Sansa-Clip-Firmware-Update-01-02-16/td-p/150227") for Windows.

---

### Post by ieShae5d on 2012-01-06
Update: it worked! I already had the latest firmware, version 1.02.16A, and the firmware updater (in Windows 7) wouldn't automatically overwrite the existing firmware with the same firmware. I had suspected that something might have gotten messed up with the firmware -- which was already version 1.02.16A -- that came with the Sansa Clip+ when my girlfriend had originally bought it for me.

To resolve this issue, I first backed up my my music to my hard drive on my laptop with Windows 7 on it.

Next, I formatted the Sansa Clip+ from the Clip+'s settings menu. I then had to download the compressed firmware manually from here to my laptop running Windows 7.

After extracting the .zip file to reveal the .bin file inside, I moved the .bin file to the Sansa Clip+. I removed the Clip+ and USB-to-USB-mini cable from the laptop. After restarting the Clip+, it reinstalled the firmware automatically.

I then turned the Clip+ back on and switched it to MSC mode in the device settings. I connected the Clip+ to my laptop and copied my music files -- most, or all, of which were encoded as .mp3 -- back onto the Clip+.

I unplugged the Clip+ from my Windows 7 laptop and connected it to my Gateway SX2800-01r desktop PC running Joli OS, based on Ubuntu 10.04. Lo and behold, the device mounted and appeared in the Nautilus file manager! Not only could I see the basic AUDIBLE, AUDIOBOOKS, MUSIC, PODCASTS, and RECORD directories on the Clip+, but this time, I could also navigate to the artist directories within the MUSIC directory and could see -- and play -- the music files from the Clip+!  I hope this solution helps someone else!

---

