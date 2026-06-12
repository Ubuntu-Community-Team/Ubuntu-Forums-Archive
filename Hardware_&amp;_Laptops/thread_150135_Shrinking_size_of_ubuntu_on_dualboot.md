---
title: "Shrinking size of ubuntu on dualboot"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by abrainlessdude on 2006-03-25
is there a way to shrink the size of ubuntu (i gave it 10 gigs at first on my laptop, but now I need the size for a school program).

Is there a way to shrink or even (sadly) take ubuntu off of my laptop, I still have it on my pc, but I cant think of any way to shrink it.

---

### Post by aysiu on 2006-03-25
You can shrink it with a live CD.
Do you have a live CD (Knoppix or Ubuntu)?

---

### Post by taurus on 2006-03-25
Just install gparted and use it to resize your Ubuntu then.
```

sudo apt-get install gparted

```

---

### Post by aysiu on 2006-03-25
[QUOTE=taurus]Just install gparted and use it to resize your Ubuntu then.
```

sudo apt-get install gparted

```[/QUOTE] But if you're using Ubuntu, you can't resize the partition you're using--resized partitions need to be unmounted, which is why a live CD is necessary.

---

### Post by abrainlessdude on 2006-03-25
[QUOTE=aysiu]You can shrink it with a live CD.
Do you have a live CD (Knoppix or Ubuntu)?[/QUOTE]
I have ONE live CD left, those things go like hotcakes. I cant burn them fast enough at my school.


[I'm spreading ubuntu like the common cold in the place!]

So use Gparted and... I know this is noobish, but would you mind giving me a fast walkthrough of the steps, I havent used gparted, I've never had to do this before :(

---

### Post by aysiu on 2006-03-25
[QUOTE=abrainlessdude]
So use Gparted and... I know this is noobish, but would you mind giving me a fast walkthrough of the steps, I havent used gparted, I've never had to do this before :([/QUOTE] If it's a Ubuntu live CD, boot it up, then go to Applications > Accessories > Terminal and type ```
sudo apt-get update
sudo apt-get install gparted
sudo gparted
``` the rest shoud be obvious.

---

### Post by abrainlessdude on 2006-03-25
[QUOTE=aysiu]If it's a Ubuntu live CD, boot it up, then go to Applications > Accessories > Terminal and type ```
sudo apt-get update
sudo apt-get install gparted
sudo gparted
``` the rest shoud be obvious.[/QUOTE]I deleted the wrong drive, oops. ](*,) 



So now I'm getting another XP professional shipped to me.  Untill then, I get to enjoy the bliss of not being a microsoft noob.  After then... well, :cry: 


I will never give up though, I'm trying to get wine to run the prog.

---

