---
title: "[SOLVED] Volume control on Thinkpad"
date: 2008-11-10
forum: General Help
---

### Post by rafe101 on 2008-11-10
Has anyone figured out a way to get Ubuntu to quit raising the volume twice?  I know why it's happening, and I've seen some solutions, but I want to keep the Gnome OSD.  It worked before an update a while back.

---

### Post by rafe101 on 2008-11-19
I've really been striking out with my questions lately.

---

### Post by rafe101 on 2008-11-19
I've really been striking out with my questions lately.

---

### Post by rafe101 on 2008-11-23
It's pretty quiet.  I've seen this issue talked about on other sites, but didn't like their solutions.  I would like to have the gnome icons.  Isn't anyone else encountering this?

---

### Post by rafe101 on 2008-12-02
I hate to keep asking, but it really bothers me.

---

### Post by etnoy on 2008-12-13
I did the following, it ain't a fix but at least you won't have to fight the volume control. 
Open the sound settings and choose "CD" as your standard mixing device (I don't exactly know what it says in English, but it's the list on the bottom of the dialog). This way the volume control will just control a dummy device (e.g. the CD mixer) and leaving the hardware controller to do the real work.
This is one nice thing with thinkpads, the keyboard keys for volume control go to the hardware and change the volume without delay, regardless of system load. 

HTH.

---

### Post by rafe101 on 2008-12-13
Thanks, it really does help.  I wonder if I should mark this as "solved" or not.  It's a good work-around, but the problem still exists.

---

### Post by rafe101 on 2008-12-16
As a follow-up, I have the best control over the sound by having it set to [HDA Intel (Alsa Mixer)] and then [Digital].  I do like a few things about the Thinkpads.  I'm very rough on my hardware, and it holds up great—been dropped more times than I can remember and from heights I don't want to.

---

### Post by AnythingBut on 2009-01-07
I'm probably a bit late, but you can also try [http://ubuntuforums.org/showthread.php?t=966588](http://ubuntuforums.org/showthread.php?t=966588)

---

### Post by rafe101 on 2009-01-07
The patch worked great for me, even using it in Hardy.  Thanks a lot.

---

