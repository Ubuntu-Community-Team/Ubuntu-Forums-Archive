---
title: "What to do with Binaries?? HELLLP!?"
date: 2008-08-05
forum: General Help
---

### Post by Thyssenkrupp on 2008-08-05
Okay, so, i finally rebuilt my computer with a nice new case, blue fans and bubble lights, and i looked at my set up an thought, wow, this looks like an online gamers laaaaaaair, so, i was thinking i wanted to start playing an online game, and have just now downloaded Planeshift.

I have downloaded the linux binary (as i dont have much luck with Wine)

So, how will i  install the game? ive never used a binary (knowingly) before so is there something i have to do different with it or what?

(Btw, its the 32 bit version.)

Thanks for the help!

Jak

---

### Post by Titan8990 on 2008-08-05
I assume you already untarred it? If not do the following:


$ tar -xvf <name of tarred package>

$ cd <name of new untarred directory>

$ ls


Post the contents of the ls command.

---

### Post by Paradoxalley on 2008-08-05
> **Thyssenkrupp said:**
> Okay, so, i finally rebuilt my computer with a nice new case, blue fans and bubble lights, and i looked at my set up an thought, wow, this looks like an online gamers laaaaaaair, so, i was thinking i wanted to start playing an online game, and have just now downloaded Planeshift.

I have downloaded the linux binary (as i dont have much luck with Wine)

So, how will i  install the game? ive never used a binary (knowingly) before so is there something i have to do different with it or what?

(Btw, its the 32 bit version.)

Thanks for the help!

Jak


Usually, installing a binary requires that you first make it executable and then execute it...
for these purposes, we will assume that you have downloaded the binary named "PlaneShift-v0.4.01-x86.bin" to your desktop. open a terminal window by clicking "Applications" >> "Accessories" >> "Terminal".
At the terminal window type:
```
cd Desktop
```
(this will change to your Desktop)
then type
```
sudo chmod 755 ./PlaneShift-v0.4.01-x86.bin
```
(This will set the executable bit on the Planeshift binary)
then type
```
./PlaneShift-v0.4.01-x86.bin
```

usually, the binary installer will ask you a few questions and let you know if anything needs to be done to install properly so pay attention to the output on the terminal

Let us know if you run into any trouble.
Seth

---

### Post by Thyssenkrupp on 2008-08-05
Ahh i see, thanks both of you, i will try this out  when its finished dwnloading (1hr 32mins) and repost to say the results..

Thanks again.

Jak

---

### Post by Titan8990 on 2008-08-05
Also it is usually customary for them to include instructions in the package. It is common for this to be called README or INSTALL:

$ less README

$ less INSTALL

---

