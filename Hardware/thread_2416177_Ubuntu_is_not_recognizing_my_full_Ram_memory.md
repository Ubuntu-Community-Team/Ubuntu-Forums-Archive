---
title: "Ubuntu is not recognizing my full Ram memory"
date: 2019-04-06
forum: Hardware
---

### Post by fenix1jm on 2019-04-06
Hello, I have recently got a new laptop and I decided to install Ubuntu, everything works fine except that for some reason, Ubuntu doesn't seem to recognize my full 16GB Ram but instead only recognizes 15.5 GB. I've checked in BIOS to see if the correct amount of Ram is installed, and it is. It probably has something to do with Ubuntu, right? How do I fix this? Any advice would be greatly appreciated.

---

### Post by Autodave on 2019-04-06
There is nothing to fix.  It is just the way that it is reported.  It could also be that your onboard GPU is using some of the RAM as graphics RAM.

And with Ubuntu, 16 gig is way more than most people will ever see in use running programs.

---

### Post by yancek on 2019-04-06
A possible explanation at the site below.

[https://askubuntu.com/questions/923371/why-does-ubuntu-show-slightly-less-ram-than-my-computer-has-built-in](https://askubuntu.com/questions/923371/why-does-ubuntu-show-slightly-less-ram-than-my-computer-has-built-in)

---

### Post by fenix1jm on 2019-04-06
> **Autodave said:**
> There is nothing to fix.  It is just the way that it is reported.  It could also be that your onboard GPU is using some of the RAM as graphics RAM.

And with Ubuntu, 16 gig is way more than most people will ever see in use running programs.
But will it effect gaming performances or programs that require a large amount of ram?

---

### Post by fenix1jm on 2019-04-06
> **yancek said:**
> A possible explanation at the site below.

[https://askubuntu.com/questions/923371/why-does-ubuntu-show-slightly-less-ram-than-my-computer-has-built-in](https://askubuntu.com/questions/923371/why-does-ubuntu-show-slightly-less-ram-than-my-computer-has-built-in)
Most likely, it seems that my GPU has reclaimed some of the ram, seems kind of a lot though from 16 to 15.5GB but if that's how it should be. My question now would be, if it would affect gaming performances or programs that require a large amount of ram?

---

### Post by Autodave on 2019-04-06
I game on this machine.  I have never seen it use anywhere near 8 gigs (and I have 16 gigs).  You video memory will be sucked up gaming, though. Do you have a seperate GPU on that rig or just the onboard GPU?

---

### Post by fenix1jm on 2019-04-06
> **Autodave said:**
> I game on this machine.  I have never seen it use anywhere near 8 gigs (and I have 16 gigs).  You video memory will be sucked up gaming, though. Do you have a seperate GPU on that rig or just the onboard GPU?
I have two GPU's Nvidia GTX 1060 and a integrated Intel GPU. For example, if a certain game recommendation is 16GB of ram, and if only 15.5GB are usable, will it affect my performance?

---

### Post by Autodave on 2019-04-06
That is not going to affect your game.  Also, keep in mind that when gaming, the Nvidia GPU should be the one veing used and that unused RAM that the integrated Intel is using may be freed up......not sure.  But anyway, you are good to go.

---

### Post by CatKiller on 2019-04-07
> **fenix1jm said:**
> For example, if a certain game recommendation is 16GB of ram, and if only 15.5GB are usable, will it affect my performance?

Compared to what? [This answer](https://askubuntu.com/a/743669)  describes the memory allocation, and how to check it, quite well. All  operating systems need to have the kernel loaded into RAM to function.  This RAM is simply not available to other applications - you can't  unload the kernel and still have your computer function - and so Linux  reports as available memory that memory which is actually available.

Again,  all operating systems must do this, even if they don't tell you that  they're doing this. It is a given for memory allocation.

Further,  minimum hardware requirements for software are simply the  configurations that the developers could be bothered to test. If all of a  game's assets, and the overhead of the desktop environment, and all of  the other software that you might be running at the same time, could  actually fit inside 10 GiB of RAM, no one is going to bother to test  that (for every possible configuration and game state), and to say that.  The process is that most users will probably need more than 8 GiB: call it 16 GiB and call  it a day.

---

### Post by fenix1jm on 2019-04-07
> **Autodave said:**
> That is not going to affect your game.  Also, keep in mind that when gaming, the Nvidia GPU should be the one veing used and that unused RAM that the integrated Intel is using may be freed up......not sure.  But anyway, you are good to go.
Alright, thank you.

---

### Post by fenix1jm on 2019-04-07
> **CatKiller said:**
> Compared to what? [This answer]("https://askubuntu.com/a/743669")  describes the memory allocation, and how to check it, quite well. All  operating systems need to have the kernel loaded into RAM to function.  This RAM is simply not available to other applications - you can't  unload the kernel and still have your computer function - and so Linux  reports as available memory that memory which is actually available.

Again,  all operating systems must do this, even if they don't tell you that  they're doing this. It is a given for memory allocation.

Further,  minimum hardware requirements for software are simply the  configurations that the developers could be bothered to test. If all of a  game's assets, and the overhead of the desktop environment, and all of  the other software that you might be running at the same time, could  actually fit inside 10 GiB of RAM, no one is going to bother to test  that (for every possible configuration and game state), and to say that.  The process is that most users will probably need more than 8 GiB: call it 16 GiB and call  it a day.
I didn't know this, thank you for the explanation.

---

### Post by Yellow Pasque on 2019-04-07
> **fenix1jm said:**
> For example, if a certain game recommendation is 16GB of ram, and if only 15.5GB are usable, will it affect my performance?

If the game actually used that much RAM, then theoretically, it might. But there's nothing you can do about it short of adding more RAM. I suggest you not worry about it and enjoy your laptop. ;)

---

