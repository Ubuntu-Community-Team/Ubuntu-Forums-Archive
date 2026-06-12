---
title: "Yet another sound post"
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by fluideye on 2005-07-02
I have been reading the sound posts over the last couple of months.  I was able to get sound working properly on my Averatec 3270 but I  installed Hoary on my Dell Dimension 3000 a couple of days ago and have had no success.  I am able to get system sounds but can't hear my cd playing with xmms.  I disabled my onboard sound and installed Ensoniq AudioPCI chip Cirrus Logic CS44297A rev4.  Any ideas to why I can't hear CD's?

---

### Post by PMO6022 on 2005-07-02
In a console type[b]:
[/b][b]alsamixer

[/b]This will bring up a mixer in your console window.  Make sure the appropriate settings are unmuted and turned up.  Look for "CD" in particular.

Do you have other sounds besides just cd's?  You could also look at the preferences menu under xmms.

---

### Post by fluideye on 2005-07-02
I've followed all the "alsamixer suggestions" but now I'm thinking it's a problem specific to xmms because I am able to play CD's through totem (doesn't sound very good however).  I don't know if I'm missing some dependencies or what.

---

### Post by PMO6022 on 2005-07-02
[QUOTE=fluideye]I've followed all the "alsamixer suggestions" but now I'm thinking it's a problem specific to xmms because I am able to play CD's through totem (doesn't sound very good however).  I don't know if I'm missing some dependencies or what.[/QUOTE]
 First of all, can you play mp3's in xmms?  Is it just audio cd's that you don't hear?

In xmms go to "Options" -> "Preferences".  What output plugin is selected?

Click CD Audio Player, then configure.  What does it say under devicd and directory?  Is Analog or Digital audio extraction selected under Play mode?

---

### Post by fluideye on 2005-07-02
Thanks PMO6022, it's working now, analog was selected.

---

