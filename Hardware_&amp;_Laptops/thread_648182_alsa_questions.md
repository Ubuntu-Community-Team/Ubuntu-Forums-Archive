---
title: "alsa questions"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by Bartender on 2007-12-23
New Acer 5920 laptop, new Ubuntu 7.10 install with updates.
Alsa website says first thing to do when troubleshooting is unmute "Master" and "PCM".  I've gone into alsamixer via CLI and by using the gnome "speaker" applet.  Neither is showing a Master channel.
I was hoping a few people would look at their rigs and tell me if they see master channels.  

Thanks!

---

### Post by bwhite82 on 2007-12-23
Yes I see the master channel on alsamixer. When you go there is it showing your correct card at the top?

---

### Post by Bartender on 2007-12-24
Well, I'm a little confused about that.  In "lspci" there's a line that says Intel ICH8 Audio.

In alsamixer it says Intel HDa for card, then Realtek AC888 (or something similar) for chip.

I took that to mean that even though it's an Intel Southbridge there's still a Realtek sound chip somewhere on the board.  But I don't know what's what yet.

Any help to figure out exactly what's going on inside would be greatly appreciated.

---

### Post by ugm6hr on 2007-12-24
> **Bartender said:**
> New Acer 5920 laptop, new Ubuntu 7.10 install with updates.
Alsa website says first thing to do when troubleshooting is unmute "Master" and "PCM".  I've gone into alsamixer via CLI and by using the gnome "speaker" applet.  Neither is showing a Master channel.
I was hoping a few people would look at their rigs and tell me if they see master channels.  

Thanks!

Trouble-shooting for what?  Presumably your sound is not working?

Does this help explain?
[http://ubuntuforums.org/showpost.php?p=4009147&postcount=5](http://ubuntuforums.org/showpost.php?p=4009147&postcount=5)

The channels have different names depending on your soundcard.  And sometimes you have to use arrow keys to move past the window border to find some channels.

---

### Post by ebbygonzo on 2007-12-24
I've had issues myself.  After the kernel upgrade, my sound crapped out.  I recompiled alsa and things started to work fine, but after that the gnome "speaker" stopped controlling the sound.  I have to everything through the alsa mixer.  Any way to fix this?

---

### Post by Bartender on 2007-12-25
Hi, ugm6hr -
Yeah, I get only the right chassis speaker in Ubuntu.  Left channel works fine with vista.  Also, headphones don't kill the chassis speakers regardless of "switch" setting in gnome speaker applet.

I'd already read the post you linked.  That's how I found out about the 'alsamixer" function.  Thanks for that!

---

