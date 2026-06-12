---
title: "lenovi T61 // suspend"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by jaskah on 2007-10-20
hello
i've just installed gutsy on my lenovo t61. everything seems to be working fine so far except that i can't wake the computer from suspend mode.
does anyone know a way to fix this?
my computer has the intel video and wirelesss chips.
thanks in advance for any help!

---

### Post by ColombianGold on 2007-10-20
hi

have you tried this...
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61)

hope it helps.

CG

---

### Post by lamborghiniwang on 2007-10-21
> **ColombianGold said:**
> hi

have you tried this...
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61)

hope it helps.

CG

It doesn't work on my T61p. I always get a black screen and the laptop stops response when it tries to wake from suspend. the thinkwiki article mentions that the suspend works with 2.6.22-12 kernel, but I think the official release of 7.10 comes with 2.6.22-14. Maybe that is the difference.

---

### Post by jaskah on 2007-10-21
hello again
this doesn't work for me, either. i am using kernel 2.6.22-14.
does anyone know a fix for this?
thanks in advance for any help on this!

---

### Post by cymacyma on 2007-10-22
If you're using driver by restricted drivers manager, search the santarosa macbook pro on ubuntu wikis. It was reported that glx-new has suspend problem, but it can fix with 1 line commend i guess.

---

### Post by jaskah on 2007-10-22
thanks for your reply, but i am not using any restricted drivers on my computer (this according to the restricted drivers manager).
any other ideas?

---

### Post by cymacyma on 2007-10-22
I didn't see any problem reports on open 'nv' drivers. I recommend you to go thinkwiki talk pages...

[http://thinkwiki.org/wiki/Talk:Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61#Black_screen_at_boot](http://thinkwiki.org/wiki/Talk:Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61#Black_screen_at_boot)

---

### Post by cymacyma on 2007-10-22
It seemed that mactel users experiening with same problems

See, [http://ubuntuforums.org/showthread.php?t=577888&page=2](http://ubuntuforums.org/showthread.php?t=577888&page=2)

I think that gutsy is too buggy on stability in mobile systems :-( 

(+, I can't read English very well, so this link can be nully on your problems...)

---

### Post by jaskah on 2007-10-22
hi
thanks for your answer, but there seems to be nothing at the link
[http://thinkwiki.org/wiki/Talk:Insta...screen_at_boot](http://thinkwiki.org/wiki/Talk:Insta...screen_at_boot)
about intel drivers and problems with a blank screen after suspend. they are talking about nvidia driveres here.
there is in fact a problem with this as other t61 owners with intel video cards have reported the same problem.
anyone else have an idea?
thanks again!

---

### Post by jsully1 on 2007-10-22
I can't suspend either on my T60 - very frustrating.  I've already tweaked /etc/defaults/acpi-support as per a few faq's, nothing works though.

---

### Post by jaskah on 2007-10-22
yes, i tried a couple of these suggetions as well but nothing seems to make a difference yet...everything else works great though!
anyone know a solution for this? there is a bug report...

---

### Post by cymacyma on 2007-10-24
intel graphics' problems reported on lunchpad and thinkiwiki

link here: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61#Hibernate.2FSuspend](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61#Hibernate.2FSuspend)

this shows that instant fix, ctrl alt f1(virtual terminal) than ctrl alt f7 to back X and radical solution. I think that gutsy is too buggy...

---

### Post by jaskah on 2007-10-24
thanks, but as mentioned before this does not fix the problem (see first post).
anyone else with an idea on how to fix this suspend problem?

---

