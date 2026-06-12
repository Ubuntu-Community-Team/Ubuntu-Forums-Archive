---
title: "Where'd my space go?"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by Roasted on 2006-09-06
I have 2 hard drives. Each are SATA II 7200 RPM 16 meg buffer 250 gigabyte drives.

One has the operating system and programs on it. 
The other is set up like a typical "slave" drive would be. It just sits there, and I copy files to it for backup and sense of security.

Question is this.

They are 250 gig, yet Linux reads them as 233 gig. K, fine. But why does Drive A (which has the OS and all programs on it) have 174 gig free, while my second drive, which ONLY has the contents of Drive A's home folder on it, only has 161 gig free? 

Each drive has the HOME folder on it. Only Drive A has programs and such. So typically you'd think Drive A would be fuller. Not the case... Drive B is trailing behind.

Strangely enough when I formatted my 2nd drive in GParted I believe I remember seeing it readable as 217 gig, and I remember thinking WTF? Down from 233? 

Just help me make sense of this please.

---

### Post by azraelx401 on 2006-09-06
you might want to check to see if you have any unformatted space.  every now and again when formatting you tell it to format the whole drive but it really only does 95-99% of the drive.  computers are weird like that.  also keep in mind that different OS's read hard drive space differently.  but if you can't find a real solution to your problem i suggest since your second hard drive is just a back up to compress your files every so often to save space.

---

### Post by Roasted on 2006-09-06
Yeah I know different OS's read space differently. That's what has me stumped. Drive B HAS NO OS, yet Drive A does. So you'd think if A has Home+OS, and B just has Home, that A would be bigger... 

Oh well. We'll figure more out tomorrow when I'm not so sleepy. G'night!

---

