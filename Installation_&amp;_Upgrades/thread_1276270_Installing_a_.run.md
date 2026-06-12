---
title: "Installing a .run"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by teitzelb09 on 2009-09-26
Hey,

New to ubuntu

I got really tired of windows. So i converted :D. Anyways, so im new right.. i dont fully understand so speak clearly and explain why things are the way they are. I am a quick learner and i love to learn about this kind of stuff but so far im having trouble because this is all so new. anyways. i need some graphic drivers and i downloaded them to my desktop. its a .run file. i did some reading and i right clicked it and made the program run and then double clicked and ran it in terminal.. it works.. but then it says i have to be root. im not to sure about the command system. still reading up on it a little bit... and whenever i try to log on to root just to see if i can do it. it asks for a password but my keyboard wont let me type anything? hmm.. lol anyways.. thank you and i appreciate the help and bare with me on the explaining. any one who has msn that wouldnt mind keeping me up to date and helping me out a little add me. [EMAIL="bwt05@hotmail.com"]bwt05@hotmail.com[/EMAIL]. (well not actually msn but like amsn or w.e :D lol)


ALSO: i did read some other threads and they taught me some but they didnt seem to work..

---

### Post by rreese6 on 2009-09-26
First of all let me say "Congratulations for becoming free".
Linux is great, but there a few things to remember.
Linux is safe as long as you install from the program manger system.
all files there are in packages that are checked to be compatible (cough) but the main thing is that they are safe to use.
Now we all get to the point we need something that is in a .run or .bin.
understand that allowing a program to run that way could mean that your system might be compromised...So you loose the security of Linux. Especially when a program is asking to be run as root.

Ok now that the lecture (short version) is done. tell us more.
what version of ubuntu are you running?
what is the name of the graphic program you want to run?
Tell us why you think you need to run it (there may be an easier solution and a safer one).
Please don't think that I am being difficult, I want to help you and at the same time keep you and safe and your system stable.
Linux users install differently than the Windows world.

I will explain how to install it once you reply back. At that time I will explain about the password "mystery".

---

### Post by teitzelb09 on 2009-09-26
Okay.. I agree...  I am running the newest ubuntu 9.04 i believe its the exact number.

Is that program on by default or do i need to get it and whats the exact name of it (to search for)

I have a GeForce 6800 gt so i went and downloaded the drivers for it from the official nvidia site. i trust them because thats what i like to buy :D

the file name is NVIDIA-Linux-x86-185.18.36-pkg1.run

---

### Post by teitzelb09 on 2009-09-26
also, what are .rpm files. are those the same as like .rar for windows? and do i need like codecs packs or what..

---

### Post by oboedad55 on 2009-09-26
> **teitzelb09 said:**
> Okay.. I agree...  I am running the newest ubuntu 9.04 i believe its the exact number.

Is that program on by default or do i need to get it and whats the exact name of it (to search for)

I have a GeForce 6800 gt so i went and downloaded the drivers for it from the official nvidia site. i trust them because thats what i like to buy :D

the file name is NVIDIA-Linux-x86-185.18.36-pkg1.run

Look under Administration>Hardware Drivers for your nVidia card. I've got a 6200 which works great with these drivers. It gets sticky trying to install the kind of drivers you're trying to run. As for other programs look in Administration>Synaptic Package Manager. There you can do a search for type of program, etc. If you're looking for something to do a specific thing post back and you'll get lots of good advice. Main thing is take it slow and don't panic.

---

### Post by rreese6 on 2009-09-26
+1 Oboedad

See there there is a way to do it with having to do the .run file.
the the Hardware Driver Program will let you select to install the proprietary driver.. and you stay safe
now for the "Mystery" of the root password.

When you type the root password in the termnal you will never see anything as you type, but it is being accepted. that is just a part of good security so no one could see wow many letters your password is by counting the number of symbols * returned tot he screen

your root password is the same as the one you log in with.
if you need to do something in the terminal that need permission, use the sudo command...but be really careful and be sure you know what you are doing..
Take care and have fun!

---

### Post by teitzelb09 on 2009-09-26
Hey thanks alot. both of you. I got what i was looking for and more. Ill definitly be staying here. you guys made a great first impression. kudos!

---

### Post by teitzelb09 on 2009-09-26
Also. so i play cabal. which can not be run in linux. but would it even be worth the try to get VMware and play it through that. or will it slow down.

---

### Post by j.bell730 on 2009-09-26
> **teitzelb09 said:**
> also, what are .rpm files. are those the same as like .rar for windows? and do i need like codecs packs or what..

To get codec packs do this:
**System** > **Administration** > **Software Sources**
Tick the "*Software restricted by copyright or legal issues (multiverse)*" checkbox.

**Applications** > **Accessories** > **Terminal**
Type this:
```
sudo apt-get install ubuntu-restricted-extras
```

Also, about the packages:
**Distro specific** (packaged for your easy installation)
[Debian, Ubuntu] = .deb
[Red Hat, Fedora] = .rpm

**Non-distro specific** (tougher to install)
.tar.gz
.tar.bz2

---

### Post by oboedad55 on 2009-09-26
> **teitzelb09 said:**
> Also. so i play cabal. which can not be run in linux. but would it even be worth the try to get VMware and play it through that. or will it slow down.

Can you supply a link? I Googled "cabal" but as you might suspect I got lots of stuff!

---

### Post by teitzelb09 on 2009-09-26
Cabal Online is the real name of it. made my ogplanet.

---

### Post by oboedad55 on 2009-09-26
> **teitzelb09 said:**
> Cabal Online is the real name of it. made my ogplanet.

If it's an online game, which I can't really tell, it should work in any browser. You may need to have flash installed but that's easy enough.

---

### Post by teitzelb09 on 2009-09-26
it is a browser game. its a actual program with servers and everything. its similiar to like world of warcraft

---

### Post by renkinjutsu on 2009-09-26
i just searched wine's appdb for cabal, and it's rated as garbage as far as running on wine.. so a VM might do the trick.. How much RAM do you have?

---

### Post by teitzelb09 on 2009-09-26
So what does that mean. i have wine. Ive only got 1 gig of ram. hehe this was a good computer.. about a decade ago ha. this is my old computer that had a virus so i put linux on it so that i can learn it before upgrading my laptop and gaming computer

---

### Post by oboedad55 on 2009-09-26
> **teitzelb09 said:**
> So what does that mean. i have wine. Ive only got 1 gig of ram. hehe this was a good computer.. about a decade ago ha. this is my old computer that had a virus so i put linux on it so that i can learn it before upgrading my laptop and gaming computer

It means that it probably won't run well with wine. So you can run windows in a virtual machine, like virtualbox, under Ubuntu. Google virtualbox and you'll see.

---

### Post by teitzelb09 on 2009-09-26
You wouldnt happen to have instant messenger of somesort that i could talk and ask a lot of little questions?

---

### Post by oboedad55 on 2009-09-27
> **teitzelb09 said:**
> You wouldnt happen to have instant messenger of somesort that i could talk and ask a lot of little questions?

I'm "oboedad55" on aim and yahoo.

---

