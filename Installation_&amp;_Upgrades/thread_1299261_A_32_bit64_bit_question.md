---
title: "A 32 bit/64 bit question"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by tkrisz on 2009-10-23
I have a stupid question. Currently i have a 64 bit system with separate /home partition. I consider switching back to 32 bit (i watch too much flash videos :P). Will the system go crazy if i keep the 64 bit /home partition?

---

### Post by Cybie257 on 2009-10-23
> **tkrisz said:**
> I have a stupid question. Currently i have a 64 bit system with separate /home partition. I consider switching back to 32 bit (i watch too much flash videos :P). Will the system go crazy if i keep the 64 bit /home partition?

Unless there is some odd thing I don't know, your /home directory is nothing but storage and has nothing to do with your OS, so as long as you don't delete it, you should be able to attached it just fine with any other install you do, whether 32 or 64 bit. 

BTW, I use 9.10 64-bit (used to use 9.04 64-bit) and have had no issues regarding flash videos. What sort of problems are you encountering?

-Cybie

---

### Post by tkrisz on 2009-10-23
Thx. That's great. I was 90% sure, that this is the case, but wanted to hear it from someone more experienced.
Is it possible to attach my /home to 2 systems at the same time? So i can test if there is difference between 32bit and 64bit in the quality of flash videos. (And some other things, as well.)
Btw, my problems: it jumps frames, eats up 100% of my CPU many times, full screen jumps much more frames (actually shows only a few frames) sometimes can't even quit fullscreen and freezes FF.

---

### Post by Cybie257 on 2009-10-23
> **tkrisz said:**
> Thx. That's great. I was 90% sure, that this is the case, but wanted to hear it from someone more experienced.
Is it possible to attach my /home to 2 systems at the same time? So i can test if there is difference between 32bit and 64bit in the quality of flash videos. (And some other things, as well.)
Btw, my problems: it jumps frames, eats up 100% of my CPU many times, full screen jumps much more frames (actually shows only a few frames) sometimes can't even quit fullscreen and freezes FF.

Well, you can use the LiveCD version and test that way. Also, when it comes to video, there are more things to consider when it plays like that. It could be an insufficient video card, drivers that lack full support, and the player itself. 

What video card do you have and have you checked to see if you are using opensource drivers or a proprietary driver. 

So,yeah, before you go and install a 32 bit version, try the LiveCD and see if it improves. You can install things into the LiveCD version if need-be such as a flash player, so it can be fully tested.

EDIT/ADDED: I see your profile says you are using Jaunty 9.04. There have been known issues with flash video in Jaunty. Dunno if they've been fixed as I have been using Karmic Koala since about the beginning of the Alpha stage. I had similar issues with Flash doing such things and there IS a workaround, which I believe is (force) installing the 32-bit version. Don't quote me on that, but something I think I recall from about 6-8 months ago. If I can relocate that information, I will post here again with any links/help.

-Cybie

---

### Post by tkrisz on 2009-10-29
Well, this was not working. 
Installed the 32 bit Koala for testing reasons (the 64 bit is Koala as well, i installed it as it became beta) at the remaining gigabites of my HD, and defined the /home partition of the 64 bit OS as the /home partition of the 32 bit install. I can't boot into the 32bit install. I get only a login prompt. But the screeen is flashing heavily and it gets only every 10th hit on the keyboard in average. So hopeless to even type in the password. No (new) problem with the 64 bit OS.
Just thought to share the experience.

---

