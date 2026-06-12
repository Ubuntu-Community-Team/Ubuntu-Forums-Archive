---
title: "Left Alt key doesn't work"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by shane2peru on 2006-11-14
Ok, I have seen a few threads and tried a few of the solutions, but it seems as though mine is an original problem.  I have a Toshiba Satellite laptop, that works great with Ubuntu.  I have used Ubuntu for some time.  I recently upgraded to Edgy, and found to many problems, and went back to Dapper Christian edition.  My left alt key worked before.  When I re-installed Dapper, I left my /home directory so I wouldn't have to loose everything.  When I re-installed my left alt-key doesn't work.  I can't hit alt-tab to switch windows, I can't hit alt-F2 to start the run command thing.  I tried to change my keyboard layout to another Toshiba layout, didn't work.  I tried to change it to 105 keys layout didn't work.  I booted a live CD, and my left alt-key worked.  I checked to see what the keyboard layout was, it was 104 key generic layout.  I switched my Keyboard layout to the 104 generic keyboard layout, and nothing.  I found another post about the third level thing in Keyboard Layout options, I set the left-alt key to choose third level and it didn't work.  I'm sure it has to do with the settings left from Edgy in my /home directory because Dapper worked fine before.  Any ideas??  I know there is a way to re-configure gnome too, but I don't remember how to do that, and would prefer a simpler way if there is one.  Thansk in advance for the help!

Shane

Ps.  It is very annoying to not have the alt-tab function as I use it **all** the time!  Even out of habit I still use it even though it currently doesn't work.

---

### Post by strategischen on 2006-11-14
I don't how it's suppose to work, but was not working on my computer.

Then I install the beryl and started to work very good

I use this section  [http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl]("http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl") to setup the Nvidia drivers.

hope it will work.

Regards

---

### Post by shane2peru on 2006-11-14
I'm back to dapper, and not too interested in installing Beryl.  Sounds to experimental for me.  I need my desktop for work.  Plus I don't have Nvidia drivers or ATI, at least I don't think I do.  I'm just using a laptop, and I believe everything is Intel.  I really don't know that much about the guts of my computer.  Anyway, I installed XCFE desktop, and really seem to like it, it works nice and is very similar to Gnome.  My alt key works in this desktop, however still not fixed in Gnome.

Shane

---

### Post by shane2peru on 2006-11-14
Ok, no more XFCE, no multiple keyboard support.  This is not good for me.  The Alt-Tab function worked well though!  I need multi-keyboard layout at my finger tips.  Any ideas on how to get my alt key back???  Consequently my right alt-tab doesn't work either.  I alt-less.  This is not good.  ](*,)

Shane

---

### Post by shane2peru on 2006-11-14
Ok, if someone can just tell me what file to remove that configures Gnome, I will remove it and remove - re-install gnome desktop via aptitude.  I need to know what file is used to configure gnome though, and especially the keyboard thing.

Shane

---

### Post by shane2peru on 2006-11-16
Wow I sure appreciate the help here!  -- yes that is sarcastic. - no offense toward [strategischen]("http://www.ubuntuforums.org/member.php?u=193890") since he was the only poster.

Anyway, if anyone stumbles across this thread and has the same problem, here is the fix I used:

This fixed it for me.  I opened the Keyboard Layout options and set the alt/win key behavoir to defualt, and my alt keys started working again.  It was that simple!  Worked for me.  I would give it a try.  I went through all the options one of those options in there had my keyboard messed up.  I also changed the Group Shift Lock behavior to something else.  Anything that had to do with the alt key, I unchecked, and everything works now.  Hope this helps.

Shane

---

### Post by positron on 2006-11-21
For those interested, I had the EXACT same problem after I installed beryl.  Any key shortcut involving the alt-key did not work.  I went to Preferences -> Keyboard (in Edgy) and changed the keyboard Layout to US 101-key keyboard and a few other options and it magically started working again.

The alt-key only broke after starting the beryl window manager.

---

### Post by camel1cz on 2008-03-04
I have the same problem on 7.10 32-bit... but it happens only "sometimes"... left alt doesn't work, I restart the computer and it's OK again... don't know (and see) any rule in it...

---

