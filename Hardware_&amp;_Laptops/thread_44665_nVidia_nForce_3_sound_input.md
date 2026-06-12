---
title: "nVidia nForce 3 sound input?"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by fares on 2005-06-27
Hi everybody,

I'm experiencing some trouble with an nForce 3 250Gb chipset. Everything works just fine, except for the audio input. 
So, I'm basically unable to record anything with this box while sound from different apps plays without problem.

Some time ago I messed around with the official nVidia drivers but this didn't solve my problem.

I was asking myself is someone found a solution or if anybody knows where I could look for some extra info.

Thanks in advance!

---

### Post by intangible on 2005-06-27
See if this helps: [http://www.ubuntuforums.org/showthread.php?p=230948](http://www.ubuntuforums.org/showthread.php?p=230948)

---

### Post by fares on 2005-06-28
Hi,

I just tried but the problem is still there, no mic input.

Thanks for your help by the way!

---

### Post by intangible on 2005-06-28
Try opening up the volume control, Under "File->Change Device" choose "Alsa Mixer".  Then, under "Edit->Preferences" Enable all the check boxes.  Now look through the settings and see if you see an "option" tab, on it, look for "Mic Select" and try selecting a different option.

That's what I had to do to get my front mic working.  (Attached a screenshot)

---

