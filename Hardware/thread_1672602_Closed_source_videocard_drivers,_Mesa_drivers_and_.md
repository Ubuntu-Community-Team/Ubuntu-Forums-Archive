---
title: "Closed source videocard drivers, Mesa drivers and OS update relationship"
date: 2011-01-21
forum: Hardware
---

### Post by Avithohol on 2011-01-21
Hello All

I would like to get a general picture about 
Vendor closed source videocard drivers, Mesa drivers and OS update relationship.

I have a bit old gamer laptop, which has an ATI X1600 video card,
and i use it to develop OpenGL demos, frameworks, my game-engine.




I learned that Mesa driver is actually emulates OpenGL, so it cannot provide the same good performance that vendors (ATI, Nvidia) closed source drivers can.
So why not to install the closed source driver, right ?

There is no problem if you have the newest hardware,
the vendor will probably provide the closed source driver for it,
so you can download & install it on Ubuntu, then have fun.



The problem is if your hardware a bit outdated but still want to use it.
You have an up to dated Ubuntu (10.10) and its X window server (?)
is not compatible anymore with the old closed sourced driver.
I learned it from forums, that i should switch back to Ubuntu 8.x
if i want to use the OS with closed source driver.




Iam just wondering. What if i buy now the latest hardware which i want to use for years in the future, and still want have the most recent Ubuntu on it ?
One day in the future the Ubuntu will upgrade itself and saying,
that "sorry, but my X window system is no longer supporting your closed source
driver therefore i install the Mesa driver"

Could anybody describe the roadmap,
how it works in long term.


Thank You

---

### Post by Avithohol on 2011-01-31
Maybe i classified this topic wrong ?
Any suggestion where should i move it ?

Cheers
A

---

### Post by cascade9 on 2011-01-31
> **Avithohol said:**
> The problem is if your hardware a bit outdated but still want to use it.
You have an up to dated Ubuntu (10.10) and its X window server (?)
is not compatible anymore with the old closed sourced driver.
I learned it from forums, that i should switch back to Ubuntu 8.x
if i want to use the OS with closed source driver.

You really dont want to go back to 8.04. Desktop support runs out in april 2011. 

> **Avithohol said:**
> Iam just wondering. What if i buy now the latest hardware which i want to use for years in the future, and still want have the most recent Ubuntu on it ?
One day in the future the Ubuntu will upgrade itself and saying,
that "sorry, but my X window system is no longer supporting your closed source
driver therefore i install the Mesa driver"

That happens with windows as well, but its worse. You wont be able to install at all if your hardware isnt supported. 

Not much you can do about it. :(

---

### Post by Avithohol on 2011-02-02
Thank you Cascade9, it seems to be pretty logical,
i just wanted to hear it from somebody more expert :)

So i think i have to check specification of the "major version" updates, to see if they are still compatible my closed source driver.

Cheers

---

### Post by cascade9 on 2011-02-02
> **Avithohol said:**
> So i think i have to check specification of the "major version" updates, to see if they are still compatible my closed source driver.

They wont be. Unless ATI/AMD make new drivers, which is very, very unlikely. 

The open soruce drivers get better and better over time though. I find the current open source drivers work well with my 9600XT. BTW, ubuntu doesnt have the newest open soruce drivers, to get them you need to add a PPA.

---

### Post by mastablasta on 2011-02-02
open source are not bad on all cards. they are just a mess on some.
 
9600XT is really working well with default ones. i haven't even touched the beleding edge ones.
 
anyway with each update of ubuntu all other things (like Xserver and such) also get an update. it happens every 6 months here. in windows usually every couple of years. with older cards you would (to my expericne) at least have basic funcitonality. which is the same in linux i believe. 3D acceleration really depends. some work nice, some don't. i have an S3 old on a very old notebook i got. i don't think there is any 3d acceleration but otherwise the whole thing works fine. even flash videos. after so many years.
 
It was only "fate" that XP hold out for so long (i think it's support ends in 2012). Otherwise we would probably be upgrading more (especially since they double system requirements each time). :-)

---

### Post by Avithohol on 2011-02-10
Thank you, i think i see the point now.

You are right about XP "fate", and iam pretty sure M$ is actually changing policy, they will throw out their new OSes in every 1-2 year in the future and they will be nothing more but just updates of previous releases but with doubled sys.req.

By the way, awesome manual in your signature ;) did not see it before.


Have a nice day !

---

