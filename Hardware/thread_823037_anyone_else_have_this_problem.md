---
title: "anyone else have this problem?"
date: 2008-06-08
forum: Hardware
---

### Post by 900donuts on 2008-06-08
heres my problem 
the only cards that i have are nvidia drivers
but nvidia drivers dished out by the restricted driver manager are not working with my cards the computer will boot up alright use the best screen resolution i want but when i try to use software that tries to use hardware acceleration the program fails to open with an illegal instruction error 

the software that i tried are 

bzflag
blender3D
phun
teeworlds
gridwars2
screensavers

if any one else has this problem tell me

---

### Post by Victormd on 2008-06-08
You might want to try installing the drivers using Envy-NG (listed in the repos as envyng). From what I understand, this will install the latest NVIDIA drivers (different from the restricted drivers)

---

### Post by 900donuts on 2008-06-21
sry it took to long but i tried it twice and...

it didn't work:(

my computer simply doesn't seem to work with the 169.12 driver i tried it with my 5200fx which apparently uses the same driver

any other idea and/or explanations as to why this is happening

---

### Post by 900donuts on 2008-06-23
bump (my summer is draining away and I'm getting desperate)

---

### Post by sdennie on 2008-06-23
My guess is that you need to use the legacy drivers and not 169.12.  I'm not sure how to do this without using envyng (though, I'm sure it's possible).  Try:

```

sudo apt-get install envyng-gtk

```

Then go to Applications->System Tools->EnvyNG and install the legacy drivers.

---

