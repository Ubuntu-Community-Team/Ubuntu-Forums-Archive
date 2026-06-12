---
title: "MP3 player"
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by served on 2005-07-07
How can i install my mp3 player (Yakumo Hypersount XD 256mb)?

If i connect the player then player shows that its ready but computer cant read it so should i install it or something??

---

### Post by geearf on 2005-07-07
Something to mount maybe ?

---

### Post by served on 2005-07-07
Ok i figured it out.
I write in the console 
mount /dev/sda1 /mnt/<MOUNT POINT>
mount /dev/sda1 /mnt/usb

But now i can see these songs but i cant del or remove them. What next?

---

### Post by geearf on 2005-07-07
do you have the rights to do so ?
what do an ls -l print ?

Maybe you need to do it as a sudo (i really don't know, just guessing).

---

### Post by served on 2005-07-07
I own my pc. so im administrator and i may do what ever i want to do. But i cant do what ever bcs im 2 noob with Linux

---

### Post by geearf on 2005-07-07
i was talking about your mp3 filesystem's right ..

---

### Post by served on 2005-07-08
well its my mp3 i copyed songs by my self. I did it under windowsXP. So what rights do i need?

---

### Post by geearf on 2005-07-08
i don't know, that is why i suggested a ls -l to see what is there.
Also it's in fat32 i suppose ?

---

### Post by served on 2005-07-27
total 2
-r-xr--r--    1 root     root          399 2002-12-27 17:44 settings.dat

if i delete file on the player in PC then it doesnt delete it from the player i just wont see thouse files anymore

---

### Post by geearf on 2005-07-27
hmm, 

I don't really know, you can still try with sudo maybe.
(sudo rm blabla).

---

### Post by served on 2005-08-08
i still havent solved the problem.

---

### Post by served on 2005-08-13
up! HELP!!

---

### Post by served on 2005-08-17
ok now i have some info: When i chose sda1 properties->Premissions
the&#324; down there is a line "You are not the owner, so you can't change these premissions" so what to do?

---

### Post by TestDummy! on 2005-08-17
You could try running nautilus using sudo. 
That's what I usually do when I get a pesky file I can't work with because of it's permissions  

Haven't learned Terminal well yet.  ](*,)

---

### Post by served on 2005-08-17
Thanks dudes but i solved it \\:D/ 
I did next: right click->File Browser.
Now i can do any thing  :razz: 
But thanx for helping, im smarter now.

---

