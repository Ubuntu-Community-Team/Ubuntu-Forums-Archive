---
title: "Toshiba P105 No Sound"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by HuXu on 2007-06-30
Card: Intel HDA
Chip: Conexant

screenshot of alsamixer [http://s16.photobucket.com/albums/b28/blueexplore/?action=view&current=myalsamixer.png](http://s16.photobucket.com/albums/b28/blueexplore/?action=view&current=myalsamixer.png)

Problem: I have no sound, how do i install new drivers and where do i get the drivers?

---

### Post by DishBreak on 2007-06-30
[http://ubuntuforums.org/showthread.php?t=205449&highlight=Comprehensive+Sound+Guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=Comprehensive+Sound+Guide)

This is a comprehensive sound guide i found. I use a Toshiba Satellite A135, and I had a similar problem. I ended up just having to edit 1 line of code in a system file. 

[www.alsa-project.org](www.alsa-project.org) will be of great help to you. It will tell you how to set up the drivers. 

Good luck!

---

### Post by xcat442 on 2007-07-01
Hello, This hack fixed my Toshiba A135

It was just one line of code that needed to be added to the **alsa-base** file.

Here's the line. Just don't add it to the bottom of the file.
options snd-hda-intel model=3stack

The line above needs to be above this line.
# Ubuntu #62691, enable MPU for snd-cmipci

Here's the link to the full tutorial.
[http://ubuntuforums.org/showthread.php?t=464020]("http://ubuntuforums.org/showthread.php?t=464020")

---

### Post by HuXu on 2007-07-01
ok i tried that, and it didnt work... should my sound pref's be like this also?
[http://s16.photobucket.com/albums/b28/blueexplore/?action=view&current=Screenshot-SoundPreferences.png](http://s16.photobucket.com/albums/b28/blueexplore/?action=view&current=Screenshot-SoundPreferences.png)

another place advised me to put snd-hda-intel into the /etc/modules file.  So i've done that also.

---

