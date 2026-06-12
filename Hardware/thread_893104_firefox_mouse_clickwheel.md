---
title: "firefox mouse clickwheel"
date: 2008-08-17
forum: Hardware
---

### Post by patriotpie on 2008-08-17
In the Windows version of Firefox, I could hold down the wheel on my mouse and move the pointer up or down on the screen to scroll in that direction. I noticed that this does not occur in the Ubuntu version of Firefox. How can I fix this?

---

### Post by crazyness003 on 2008-08-17
lemme be the first to tell you, this has little, if nothing to do with firefox. Everythign mouse-related is confined to your xorg.conf file. 
Unfortunately, i havent really messed arroud with it, so i caont help you too much, But if any other gentle soul would like to take it from here, you are more than welcome

---

### Post by MrMarc on 2008-08-18
Actually, this had me puzzled for a long time but I found out that's a setting within Firefox itself.

Go to Edit / Preferences, and under the first tab of Advanced, make sure 'Auto Scrolling' is enabled. If your middle mouse button works elsewhere (such as opening new tabs), this 'should' work. 

Had me puzzled for a long time thinking it was my xorg.conf but it's something so simple to overlook lol.

---

### Post by spacedoggy on 2008-08-18
cool, i didn't even think this was possible in firefox, thanks!

---

### Post by MrMarc on 2008-08-18
It's a very simple feature but nevertheless it's a very useful feature too. I feel like I have to ask - why is it that this seems to always be disabled by default for fresh Ubuntu installations?

For Windows users who are just used to middle clicking and then scrolling down by default and by instinct, it's possible (as shown here!) for people to overlook it's option in Firefox's preferences.

---

### Post by spacedoggy on 2008-08-18
don't get me started about ubuntu defaults, 

pcspkr keyboard shriek by default if no. 1 on my hitlist

---

### Post by Xm3buX on 2008-08-18
> **MrMarc said:**
> Actually, this had me puzzled for a long time but I found out that's a setting within Firefox itself.

Go to Edit / Preferences, and under the first tab of Advanced, make sure 'Auto Scrolling' is enabled. If your middle mouse button works elsewhere (such as opening new tabs), this 'should' work. 

Had me puzzled for a long time thinking it was my xorg.conf but it's something so simple to overlook lol.
Thanks alot, this has been annoying me for a while now.

---

### Post by crazyness003 on 2008-08-19
wow, well prove me wrong why dont you. [#-o]("http://ubuntuforums.org/post_thanks.php?do=post_thanks_add&p=5611689")
Thats a handy thing to know, personally i never had a chance to test it out, since im on a laptop with a trackpad. But there were some other posts (cant remember where) that would always point to xorg for the solution. Like the touch-scrollup/down on the trackpad of a laptop for back/forward, and middle-clicking, backspace for back. all this other stuffs.

and to thank you for correcting me...i thanked you [[IMG]http://ubuntuforums.org/images/buttons/post_thanks.gif[/IMG]]("http://ubuntuforums.org/post_thanks.php?do=post_thanks_add&p=5611689")

---

### Post by patriotpie on 2008-08-20
> **MrMarc said:**
> Actually, this had me puzzled for a long time but I found out that's a setting within Firefox itself.

Go to Edit / Preferences, and under the first tab of Advanced, make sure 'Auto Scrolling' is enabled. If your middle mouse button works elsewhere (such as opening new tabs), this 'should' work. 

Had me puzzled for a long time thinking it was my xorg.conf but it's something so simple to overlook lol.

thanks!

---

### Post by forestlake on 2013-03-24
> **MrMarc said:**
> Actually, this had me puzzled for a long time but I found out that's a setting within Firefox itself.

Go to Edit / Preferences, and under the first tab of Advanced, make sure 'Auto Scrolling' is enabled. If your middle mouse button works elsewhere (such as opening new tabs), this 'should' work. 

Had me puzzled for a long time thinking it was my xorg.conf but it's something so simple to overlook lol.

OMG you are a genius !!! this has plagued me for ever !!! thanks for the great tip :D

---

