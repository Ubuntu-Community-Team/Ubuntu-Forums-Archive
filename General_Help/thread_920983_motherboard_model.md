---
title: "motherboard model"
date: 2008-09-15
forum: General Help
---

### Post by overtime on 2008-09-15
How do i find my motherboard model?

The reason i ask is because i want to see if i have the requirements to dual boot into ubuntu and vista.

---

### Post by oilchangeguy on 2008-09-15
> **overtime said:**
> How do i find my motherboard model?

The reason i ask is because i want to see if i have the requirements to dual boot into ubuntu and vista.

just tell us the computer specs. cpu speed, amount of ram, hard drive size. and it appears you already know about your motherboard:
[http://ubuntuforums.org/showthread.php?t=798115](http://ubuntuforums.org/showthread.php?t=798115)
so are you a troll? and if your computer was not born with vista, it will most likely not run vista. because of it's high power requirements, which have little to do with who made the mother board!

---

### Post by overtime on 2008-09-15
lol. whats a troll? and yes i just realized that i posted awhile back about some similar issues. 

But i still want my question answered about finding my motherboard model without opening up the case. Yes i know what my motherboard model is but this is just for piece of mind.

It does have to do with my board because depending on what my board can handle i might be able to make it compatible.

---

### Post by oilchangeguy on 2008-09-15
> **overtime said:**
> lol. whats a troll? and yes i just realized that i posted awhile back about some similar issues. 

But i still want my question answered about finding my motherboard model without opening up the case. Yes i know what my motherboard model is but this is just for piece of mind.

if you bought the computer new, it should include info on the motherboard. otherwise you get to open the case and try to read very small writing.

---

### Post by Whiffle on 2008-09-15
In Linux, 

sudo dmidecode 

may tell you your motherboard model.

---

### Post by overtime on 2008-09-15
> **oilchangeguy said:**
> if you bought the computer new, it should include info on the motherboard. otherwise you get to open the case and try to read very small writing.

I did not buy it new and I am trying to avoid opening the case.

---

### Post by oilchangeguy on 2008-09-15
> **overtime said:**
> I did not buy it new and I am trying to avoid opening the case.

don't be scared. it won't bite you. after you open the case do not touch any thing inside unless you've first touched the metal case frame.

---

### Post by jerome1232 on 2008-09-15
Also lshw shows alot of information on you computer.

```
sudo lshw
```

This will output alot of text so you'll have to scroll through it

adding a -C flag you can only get some information but I couldn't figure out how to only show motherboard

---

### Post by Vivaldi Gloria on 2008-09-15
Try 

```
sudo lshw -C system
sudo dmidecode -t system -t baseboard
```

---

