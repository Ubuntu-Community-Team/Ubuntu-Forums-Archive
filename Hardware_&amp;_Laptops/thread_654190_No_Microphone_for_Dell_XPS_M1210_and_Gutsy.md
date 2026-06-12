---
title: "No Microphone for Dell XPS M1210 and Gutsy"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by damnhappy on 2007-12-30
I am trying to get my external line mic to work with Skype, WOW and Teamspeak.  Ive read the posts here and some on Dell Support and also google, and I can't find a solution. Any suggestions would be appreciated. 
I have a Dell XPS M1210 laptop with Gutsy. 
It is a Sigmatel STAC 9221 card.

---

### Post by linuxwizard on 2007-12-30
Look over these. You might have already seen them.

[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

Also might be something here
[https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1210](https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1210)

---

### Post by luzdegas on 2008-01-01
I have exactly the same notebook as yours, running under Gutsy. I've solved the problem recompiling the alsa drivers from scratch, modifying the patch_sigmatel.c. I've basically followed this thread  

[http://mailman.alsa-project.org/pipermail/alsa-devel/2007-June/001414.html]("http://mailman.alsa-project.org/pipermail/alsa-devel/2007-June/001414.html")

but in the newest version of the alsa drivers (1.0.15) there is an especial variable for the case of XPS M1210 (and for some reason this still does not work by default!). If you edit the code of the patch you will find it documented. I modify the 3rd value of the array replacing exactly the same digit as the post said by an hexa 'A'. Then I recompile the drivers, installed them and the mic started working (but **without** the "model=ref" suggestion, because that made the mic not working again)

---

### Post by damnhappy on 2008-01-03
I appreciate the help, and I actually ran across that in my search, but it seems a bit out of my league at the moment. Any other suggestions?

---

### Post by latencianeuronal on 2008-02-20
so, you use de drivers from alsa, compile and everithing is ok, i can just download from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download), decoment, and compile, and everything is gonna be ok?,

---

