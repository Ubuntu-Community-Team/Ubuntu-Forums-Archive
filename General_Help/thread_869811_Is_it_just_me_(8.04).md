---
title: "Is it just me? (8.04)"
date: 2008-07-25
forum: General Help
---

### Post by milagre23 on 2008-07-25
Dear friends,

I' m just a regular user, don't know much about computers, but I use Ubuntu almost since the first version. Some times there are problems to be solved, that's normal in all the OS, and always had the support of the forums. But, for the first time, this 8.04 is giving more trouble that I can handle, new small problems each update. That's why I desperately need your help and advise.

- Each time a new kernel is updated some things start to fail (Some message says that don't recognize the X window environment so I can't get in the system, or don't recognize my screen definitions - fortunately this last one that finishes in 19 is working fine) 

- Each time I restart the computer I loose the keyboard definitions (when I go there it is in the Portuguese layout but doesn't work, I have to redefine the Portuguese layout to have the correct accentuation, etc)

- Each time I restart the computer it doesn't recognize my main partition (a FAT 120 gb that I share with XP), so I have to go to the menu > Places (where the partition is listed) and mount it.

- The updates of Firefox have been a disaster and the last one blocked the search bar and the search engine (the search engine lost all the configurations I had, and when I try to use it a second window is open and freezes all the browser).
At the moment I'm using Swiftweasel and I'm fine.

There are more little details that are not so annoying in particular but in general start to bother me.
The point is that I'm used to a very stable system and at the moment I'm a little worry about this version. I'm a big Ubuntu fan so I wont change easily my OS but I would like to ask if you also had problems with it and when does it come a new version (that I hope that goes back to the stability that I'm used to)? Or even if you think I loose a lot if I downgrade to a older version. 

Thank you very much for your attention.

---

### Post by olbaidle on 2008-07-25
Been having some problems myself...VMWARE-server setup was destroyed and firefox 3 was a disaster.....

I trying to work this stuff out now....when i get some answers i can perhaps help...

I did fix the Vmware server by downloading the Beta version 2.01 and re installing...

Perhaps its a push to get all software up to date....:confused:

---

### Post by sgage on 2008-07-25
> **milagre23 said:**
> 
- Each time I restart the computer it doesn't recognize my main partition (a FAT 120 gb that I share with XP), so I have to go to the menu > Places (where the partition is listed) and mount it.

You can make your FAT partition auto-mount by editing /etc/hal/fdi/policy/preferences.fdi

Don't forget to back up the file first!

Find the line:

<merge key="storage.automount_enabled_hint" type="bool">false</merge>

and change false to true. Your FAT partition should mount at your next boot.

I'm sure there's an easier way, but that worked for me.

- sgage

---

### Post by editrix on 2008-07-25
No, it's not just you. What's driving me nuts is, every time I research something not working, I end up on a Launchpad bugs page, and much of the time it's not a Hardy bug, but something left over from an earlier release.

---

### Post by Growbag on 2008-07-25
Yes, this started for me with Kubuntu 7.10.  The endless kernel updates that sorted out one problem, then caused 2 more!

Plus the other updates that simply hosed the entire system.

I think it started to go downhill after 7.04.

It started to feel as though I was simply a "testing guinea pig", the stability was compromised in favour of "forging new paths" or something.

I switched to openSUSE 10.3, and was shocked at how solid it was compared to Ubuntu.  I installed it once, and never had to touch it again.

Unfortunately the same can't be said for openSUSE 11.

I think it's a new philosophy behind all distros these days, forget what used to work, lets try new stuff, sod the consequences.

KDE4 is a shining example of that "new philosophy".

I would recommend returning to 7.04, or even 7.10, but they close down the repos a little while after announcing "end of support".

I was a little shocked to find the 6.06 repos down :(.

But, if your system works fine with an older version, install it, update it, and forget it.

It seems to me like a relic of the "Microsoft Way", we are all brainwashed into wanting new things all the time, for no logical reason.

I mean your computer never gets younger, so why put newer and potentially more bloated stuff onto it just to slow it down?

---

### Post by Archimedes0212 on 2008-07-25
you can fix your keyboard problem by editting the keyboard section of xorg.conf.

I had that problem recently and modifying xorg did the trick

---

### Post by milagre23 on 2008-07-25
> **sgage said:**
> You can make your FAT partition auto-mount by editing /etc/hal/fdi/policy/preferences.fdi

Don't forget to back up the file first!

Find the line:

<merge key="storage.automount_enabled_hint" type="bool">false</merge>

and change false to true. Your FAT partition should mount at your next boot.

I'm sure there's an easier way, but that worked for me.

- sgage

Thank you, Ill try it.

---

### Post by milagre23 on 2008-07-25
> **editrix said:**
> No, it's not just you. What's driving me nuts is, every time I research something not working, I end up on a Launchpad bugs page, and much of the time it's not a Hardy bug, but something left over from an earlier release.


You right!

---

### Post by milagre23 on 2008-07-25
> **Growbag said:**
> Yes, this started for me with Kubuntu 7.10.  The endless kernel updates that sorted out one problem, then caused 2 more!

Plus the other updates that simply hosed the entire system.

I think it started to go downhill after 7.04.

It started to feel as though I was simply a "testing guinea pig", the stability was compromised in favour of "forging new paths" or something.

I switched to openSUSE 10.3, and was shocked at how solid it was compared to Ubuntu.  I installed it once, and never had to touch it again.

Unfortunately the same can't be said for openSUSE 11.

I think it's a new philosophy behind all distros these days, forget what used to work, lets try new stuff, sod the consequences.

KDE4 is a shining example of that "new philosophy".

I would recommend returning to 7.04, or even 7.10, but they close down the repos a little while after announcing "end of support".

I was a little shocked to find the 6.06 repos down :(.

But, if your system works fine with an older version, install it, update it, and forget it.

It seems to me like a relic of the "Microsoft Way", we are all brainwashed into wanting new things all the time, for no logical reason.

I mean your computer never gets younger, so why put newer and potentially more bloated stuff onto it just to slow it down?


You are absolutely right and we have to change this attitude. This is a very important experimental world but not everyone is able to get that train. Some, like me, that are just regular users, just want a stable platform to work and have some fun too. Thanks for sharing.

---

### Post by milagre23 on 2008-07-25
> **Archimedes0212 said:**
> you can fix your keyboard problem by editting the keyboard section of xorg.conf.

I had that problem recently and modifying xorg did the trick

Can you explain me how to do that, Archimedes0212?

Thanks.

---

### Post by Archimedes0212 on 2008-07-25
absolutely. 

I'm not at my ubuntu system right now but I'll do the best I can.

There is a whole section of xorg.conf labeled Keyboard.  Obviously you want to edit this part.

There is a 'layout' option and a 'variant' option in this section - I forgot their exact names, but you will know what I'm talking about when you are looking at xorg.conf.

These two Options will have certain values.  You need to change them to whatever you need. 

When I had this problem, I found what I needed in Applications-Other-Keyboard Layout.

my xorg looked along these lines

... "Keyboard"
....

Option ...layout "us"
Option ...variant "none"


and i needed to change my "none" value to "basic"

If you need something a little more detailed, you can send me a private message and I will give you something much more detailed when I'm sitting in front of my ubuntu computer

Hope this helps though.  Good luck!

---

### Post by milagre23 on 2008-07-28
> **Archimedes0212 said:**
> absolutely. 

I'm not at my ubuntu system right now but I'll do the best I can.

There is a whole section of xorg.conf labeled Keyboard.  Obviously you want to edit this part.

There is a 'layout' option and a 'variant' option in this section - I forgot their exact names, but you will know what I'm talking about when you are looking at xorg.conf.

These two Options will have certain values.  You need to change them to whatever you need. 

When I had this problem, I found what I needed in Applications-Other-Keyboard Layout.

my xorg looked along these lines

... "Keyboard"
....

Option ...layout "us"
Option ...variant "none"


and i needed to change my "none" value to "basic"

If you need something a little more detailed, you can send me a private message and I will give you something much more detailed when I'm sitting in front of my ubuntu computer

Hope this helps though.  Good luck!
It worked!

In the System> Preferences > Keyboard menu I had the PT (Portuguese) layout but when I went to see the xorg.conf it was US layout. I can't understand why are there so may contradictions between some orders in the command line and the GUI menus (its not the first time, believe me).

Thank you very much.

---

### Post by editrix on 2008-07-28
> **Growbag said:**
> Yes, this started for me with Kubuntu 7.10.  The endless kernel updates that sorted out one problem, then caused 2 more!

I'm glad you said this, because I hadn't upgraded (if that's the term) since Dapper, and was wondering how far back I had to go for a fully working system.

> But, if your system works fine with an older version, install it, update it, and forget it.

I installed 8.04 when someone gave me his old computer that's twice the machine my old one was. I am **so** tempted to install Dapper on this new(ish) box, but there are programs I really want the latest versions of, specifically Gimp, OO and Scribus. Would you happen to know how fiddly it would be to install Hardy versions of programs on Dapper?

> It seems to me like a relic of the "Microsoft Way", we are all brainwashed into wanting new things all the time, for no logical reason.

I mean your computer never gets younger, so why put newer and potentially more bloated stuff onto it just to slow it down?

Given the long gap between Dapper and Hardy, I was shocked by how much under-the-hood had changed. But I think they're struggling to keep up with the new hardware technologies--unfortunately, at the expense of the established technologies. e.g., I'm on dialup, and have read on this forum that it's "deprecated" and that's why no one's making it easier for people to use dialup connections. But the (K)Ubuntu folks aren't responsible for every single program on our computers. They have to rely on whoever's maintaining the applications, too. And if those folks aren't fixing bugs, or creating new ones ...

IOW I agree with you, but I think we're in the minority, in terms of both users and programmers.

---

### Post by Archimedes0212 on 2008-07-28
glad it worked

---

### Post by Dasvinder Singh on 2008-07-28
Are there problems between vista and outlook?

---

