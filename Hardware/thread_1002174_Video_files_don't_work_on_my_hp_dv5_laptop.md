---
title: "Video files don't work on my hp dv5 laptop"
date: 2008-12-04
forum: Hardware
---

### Post by Footballer21 on 2008-12-04
Alright I've downloaded all these codecs for GStreamer aka Movie Player and I can't get any video files to play. Such as avi, wmv and even ogg. What happens when I play a video clip is the computer freezes. I can still move the cursor but I can't click on any programs or right click on anything. I am willing to try many solutions to fix this because I don't want to go back to windows. Thanks.

---

### Post by taurus on 2008-12-04
Do you have compiz running?  Try another video player like vlc.

```
sudo apt-get update
sudo apt-get install vlc
```
It now should be in Applications -> Sound & Video.

---

### Post by drpaul on 2008-12-04
Also, say what version of Ubuntu you are using. My experience is that 8.04 works well on my dv6000 series with Intel chips; 8.10 seems to have many problems [for me].

HTH

Paul

---

### Post by Footballer21 on 2008-12-04
I'm using version 8.04 which seems pretty stable overall. I installed vlc and tried a random video clip (it was an avi file) and it played for about 2 seconds and then the screen went blank, the colors of the desktop were all fragmented and weird and then the computer froze (and i seriously mean that I could not move the cursor this time).

---

### Post by drpaul on 2008-12-05
What kind of chips are in your laptop? Have u looked for others that are having troubles with those chips?

In the past, I have had some success with compiling the latest version of the sound software to get around audio problems. Do u have problems with audio only files, like mp3?

Paul

---

