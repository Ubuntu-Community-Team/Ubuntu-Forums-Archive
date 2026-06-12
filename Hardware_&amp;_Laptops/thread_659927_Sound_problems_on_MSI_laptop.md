---
title: "Sound problems on MSI laptop"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by kr0ots on 2008-01-06
Hello ,

I'm using Gutsyon my MSI EX600. I have the famous bug of headphones. When you plug it it doesnt switch the speakers off.

So i decide to compile the new drivers of ALSA. I did it without problems but the bug was still here . SO i read some topics about the /etc/modprobe.d/sound modifications.

I put this line options snd-hda-intel model=3stack. and the end of the sound file.It was working not so bad but not really perfect . SO i decide to change the 3stack options in another i found in the wiki.
I made many changes & many reboot...One time the sounds becomes horrible ( i bet its because the mic is near the speakers ). Its cryinng just after the Desktop appear..and freeze 10 sec later...
I reboot in recovery copy the /etc/modprobe.d/sound with the backup with 3stack inside and reboot 

But the sounds is the same, i try to chande the sound file , to delete it but i cant fix this.......

I use some options of the sound file where the mic is not recognize but the sound going crazy !!!!!!!!!!

I dont know how to fix that. However the PC freeze each time so i cant use it ,:(

If somebody have a clue....

thanks

NB: sorry for the english mistake , i 'm french :)

---

### Post by kr0ots on 2008-01-07
nobody can help me??

---

### Post by jkpere on 2008-01-23
If u still haven't find a solution, it's about to write
```
 options snd-hda-intel model=targa-dig 
```
 well, it worked at my MSI EX600 in Debian. :)

---

### Post by knock86 on 2008-06-08
Hei, i' ve the same headphones bug in my MSI EX600...I'm a beginner in the linux world so if sombody might give me more information on how to solve this problem, i'll be very grateful...
thanks again...

---

