---
title: "[SOLVED] Firefox launches with no window decoration and obscures the panel"
date: 2008-11-25
forum: General Help
---

### Post by Squonk07 on 2008-11-25
This is an odd issue that began several days ago for me.  Whenever I launch Firefox, the maximized window fills the screen--it not only appears without window decorations (so I can't close it), but it also obscures my panel.  However, it's not fullscreen mode because when I tap F11, it goes into the actual Firefox fullscreen mode (with the disappearing navigation and tab bars).  Tapping F11 yet again seemingly fixes the problem (the decoration bar and panel appear again), but this same thing happens every time I open Firefox.  So far, I have found no other program that behaves this way.

Interestingly, Firefox also overrides a window that has been designated to stay on top, which is what I tried to do with the screenshot utility.  I had to set a timer on it because when I opened Firefox, the screenshot program got buried beneath the Fx window and I couldn't get to it.

Has anybody else experienced this before, and if so, can anybody help me fix this?  It's excruciatingly annoying.

[ATTACH]94078[/ATTACH]

---

### Post by madverb on 2008-11-25
I had this exact same problem... I had to delete a file from ~/.mozilla/firefox/xxxxxxxx.default
I think it was 'prefs.js', I can't really remember though because I just made a backup of my profile and then deleted files gradually until firefox started normally again and then I removed the problematic file from my back up and replaced it.
Fixed it all up.

---

### Post by jdorenbush on 2008-11-25
I have this problem too. Super annoying.

I have to goto View > Full Screen then I have to click Unmaximize then I have to use the Move and Resize tools. Ugh.. ubuntu for me has turned into bug-city.

---

### Post by Squonk07 on 2008-11-25
> **madverb said:**
> I had this exact same problem... I had to delete a file from ~/.mozilla/firefox/xxxxxxxx.default
I think it was 'prefs.js', I can't really remember though because I just made a backup of my profile and then deleted files gradually until firefox started normally again and then I removed the problematic file from my back up and replaced it.
Fixed it all up.

I ended up doing pretty much the exact opposite as you. :)  I went ahead and cut and pasted away all the files (none of the folders) in that directory.  Then, I took my old 'Prefs.js' file and replaced the newly-generated one.  I'm going to have to redo all my passwords and cookie exceptions, but other than a few other preferences that got reset to factory (arrangement of elements of the UI), this fixed the problem.

Thanks for setting me in the right direction, anyway.  I never thought of just clearing out all those profile files and letting Fx regenerate them.

---

### Post by madverb on 2008-11-25
The file that causes the problem and that needs to be removed is localstore.rdf

---

### Post by Chamillionaire2 on 2008-11-25
I had same prob to. re installation fixed it.

---

### Post by jdorenbush on 2008-11-25
> **madverb said:**
> The file that causes the problem and that needs to be removed is localstore.rdf


is it prefs.js or localstore.rdf?? - I want to know in case this happens in the future. Thanks!

---

### Post by cyberbug on 2008-11-25
The file to remove is - localstore.rdf
solved the problem for me.

---

### Post by DaveySpeedstar on 2008-11-29
Thanks for that tip, this has been annoying me for a few days.

I don't know if it's any coincidence, but it started to happen shortly after I watched BBCiPlayer in full screen mode.

Thanks again for the fix!!!

---

### Post by zero777zero on 2008-12-02
how do i fix this then:

Could not move "localstore.rdf" to trash.
Moving "/etc/firefox-3.0/profile/localstore.rdf" failed: Access denied.

---

### Post by jdorenbush on 2008-12-02
> **zero777zero said:**
> how do i fix this then:

Could not move "localstore.rdf" to trash.
Moving "/etc/firefox-3.0/profile/localstore.rdf" failed: Access denied.

Hit Alt+F2 and type, **gksu nautilus**. Then you should be able to browse to the */etc/firefox-3.0/profile* directory and delete localstore.rdf.

---

### Post by zero777zero on 2008-12-03
file deleted, still getting the error. didnt want to say goodbye to my desktop fx, but looks like thats the only way i'm going to get ff to work.

---

### Post by patond on 2008-12-22
I had this problem a week or two ago.  Are you using compiz effects - if so untick fading windows.  I found it somewhere in the forums - Worked for me - I don't know how.

Good luck.

---

### Post by beynac on 2008-12-23
I had the same problem and solved it using a different solution, before seeing this thread.

Previous problems I've seen with Firefox have usually been down to a corrupt profile or an Add-on. I looked at my Add-ons (Tools => Addons) and there was one called "Ubuntu Firefox Modifications 0.6". I disabled it and restarted Firefox. The problem had gone. I re-enabled it and again restarted Firefox. It was still OK and has been so since.

---

### Post by jdorenbush on 2008-12-23
> **beynac said:**
> I had the same problem and solved it using a different solution, before seeing this thread.

Previous problems I've seen with Firefox have usually been down to a corrupt profile or an Add-on. I looked at my Add-ons (Tools => Addons) and there was one called "Ubuntu Firefox Modifications 0.6". I disabled it and restarted Firefox. The problem had gone. I re-enabled it and again restarted Firefox. It was still OK and has been so since.

What exactly does the *Ubuntu Firefox Modifications* even do?

---

