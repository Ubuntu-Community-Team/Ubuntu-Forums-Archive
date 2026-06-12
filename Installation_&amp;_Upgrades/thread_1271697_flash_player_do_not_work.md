---
title: "flash player do not work"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by saikas on 2009-09-21
hi,
i just installed jaunty and i cant install flash player. i tried several ways but still no good. i managed to do that videos in youtube was runing, but some flash based websites was not. i think now i have installed to much and even youtube videos dont work. sounds runs good.
can someone could help me and could tell me how remove everything and what to do?

thanx

---

### Post by presence1960 on 2009-09-21
a little more info will help. Are you running 32 bit or 64 bit Ubuntu? Exactly what flash packages have you tried to install?

---

### Post by yoyowazzup on 2009-09-21
Hi saikas,

You should try installing/upgrading this self-installing (best kind) .deb package from Adobe's website.

[http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

-yoyowazzup

---

### Post by fanglinyong on 2009-09-21
yes,download the .deb package from adobe network ,and you will found that it worked good !

---

### Post by presence1960 on 2009-09-21
> **fanglinyong said:**
> yes,download the .deb package from adobe network ,and you will found that it worked good !

if he is running 64 bit that will install 32 bit flash, if it will even run on 64 bit architecture. He should install 64 bit Flash from [here]("http://ubuntuforums.org/showthread.php?t=1259102") if he is running 64 bit ubuntu. that is why I asked for more info.

Don't install until you verify what architecture you are running 32 bit or 64 bit. Then install the correct version of flash for your OS.

---

### Post by yoyowazzup on 2009-09-21
> **presence1960 said:**
> if he is running 64 bit that will install 32 bit flash, if it will even run on 64 bit architecture. He should install 64 bit Flash from [here]("http://ubuntuforums.org/showthread.php?t=1259102") if he is running 64 bit ubuntu. that is why I asked for more info.

Don't install until you verify what architecture you are running 32 bit or 64 bit. Then install the correct version of flash for your OS.

True, however most people who do not post what processor architecture they are running are probably running 32-bit.  And by the way, it works on one of my 64-bit systems just fine, and it will probably fix saikas' problem.

-yoyowazzup

---

### Post by saikas on 2009-09-21
first i run 32 bit system.
second i tried install flash from adobe web and i think its runing, but not very well
how i told befor in some websites every thing is ok,but some well like syfy.com is a mess.
i have installed gnash now, i hoped it wuold help
few days ago i tried karmic and there was every thing ok. there was some problems with installing flash from adobe site so somehow i managed to install it with terminal

---

### Post by snowman4839 on 2009-09-21
Uninstall Gnash and install package "flashplugin-nonfree". Works for me every time.

---

### Post by yoyowazzup on 2009-09-21
> **snowman4839 said:**
> Uninstall Gnash and install package "flashplugin-nonfree". Works for me every time.

Yes, try this if the .deb package didn't do the trick.

-yoyowazzup

---

### Post by saikas on 2009-09-21
ok it helped a little bit youtube is runing, but still other sites where is some flash is still no good. syfy still not working and i tries go to starcraft2 page there is nice cinematic, that loads very slow and after that it is big pause and tha it begins but so slow.
is there any way to bring system to default setings and start over?

---

### Post by presence1960 on 2009-09-21
> **yoyowazzup said:**
> True, however most people who do not post what processor architecture they are running are probably running 32-bit.  And by the way, it works on one of my 64-bit systems just fine, and it will probably fix saikas' problem.

-yoyowazzup
Well the OP is running 32 bit, but that was a lucky guess on your part. I have learned a thing or two in here, one thing i learned is that never assume what someone is running or how their machine is set up.

maybe you are content with 32 bit flash on 64 bit, but really you should run 64 bit software or just install 32 bit ubuntu.

---

### Post by yoyowazzup on 2009-09-21
> **saikas said:**
> ok it helped a little bit youtube is runing, but still other sites where is some flash is still no good. syfy still not working and i tries go to starcraft2 page there is nice cinematic, that loads very slow and after that it is big pause and tha it begins but so slow.
is there any way to bring system to default setings and start over?

You could try reinstalling Firefox in Synaptic (assuming that is the browser you are using).

Although some of the things you mentioned seem like they could be due to a slow internet connection.

> **saikas said:**
> there is nice cinematic, that loads very slow and after that it is big pause and tha it begins but so slow.


What kind of hardware are you using?  If you are running a 64-bit system, then you could try removing the packages you have installed:

(Modify this code if you installed different packages)
```

sudo apt-get remove adobe-flashplugin flashplugin-installer flashplugin-nonfree

```Then reinstall the ones that presence1960 recommended:

[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

Hope this helps.

-yoyowazzup

---

### Post by saikas on 2009-09-23
about speed:) on windows everything runs fine:)

---

