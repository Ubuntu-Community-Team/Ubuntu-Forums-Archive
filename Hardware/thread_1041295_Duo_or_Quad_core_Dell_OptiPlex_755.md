---
title: "Duo or Quad core Dell OptiPlex 755"
date: 2009-01-16
forum: Hardware
---

### Post by jakyra_1 on 2009-01-16
I'm getting a new computer at work and I've been given a choice about whether to get a Duo or Quad core computer.

I've got no support for being on Linux here, so it's my responsibility to make sure that Ubuntu is doing to work on the computer that is purchased. Also, if there are issues between the hardware and software I need to resolve them myself. 

I've only been using Ubuntu for a few months (Previously was on Fedora), and I'm relatively new to Linux in general. It was pretty challenging for me to move to Ubuntu, and because of the lack of support, it's a bit of a political issue for me to be down for an extended length of time setting up my machine.

Issues of concern for me:
Dual head Radon. (Currently using [http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html) for setup although that was a beast and a half to figure out.)
LAMP (MySQL and PHP 5)
VirtualBox would be nice although I don't currently have it set up.
Mounting highly secure Windows boxes

The two machines I'm looking at are:
OptiPlex 755 Small Form Factor  with 
Intel® Core™ 2 Quad Processor Q6600 (2.40GHz, 8M, 1066MHz FSB)  	
 
and
OptiPlex 755 Small Form Factor with
Intel® Core™ 2 Duo Processor E6850 (3.0GHz, 4M, VT, 1333MHz FSB)

Both with
Memory: 4.0GB DDR2 Non-ECC SDRAM, 800MHz, (4DIMM)
Vidoe Card: 256MB ATI Radeon 2400 XT, Dual Monitor DVI or VGA (TV-out), low profile

Does anyone know if I'll have more or less problems with one of these or with this config? Are there other hardware gotchas?
Also I'm wondering if I should go with x64 or x32. Any experience there?

Any assistance would be appreciated.

---

### Post by iggykoopa on 2009-01-16
you shouldn't have problems with either of these setups, for what you are going to be running though I think the dual core processor will run better for you, it has a higher clock speed and since not many applications are properly written to support smp it should run faster. I would only recommend the quad core if you are going to be encoding videos on it or if you are going to be running multiple clients in virtualbox when you set it up.
I would recommend x64 or you want be able to use all 4gigs of ram, also most of the problems with 64 bit have been resolved by now...there is native flash, java installs fine, etc. I've been running 64bit on two of my machines and havent had any problems so far.
I don't have any experiance with the ati cards, but they are supposed to be in the process of opening their drivers so I can only see the support for them getting better.

---

### Post by jakyra_1 on 2009-01-20
Thanks. That's all good to know.

I had heard that x64 were buggy, it's good to know that most of that is worked out. I can't really afford something that consumes a lot of my time right now. 

I appreciate your time.

Thanks again.

---

