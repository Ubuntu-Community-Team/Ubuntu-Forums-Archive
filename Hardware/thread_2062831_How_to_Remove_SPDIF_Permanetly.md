---
title: "How to Remove SPDIF Permanetly"
date: 2012-09-25
forum: Hardware
---

### Post by shifattk on 2012-09-25
I recently switched to Ubuntu 12.04 on my Toshiba laptop. I haven't had any issues except for one.

I realized that there is a red light coming out of my earphone jack. It's something like this: [http://i.stack.imgur.com/gokuH.jpg](http://i.stack.imgur.com/gokuH.jpg)

I also found out that when I mute the speakers, the light goes away. But when I unmute it, it comes back.

I don't mind having this but since my laptop is 2 years old, the battery drains a bit faster because of this.

I tried this but it never worked :

[LIST]
[*]Open Terminal by Ctrl + Alt + T
[*]Type in sudo alsamixer
[*]Use the arrow keys to move around and when over S/PDIF press M to mute
[*]Hit the Escape key.
[*]Type sudo alsactl store
[/LIST]

So I want to know how to disable it permanently without using alsa, because it does not seem to work.

I knew a way to do this in older Ubuntu 9 and 10 but when the developers decided to put in Unity, it messed everything up and I don't know where everything is. (It kinda feels like switching from XP to Vista :P )

---

