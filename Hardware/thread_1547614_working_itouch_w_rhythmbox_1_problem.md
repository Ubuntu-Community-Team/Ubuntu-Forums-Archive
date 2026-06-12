---
title: "working itouch w/ rhythmbox: 1 problem"
date: 2010-08-07
forum: Hardware
---

### Post by shogo1207 on 2010-08-07
I got the itouch finally recognized by rythmbox, i can delete music off of it and take music from it; i cannot put music on it.  I have tried countless times to drag and drop the song name, the artist name, or album name from lists in music section of rhythmbox.  While dragging the files over to the itouch listed under "devices", it shows the little +file sign like i can drop it, but absolutely nothing happens.

Please Help,
Thanks,
Ubuntu Newbie

---

### Post by IcarusR on 2010-08-07
Sounds like a permissions problem.

Check that your user has write perms to the mount point.

How are you mounting the itouch ?

---

### Post by bwitte on 2010-08-10
When I checked my permissions for my iTouch I saw;
"The permissions of "me" could not be determined."

This is after mounting the iTouch with the supplied USB cord.
How would I change permissions for it?
BTW, same problem, cannot add music to the iTouch via Rhythmbox even though it is 'synced'.

Thanks in advanced for the help!

---

### Post by BoostChild on 2010-08-10
Hi there,

I had the same problem and eventually found it was a permissions problem, im sure there is a work around but for me the easiest solution was to read music off other peoples ipods or yours with Linux and use rythmbox to play the files etc. 

Whilst using xp and itunes to actually save the files to the ipod, i do this with a duel boot system, however im sure the same could be done with wine. 

There have been documented problems in the past with the ipod becoming corrupted by rythmbox etc, how true this is i don't know but maybe worth remembering. 

Rob,

---

### Post by bwitte on 2010-08-12
Rob, 
  running XP is not what I would call help ;-)

---

### Post by bwitte on 2010-08-18
This [http://ubuntuforums.org/showthread.php?t=1467575&page=2](http://ubuntuforums.org/showthread.php?t=1467575&page=2) is what worked for me finally. To summarize; "(sudo gconf-editor in a terminal window), navigated to apps-rhythmbox-plugins-ipod, unchecked "active" in the right pane".

---

