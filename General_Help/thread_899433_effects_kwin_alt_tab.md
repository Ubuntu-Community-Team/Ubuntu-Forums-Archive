---
title: "effects kwin alt tab"
date: 2008-08-24
forum: General Help
---

### Post by skintythe1andonly on 2008-08-24
Hi 

I am having some problems with the desktop effects in kde4, well ive upgraded to kde4.1. I am not using compiz but want the nice alt+tab effects that are built into kwin. They were working but dont seem to be working now. I have turned them on in system settings->Desktop. I am looking for the cover switch or the flip switch to work, but neither do. When i hit alt+tab now, the windows just raise one on top of the other. A box doesnt even apear with all the other windows in it. The other effects seem to work tho like the login and logout and a few others. It just seems to be the window management that is acting up. It worked before, and I dont what changed. I dont see the point in installing compiz when the effects i want are already there in kwin.

---

### Post by skintythe1andonly on 2008-08-26
I caved and installed compiz. Il stick with it but I couldnt figure out why kwin window management stopped working

---

### Post by benerivo on 2008-08-26
I read your initial post, but had no answer to it. It sounds as if Alt+Tab was working, but then for some reason it stopped? What other kde4 effects are still operative (does 'snow', 'translucency', 'scale', 'wobbly windows' still work? If they do, then i would look at the keyboard button combination (Alt+Tab in this case) as the culprit.

Forget about the desire to use the native kwin effects rather than compiz. Do you know that gnome has it's own [effects]("http://www.youtube.com/watch?v=JpRQkiB7Rrc"), but that they are disabled by default - like kde the effects are - it is just that in gnome, they are much harder to find in the desktop configuration utilities.

---

### Post by ghanarama on 2009-02-01
I had the same problem and was able to fix it by deleting ~/.kde/share/config/kwinrc. Apparently there was a line:
> AltTabStyle=CDE
that was causing the problem. Changing it to KDE should work, but reconfiguring everything from scratch is probably a better idea.

---

### Post by aurelieng on 2009-05-06
Hi have the same symptoms with KDE 4.2.2 installed Intrepid Ibex. All desktop effects work fine. My kwinrc file does not contain the AltTabStyle keyword, and no matter what I select in the drop down list "Effect for window switching" of the "Configure desktop effects" dialog, there is no effect for Alt+Tab switching...

Any idea ?

---

### Post by skintythe1andonly on 2009-05-07
I switched back to gnome in the end as I ended up spending my time configuring instead of getting things done which is the point. I like the look of kde 4.2, it looks a lot more polished. I may give it another go further down the line when I done have as much actual work to do

---

### Post by Penguin3D on 2009-11-10
I had this problem as well, and was bugging me - finally figured it out... Switch your setting for 'Window Behavior->Policy' to 'Focus Follows Mouse' and the Alt+Tab effects will work for you..

---

