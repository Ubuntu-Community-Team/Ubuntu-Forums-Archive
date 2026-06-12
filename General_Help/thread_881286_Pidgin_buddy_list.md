---
title: "Pidgin buddy list"
date: 2008-08-05
forum: General Help
---

### Post by merrif on 2008-08-05
Heyas!

As the total newbie I am I managed to clear my buddy list in pidgin. After bootin in xp and checking msn I realised that I (thankfully) didnt delete my buddy list on msn server. After trying to google for my answer i found out that Pidgin stores the buddy list locally, and I did find out that in Windows if you delete it, it will retrive a new one next time you start the program. My question is if its same way in ubuntu? And whats the name of the file? Or is there any way for me to get my list back without having to readd everyone?

:(](*,)

---

### Post by y-lee on 2008-08-05
> Pidgin stores the buddy list locally, and I did find out that in Windows if you delete it, it will retrive a new one next time you start the program. My question is if its same way in ubuntu?

Look for the file blist.xml located /home/username/.purple where *username* is your username.

Note .purple is a hidden folder so if you use nautilus you have to selected show hidden files under the view menu.

---

### Post by merrif on 2008-08-06
thank you

---

### Post by y-lee on 2008-08-06
> **merrif said:**
> thank you

Hey No problem. Hope that works for you and btw we have a system in place to thank people. Click the yellow star for the post you wish to thank.

---

### Post by totlinuxnewbichik on 2008-12-22
I had the same thing happen to me this morning. I woke up to find my Pidgin buddy list sitting there with 1 contact in it. I found the .purple folder and opened it. Now what? :confused: (And, yes, I know anyone reading this is probably pulling their hair out at my vast wisdom but, hey, that's what I'm here for!)

---

### Post by y-lee on 2008-12-22
> I woke up to find my Pidgin buddy list sitting there with 1 contact in it. I found the .purple folder and opened it. Now what?

You delete the file blist.xml located /home/username/.purple  and pidgin should recreate it :)

---

