---
title: "will uBuntu support my current hardware spec?"
date: 2010-12-21
forum: Hardware
---

### Post by TweFoju on 2010-12-21
Hi, i am migrating from Windows to uBuntu as for today, but i have a little concern that my spec is too high or maybe uBuntu doesn't support my Hardware Drivers, because i am planning to totally wipe out Windows, so if this hardware's driver of mine is not supported yet, i will not bother to install uBuntu

ok here goes, im using:

AMD Phenom II X6 1090T
Asus Crosshair 4 Formula
Corsair Dominator GT 8gb
Patriot Inferno 120gb + WD 1gb
6870 1gb Xfire

i think that's it

i am not sure if i should ask this to the respective vendors or this forum

but ill just start here 1st

thanks!

---

### Post by Sylos on 2010-12-21
Your spec is well above anything I have used but one of the best ways to see if your hardware is supported is to run a live CD before installing and see what works. Download the OS - burn it to disc - pop it in the drive and select the "Try without installing" option. That should give you a reasonable starting point.

EDIT: For accelerated graphics you may want to see if your card is currently supported. That appears to be an ati card but AMDs site is lame and only appears to be offering drivers for windows ofr HD 6xxx series cards (I assumed thats what you have).

Good luck

---

### Post by mastablasta on 2010-12-21
the easiest way is to download Ubuntu, put it to a CD and then boot from CD and use the try it button. this will load the system into RAM (might take a while) but it won't change anything in your windows. if everythign loads ok and works ok chances are it will likely work on real install. perhaps even better. to try out flash and such you can try Linux Mint or PinguyOS that comes with lots of stuff preinstalled.
 
you can also dedicate only part of the disk for Ubutnu install and install it there (create dual boot) that way you keep windows arround and try and fully test Ubuntu.
 
The only issue here could be your graphcis card.
 
EDIT: one more thing - don't expect to be able to run all windows programms (especially games) in Linux. only some can run and some run limited using virtualizations or emulators. Linux is not windows. Games are often designed to run with DirectX which is a Microsoft thing only available in their products.

---

### Post by cascade9 on 2010-12-21
Everything should work except for- 

> **TweFoju said:**
> 6870 1gb Xfire!

As far as I can tell, ATI still hasnt got the linux drivers out for the 6XXX series. You can run the drivers made for the 5XXX series, but then you get an 'unsupported hardware' watermark down the bottom of the screen (if you dont do software hacks, and if it works with crossfired 6870s anyway). 

I dont have any idea if/how well crossfire works with the opensource drivers whcih are rhe only other option.

---

### Post by TweFoju on 2010-12-21
that's what i am worry about, because to my knowledge, Linux works best with Nvidia card, or so i heard

so i am a bit worried that once i use uBuntu, my ATi 6870 wont have drivers, even for some of my Mobo Drivers ( the USB 3.0 NEC Controller and such ), because Crosshair Formula is quite new in the market

yeah, i think the best way is to try from the Live CD and see if it can find drivers for all my components

the most i am worried about is my VGA, because i plan to watch HD movies, without it, useless as well

i am kinda looking for AMD Linux users, but havent been able to find any on this forum..

---

### Post by Yellow Pasque on 2010-12-21
> **TweFoju said:**
> the most i am worried about is my VGA, because i plan to watch HD movies, without it, useless as well

Unless you hack xvba support ( [http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/) ) into your install, there won't be any HD video decoding. Even if you do that, it's not always perfect.

---

### Post by TweFoju on 2010-12-21
So you are telling me that without hacks, i wont be able to watch HD movies on uBuntu?
well maybe i can accept that, all i need to know is if Ubuntu 10.10 can detect driver for my Radeon 6870

best way to know is try it myself, yes i know, but while i wait for my uBuntu downloads, if i can get answer, it would be nice :P

----edit-----

ok, found my answer, 6xxx GPU Drivers not supported yet

sigh, guess should wait longer until i jump to Linux

also, usually how long for a driver to release for new hardware? ( roughly ) ?

---

### Post by cascade9 on 2010-12-22
> **TweFoju said:**
> that's what i am worry about, because to my knowledge, Linux works best with Nvidia card, or so i heard

so i am a bit worried that once i use uBuntu, my ATi 6870 wont have drivers, even for some of my Mobo Drivers ( the USB 3.0 NEC Controller and such ), because Crosshair Formula is quite new in the market

i am kinda looking for AMD Linux users, but havent been able to find any on this forum..

Linux works with ATI cards as well. Generally, these days nVidia has the better proprietary drivers, ATI has better open source drivers. 

That motherboards isnt so new. The chipset (890FX/SB850) has been out over 9 months, and it is just a minor rivison to 790FX/SB7XX chipsets. The 890FX chipset should have work, out of the box, from release. I've had an onboard NEC USB 3.0 controller for months now, never had any issues. Not that I'm running ubuntu on that box, but with newer ubuntus I dont think there will be any problems with the USB 3.0 controller. 

I've been using a majority of AMD CPUs for years now, and I'm not the only person here like that.... 

> **TweFoju said:**
> So you are telling me that without hacks, i wont be able to watch HD movies on uBuntu?
well maybe i can accept that, all i need to know is if Ubuntu 10.10 can detect driver for my Radeon 6870

best way to know is try it myself, yes i know, but while i wait for my uBuntu downloads, if i can get answer, it would be nice :P

----edit-----

ok, found my answer, 6xxx GPU Drivers not supported yet

sigh, guess should wait longer until i jump to Linux

also, usually how long for a driver to release for new hardware? ( roughly ) ?

No, thats not what Temüjin was saying. 

What he meant was 'if you dont hack XvBA, you wont be able to decode HD by GPU.' 

That system would have more than enough power to decode any HD with the CPU. 

Who knows how long ATI is going to take to get linux 6XXX drivers. I know that the 6XXX cards are meant to run fine with fglrx 10.11 (ATI proprietary drivers) but I just dont know about crossfire working.

---

