---
title: "[SOLVED] help me pls,problem with linux ubuntu..."
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by peter bee on 2008-02-29
dear all..... 

 ook first i'm a new user on ubuntu os,i juz brought a new hard disk 120gb on yesterday becoz  my OS hard disk only 80gb...problem is when i wanna format the new hard disk time i cant see the hard disk in  
my file system,so what can i do now??????
 and the 2nd is how to format the hard disk in ubuntu??izzit need command to write???




hope everyone can teach n help me pls....

[SIZE="5"]THANKS[/SIZE]

---

### Post by Yellow Pasque on 2008-02-29
Go to System -> Administration -> Partition Editor (on Ubuntu)
If you're using Kubuntu, I don't know the GUI way to fire up gparted off the top of my head. You'll have to go to a terminal and type:
```
kdesu gparted
```


Just don't do anything stupid like deleting existing partitions :)

---

### Post by belda on 2008-02-29
first of all and most important is subject of your question
this is ubuntuforums.org, 
we know, you have **problem** otherwise you wouldn't write here 
we understand you want to **help with it** otherwise you wouldn't write here 
we suspect it is problem with **ubuntu** otherwise you wouldn't write here 
and believe me, we realize ubuntu is linux :):):):)

to your problem, the new hdd is not formatted nor has it partitions, therefore you probably dont see it, what I recommend would be ideal for you  is gparted, which has good gui for this. it is located on the installation cd, but i suggest you install it via aptitude or from console
```
sudo apt-get install gparted
```
but be careful when working with gparted, because you can easily erase the system partition (check twice if you are changing the 80 or 120 GB disk

---

