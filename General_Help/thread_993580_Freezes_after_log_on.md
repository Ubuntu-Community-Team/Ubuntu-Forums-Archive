---
title: "Freezes after log on"
date: 2008-11-25
forum: General Help
---

### Post by oomar on 2008-11-25
System:
Crappy Dell D610
Problem: 
Freezes up or at least moves very very very slowly so i cant do anything. Including opening up the system stuffs to figure out the problem.
Solution I want: 
Some way to fix the problem short of reinstalling the system. Something like through the command line cause i can do that just fine.


anyway yea. it sucks. I boot up. it starts fine. A little slower than it used to and then i log in. then it takes forever to load all the icons and now the panel wont even fully load. I come up with an error saying the volume control didnt load right. Though I suspect that to be a side effect of it working bad since its the first time its ever done that.
After this i try to click on system or anything that I could to try and disable what ever is slowing it down but it is simply too slow. Ive been waiting for like 35 min for the system tab to come up and it simply... hasnt. so I really need help. Im beyond noob level but... alas not really that good lol. Please help


Thanks

oomar
logan Collins
T.D.

---

### Post by sstusick on 2008-11-25
You could try making a new user account, to see if its just your current account that is screwed up. If that's the case, then you can easily transfer all your files and settings from one account to the other.

---

### Post by oomar on 2008-11-25
sounds great!
one problem. lol how do i do that from terminal? cause i cant through any form of GUI as it freezes up pretty much instantly.

---

### Post by sstusick on 2008-11-25
In the terminal, type  > sudo adduser <username>

---

### Post by theozzlives on 2008-11-25
```
sudo adduser username
```

---

### Post by oomar on 2008-11-25
haha oh thats annoying... umm while im waiting for it to do its mandatory HD check:

will that account have administrative privilages or do i need to add something for that?

EDIT: oh and whats with the real name username thing? not sure i get it.

---

### Post by oomar on 2008-11-25
alright well it seems to just be my default acc thats the problem. 

i think it might be that i added like 4 other language packs to the computer. any other slightly more intelligent idea as to why it would freeze up like it does?
EDIT: oh and now that ive logged in on my new account... it doesnt exactly have adminitrator access... help?

---

### Post by theozzlives on 2008-11-25
> **oomar said:**
> haha oh thats annoying... umm while im waiting for it to do its mandatory HD check:

will that account have administrative privilages or do i need to add something for that?

EDIT: oh and whats with the real name username thing? not sure i get it.

just go with the adduser

---

