---
title: "TS-L632D - burning and playback problems"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by dogscoff on 2009-07-11
I have strange troubles with my laptop's DVD drive. It's an Asus S96s with a TS-L632D DVD drive, running Jaunty 64. Graphics card is Nvidia 8600M GS running the 180.44 Nvidia driver.
I have libdvdcss, libdvdread, libdvdnav, w32, medibuntu and so on all installed. My DVDs are region 2 (Europe).

- Attempting to write any media in brasero simultaneously says "successfully completed" and gives an error message. The resulting disc is useless. This has been true since I installed Jaunty in April.
- I can burn DVDs in gnomebaker no problems. 

- I can read any CD and home-burned media just fine.
- Older DVDs will play OK.
- Newer DVDs (from about 2008, I think) will not mount and cannot be played in VLC, mplayer or anything else. 
- Strangely, a few of the newer CDs that won't mount (300, Jumper) HAVE worked on this setup before, at the end of May 2009. I have folders for them in .dvdcss so I think something must have been updated since then break playback.

The fact that older DVDs behave differently to newer ones suggests something in the DVD decryption (I'm guessing the olders ones use older/  DRM). However the fact that the problem doesn't seem to be affecting all Ubuntu users everywhere says to me that maybe there's a hardware element. It's beyond me though, I'm not a coder.

I have found other people with the same problem - someone on IRC and some other ubuntuforum threads, for example [http://ubuntuforums.org/showthread.php?p=7600079#post7600079](http://ubuntuforums.org/showthread.php?p=7600079#post7600079) - note the thread mentioned there has the same DVD hardware as me. 

Can anyone else with similar hardware confirm this problem? I would really like o find a fix. Does anyone have any idea what update might have broken playback and whether it can be reverted?

I will glady provide more info to anyone with the skills to troubleshoot this.

---

### Post by dogscoff on 2009-07-24
Playback fixed: I had libdvdread4 installed, but apparently it doesn't work until you run sudo /usr/share/doc/libdvdread4/install-css.sh 

found the command here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I doubt it has fixed the DVD burning issue, but I will try it and report back.

---

### Post by dogscoff on 2009-07-24
I may have been premature - one of my problem DVDs is better, but two others aren't. Curses.

---

