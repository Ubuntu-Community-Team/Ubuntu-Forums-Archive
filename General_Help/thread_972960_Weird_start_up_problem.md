---
title: "Weird start up problem"
date: 2008-11-06
forum: General Help
---

### Post by grayfox444 on 2008-11-06
I'm really worried about this... I downloaded the new updates, and it prompted me to restard.  After typing in my username/password the screen just sits still with an orange background for about 10 seconds, then a gray box appears in the corner and just sits.
I'm really not sure what I can do to get around this, since I haven't been able to get on to my computer to even attempt to fix it.
Thanks.

---

### Post by thomasyen on 2008-11-06
I've seen the gray box you speak of before. It's a warning that GNOME Display Manager wasn't started correctly. Not sure how to fix this; last time I had this problem, it went away next time I rebooted.

---

### Post by grayfox444 on 2008-11-06
I've rebooted at least 10 times, still get the same result.

---

### Post by thomasyen on 2008-11-06
Did you upgrade to Intrepid, or was it a clean install?

---

### Post by grayfox444 on 2008-11-06
No I'm still on Hardy Heron.

---

### Post by geirha on 2008-11-06
Sounds like it could be an issue with the video card driver. What driver are you using and how did you install it?

Try booting with the previous kernel. When Grub starts loading hit Esc to show the menu, then select the previous kernel entry and hit enter.

---

### Post by grayfox444 on 2008-11-06
> **geirha said:**
> Sounds like it could be an issue with the video card driver. What driver are you using and how did you install it?
To be honest I really have no idea. 

> **geirha said:**
> 
Try booting with the previous kernel. When Grub starts loading hit Esc to show the menu, then select the previous kernel entry and hit enter.

I saw this option at the login screen as well under "options" in the lower left hand corner. I'll give this a shot after work.

Could it help if I upgraded to Intrepid if I'm able to get on using previous kernel entry?

---

### Post by thomasyen on 2008-11-06
I think what geirha means is, what video card (ATI, nVidia, ...) you are using, and whether you installed a proprietary driver.
Also, I think it's better if you don't upgrade (at least not now) until we sort this out, because a flaky upgrade could complicate things.

---

### Post by lionel47 on 2008-11-06
It might behoove you to just upgrade to Intrepid through a new install.  I was experiencing some trouble with kernel upgrades in Hardy.  Ibex uses kernel -27 and also has some Red Hat-contributed utility that rebuilds the new kernel the way you had your old kernel (if I understand the concept correctly).  This should prevent shimshams like what you are experiencing.  Anyway, I upgraded to Ibex and things look fine so far.

---

### Post by grayfox444 on 2008-11-06
I have an nVidia card, I can't remember which one exactly.  I don't recall installing a driver for it as it seemed to work fine, and has for over a year now.  
This is the first time it's been failing.

---

### Post by grayfox444 on 2008-11-06
> **lionel47 said:**
> It might behoove you to just upgrade to Intrepid through a new install.  I was experiencing some trouble with kernel upgrades in Hardy.  Ibex uses kernel -27 and also has some Red Hat-contributed utility that rebuilds the new kernel the way you had your old kernel (if I understand the concept correctly).  This should prevent shimshams like what you are experiencing.  Anyway, I upgraded to Ibex and things look fine so far.

Yeah I'll do this, I just really want to get back on so I can put my music/pictures/etc on my external so I don't lose all the stuff I haven't put on recently.

---

### Post by grayfox444 on 2008-11-06
> **geirha said:**
> Try booting with the previous kernel. When Grub starts loading hit Esc to show the menu, then select the previous kernel entry and hit enter.

I'll try this after work and get back to you. 

I'm hoping to just be able to get on and copy some newer files to my external harddrive and then do a new install with intrepid.

---

### Post by grayfox444 on 2008-11-06
it's not working.

---

### Post by geirha on 2008-11-06
Then my guess was probably wrong. After a failed login, go to a console terminal with Ctrl+Alt+F1, log in and do ```
pager ~/.xsession-errors
``` Does it show any error messages related to the login?

---

### Post by grayfox444 on 2008-11-06
hasn't shown any errors. But it says (END) and I'm unable to type.

---

