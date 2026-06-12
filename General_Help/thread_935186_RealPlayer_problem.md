---
title: "RealPlayer problem"
date: 2008-10-01
forum: General Help
---

### Post by kingfourat on 2008-10-01
Hi all,
I like Ubuntu but the problem is that all the video players that work with suck :(

I got Kaffeine but subtitles in it are very small, then I installed MPlayer but it tells me "Error Opening/....", VLC don't read my subtitles. Finally, I downloaded RealPlayer 10.0.9.809, when I open a video it tells me "The player dosen't have the capabilities to play back this content":
[http://img143.imageshack.us/my.php?image=screenshot1jr5.png](http://img143.imageshack.us/my.php?image=screenshot1jr5.png)

And when I click "Check for updates" i get "Your player is up to date":
[http://img363.imageshack.us/my.php?image=screenshot2vs3.png](http://img363.imageshack.us/my.php?image=screenshot2vs3.png)

I think i have installed many codecs including w32codecs

---

### Post by Julius1988 on 2008-10-01
have u tried?(real player 11)
[http://www.real.com/linux](http://www.real.com/linux)

---

### Post by kokkus on 2008-10-01
Kaffeine reads the subtitle files in its default font size.
YOu can use Gaupol subtitle editor or gnome subtitles to change the text size, color and stuff.
Btw, what does this have to do with RealPlayer?

If you need RealPlayer, do following:
Open a terminal window and type in:
sudo apt-get install realplayer
killall gnome-panel

The second command refreshes the GNOME panel.

After that you can find RealPlayer 10 in the Gnome menu under Applications -> Sound & Video.

---

### Post by kingfourat on 2008-10-01
> **kokkus said:**
> Kaffeine reads the subtitle files in its default font size.
YOu can use Gaupol subtitle editor or gnome subtitles to change the text size, color and stuff.
Btw, what does this have to do with RealPlayer?

the subtitles works fine in Windows, and i edited the font size of the subtitles and Kaffeine still show them in small size

> 
If you need RealPlayer, do following:
Open a terminal window and type in:
sudo apt-get install realplayer
killall gnome-panel

The second command refreshes the GNOME panel.

After that you can find RealPlayer 10 in the Gnome menu under Applications -> Sound & Video.

[IMG]http://img221.imageshack.us/img221/5481/screenshotkingkingpcdd5.png[/IMG]

And RealPlayer still can't read any video file

Thank you for your reply

---

### Post by kingfourat on 2008-10-03
So no one knows how solve this ????
(Sorry for up)

---

### Post by Sycron on 2008-10-03
Totem it just works. Also did you tried gxine ?

---

### Post by kingfourat on 2008-10-03
Totem don't read subtitles, I installed gxine from the synaptic and it reads the just like Kaffeine (too small). Is there any way to make realplayer work ?
Thanks for the reply

---

