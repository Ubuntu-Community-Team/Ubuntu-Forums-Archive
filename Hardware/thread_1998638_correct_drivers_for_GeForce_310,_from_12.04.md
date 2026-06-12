---
title: "correct drivers for GeForce 310, from 12.04"
date: 2012-06-07
forum: Hardware
---

### Post by jamaas on 2012-06-07
I'm having no end of problems trying to rebuild a system after a crash, didn't resume properly.

I have a Dell machine that tells me it has a nvidia GT218 or GeForce 310 rev2 card in it but I can not seem to get the correct drivers for it.  Can anyone please tell me which of the many nvidia drivers I have avaialble to me in synaptic, is likely to be the correct one?

I've tried unsuccessfully to load using "additional drivers" but that didn't work either.

I'm using 12.04 and a Benq G2420HD monitor.

Thanks a bunch.

Jim

---

### Post by jamaas on 2012-06-09
It appears that lots of people have had a look at this post but no one had a solution. I got a solution of sorts 

booted to recovery mode, got a terminal window

sudo apt-get purge nvidia*

then downloaded the latest nvidia drivers for this card from the nvidia website, a file that ended .run, changed it to executable using

sudo chmod u+x *.run

the executed the file using 

./.......run 

and it ran and now it boots.  However still don't have 3D acceleration and 
Gnome 3 will not run properly.  Any thoughts or suggestions on how to overcome this would be most welcome.

Thanks

J

> **jamaas said:**
> I'm having no end of problems trying to rebuild a system after a crash, didn't resume properly.

I have a Dell machine that tells me it has a nvidia GT218 or GeForce 310 rev2 card in it but I can not seem to get the correct drivers for it.  Can anyone please tell me which of the many nvidia drivers I have avaialble to me in synaptic, is likely to be the correct one?

I've tried unsuccessfully to load using "additional drivers" but that didn't work either.

I'm using 12.04 and a Benq G2420HD monitor.

Thanks a bunch.

Jim

---

### Post by Thras0 on 2012-06-09
Hi. I had a similar problem with my Lenovo v370 when running Ubuntu 12.04. My card is GF 410m , and the only solution was to disable Optimus from Bios. Although I have a dedicated button to switch between graphic cards , it doesn't work on Linux.

I'm using Linux Mint 13 (Cinnamon desktop with graphic card disabled from bios) and it's beautiful. No screen tearing , no overheating due to crap nvidia drivers, battery life is decent.

If you have the option to disable nvidia, then why not.

P.S. Running nvidia proprietary drivers ended in a kernel panic for me :)

---

### Post by jamaas on 2012-06-10
Thanks Thras0,

I'm sure you are correct.  I'm no expert at this and as you know, it gets difficult when you loose you're graphics because it leaves you in command line mode trying to fix things.  This is a desktop, not a notebook so I'm assuming that is a physical graphics card as opposed to some chip on the motherboard, but I should tear it apart and see.  

If I understand correctly, what you are saying is that installed correctly,  using the intel hardware only and the correct driver I can still get 3-d graphics and thus Gnome 3 working correctly again?

If anyone knows a howto for this would be useful.  I know there is lots of stuff spread around but for novices it is hard to corroborate.

Thanks

J

> **Thras0 said:**
> Hi. I had a similar problem with my Lenovo v370 when running Ubuntu 12.04. My card is GF 410m , and the only solution was to disable Optimus from Bios. Although I have a dedicated button to switch between graphic cards , it doesn't work on Linux.

I'm using Linux Mint 13 (Cinnamon desktop with graphic card disabled from bios) and it's beautiful. No screen tearing , no overheating due to crap nvidia drivers, battery life is decent.

If you have the option to disable nvidia, then why not.

P.S. Running nvidia proprietary drivers ended in a kernel panic for me :)

---

### Post by Thras0 on 2012-06-10
Hello again.

Yes I am only using the Intel integrated card on my laptop with Linux Mint 13 (everything worked out of the box).

I also have a desktop running Kubuntu , but that one has a dedicated ATI card. The opensource drivers work fine on that machine. I play some (older) games under wine (Dota, Diablo 2, etc .. )on it, without any problems. 

You might wanna take a look at : [COLOR="DeepSkyBlue"][https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")[/COLOR] , in case you haven't already.

It's the opensource approach to nVidia Optimus technology.

Hope it helps, or at least sheds some light upon your problem.

---

