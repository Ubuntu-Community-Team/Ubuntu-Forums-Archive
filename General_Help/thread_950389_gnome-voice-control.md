---
title: "gnome-voice-control"
date: 2008-10-17
forum: General Help
---

### Post by agim on 2008-10-17
I just downloaded gnome-voice-control from the repos. Now I can't find the program. Someone help!

---

### Post by ajmorris on 2008-10-17
> **agim said:**
> I just downloaded gnome-voice-control from the repos. Now I can't find the program. Someone help!

hi there,
In your synaptic GUI, you can select in options, to show installed files, or with apt you can apt-get install apt-file and use that to list the installed files of that package. However, i am assuming that the binary/script for that package, will be in /usr/bin  and most likely /usr/bin/gnome-voice-control
Also, is it not in your gnome menus... under Applications --> Multimedia or something?

Aj

---

### Post by /////// on 2008-10-17
gnome-voice-control is a panel applet, right click the panel at the top, go to add to panel and then double click on voice control

---

### Post by ajmorris on 2008-10-17
heh, my bad, didnt realise that it was a panel applet.

---

### Post by wjwh on 2009-03-06
> **/////// said:**
> gnome-voice-control is a panel applet, right click the panel at the top, go to add to panel and then double click on voice control

Unfortunately, this doesn't work on my machine (in 8.04).  I get a message:

*"The panel encountered a problem while loading "OAFIID:GNOME_VoiceControlApplet"."*

Any other suggestions?

---

### Post by wjwh on 2009-03-09
> **wjwh said:**
> Unfortunately, this doesn't work on my machine (in 8.04).  I get a message:

*"The panel encountered a problem while loading "OAFIID:GNOME_VoiceControlApplet"."*

Any other suggestions?

I have now found the answer to my problem here:

[http://ubuntuforums.org/showpost.php?p=5253985&postcount=10](http://ubuntuforums.org/showpost.php?p=5253985&postcount=10)

What I do find surprising is that this problem was solved nine months ago, yet the package in the repositories has not been corrected and no patch has been added to the update system!

---

### Post by jakupl on 2009-05-29
> **wjwh said:**
> I have now found the answer to my problem here:

[http://ubuntuforums.org/showpost.php?p=5253985&postcount=10](http://ubuntuforums.org/showpost.php?p=5253985&postcount=10)

What I do find surprising is that this problem was solved nine months ago, yet the package in the repositories has not been corrected and no patch has been added to the update system!

almost a year now and still nothing... Why is there absolutely nothing happening in linux speech recognition... maybe they need a good and hard donation.

---

### Post by mofrikaantje on 2009-06-01
> **jakupl said:**
> almost a year now and still nothing... Why is there absolutely nothing happening in linux speech recognition... maybe they need a good and hard donation.

Or the possibility to compile from source, so more options can be added by other users... I've been struggling for like HOURS to get it to compile, and always that same gcc error message... Really frustrating :(

---

### Post by rvk on 2009-08-21
I am not a coder myself, but I think it is possible to [download the code for gnome-voice-control here]("http://live.gnome.org/GnomeVoiceControl"). I know that the [current maintainer of gnome-voice-control]("http://live.gnome.org/NickolayShmyrev") is very busy and would love to get some help. I am also looking forward to your improvements ;)

By the way, some time ago I helped to set up the collection of Dutch speech at VoxForge and we need much more to get decent acoustic models for the Dutch language. So if you speak Dutch, please help!

Also, it is probably better/faster to ask questions about speech recognition at the VoxForge forums or at some other more specialised forum.

---

### Post by GaaraOfDSand on 2009-09-19
I used synaptic to install gnome-voice-control in Xubuntu, it installed without any errors, but when I try to add it in the panel, I can't find it in the list, any help please? Or does it work on Xubuntu at all?

---

### Post by Rodnox on 2009-09-29
its listed on the very bottom as "Voice controler" ..

Standart commands are:

Run Terminal
Run Mail (Evolution by default)
Run Browser (Ephany by default)
Run Text Editor
maximize window
minimize window
close window
next window (changes windows in order)

---

### Post by GaaraOfDSand on 2009-09-30
Thanks and sorry for the late reply, with more research I learned that I had to have some options turned on..

---

### Post by cabez0n on 2009-10-20
Any of you got this to run correctly on amd64 ?
I can source compile latest version but it doesn't seem to add the panel applet to the list so I can't add that applet.

---

