---
title: "those of you with bad ndiswrapper builds"
date: 2006-01-07
forum: Hardware &amp; Laptops
---

### Post by zahidism on 2006-01-07
ndiswrapper not working?  getting some kind of fatal error when you modprobe?? chances are you didnt compile ndiswrapper at some point correctly. 

**disclaimer: i am a complete noob, im just telling you what worked for me when i was getting some fatal error when i tried to get ndiswrapper into modprobe because i didnt compile ndiswrapper correctly.**

 i suggest googling module-assistant and then i found it, added the repo, updated, and installed module assistant then i ran

> sudo module-assistant auto-install ndiswrapper 


and lo and behold! it's working....actually it's working 100 times better w/ this linux fake driver than the windows one.  in windows my signal strength was iffy (i'm at the other end of the house), now it's always up (i dont know exaclty how or why...but it is and the performance is significantly different)

-z

---

### Post by jesse on 2006-01-07
Which repositories do you use? I can't even get my computer to detect the presence of my wireless card, even though it's inserted and its little green light blinks. 

I tried building ndiswrapper using your instructions exactly, but it ended with dependency errors. 

Do I need to use non-Ubuntu repos? (e.g. Debian)

---

### Post by zahidism on 2006-01-07
[http://packages.ubuntu.com/breezy/misc/module-assistant](http://packages.ubuntu.com/breezy/misc/module-assistant)
universe

add it in your repo, when i did i remembered it gave me some error about it didnt get all of the something but i just clicked ignore or continue because it wasnt needed for the ndiswrapper build.  as far as the dependency errors adding this repo should take care of it.  try it out, then of course you have the task of finding the right driver, wooo

i also remember getting a ndiswrapper.ko fatal error when i modprobed before i compiled ndiswrapper with module-assistant for what it's worth.

---

### Post by jesse on 2006-01-07
Ok. I did all of that and resolved the dependencies, and it still doesn't detect the presence of my card even after reboot.

---

### Post by zahidism on 2006-01-08
hmmm, then it's not ndiswrapper's fault.  it's gotta be something else.  do a lspci in terminal see what you get.

---

### Post by fuscia on 2006-01-08
i could never get ndiswrapper to work. ndisgtk, which i guess is a graphical version of the same, worked great for me. it's available through the synaptic package manager.

---

