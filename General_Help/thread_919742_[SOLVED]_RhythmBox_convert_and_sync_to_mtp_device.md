---
title: "[SOLVED] RhythmBox convert and sync to mtp device"
date: 2008-09-14
forum: General Help
---

### Post by lucast on 2008-09-14
I have a Creative Zen V 4gb which is an mtp device.  I have Ubuntu 8.04 and I am using Rhythmbox as my media player.

I have enabled the plugin in Rhythmbox 'Portable Players - MTP' and when my device is plugged in I can see it and transfer music to it (if its in mp3 format)

**_THE PROBLEM:_**

My Zen player dosent support .ogg and most of my music collection is in ogg format.

Can you tell me if its possible when dragging my music in RhythmBox to my Zen player can it convert ogg to MP3 at the same time?

I don't really want to use an external script, I would rather do all this as a drag and drop thing inside RhythmBox.

Any help is much appreciated.

---

### Post by lucast on 2008-09-17
I just plugged the Zen player into a windows machine and have found that when dragging and dropping the files to my Zen player in RythmBox it was actually converting them to MP3, BUT it didn't add the tag info (Artist, Album etc.) and therefore wasn't showing up on my player.

Any idea why It wouldn't add the tag info?

I added the tag data to the files manually on my Zen player and can now play the music, but for some reason there is a minute at the end of each song, where it keeps repeating the last second of the song, like a record is stuck.  Bizzare.

---

### Post by pgilmon on 2009-01-23
In order to enable on-the-fly conversion from oga to mp3 (in order to be able to transfer files to a mp3 device which supports mp3 but not oga/ogg) you should install the package gstreamer0.10-plugins-ugly-multiverse. Then it will work automatically. 

Perhaps there are more packages which are needed. ubuntu-restricted-extras installs a bunch of packages for mp3 conversion and so on. You can also try with that if the above doesn't solve your problem.

---

