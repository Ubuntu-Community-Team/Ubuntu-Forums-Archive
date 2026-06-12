---
title: "64bit dual core"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by Chymera on 2007-08-05
I want to run ubuntu on a comp with Intel Xeon 5050 processor (dual core, 64bit).

I found the 64bit  version of ubuntu on the dl page, however theres no mention of dual core. I searched the forums and found smth about a SMP kernel or smth like that. Where do i get that? do i have to compile it myself ? :( 

And after i get it, will all the apps i dl via synaptic automatically be installed in 64bit mode? What if i want to add apps that are not under synaptic, like pidgin or smplayer? will i have to compile 64bit versions of them? (i dont see any 64bit downloads on their sites)

---

### Post by tgm4883 on 2007-08-05
Yes the 64-bit version will automatically use both cores (or more than 2 if you have that many).  It is compiled like that in the generic kernel.

Anything that you apt-get (or synaptic) will be for 64-bit.  If you need things that are not in synaptic, then you will either need to see if they have a 64-bit version, or look for a workaround (although most things are in synaptic.)

Check the 64-bit forum for more info.  You will need to manually install flash and such, but it's really easy.  Hardly worth mentioning

---

### Post by avik on 2007-08-05
Exactly what tgm4883 said.  I'm running the 64bit version on a dual core PC, and it works just fine.  There's nothing to set up to get that working, and there are HOWTOs and scripts on this forum on getting things working with regards to flash and so on.

Pretty much anything in the repos will have a 64bit version and that version will automatically be installed when you ask for that program.  It's no big deal.

---

### Post by Chymera on 2007-08-05
The iso install cd for 64bit is called amd64, and the discussion board x68 64-bit users has the title comment
> For the discussion of Ubuntu on the AMD 64 platform

Does that mean intel users are not included? or why does it specifically state that it is for users of the "AMD 64 platform"?

---

### Post by tgm4883 on 2007-08-05
don't worry about that.  AMD came out with 64-bit first so thats where it all comes from.  Intel followed and is compatible with the AMD64

---

