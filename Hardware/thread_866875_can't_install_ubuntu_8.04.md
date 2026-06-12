---
title: "can't install ubuntu 8.04"
date: 2008-07-22
forum: Hardware
---

### Post by erik.tamsen on 2008-07-22
so i got an older laptop from a friend and now im trying to install ubuntu on it. i had an old version 5.04 laying around so i tryed it with that and it worked without problems. now i discovered that it is so old that there are no longer updates. so i downloaded 8.04. now im trying to install it but is just doesnt work. the first screen shows up where i can choose the language, then i can decide if i want to install or test the cd etc. i checked the cd for defects, there where none, i did the test memory and everything was fine. but when i do the install ubuntu, the logo and a bar show up and then there is a black screen with a little line blinking in the upper left corner. 
the laptop is kinda old, its a dell latitude ls.
i have never worked with linux before but im sick of using windows...
i hope someone can help me.

---

### Post by Potatoj316 on 2008-07-22
How much memory does the laptop have, and what is the processor speed?

---

### Post by snowpine on 2008-07-22
Hi Erik, I have a Dell laptop from about the same era (Latitude Cpx) so here is my experience. In order to install Ubuntu from the Live CD, you need to upgrade your RAM to 384mb (or even better 512), and even then, it will not be fast. If you only have 256mb, you'll need to install using the Alternate CD instead, and if you have less than 256mb, forget about using Ubuntu. 

If you are looking for a beginner-friendly Linux that is a little quicker than Ubuntu, check out Xubuntu instead (I recommend installing from the Alternate CD as well). It runs well with 256mb of ram and is about 90% the same as Ubuntu. There are other "distros" that are quicker on old machines, but not necessarily as beginner-friendly. Personally I use Fluxbuntu on my old Dell laptop. It is quite a bit faster than Xubuntu, but I hesitate to recommend it to you at this stage in the game. :)

---

### Post by mgm2rr on 2008-07-22
I have had a similar problem.  If old hardware locks up during the install process, try the alternate install CD.  Just go [here]("http://www.ubuntu.com/getubuntu/download") and check the alternate CD box right under the green "Start Download" button before clicking on it.  It does not include live CD functionality, but it allows you to do the install just as easily in a text based environment.  Once its installed and you have added a SWAP partition (which is automatically part of the install) the machine will be able to use the swap space in lieu of extra RAM and it should be able to run.  Of course, the other option as mentioned before is to just buy more RAM for your machine.

---

### Post by erik.tamsen on 2008-07-22
thank you.:-D
i'm actually not sure how much memory it has, cause i just got it. but i will look it up after i get up.
i will try it with the alternate cd, and or xubuntu.

---

### Post by erik.tamsen on 2008-07-23
ok i think it has 126mb.
so i used the xubuntu alternate disc now and everything worked out fine during the instalation.
the first time i booted though it didnt work.
it said:
[2381.526151] ata1.00: status: {DRDY}
[2382.854535] ata1.00: status: exception Emask 0x0 SAct SErr 0x0 action 0x2 frozen
[2382.854653] ata1.00: status: cmd c8/00:08:00:00:00/00:00:00:00/e0 tag 0 dma 4096 in
over and over just with different numbers
sometimes there was also a Boffer I/O Error on device sda, logical block 0

i rebooted it and now its working (i havent rebooted a second time jet)
should i worry about that?

---

### Post by paul101 on 2008-07-23
if it works fine. . . you shouldn't be worried :)

---

