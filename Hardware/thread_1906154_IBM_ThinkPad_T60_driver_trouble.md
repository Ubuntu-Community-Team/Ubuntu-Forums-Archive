---
title: "IBM ThinkPad T60 driver trouble"
date: 2012-01-08
forum: Hardware
---

### Post by Rath- on 2012-01-08
I have an ibm thinkpad t60 and i cant seem to get any sound out of my system. also the thinkvantage and volume buttons are unresponsive. i am running ubuntu 11.10 ..and i am dual booting with windows xp. I am assuming i need the drivers because when i got the computer originally everything worked fine. if anyone knows how to find these drivers or if there is a tutorial on how to compile drivers i am more than willing to learn. thank you all in advance.

---

### Post by Rath- on 2012-01-08
Oh and i have  the wine plug-in as well ..im not sure if that matters but as of yet it hasn't seemed to make a difference in my endeavors

---

### Post by Mark Phelps on 2012-01-09
Sorry, don't have the link, but if you look around for the ThinkWiki pages, you'll find some devoted to running Linux on Thinkpads.  The T60 is a common model, so you should have no trouble finding WIKI pages dealing with it.

---

### Post by MoreOrLess on 2012-01-09
You don't need new drivers if the sound worked fine at one point. The drivers are built into the kernel as modules anyway.

The most common way people lose sound is corrupt/incorrect .pulse files, so delete them to generate fresh ones:
```
rm -rf ~/.pulse*
```

If you had sound, the volume buttons would work, though a hack is needed to see an on-screen display (OSD): [https://help.ubuntu.com/community/T60](https://help.ubuntu.com/community/T60)

The thinkvantage button needs to be manually binded to do something: [http://www.thinkwiki.org/wiki/Installing_Fedora_13_on_a_ThinkPad_T60#Audio](http://www.thinkwiki.org/wiki/Installing_Fedora_13_on_a_ThinkPad_T60#Audio)

---

### Post by Rath- on 2012-01-10
Thank you so much guys. all of this was really helpful. :P

---

