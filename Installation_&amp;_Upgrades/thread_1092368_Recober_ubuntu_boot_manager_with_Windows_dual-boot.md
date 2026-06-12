---
title: "Recober ubuntu boot manager with Windows dual-boot."
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by ScavengerProductions on 2009-03-10
Hi,
I got this school-pc where I'm forced to have a XP and Vista, (now changed for Windows 7). This is OK. 
However, I have Ubuntu on it as well. But when I updated to the newest Windows 7, it promptly removed my ubuntu boot manager. 
I want it back!:eek: But without harming my current Windows dual-boot. 

The computer is a Lenovo R61i with a 160GB HDD. With five partitions. One is about 50GB for XP, 50GB for Windows 7, 45GB for a DATA and 12GB for my Ubuntu with a 2GB swap. 
I am a complete newbie and therefore require a step by step guidance. The ubuntu is the Ultimate Edition.

Help will be immensely appreciated.

---

### Post by cariboo on 2009-03-10
Follow this [howto]("http:///ubuntuforums.org/showthread.php?t=224351"), to repair grub.

Jim

---

### Post by Neo_The_User on 2009-03-10
Terminal:

```

sudo update-grub

```

might help as well or you can edit menu.lst by hand and configure everything your way.

---

### Post by ScavengerProductions on 2009-03-10
Thanks for responses. 
But two problems: the link you gave didn't work and i don't have access to my ubuntu installation. (or can I do it with a Live CD?)

---

### Post by Neo_The_User on 2009-03-10
Well you can always edit menu.lst from livecd. Its kind of a pain if this is going to be your first time so if you wanted me to teach you, the guide would have to be pretty in-depth.

---

### Post by ScavengerProductions on 2009-03-10
Ok. Is it possible for you to do it? 
I'm not a absolute complete newbie. I have been doing some things, I understand some basic stuff in the terminal. But I don't know the "logic" in it so I can't figure out what to do. If you know what I mean. Difficult to explain. You can say that I have a head for PC's.

---

