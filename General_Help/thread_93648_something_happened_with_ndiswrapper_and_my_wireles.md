---
title: "something happened with ndiswrapper and my wireless card"
date: 2005-11-22
forum: General Help
---

### Post by Llewxam on 2005-11-22
i dunno how it happened but out of the blue, ubuntu is not recognizing the wireless card. this is the error i get: SIOCGIFFLAGS error: No such device. it was working perfectly and now it's not even showing in the network admin settings. ndiswrapper is installed and works fine outside of this. if it's needed i have a linksys wpc54g v3. please any little help since i worked on it last night and couldn't find a successful solution

---

### Post by littlepr on 2005-11-22
Did you run any updates/upgrades? This sometimes may be the cause of ndiswrapper shooting the crap.

---

### Post by Llewxam on 2005-11-22
[QUOTE=littlepr]Did you run any updates/upgrades? This sometimes may be the cause of ndiswrapper shooting the crap.[/QUOTE]
outside of the rpm update i haven't ran any updates as of late. certainly none for ndiswrapper either. i do have a certain doubt that it prolly happened after i deactivated the wireless card while at home since i use both lan and wifi (when i'm in my room and when i'm around the house respectively) and i leave them connected at the same time. it was just shortly after that when i got to work that when i noticed this wasn't recognizing it... :confused:

---

### Post by littlepr on 2005-11-22
Try uninstalling the driver for the wifi card and re-install it.

---

### Post by Llewxam on 2005-11-22
i tried with ndis but yea i'm gonna try with the drivers... didn't think of that one.

---

### Post by Llewxam on 2005-11-24
well tried to reinstall the drivers and no. it doesn't recognize the wifi card yet. it's a physical problem it's having. on boot, i get the message that it could not allocate resource. since it goes by so fast that's mostly what i can remember off the top of my head.

edit: 'could not allocate resource 0 something or other of device etc etc...' that's what i see at boot.

---

### Post by littlepr on 2005-11-26
Llewxam,

Have you had any luck un figuring this one? I had the same thing hapen to me after an update available notification which was for kernel ver 2.6.12-9-386. I have not tried to fix it yet because I had to travel  to Florida on Thanksgiving day. Now I am back but to tired to dig into it. Once I figure it out I will post my findings. I have a feeling a pre-compile of drivers and maybe ndiswrapper in conjunction with the latest kernel will be the fix, I hope.

---

### Post by Llewxam on 2005-11-26
well i went into the ubuntu help channel for some help. but i didn't get anything out of that. spent all night tweaking around with the network settings and i managed to fix it. problem is i do not remember what i did 'cause it was almost 5 in the morning -.-

---

### Post by littlepr on 2005-11-28
Well, in my case it was exactly what I assumed. An update of the Kernel is what hosed my wifi driver setup. I had to download the headers for the new updated kernel and pre-compile. Good to know you at least got it working.

---

### Post by zi99y on 2005-11-28
[QUOTE=littlepr]Well, in my case it was exactly what I assumed. An update of the Kernel is what hosed my wifi driver setup. I had to download the headers for the new updated kernel and pre-compile. Good to know you at least got it working.[/QUOTE]

Hey this is exactly what happened to me last night when I went through the newbie kernel recompile howto for the first time. I'm back using the old kernel until I can sort it.

Any more hints for me, I'm not sure how to download headers and pre-comile?!

---

### Post by littlepr on 2005-11-28
zi99y,

Later on tonight I will be on and will be able to help you (8:00 pm New York time) or maybe not (1:00 am for you) I am at work right now. Do you have Skype installed on your PC? If you do I can walk you through the steps with my voice.

---

### Post by zi99y on 2005-11-28
thanks littlepr, that's a very kind offer. But I will be chasing stardust at that time, unfortunately my time is very limited at the moment as I have no home and am staying with family and friends. I'll have a search around and see what I come up with or I'll get back to you

damn you linux people are nice :KS

---

### Post by zi99y on 2005-11-30
woo! I managed to sort it out by following this hand howto: [http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200)

I can barely see XP in my rear view now!

---

### Post by Llewxam on 2005-11-30
it was indeed the kernel update and i also just updated to breezy. only problem i got is that opera is not opening... this is the error i get
maxadiel@B166ER:~$ /usr/bin/opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/8.51-20051114.6/opera: Symbol `_ZTI11QDragObject' has different size in shared object, consider re-linking
/usr/lib/opera/8.51-20051114.6/opera: Symbol `_ZTI10QPopupMenu' has different size in shared object, consider re-linking
/usr/lib/opera/8.51-20051114.6/opera: Symbol `_ZTI7QPixmap' has different size in shared object, consider re-linking
/usr/lib/opera/8.51-20051114.6/opera: Symbol `_ZTI7QWidget' has different size in shared object, consider re-linking
Segmentation fault

---

### Post by littlepr on 2005-11-30
Llewxam,

Good to know have it working and that my suggestion worked. I can't help much with your Opera problem because I personally do not use it. Have you tried uninstalling it and re-installing?

---

### Post by Llewxam on 2005-11-30
yes i have actually. since the version i had was for hoary, i uninstalled it and then downloaded and installed breezy's version off opera's main site. somehow, that is the error i get and i was hoping it would work since i mainly use they keyboard to work around my computers and opera is perfect for that, also i'm used greatly to it's keyboard shortcuts... it's not the same to browse tabs in firefox than it is there. i hope i can get it fixed soon :( and then to move on finally to installing the p5 glove... somehow.... :confused:

---

### Post by Llewxam on 2005-11-30
alright, i just followed the entire wiki and fixed opera as well. phew. god i missed it. and somehow i did not loose all my settings :confused: oh well... joy. now to make it the default browser.

---

### Post by littlepr on 2005-12-02
Llewxam,

I installed Opera on my system. I used it with windows way back in early 2000's but it had the advertising banner. It's different now, no more banner. Pretty neat.

---

