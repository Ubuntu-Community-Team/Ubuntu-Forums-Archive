---
title: "Fans and Heat"
date: 2008-09-03
forum: General Help
---

### Post by Kalith on 2008-09-03
Hello,in windows i used various software to control fan speeds etc...in ubuntu i can only change cpu fan speed not gpu.The heat is crazy because of my pentium d 925/central heating.Im sitting around 52c idle,in windows i had it at about 46 with my gpu fan speed at 100% all the time using riva tuner etc...so right now my case is too hot which is causing artifacting after a while playing games using my 9600gt,i know from windows and playing around it doesnt like heat too much,fans at 100% solved that.Im planning on upgrading my cpu to a core 2 duo in the next 4 months or so ie less heat.But right now i cant play games for very long...and i dont want to install windows again.Nvclock is the only thing i know for nvidia cards and that hasnt been updated in a while and doesnt support 9600gt.SO cut it short,is there ANY way to change gpu fan speeds in ubuntu?

CHeers

---

### Post by Whiffle on 2008-09-03
Try installing

nvidia-settings

---

### Post by Kalith on 2008-09-03
Its installed,no settings for fan speed etc i assume your talking about x server settings? that only shows temperature and clock rates.Plus image quality settings.

---

### Post by Whiffle on 2008-09-03
Well, there seems to be nvidia-xconfig and nvidia-settings.  But I think you have the one I'm thinking of.  I think your best bet might be nvclock, whenever it gets updated.

---

### Post by Kalith on 2008-09-05
Thanks...but from what i can tell...that wont be too soon! :) I was thinking why i couldn't just flash the bios to have fans at 100% all the time...there was a tuorial about it online by using nibitor in wine(it was from 2005 though) anyway it runs fine...but it doesnt recognise my bios or device when i try to read it..Any thoughts about this?

Thankyou

---

### Post by Kalith on 2008-09-08
bump...sorry...really struggling here.Tried lots of things...still wont find my card or bios version when i read using nibitor.

---

### Post by Predator106 on 2008-09-08
If it won't find your hardware, I'm pretty sure there is nothing you can do. That's the problem with Wine, from what I've seen, hardware doesn't work well (which is understandable, really).

---

### Post by sloggerkhan on 2008-09-08
There is something in ubuntu somewhere that is dynamically controlling at least some of your fans. If you can not hard-lock their rpm's in bios and research does not yield any more informative results, you can get case mounted fan controllers for maybe $12- 30.

---

