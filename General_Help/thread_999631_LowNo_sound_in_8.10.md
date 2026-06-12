---
title: "Low/No sound in 8.10"
date: 2008-12-02
forum: General Help
---

### Post by Historyman on 2008-12-02
I've had mixed success in trying  to get my sound to work in Ubuntu 8.10.  At this moment if I turn my desktop speakers (which are connected to the headphone port on my laptop) all the way up, I can barely hear sound.  

I'm not exactly sure on what you need to know to help me, so please let me know which console commands can give you guys the info you need to help me fix this.

---

### Post by DagMan on 2008-12-02
Are the normal speakers for the laptop working, and if so, what's the brand and model of the laptop?

Also, double click on the volume thing and make sure everything is unmuted and turned all the way up and then type alsamixer at a terminal and make sure the bar is all the way to the top there.

---

### Post by Historyman on 2008-12-02
Everything is up and running in terms of the volume meters.  Without my desktop speakers there is no noticeable sound coming from the laptop (which is a gateway mx7525). I should also note that the headphone volume dial in the volume control seems to be the one that controls the sound output in my speakers.  If that is up all the way, then I can barely hear my computer (with my desktop speakers up all the way0

---

### Post by Historyman on 2008-12-02
bump

---

### Post by Historyman on 2008-12-02
anyone?

---

### Post by DagMan on 2008-12-02
This thread is very old and the sound drivers are not necisarrily the same now, so this may indeed not work [http://ubuntuforums.org/showthread.php?t=171896](http://ubuntuforums.org/showthread.php?t=171896)

In addition to the above, btw, when you mess around with the mixer gui make sure you enable all the checkboxes if you find any extras.  Take note that on some rare occasions the driver thinks there's more functionality to a card than what there actually is and disabling some thing sometimes can help.

Someone suggests installing **paman** and without any further configuration fixes sound on that laptop. 

Beyond this, I can't find any further help.  Often times you can pass a paramater the main sound module to tell it more specifically what your card needs, but I didn't turn anything up.

---

### Post by Historyman on 2008-12-02
Thanks Dagman, worked like a charm!

---

