---
title: "Sound and other problems"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by Shay Guy on 2008-03-02
Hello, all.

I recently got a new HP Pavilion dv6700t, and one of the first things I did was install Ubuntu 7.10 on it. Currently, I'm having a variety of problems:

[LIST=1]
[*]There's no sound. At all. No matter what I adjust.
[*]My university uses [WebCT](http://en.wikipedia.org/wiki/WebCT), and whenever I try to access it in Ubuntu, Firefox freezes up. It works fine in Vista.
[*]A whole bunch of problems with MPlayer, including the GUI not working and subtitles not rendering properly. (Of course, the lack of sound is a bigger problem.)
[/LIST]

For reference:
```
 lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

---

### Post by loserboy on 2008-03-02
[http://ubuntuforums.org/showthread.php?t=582220&highlight=dv6000](http://ubuntuforums.org/showthread.php?t=582220&highlight=dv6000)

my friend has a dv6000 and we had to put feisty on it just to even get it going....couldnt even boot with gutsy.

theres some good stuff here [http://ubuntuforums.org/showthread.php?t=512059&highlight=dv6000](http://ubuntuforums.org/showthread.php?t=512059&highlight=dv6000)

---

### Post by Shay Guy on 2008-03-02
...Crap. So, what, I'm screwed? Should I just burn 7.04, remove 7.10 altogether, and reinstall?

---

### Post by superprash2003 on 2008-03-03
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by loserboy on 2008-03-03
[http://ubuntuforums.org/showthread.php?t=523733&highlight=ICH8+Family](http://ubuntuforums.org/showthread.php?t=523733&highlight=ICH8+Family) this has some info about sound, maybe helpful, maybe not

i started googling around for help on your problem and noticed that alot of people say gutsy often breaks sound for people.

I dont think you're screwed, but if you can't find anything to fix it, i would suggest testing feisty before giving up.... not sure how long you've been messing with ubuntu, but gutsy reminds me of edgy (6.10)... it had a lot of neat new stuff, but it seems like they took a step back on other stuff.

---

