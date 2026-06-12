---
title: "Permissions of a partition"
date: 2007-07-21
forum: Hardware &amp; Laptops
---

### Post by Shaggmire on 2007-07-21
i got a gateway cx200x from a friend of mine, it had windows on it but a system file was corrupted on it so i had to wipe it, first i was going to repair it, but it gave me the oddest error message ver, it said i didnt have a hardrive eventually i said **** windows and put in my ubuntu 7.14 cd and wiped the whole hdd, i partitioned my 60gb hdd in half in hope that i could get windows on here some day on the second partition, ive givin up hope on that, but now im stuck with two 30 gb hdds but the second one i cant use because the pemissions are to root, i can use the gnome partition editor to erase it and cange formats, but the permissions are always for root. Please some one help me. How do you take permissions of partitions? i really need that little bit of extra space, and i dont have anything to back up on and i dont want to wipe everything and start over.

---

### Post by markusf21 on 2007-07-21
where is the drive mounted?

---

### Post by Shaggmire on 2007-07-22
dev/sda2

---

### Post by markusf21 on 2007-07-22
try this 
```
sudo chown username:username dev/sda2 
```
username = your username
This will make you the owner so u can do what u want with it

---

### Post by Shaggmire on 2007-07-22
thanks, it seemed to work but not completely i can click and drag things into it but thats it, it only copies thing in, i cant edit or creat folders or anything
ps, i got it wrong its actually mounted as /media/disk
and my username is danial

i put in

sudo chown danial:danial /media/disk

did i do it right? it didnt ask me for my password like it usually soes when i use sudo

---

### Post by markusf21 on 2007-07-24
U did it right but I didn't I forgot 1 small bit
```
sudo chown -R username:username dev/sda2
```
I forgot the -R witch means recursive so it changes the folder and everything in it 
Sorry

---

### Post by Shaggmire on 2007-07-24
right right no worries

---

### Post by Shaggmire on 2007-07-24
Thank you thank you!!!!

---

### Post by markusf21 on 2007-07-24
Glad to help

---

