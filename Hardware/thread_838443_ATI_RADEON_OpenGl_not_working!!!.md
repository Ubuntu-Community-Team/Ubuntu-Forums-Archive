---
title: "ATI RADEON OpenGl not working!!!"
date: 2008-06-23
forum: Hardware
---

### Post by Lildragon88 on 2008-06-23
Hi. Ive had the same graphics card in my pc for quite a while now (ATI Radeon x5550) i recently decided (after a time of using it) that i wanted to set up proper partitions so i could use Ubuntu (linux) and windows on the same pc which was working fine. Anyways i fomatted my hard drive and reinstalled windows then using the partitions i had already made i installed ubuntu. Since then OpenGl has stopped working on windows and ubuntu. Ive tried reinstalling the drivers on windows and ive tried unistalling and reinstalling the drivers provided on ubuntu (intrepid) and neither work. The reason i know that opengl isnt working is ive run tests on windows and ubuntu and also a few of the games i play dont seem to be working properly either (they play fine for 1-10 minutes then the pc crashes and i have to reboot) I hope someone can help

---

### Post by stchman on 2008-06-23
> **Lildragon88 said:**
> Hi. Ive had the same graphics card in my pc for quite a while now (ATI Radeon x5550) i recently decided (after a time of using it) that i wanted to set up proper partitions so i could use Ubuntu (linux) and windows on the same pc which was working fine. Anyways i fomatted my hard drive and reinstalled windows then using the partitions i had already made i installed ubuntu. Since then OpenGl has stopped working on windows and ubuntu. Ive tried reinstalling the drivers on windows and ive tried unistalling and reinstalling the drivers provided on ubuntu (intrepid) and neither work. The reason i know that opengl isnt working is ive run tests on windows and ubuntu and also a few of the games i play dont seem to be working properly either (they play fine for 1-10 minutes then the pc crashes and i have to reboot) I hope someone can help

Install the restricted ATI driver.

```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by Lildragon88 on 2008-06-24
I've tried that but im still getting problems with compiz and none of the games i usually play are working they run for a few seconds then close :( Really not sure what it could be. Is there any program that can test the hardware for problems?? Also if it means anything to anyone reading when i use the ubuntu memory test utility at start up i get a lot of red entries (upto 70 thousand) then my computer makes an error sound (constant) then shuts down. Not sure if this could be related or not....

---

