---
title: "Radeon Xpress 1150 not working with 12.04?"
date: 2012-05-06
forum: Hardware
---

### Post by ualla on 2012-05-06
Hi all,
 
I'm in the process of pensioning my old laptop, a Dell Vostro 1000 (AMD TurionTM 64 X2 Dual Core Processor TK-53, 2GB Ram and Ati Xpress 1150 integrated graphics).
 
I'd like to use Ubuntu as OS, but I seem to be having a problem. Every time I try installing Ubuntu 12.04 (I have tried the previous release as well), I get a screen with vertical coloured lines. Red, green and blue lines on a black background, so I can't see anything at all. 
 
I've tried both 32 and 64 bit versions and i've tried actually installing the OS and just trying the live USB. The results are always the same unfortunately.
 
A few years ago (around build 7 I believe) I did manage to run Ubuntu, and from a little bit of research I've read that some things have changed from version 8.
 
Is there anything I need to change with regards to the setup or do I have to include different drivers in the installation USB? I've read that the Vostro 1000 is in the compatibility list + I haven't read about this issue I am having anywhere else.
 
Any help would be greatly appreciated!
 
Thanks!

---

### Post by ualla on 2012-05-09
Uppity up?

Anybody with an idea? I'm ready to give any possibility a go. 

Cheers!

---

### Post by WarezCoxtrong on 2012-05-10
I have the exact same laptop (came with 1GB ram though, I upgraded to 3GB) and I'm running 12.04 64-bit.  I didn't install 12.04 directly though, I started by installing 11.10 on here several months ago, and then this morning upgraded to 12.04 through the Update Manager, and the video card does still work, but not with the proprietary drivers for this specific card. (fglrx drivers I believe)  I had to use the generic ATI drivers with it.
Basically, you won't get any real video acceleration (so newer games will play like garbage/not play at all), but the display will work. I'm able to run Quake III through WINE with no issues though, even with no real video acceleration.

From what I understand, ATI quit supporting this specific chipset on their proprietary drivers somewhere around 8.10, and on the 32-bit versions of Ubuntu at least (not sure about 64-bit), there were supposedly ways to force it to work up to 9.10 I think.

Try switching to a terminal (Ctrl+Alt+F1 - Ctrl+Alt+F6) and type ```
modprobe ati
``` and see what happens.

---

### Post by ualla on 2012-05-29
Hi there,

first of all thank you so much for your reply. I had actually abandoned the possibility of somebody replying to me at a certain point :)

To be honest I'm not too bothered about acceleration as I'd like to use the laptop as a sort of server and internet portal. Only problem is that I can't get anything to appear on screen. It is so weird.

I can't even access a terminal as all I see is vertical coloured lines.

I guess I might have to try including the proprietary drivers in the ubuntu installation (if at all possible).

Thanks again for your help!

---

