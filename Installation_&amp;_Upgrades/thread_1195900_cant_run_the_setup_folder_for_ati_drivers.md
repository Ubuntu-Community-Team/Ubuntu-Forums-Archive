---
title: "cant run the setup folder for ati drivers"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by cnand on 2009-06-24
Hi i have downloaded the specific drivers for ati radeon 9600 for ubuntu 9.04 and when i try to run it i get the this warning

[IMG]http://img31.imageshack.us/i/screenshotsda.png/[/IMG]
[http://img31.imageshack.us/i/screenshotsda.png/]("http://img31.imageshack.us/i/screenshotsda.png/")

i tried the second choise also in the character coding but neither western worked.
What do i do to install the drivers?
Thank you in advance i would appreciate an answer

---

### Post by cnand on 2009-06-24
anyone?

---

### Post by cnand on 2009-06-24
still w8ing for some help

---

### Post by cnand on 2009-06-25
i cant find a way to run the file anyone knows anything?

---

### Post by Divider on 2009-06-25
first rename it to ati.run

next open terminal.

type 
```
cd Desktop 
``` ^-- captial D


```
sudo sh ati.run
```

Enter your password and there ya go.

Remember to do an 
```
 sudo aticonfig --initial 
```

before you reboot.

---

### Post by Mark Phelps on 2009-06-25
> **cnand said:**
> Hi i have downloaded the specific drivers for ati radeon 9600 for ubuntu 9.04 and when i try to run it i get the this warning


Basically, there are no ATI drivers that will work with your card in Ubuntu 9.04, regardless of what you downloaded.  AMD/ATI dropped support for all but the new "HD" cards in their drivers, starting with Catalyst 9.4.  While support for the older cards is in Catalyst 9.3 and prior, those versions will not work with the Xorg in Ubuntu 9.04.

So, if you figure out a way to FORCE the installation of these drivers, you will most likely get a black screen as a result.

Pays to do some forum searching (there are dozens of posts about this problem!) before you try installing restricted drivers.

---

### Post by cnand on 2009-06-25
Divider thank you very much m8 for giving a path on how to start, but still that doesnt work as the other fellow replied i think that my card is not compatible with 9.04.Same problem that i had in 7.10...
I ill try different ways but i dont want to force myself to get back to the cage's so-noftware...You can understand what i am saying here.Ubuntu is my only way out of errorwindows and pure enviroment i ll try my best here to find that solution.I have done till now in 2 days 28 formats and installs cause of that problem (cause when i try to run it in open gl of fglrx i have an error again and a screen that i cant see nothing).
Thanks again both of you m8s i appreciate your help if anyone knows another solution i would happily consider it

---

### Post by Mark Phelps on 2009-06-27
Hey, I understand your frustration ... really.  I have one of the "older" ATI cards that has been dropped from support, and for the first time since Ubuntu 7.04, I now have to do without 3D acceleration!

AMD/ATI are NOT going to suddenly feel bad about their business decision and update their restricted driver to handle what they view now as "legacy" equipment. The open source drivers now are a LOT better than they were in the 7.04 days, and perhaps over time, they will get even better.

But, as I tried to explain, other than buying a new card that IS supported, THERE IS NO SOLUTION other than the open source drivers currently installed by default.

---

### Post by cnand on 2009-07-10
Ok i tried everything but nothing seems to work as the fellow above replied ati doesnt have any drivers for ubuntu 9.0.4 regardless what it says...If i find a way to force intsall any kind of driver i will post the solution.Thanks all of you that you spend your time replying and trying to help me.

---

### Post by Mark Phelps on 2009-07-12
I've tried to make this clear, evidently not well enough ... so, I'll try again ...

No one has discovered a way to install a restricted driver for ATI cards that will work with Ubuntu 9.04 and your card. Everyone who tried either installing from the source, or using EnvyNG to force an install, ended up with a black screen and blinking cursor, or no display at all.

Some folks even tried building their own "older" Xserver from source (the version that works with the older accelerated drivers), and then discovered conflicts with the newer kernel.

So, if you built your own kernel from source as well as Xserver from source, I guess it MIGHT be possible -- but no one has reported any success in doing that.  And if anyone HAD done it, given the numbers of folks now frustrated by having to resort to open source drivers, I think we would have heard about it.

---

