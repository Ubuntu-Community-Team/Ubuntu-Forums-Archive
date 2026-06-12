---
title: "Problem with SoundBlaster Live!"
date: 2005-09-16
forum: Hardware &amp; Laptops
---

### Post by Master Shake on 2005-09-16
A while ago, I installed Ubuntu, and everything seemed to be setup properly.  Had a sound issue, but that was fixed by killing the ESD process.  Anyway, I let Ub steam for a few weeks, while I went back to XP, and now, I don't have any sound..  either in games or upon boot.  Can anyone help me out here?

---

### Post by graigsmith on 2005-09-16
did you add any new software or hardware?  or change any bios settings?  i had a computer that wouldn't see a sb live, and then i moved the card to a different slot, and it then started working perfectly.

btw nice master shake picture hehe.

---

### Post by lisje on 2005-09-17
did you try to open up the channels again with alsamixer... if you use alsa offcourse

---

### Post by Master Shake on 2005-09-17
I think what I'm gonna do is just reinstall Ubuntu (as I've not really used it for much yet anyway, as well as having changed a few things), and restart fresh, and see what happens there.

EDIT:  @ Greigsmith...  Thx...  But I have a few others that I may try as well...


Heck, changing to my favorite Shake avatar now. :)

---

### Post by graigsmith on 2005-09-18
the best thing to do right now is check alsa's website.  what sound cards do you have?

check this listing out, choose the brand in the pulldown menu,  like creative labs.  choose that, click go.  And you are taken to a compatibility page.  i have a "Sound Blaster Live Value" which works great.  and you can see the 3 by it.  at the bottom it says that a number 3 has hardware mixing.  it depends on what kind of card you have.  if you have a sb live 24 bit, you can see that it doesn't have hardware mixing.  i had some problems with cards that diddn't have hardware mixing.

[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

---

### Post by Master Shake on 2005-09-20
I got it working.  I reinstalled Ubuntu, and then ran through the instruction on the Ubuntuguide mirror.

---

