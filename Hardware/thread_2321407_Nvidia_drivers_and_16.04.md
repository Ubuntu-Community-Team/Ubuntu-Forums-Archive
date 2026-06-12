---
title: "Nvidia drivers and 16.04"
date: 2016-04-22
forum: Hardware
---

### Post by EowynCarter on 2016-04-22
I updated from 15.10  to 16.04.

Bad suprise when booting again, login screen is is poor resolution, and unity won't start.
After recovery mode and  "apt-get purge nvidia" It switch to nouveau drivers, and it "work". But,  steam needs proprietary drivers, and installing the nvidia drivers (361), get me back where I started.

Any ideas on how to fix this ?
Edit : i forgot, GPU is a Geforce 970

---

### Post by expatver on 2016-04-22
Hello Eowyn

I had a similar problem with my 16 LTS install- I ran

sudo ubuntu-drivers devicesto determine the driver I needed and then after adding the  NVidia repository
[COLOR=#333333][FONT=DINWebPro] xorg:edgers ppa
 
I installed the driver specified, re booted  and ran fine. Hope this helps. 

Regards[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

---

### Post by EowynCarter on 2016-04-22
it says :

vendor   : NVIDIA Corporation
model    : GM204 [GeForce GTX 970]
modalias : pci:v000010DEd000013C2sv000010DEsd00001131bc03sc00i00
driver   : nvidia-361 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

But nvidia 361 (from ubuntu's repositoy) won't work. I checked the nvidia website, it's the last version.

---

### Post by EowynCarter on 2016-04-22
Installed a ppa. 364 no dice either. :(

Guess it's back to windows then :( I really feel like un-installing ubuntu. This shouldn't be happening, really. I'll wait a bit see if nvidia or canonical fixes the issue.

---

### Post by anon24 on 2016-04-22
Were you getting lots of tearing on the prior release as well? I have the same graphics card and I'm getting the worst tearing I've seen in years.

---

### Post by EowynCarter on 2016-04-23
No, never noticed anything.
What drivers are you using ?

Did you tried 16.04 ?

---

### Post by rahulyup on 2016-04-23
he's right . Ubuntu is failing to support optimus cards. The same issue with me. Nothing helps ! Either installing bumblebee shows no device found or installing nvidia-prime results in black screen .

---

### Post by wanderer3 on 2016-04-23
Ubuntu and Mint as well are not particularly HP Pavilion friendly in my experience. NVidia and Broadcom issues abounded for me.

---

### Post by anon24 on 2016-04-26
Yes, I'm using 16.04. Even before I updated from 15.10, I was still having the tearing issue. 

Also, I have this issue where I'll go to play a game in Steam and the resolution bumps down automatically. Not just within Steam, but it changes Ubuntu's resolution as well. 

Just trying to get Ubuntu to work with my Nvidia card has been an absolute nightmare.

---

### Post by EowynCarter on 2016-05-17
UP !

I *really* need some help here. 
Still no change, worked for a little while, then, went broken again. (can't login unless you do a nvidia* purge)

Live CD won't boot, so clean re-install not an option. What to do ??

---

### Post by mastablasta on 2016-05-18
> **rahulyup said:**
> he's right . Ubuntu is failing to support optimus cards. The same issue with me. Nothing helps ! Either installing bumblebee shows no device found or installing nvidia-prime results in black screen .

surely you mean nVidia is failing to support their chips in Ubuntu. there is a reason why Linus flipped them off.

---

