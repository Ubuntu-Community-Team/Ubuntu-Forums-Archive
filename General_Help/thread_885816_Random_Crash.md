---
title: "Random Crash"
date: 2008-08-10
forum: General Help
---

### Post by Kurou-san on 2008-08-10
Occasionally, my system will turn white or have lines going through it. This happens randomly, from downloading a package to searching on Google. I am thinking it may have something to do with my graphics card, but I'm not sure. I've tried booting on Failsafe GNOME, but it still happens. Please assist me.

---

### Post by Kurou-san on 2008-08-10
Sorry for bumping, but this is really needed.

---

### Post by Kurou-san on 2008-08-11
Yet another bump. Please, somebody.

---

### Post by Kevbert on 2008-08-11
Please run a memory check from the grub boot menu.

---

### Post by Kurou-san on 2008-08-11
I had previously tried that. Nothing abnormal showed up to my memory.

---

### Post by Kevbert on 2008-08-11
You've checked all your video cables/connections ?  Does the video card sit snuggly in the motherboard socket ? try refitting it.

---

### Post by Kurou-san on 2008-08-31
Yes, all the cables are in place. I have ran
```
lspci | grep VGA
```
which came up with
> 01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]


---

### Post by Kurou-san on 2008-09-01
Once again... bump. Any suggestions could help.

---

### Post by Kurou-san on 2008-09-01
Double bumping... wow I look like a spammer. Someone....

---

### Post by Kurou-san on 2008-09-19
This problem went away about 2 wks ago, but I had to reinstall and now the problem is persistant. Help.

---

### Post by Kurou-san on 2008-09-19
Bumped, again....

---

### Post by Kurou-san on 2008-10-09
Another bump. Please guys.

---

### Post by sn3rd on 2008-10-09
One thing that you could try (it's a long shot), is to do System -> Administration -> Services
Then disable the powernowd service (I think it's called CPU Frequency Manager). I've read in a few places that it can cause issues (but I forget now what the conditions were). In any case, it won't hurt your computer, and it's worth trying for a while. If it doesn't help, you can always just re-enable it from the same place.

---

### Post by doas777 on 2008-10-09
I usually find that if i have just plain bizarre behavior, and none of my components fail tests (disks/RAM), and it persists across a rebuild, that it's time to buy a new motherboard. this has happened a lot less since I started buying high-end boards. 

it's just a thought. I usually watch the problem for a few months and scope out a new abit. unfourtunatly since they've gone out of the mobo biz, I'll have to work a bit harder in future.

---

### Post by Kurou-san on 2008-10-10
Thanks for responding. I'll try disabling it and see if helps. Seeing as I'm    
so young, buying a new motherboard is pretty much out of the question.

---

