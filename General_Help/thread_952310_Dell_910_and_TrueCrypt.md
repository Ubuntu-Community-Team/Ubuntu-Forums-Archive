---
title: "Dell 910 and TrueCrypt"
date: 2008-10-19
forum: General Help
---

### Post by Duroon on 2008-10-19
A friend of mine just purchased a Dell 910 with 8.04 installed on it and wants to add truecrypt to the machine. He has tried downloading the .deb file from truecrypts site (both 32 and 64 bit versions) they both give an error when attempting to install. Essentially they both tell him he has the wrong architecture for the .deb file. The Dell 910 is running a 64 bit Intel chip. Has anyone tried one of these that might point us in the right direction to install truecrypt?

The processor used in his mini laptop is the Intel Atom Processor N270 I believe.

---

### Post by Gary Stout on 2008-10-21
Duroon,

I am running into the same problem with VirtualBox. I bought the mini 9 with the intentions of being able to run VirtualBox so that I could run XP from Ubuntu, but I am getting the same architecture error. I am leaning towards sending mine back, because I really don't want to load XP by itself. I think my problem is that VirtualBox doesn't have a 64 bit version....I just assumed it would work when I ordered the mini...not really being familiar with the N270 Atom processor. 

I am going to monitor this thread to see if anyone else has a solution.

Good Luck,
Gary

---

### Post by Gary Stout on 2008-10-21
> **Duroon said:**
> Essentially they both tell him he has the wrong architecture for the .deb file. 
Has anyone tried one of these that might point us in the right direction to install truecrypt?


Basically, the solution is to wipe out the factory installed o/s and reload it with either Ubuntu 8.04 or 8.10 beta (not Dell's modified version). I reloaded mine last night and it now works fine with VirtualBox..... no more architecture errors.

Check out this site.... it has step by step instructions to reload and fix the minor problems that might arrise afterwards.

[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

HTH,
Gary

---

### Post by Duroon on 2008-10-23
Thanks, we are going to try a fresh install of 8.04 this Saturday and see if that clears everything up.

---

### Post by Gary Stout on 2008-10-27
I might add that if you are using 8.04, it needs to be 8.04.1......plain old 8.04 won't work. It gives an error and shells out at a BusyBox prompt.

HTH,
Gary

---

### Post by Duroon on 2008-10-27
The install went just fine and Truecrypt installed fine as well.

---

