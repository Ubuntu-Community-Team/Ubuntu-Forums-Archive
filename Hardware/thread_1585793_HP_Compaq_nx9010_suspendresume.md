---
title: "HP Compaq nx9010 suspend/resume"
date: 2010-10-01
forum: Hardware
---

### Post by PCTinker on 2010-10-01
I see lots of threads dealing with suspend resume issues; some resolved some not. I'll be trying some of the suggested 'fixes' tonight but meanwhile if anyone has any suggestions specific to the nx9010 I'd be grateful.
 
I did a clean install of 10.04 a few days ago and got my network card working after a bit of faffing around.
The screen saver was coming on after only 5 minutes so I moved that out to an hour. That seemed to work fine, move the mouse or hit any key, the screen clears and I am prompted for my password.
 
However, when the machine goes into suspend mode I can't wake it up.
ctrl+alt+del: no response.
cap lock: caps lock light comes on
num lock: num lock light comes on
F9 generates a fair bit of hard disk activity (no idea what it's doing). All other F keys nil response.
Move the mouse and I can see the cursor moving about the black screen.
No key combination I have tried brings back the logon window.
I've even tried guessing where the logon window would be and typing in my password blind (didn't work).
I have to hold down the power button and kill the machine, then switch on.
 
It's really strange. The keyboard, mouse and screen are live, after a fashion, I just can't logon and resume where I left off.

---

### Post by P4man on 2010-10-01
I dont have a proper solution, but try this: Press control+alt+F1 and see if you get a terminal. IF you do, press control+alt+F7 (possibly F8 ) to get back to the GUI.

If that doesnt work, then use REISUB:

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Rather than holding the power button. 
Its also possible the R in this sequence actually breaths life in the laptop. If so, try pressing alt+sysreq+R again

---

### Post by PCTinker on 2010-10-02
Thanks for the info and links P4man. Unfortunately none of the info you provided worked. 

I've done a bit of Googling and have discovered the nx9010 needed a BIOS update after XP SP2 for suspend/resume to work.

I'll update my BIOS and see if that helps.

---

### Post by agriv8ted on 2010-11-10
Just wondering if you found a sollution , PCTinker. Did the BIOS update work? I'm making my first tentative steps into real computing and am a bit nervous of re-flashing the BIOS on my NX9010. Any information would be appreciated. Thanks.

---

### Post by P4man on 2010-11-10
Try acpi_osi= kernel parameter. See my signature.

---

