---
title: "Resizing mplayer video.."
date: 2005-11-03
forum: General Help
---

### Post by f0rmula on 2005-11-03
Whatever I do, when I resize the mplayer video window, the size of the video stays the same.  Just the border round it increases..

Is this a common problem, and is there anything I'm doing wrong? :)

James

---

### Post by pickarooney on 2005-11-03
You need the zoom switch.

I use this alias and associate it with video files:
**alias play='/usr/bin/mplayer -fs -zoom -framedrop'**

---

### Post by btdown on 2005-11-03
I have this same problem...Is there any way to correct it other than the alias?

---

### Post by f0rmula on 2005-11-04
Ahh.. Thanks.

I'll probably move mplayer to mplayer-whatever and create a symlink to "mplayer-whatever -zoom" in the place of mplayer..

Thnkyou

James

---

### Post by pickarooney on 2005-11-04
[QUOTE=btdown]I have this same problem...Is there any way to correct it other than the alias?[/QUOTE]

In the file associations of whatever file manager you use, add the necessary flags.

E.g. in nautilus, navigate to a video file, right-click and select properties,
open with, add, use a custom command and paste /usr/bin/mplayer -fs -zoom -framedrop into the bar that opens up beneath the custom command option.

---

### Post by btdown on 2005-11-04
Thank you for the help. I'll give it a shot....
 
I wonder why this isnt enabled to begin with....

---

### Post by mo_x on 2005-11-04
Try another video output option, for example:
mplayer -vo xv <filename>

---

