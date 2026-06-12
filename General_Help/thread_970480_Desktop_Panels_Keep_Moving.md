---
title: "Desktop Panels Keep Moving"
date: 2008-11-04
forum: General Help
---

### Post by NoVista on 2008-11-04
I use two panels, horizontal, at the bottom.
Each panel, of course, has different items on them.

Both panels ALWAYS stay at the bottom, but they do not stay in the order that I put them. One panel always keeps moving to the top position, (on the bottom), Locked or unlocked. And even if I move all the icons from one panel to the other, since one keeps moving to the top spot, when I reboot the computer, both panels flip again. What the .. ??

I remember having same problem on Gutsy, but one day they both stayed locked in the order they were put in, but I never knew why.

Anyone else with panel order not staying put?


Edited to add:
One panel only has one item on it, the Window Selector. And that panel is the one that keeps on wanting to put itself in the top position, (at the bottom).

---

### Post by TwiceOver on 2008-11-04
No help to you, but just wanted to add that on my 8.10 system the icon placements keep moving around.  The menu always stays to the left but the other items (trash, time, user switcher, workspace switcher, tray) flop around on every boot.

---

### Post by allanlewis on 2008-11-11
I have exactly the same problem.

---

### Post by mfdc1969 on 2008-11-25
I can't offer any help either but since installing Intrepid all of the icons I have added to my panels keep moving to the far right after reboot too. I lock them all to the panel but it serves no use - only the Main Menu stays put.

---

### Post by allanlewis on 2008-11-25
> **mfdc1969 said:**
> ...all of the icons...keep moving to the far right...Your icons sympathise with the Nazis?
(Sorry, I couldn't resist :D)

---

### Post by radar.duse on 2008-11-26
> **NoVista said:**
> I use two panels, horizontal, at the bottom.
Each panel, of course, has different items on them.

Both panels ALWAYS stay at the bottom, but they do not stay in the order that I put them. One panel always keeps moving to the top position, (on the bottom), Locked or unlocked. And even if I move all the icons from one panel to the other, since one keeps moving to the top spot, when I reboot the computer, both panels flip again. What the .. ??

I remember having same problem on Gutsy, but one day they both stayed locked in the order they were put in, but I never knew why.

Anyone else with panel order not staying put?


Edited to add:
One panel only has one item on it, the Window Selector. And that panel is the one that keeps on wanting to put itself in the top position, (at the bottom).

...I've had exactly the same problem with gutsy and now with intrepid!!
I keep both panels at the bottom of screen and every time I reboot -no matter if locked or not- **they keep changing positions as if never set in  proper order.**
So I've given up and just let them be wherever they chose....
Funny eh?](*,)](*,)](*,)](*,)](*,)

---

### Post by kanikilu on 2008-11-26
I've had a slight issue with the area around the system tray reorganizing itself, but that stopped after I right-clicked each item and locked them to the panel.

Other than that, I have 3 panels on 2 monitors and I haven't seen any problems with the panels themselves moving...sorry I know that isn't any help.

A quick search brought up:

[https://bugs.launchpad.net/gnome-panel/+bug/15442](https://bugs.launchpad.net/gnome-panel/+bug/15442)

So it looks like you guys aren't alone.

There are several duplicates. Someone posted a workaround with a shell script, but I didn't try it myself, so can't verify that it works.

---

### Post by mfdc1969 on 2008-11-26
I just applied all of the intrepid-proposed updates to fix an unrelated issue with my ethernet connections. 

Ever since those updates were applied all of my panels and their icons have remained in place after several shutdowns and reboots.

Mysterious ... I have no explanation why they now stay - they were always locked in place before updates.

---

### Post by radar.duse on 2008-11-27
> **mfdc1969 said:**
> I just applied all of the intrepid-proposed updates to fix an unrelated issue with my ethernet connections. 

Ever since those updates were applied all of my panels and their icons have remained in place after several shutdowns and reboots.

Mysterious ... I have no explanation why they now stay - they were always locked in place before updates.


...it's truly mysterious because I did have this problem despite keeping my system always up-to-date anyway!
But I read a workaround solution somewhere (not this forum) and it seems this annoying peculiarity has gone...!
You just create a new panel on top of the other two , then move to it (or recreate) all items from the bottom panel (the one that keeps moving from its top position), and last, you delete the bottom panel altogether.

When you reboot the new topmost panel wil remain (magic..?!) on top.

Sounds silly and totally un-geeklike but it did the trick.8-)8-)8-)8-)

---

### Post by NoVista on 2008-12-06
> You just create a new panel on top of the other two

And that alone is not possible.
Newly created panels default to the bottom of the order.

---

### Post by drs305 on 2008-12-06
Aside from locking each individual icon, as was mentioned previously, you can lock down the entire panel starting with Intrepid. Does this work or do the panels move even after accomplishing this step?

To lock the panels, 
```

gconftool-2 --type bool --set /apps/panel/global/locked_down 'true'

```

With the lockdown feature enabled, all you can do with a right click on the panel is access 'Help' and 'About'. To enable changes again, reset the value in the above command to 'false'.

---

### Post by charlescarroll1 on 2008-12-23
I am also having the same issue.  All the icons I have set up on the top right panel move around and end up behind the clock and shutdown icon.  This doesn't happen every time, but often enough to be a nuisance.

> **drs305 said:**
> 
To lock the panels, 
```

gconftool-2 --type bool --set /apps/panel/global/locked_down 'true'

```

I tried this code to see if it works.  I will come back and post whether it worked or not.

---

### Post by charlescarroll1 on 2008-12-24
> **drs305 said:**
> 
To lock the panels, 
```

gconftool-2 --type bool --set /apps/panel/global/locked_down 'true'

```


Unfortunately, this did not work.  I still have my panel icons shifting back and forth.  I can't really see a pattern or any particular icon that is moving out of its order.  This time the work space switcher moved in front behind the notification area and my force quit icon.

---

