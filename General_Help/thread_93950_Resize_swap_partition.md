---
title: "Resize swap partition"
date: 2005-11-23
forum: General Help
---

### Post by ScreemingBlue on 2005-11-23
Hi,

Does anyone know what the best method is to resize a SWAP partition? 

Any help would be gratefull.

Cheers

---

### Post by az on 2005-11-23
You can use the installer to resize partitions.  You can use the love cd.  You cannot change the start of a partition, just the end.  You need to shrink the partition which comes before it, delete the swap and recreate it beginning at the newly created space.


But why do you need to resize your swap?

---

### Post by Pablo_Escobar on 2005-11-23
[QUOTE=azz]love cd[/QUOTE]

I couldn't help myself :D Ubuntus LOVE CD :D :D :D

---

### Post by pato101 on 2005-11-23
You may use several (two) swap partitions, as well.

---

### Post by ScreemingBlue on 2005-11-23
I read somewhere in a linux mag that you should never use more than 512MB of swap. I have 2.1GB. This was created automatically during installation. I think it may be a bit overkill as I have noticed that my swap hardly gets used. I have 1GB of RAM.

What do you think should I try and resize and re-claim some space or just leave it alone.

Thanks for the help. I am downloading the LoveCD now. :-)

Cheers

---

### Post by pato101 on 2005-11-24
> I read somewhere in a linux mag that you should never use more than 512MB of swap. I have 2.1GB. 
Hmmm, I have 4Gb swap... and I have almost filled it up once (doing hard  crunching-number computation). I have 2Gb Ram and swap is usually unused. But your milleage may vary depending on what you are doing, of course.

---

