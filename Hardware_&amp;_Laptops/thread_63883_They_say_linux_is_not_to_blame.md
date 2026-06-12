---
title: "They say linux is not to blame"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by Benzimm86 on 2005-09-09
Alright so here is the deal. Yesterday i got home from work and was going to burn a cd in Windows Xp Pro. I put the cd in the drive, went into nero, did what i had to do then i clicked burn and it asked me where i wanted to save the file. I thought this was odd since it never asked me to do this before. So i further researched, went into "my computer". Hey no cd drives. Im like ok well i will go check out the device manager. Well there you go there is a problem with my drives. So i reinstall the drivers, go to windows update and nothing works. I then go into event viewer and find an error of 
The following boot-start or system-start driver(s) failed to load: 
Cdrom
Event id: 7026 Source: service control manager
So i go to [www.eventid.net](www.eventid.net) and check out what the deal is and it tells me to go into bios and turn on my caps lock, num lock, and scroll lock, then reset my bios and then start up windows. well first of all how would this fix anything, caps lock being turned on ooook. well this didnt work either.

Then I remember a few days back i just recently installed ubuntu on an extra 40 gig partition i had that was not being used. so i went into ubuntu and hey my drives work just fine. 

So here is my question. Why do my cdrom drives work in linux and not in windows.

I put this on a different forum but they say its not fault of linux so i bring my problem here.
This is my post from the other forum if you want to see what they had to say
[http://www.tech-forums.net/showthre...&threadid=69990](http://www.tech-forums.net/showthre...&threadid=69990)

---

### Post by earobinson on 2005-09-09
i dont understand linux did not break your drivers in windows but you want help with your windows drivers from a linux forum.

you may be thinking that windows and linux use the same drivers but they do not.

---

### Post by Benzimm86 on 2005-09-09
no what i am saying is that the drives worked fine until i installed windows all of a sudden.  Now the drives do not work in windows. I am wondering if it is possible that the linux install could have screwed up my windows drives seeings thats when they stopped working in windows.

---

### Post by oneybm on 2005-09-09
Okay, between looking at the two different post you have made you have confused the heck out of me.  In  the first you state that you used Nero, Windows program, to burn a CD in Windows and that it didn't work there.  But in the second post you say almost the opposite by mentioning that the drive does not work in Linux.

If it isn't working in Windows try just uninstalling Nero and leaving it off.  I had a problem with one release where it caused my drive not to work and by removing it the problem ceased.  Now if they aren't working in Linux, you need someone with more experience than myself to answer that one.

But I'll go back to scratching my head and looking at what you've posted.

---

### Post by Benzimm86 on 2005-09-09
im sorry it was suppose to say windows.  I fixed the second post.  sorry about the confusion

---

### Post by madjo on 2005-09-09
[QUOTE=Benzimm86]im sorry it was suppose to say windows.  I fixed the second post.  sorry about the confusion[/QUOTE]
 benzimm, Linux does not in any way change anything on your drives to remove Windows support for cdrom or anything...
I really think that this is a Windows only issue...

Linux will never block you out of your drives, whether you use Windows or Linux, because it simply can't change anything like that in Windows.

---

### Post by Dolphin on 2005-09-09
I can't see this being a linux problem at all.  I'm thinking perhaps it's a coincidence that you're having this windows problem so close to the time you installed linux on a seperate partition/drive.  A linux install won't touch your windows partitions unless you tell it to, in which case it'll just wipe it out.

---

