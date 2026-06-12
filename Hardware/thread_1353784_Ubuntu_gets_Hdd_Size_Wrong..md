---
title: "Ubuntu gets Hdd Size Wrong."
date: 2009-12-13
forum: Hardware
---

### Post by Harrison Pace on 2009-12-13
Hi folks hows it going?

Now I have a really weird issue where ubuntu is getting my hdd free space wrong. So here is the story I used clonezilla to move my old 10gb partition on my old hdd. To my new 150gb partition on my new hdd. All went smooth and after updating grub I was good to go however when I started ubuntu and checked my filesystem space. It said I had 2.8 GB left like my old hdd when I should have 142 GB left. So what is going on and how do I fix this? Here is a screen-shot [http://img138.imageshack.us/img138/2936/screenshotf.png](http://img138.imageshack.us/img138/2936/screenshotf.png) 
Any help would be appreciated!

Thanks in Advanced :-)

---

### Post by Gr8world on 2009-12-13
Are you sure that you're checking the preferences of the 150GB partition? Because the 10GB partition is recognized as "unallocated space" and the preferences window says that the size is unknown. So can it be that you're checking the preferences of the 10GB partition?

---

### Post by Harrison Pace on 2009-12-13
Mate I'm sure That space was there from a partition *I* deleted earlier!

---

### Post by Harrison Pace on 2009-12-13
I know Because If I copy 4gb file to desktop it says not enough space. ;)

---

### Post by Gr8world on 2009-12-13
yea, sorry.

I didn't look at the name in preferences. I thought you were working from the CD or something.

---

### Post by Gr8world on 2009-12-13
you can try to run "disk usage analyzer" to see what's taking the place.

---

### Post by Harrison Pace on 2009-12-13
Found out something really really really strange. I'll show tomorrow going out now cya :o

---

### Post by Harrison Pace on 2009-12-13
Look at this [http://img51.imageshack.us/img51/4554/screenshotuy.png](http://img51.imageshack.us/img51/4554/screenshotuy.png) They show different results.

---

### Post by Harrison Pace on 2009-12-14
What do you thin?k

---

### Post by Harrison Pace on 2009-12-14
After a lot of messing around in gparted I got working don't worry now! Yay!!!

---

### Post by roonie on 2009-12-14
Can you tell us what you did?

I think I have the same issue. I installed it on a 20gb partition and it was showing that I had 2.8GB of free space. Now I don't even have that as I installed updates and now its down to a few hundred MB's

I dont think a Ubuntu 9.10 installation is THAT big. What do I need to check for this?

---

