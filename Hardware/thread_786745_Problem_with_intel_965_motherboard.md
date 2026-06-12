---
title: "Problem with intel 965 motherboard?"
date: 2008-05-08
forum: Hardware
---

### Post by kpashok on 2008-05-08
**Anybody please help me....**

I cant install or run the live cd of ubuntu 7.04.
Config:
Intel Core 2 Duo E6300
Intel G965RY Board
WD SATA2 HDD
LG DVD RAM

I think the 965 chipset is not compatible.
Can I solve this problem using a video card?

---

### Post by null.toaster on 2008-05-09
Hey kpashok, I'll help you out if I can, but I need a little more info. For example, does the cd start at all, does it just hang after the menu. Also, any more hardware info would help, for example, are you using onboard video or a video card, and what model is your video hardware (if onboard, my guess is gma3000).

I'm currently running 8.04 on a Vaio notebook (was running 7.xx before that), which has a 965 chipset (shouldn't be very different from a desktop), and everything works just fine.

---

### Post by kpashok on 2008-05-09
Thank you toaster,

I dont have a video card and use intel GMA x3000 onboard graphics.
The disc boots but different problems occur for different versions
eg.For ubuntu 7.04 pc edition, it shows 'user not known for the underlying authentication module'
edubuntu 7.04 shows 'Cannot read file'

I cannot install any other linux like debian.

Configuration:
Core 2 duo E6300 1.86GHz
Intel DG965RY Board
512 MB 667MHz DDR2
160 GB SATA2 HDD
DVD DL RW

Please Help Me.........

---

### Post by null.toaster on 2008-05-09
Ok, after reading around a bit, it looks like there are some serious issues with both 7.04 and 7.10, and your motherboard. It looks like the ide controller doesn't work properly with either 7.04 or 7.10. 

I hate to say it, but it looks like the easiest option, in my opinion, would be to get 8.04 (if you can't download it, i believe ubuntu will ship a copy for free).

edit: One last thing, I had a similar issue caused by my bluetooth hardware, you don't have any bluetooth hardware do you?

---

### Post by mogators08 on 2008-05-09
I too am having a problem installing 8.04 live cd on my Dg965ry. My setup:
Dg965ry
Core 2 6300
2 gig Kingston value ram 667
Nec 1712 monitor
Evga 7600 GTS
Samsung Writemaster DVD
Seagate 80  Sata drive
Wd 160 gig Sata drive

When I start the live cd I get a corrupted video and that is far as it gets. I have used the same cd on an ancient 633 celeron box and it worked perfectly. 

I have tried to disable video card in bios but vista boot manager has hijacked the f2 key that I am supposed use to get to the bios, so no luck there. Any suggestions for this noob?

---

### Post by null.toaster on 2008-05-10
@mogators08: Does it corrupt at the livecd menu, or after the menu?
If it corrupts say during the loading screen try this:
At the live cd menu, select your language, then press f6. You should see a long string of text show up near the bottom of the screen, find the word "splash" and change it to "nosplash". You might even remove the "silent" option, as it might give you a better idea what is going on. PM me if you need further help :D

Also, to get into your bios, you should be pressing the key much earlier than the boot loader.

---

### Post by mogators08 on 2008-05-10
Thanks for the reply null.toaster. Yeah I was playing with it last night and found the f4 menu, start in safe graphics mode, and it loaded up fine. The resolution looks good too.

 About the bios thing, when my box boots up I have a screen that says hit f2 for bios, which used to work. But since I've put vista on it go to the vista boot manager instead of bios like it did when I had xp. I don't know, I guess vista wants to own everything.

Hey kpashok, You might try the f4 options on the ubuntu start up and see if that gets you up and running.

---

### Post by RJARRRPCGP on 2008-05-11
If the live CD crashes, probably because the hardware is newer than the version of Ubuntu. 

But, the "Cannot read file" or similar error message sounds like a damaged or dirty CD.

---

### Post by information_entropy on 2008-05-11
I am posting from an Intel DG965RY based system
It is currently running 7.10 and was previously running 7.04

I never got it to function properly with an IDE DVD or CD drive
I tried a lot of them.

As soon as I installed an SATA DVD everything worked fine

The on board IDE controller chip can give you fits
But, you already know this. ](*,)

If you have an SATA DVD drive it should work.

---

### Post by pigbig842001 on 2008-05-11
I have DG965WH board. Ubuntu runs out of the box on it. Compiz-fusion runs like god. Quake 3 Arena is much faster than on Windows XP.

I have:

1 GB Kingston ValueRAM
LiteON LH-20A1P 20X DVD Writer
Seagate 160 GB SATA hard disk.

No issues at all.

[IMG]http://i226.photobucket.com/albums/dd309/pigbig842001/CompizFusion01.jpg[/IMG]

[IMG]http://i226.photobucket.com/albums/dd309/pigbig842001/CompizFusion02.jpg[/IMG]

[IMG]http://i226.photobucket.com/albums/dd309/pigbig842001/CompizFusion03.jpg[/IMG]

[IMG]http://i226.photobucket.com/albums/dd309/pigbig842001/CompizFusion04.jpg[/IMG]

---

