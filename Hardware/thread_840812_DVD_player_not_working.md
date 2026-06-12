---
title: "DVD player not working"
date: 2008-06-25
forum: Hardware
---

### Post by waapwoop1 on 2008-06-25
I have a compaq Evo N610c

The cd player/dvd player works. I can read cds and dvds ok. I can see the data.

When i first put a dvd in the drive, Totem opened up and downloaded codecs. Then it tried to play, and it says "**An error occurred: could not read from resource**"

I have tried 2 different dvd players in my laptop.

I installed VLC media player to see if it was the player, and when i open up a dvd disc, and it opens a bigger screen, then closes it without saying anything.

On the desktop, it says the name of the movie and everything, tried different dvds too.

The reason i think it is Ubuntu, is that i've tried different dvds, different hardware, different players. Can someone help/

---

### Post by Odrodzona-Sarmacja on 2008-06-25
Uninstall totem package and all related packages?

---

### Post by waapwoop1 on 2008-06-25
Well why would it not work on two seperate DVD playing software packages?

---

### Post by waapwoop1 on 2008-06-25
In the properties of the DVD I have:

Label: 
Size: 7.1Gb
Media: DVDROM Disc
UUID:
File System: udf

Mount Point: /media/cdrom0
File System: udf
Mount Options: ro nosuidnodev relatime

---

### Post by waapwoop1 on 2008-06-25
should the device be /dev/scd0  if that is the only one i have?

---

### Post by waapwoop1 on 2008-06-26
Any suggestions why a dvd player can read dvds but can't play them, I am pretty sure i have the codecs. And VLC usually plays anything in windows, i am assuming the same for linux.

---

### Post by westdo03 on 2008-06-26
I have the same problem, help! wanna watch the movie!

---

### Post by waapwoop1 on 2008-06-26
I tried following these instructions:  [https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-dvd)

I had two problems.

one i can't find dvdplay0 in the repositories. I have found the rest.

I installed gxine. then "Press System &#8594; Preferences &#8594; Removable Drives and Media and click on the Multimedia tab."   **there is no multimedia tab**

---

### Post by waapwoop1 on 2008-06-26
> **westdo03 said:**
> I have the same problem, help! wanna watch the movie!

I got it working now.

[http://linuxoutlaws.com/forums/viewtopic.php?f=9&t=351](http://linuxoutlaws.com/forums/viewtopic.php?f=9&t=351)

installed the restricted extras.

This didn't work. So i restarted, then installed teh updates from update manager. And now dvd playback works.

---

### Post by rainwalker on 2008-06-27
> **waapwoop1 said:**
> I tried following these instructions:  [https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-dvd)

I had two problems.

one i can't find dvdplay0 in the repositories. I have found the rest.

I installed gxine. then "Press System &#8594; Preferences &#8594; Removable Drives and Media and click on the Multimedia tab."   **there is no multimedia tab**

Those instructions were probably for Gutsy or an earlier relesae, just FYI

---

