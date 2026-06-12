---
title: "Problem With Initial Installation"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by Reynbow on 2009-04-23
I don't know if this is really stupid and newby or whatever but anyway.
I've tried searching for this problem, quickly mind you, but all I seem to find doesn't seem to relate.

Okay so I downloaded the new Ubuntu 9.04
Burnt to a DVD with CloneDVD
Restarted computer

Then it boots to a black screen with what looks like copyright info or something of the like with some guys name, can't remember the details.

Anyway it says underneath the sentence the word "boot>" I believe, I can type anything into there, initially I hit enter, nothing, my guess was that would happen but anyway...

So anyone know what's going here? This is beyond my knowledge... lol =]

---

### Post by yeats on 2009-04-23
> **Reynbow said:**
> I don't know if this is really stupid and newby or whatever but anyway.
I've tried searching for this problem, quickly mind you, but all I seem to find doesn't seem to relate.

No problem - that's why we're here...

> Okay so I downloaded the new Ubuntu 9.04
Burnt to a DVD with CloneDVD
Restarted computer

To be clear, you did an [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of the iso image and then verified the CD Integrity (option on the start menu of the live CD)?


> Then it boots to a black screen with what looks like copyright info or something of the like with some guys name, can't remember the details.

Anyway it says underneath the sentence the word "boot>" I believe, I can type anything into there, initially I hit enter, nothing, my guess was that would happen but anyway...

So anyone know what's going here? This is beyond my knowledge... lol =]

Can you be more specific about what this actually says?  Is it BusyBox? or something else?

---

### Post by Reynbow on 2009-04-23
Okay well I'm not sure if I did the md5sum thing correctly, though it would appear that mine is 'wrong'? 
So I should re-download it? 
I must say when I was downloading it, I had some internet problems so it had to be paused and resumed a few times. I'm guessing that may have had something to do with it.

[IMG]http://i41.tinypic.com/2n9mk6.png[/IMG]

Also, I'll go back to the black screen I'm talking about and take down some notes.

*EDIT: Okay here's what comes up as soon as I try to but into it;*

[B]ISOLINUX 3.63 Debian-2008-07-15 Copyright (C) 1994-2008 H. Petter Anvil
boot:[/B]

---

### Post by yeats on 2009-04-23
> 
Okay well I'm not sure if I did the md5sum thing correctly, though it would appear that mine is 'wrong'?
So I should re-download it?
I must say when I was downloading it, I had some internet problems so it had to be paused and resumed a few times. I'm guessing that may have had something to do with it.

Looks like you did md5sum correctly, but the sums don't match, which means it's a bad image :-(.  There's no use in trying to move forward until this comes up correctly...

---

### Post by Reynbow on 2009-04-23
Well I've started downloading it again, hopefully uninterrupted this time, also from a different mirror. 
I'm guessing there's no way or really no point in trying to fix the bad copy I already have. 
The new download will finish in 15 minutes anyway xD

Thankyou for your help =]

---

