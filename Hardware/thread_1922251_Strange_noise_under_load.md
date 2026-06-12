---
title: "Strange noise under load"
date: 2012-02-08
forum: Hardware
---

### Post by cj.surrusco on 2012-02-08
Hi everybody. I have a custom built desktop with an ASUS motherboard and AMD Athlon X4 CPU. I'm also running 5 HDs in RAID 0/5.

Recently I have been noticing a strange sound that comes from the computer. It is very similar to the sound that occurs a few seconds after the computer is shut off (right when the light on the mobo turns off). It's a type of beep.

Usually this noise occurs when the computer just starts to become under load. For example, right when a command is entered, or a file transfer is started. The computer sort of hesitates for a second, then proceeds normally. The sound is almost impossible to recreate, however.  

Any ideas? This problem has me stumped. Thanks!


UPDATE:

So the problem temporarily went away and I ignored it. Eventually it came back worse than ever and the computer no longer would boot. I was too busy to try and fix the problem, so I ran off of a flash-drive installed ubuntu OS (also in Raid0). 

It worked fine for a few days, but then odd things started happening. Cached images on websites would be corrupt, and show up in the wrong places, even after clearing cache. Also, the browser would sometimes refresh itself repeatedly, or whenever a key was pressed. Sometimes it would bring me back to the homepage. 

I figured the symptoms on the flash drive were independent, so I reinstalled Ubuntu on a newly formatted raid system on my hard drives. It ran fine for a few days, but now I'm having the same symptoms as I did on the flash drive (the beeping came back for a little while then left again). Corrupt cache, browser refreshing at will (happens in all types of browser).

Also, I had some images on my desktop and some of them randomly became corrupt overnight. Since these problem seem to be synonymus between the flash drives and hard drives, I think it must be the mobo, cpu, ram, or maybe the hard drive controller? It has to be something hardware. 

What do you guys think? It has me stumped real bad, and I'm desperate for my computer back. Thanks in advance!

---

### Post by cj.surrusco on 2012-02-08
I did some further investigation and the noise is coming from one of the hard drives. 

The disk utility says all of the HDs are healthy, but two have bad sectors. Is this the sound of a failing hard drive?

---

### Post by conradin on 2012-02-08
Its name that tune! You should record it an post it here!
(or on youtube, and post a link here)
You should never hear a capacitor discharging..
I would guess a fan, but it could be hard drive thrashing too.
would you say its a clicking sound?

What are your system specs? How much ram, swap, raid  controller...

---

### Post by winh8r on 2012-02-08
> **cj.surrusco said:**
> I did some further investigation and the noise is coming from one of the hard drives. 

The disk utility says all of the HDs are healthy, but two have bad sectors. Is this the sound of a failing hard drive?


It is not my intention to cause you to panic! Best thing to do is get anything you need off the drive you have identified as making the noise.

Preferably make a full back up of the drive and keep it safe, then you could take the possible failing hard drive and run some low level test/repair tools on it. Testdisk is good and I also use MHDD which you can find on the UltimateBootCD which is free and available here:

[http://www.ultimatebootcd.com/index.html]("http://www.ultimatebootcd.com/index.html")

Noisy drives are not always at risk of imminent failure, but this is a sure sign that all is not well inside the drive, better to be prepared for something happening than trying to find a way to recover from it!!!

Good Luck

---

### Post by cj.surrusco on 2012-05-14
Sorry for disappearing. I appreciate your answers, and I have updated the original post. Thanks!

---

### Post by cj.surrusco on 2012-05-15
Ok, the sporadic reloading has stopped. It was a messed up F5 key on my keyboard. Swapped it out and no problems since. I also haven't had any problems with the image cache in browsers since I swapped the keyboard. Don't understand how that's possible, but at least it's solved for now.

---

