---
title: "Volume Keys Control Mic Not Sound on ThinkPad T61p with Gutsy"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by MountainX on 2008-02-18
Questions:
1. How do I get the ThinkPad volume keys to control speakers, not mic?
2. Why do I have 3 different ways to control volume, only 1 of which actually works? See background below.
3. What in the world made my sound quit working? (see below).


Background:
Sound was working. I was trying to get wireless networking to work and I also downloaded some updates. Last thing I did was listen to [www.yeswecansong.com](www.yeswecansong.com) then turned off my computer and went to sleep. Next day, no sound.

Here is a summary of my current situation:
1. Speaker icon in control panel does not control speaker volume. I don't know what it controls.
2. ThinkPad volume buttons control mic, not speakers. I want to fix this.
3. I opened main menu > Applicaitons > Sound & Video > volume control and under the playback tab PCM volume was all the way down. I raised the volume and now I have sound again.

I searched a lot of posts, but no solution worked for me. For examplet:
[http://ubuntuforums.org/showpost.php?p=3257208&postcount=1](http://ubuntuforums.org/showpost.php?p=3257208&postcount=1)
Unfortunately, I do not have a choice for PCM only. My choices are:
1. HDA Intel (Alsa Mixer)
2. Analog Devices AD1984 (OSS Mixer)

Also found this one, but no help:
[http://ubuntuforums.org/showthread.php?t=426961](http://ubuntuforums.org/showthread.php?t=426961)

---

### Post by Yellow Pasque on 2008-02-18
Thinkwiki is your friend. The following link mentions how to change the sound keys to control speakers:
[http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p](http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p)
[http://www.thinkwiki.org/wiki/AD1984](http://www.thinkwiki.org/wiki/AD1984)

Note that it mentions installing ALSA 1.0.15. The latest version is 1.0.16 and I would recommend using that if you're going to compile the latest version. Here's a post I made in another thread that has scripts and should make it easy for you ([http://ubuntuforums.org/showpost.php?p=4347257&postcount=2](http://ubuntuforums.org/showpost.php?p=4347257&postcount=2)). As that post says, you  could also try installing backports from Hardy.

---

