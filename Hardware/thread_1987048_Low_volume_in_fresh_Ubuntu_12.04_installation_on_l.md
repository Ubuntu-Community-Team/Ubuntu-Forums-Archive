---
title: "Low volume in fresh Ubuntu 12.04 installation on laptop"
date: 2012-05-25
forum: Hardware
---

### Post by devjeetroy on 2012-05-25
Hey guys!
First post here :) .
So I just installed ubuntu a couple of days ago on my laptop, 12.04 and 32 bit. I ran into a couple of issues with 3d acceleration but got that sorted out. Now, when i tried to watch a youtube video today, I noticed that there was no volume. I figured it might be some issue with youtube, or no audio on that video. But thereafter I tried to play multiple videos and songs of various formats, and the volume was really low, and inaudible in other cases. I looked it up on google, only to find that you have to set the master volume using 'alsamixer'(idk if i spelled that correctly). I tried doing that, even saved the changes using the provided command, but the volume would not increase to a comfortable level(although it was better than initially). Do you guys know what the exact issue is? I know that a lot of people have run into this problem. 
If you guys need some diagnostic information, tell me the commands and I will update the post :).
Thanks!

EDIT:
To be clear, there is some audio. The volume is just too low.

---

### Post by kc1di on 2012-05-25
you may have already tried this , go to the volume control and then sound setting at the bottom of the box you see a slider slide it all the way to the right.

---

### Post by devjeetroy on 2012-05-25
> **kc1di said:**
> you may have already tried this , go to the volume control and then sound setting at the bottom of the box you see a slider slide it all the way to the right.

Yup tried all the basics :D

---

### Post by Enigmapond on 2012-05-25
Try deleting the .pulse folder in your home. It's hidden. It will just come back automatically with the default settings.

---

### Post by devjeetroy on 2012-05-25
> **Enigmapond said:**
> Try deleting the .pulse folder in your home. It's hidden. It will just come back automatically with the default settings.

deleted and rebooted. Still didnt work

---

### Post by anubisjap on 2012-09-16
In case of you didn't have fixed the problem, I guess that it is because you didn't select your card. So go in a terminal, write alsamixer end enter
You will see one or many S/PDIF, take the first and hit F6 and choose the name of your card, once it is done, you will see the standard form of alsa and you will have to adjust the sound ...

---

