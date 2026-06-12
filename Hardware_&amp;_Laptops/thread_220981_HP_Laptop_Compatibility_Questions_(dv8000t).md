---
title: "HP Laptop Compatibility Questions (dv8000t)"
date: 2006-07-22
forum: Hardware &amp; Laptops
---

### Post by nrwilk on 2006-07-22
Heya, everyone.  I'm excited about getting my first laptop! :)

I'm getting an HP dv8000t and I want to ask a few questions about people's experiences with these and other HPs.  The machine will be exclusively Kubuntu linux, not dual-booting.

First off, here're the specs:[LIST]
[*] Intel(R) Core(TM) Duo processor T2600 (2.16 GHz)
[*] 17.0" WSXGA+ BrightView Widescreen (1680x1050)
[*] 256MB NVIDIA(R) GeForce(R) Go 7600
[*] 2.0GB DDR2 SDRAM (2x1024MB)
[*] 120 GB 5400 RPM SATA Hard Drive
[*] Super Multi 8X DVD+/-R/RW w/Double Layer Support
[*] Intel(R) PRO/Wireless 3945ABG Network w/Bluetooth[/LIST]Now, my questions.

1. Let's start off general.  How are your general feelings/experiences with the overall compatibility of HP laptops with *buntu Linux, especially Kubuntu?

2. How well is the NVIDIA GeForce Go 7600 card supported?  Will I have decent 3D acceleration?

3. I assume the DVD burner is the same as equivalents on other HPs.  Have you has success burning CDs and DVDs with the drive?

4. How is the Intel PRO/Wireless 3945 a/b/g Network?  does it work? what kind of problems does it have?  Will I be able to use it?

5. Is the internal bluetooth module the same as on other HP models?  Does it work in *buntu?  Does it take fiddling?

6. Is the touchpad on this model the same as on other HP models?  Do it's advanced scrolling and double-tap-to-select features work correctly?  How well supported is it?


I'm sure I'll come up with more questions too. :rolleyes:

Thanks so much for any answers here! :D

nrwilk

---

### Post by BKK on 2006-07-23
I have a dv5227tx (dv5000).

I have had no serious problems considering that I am very green in Linux. The touchpad works well but the ridges used to scroll a webpage etc do not function.

I dont think I have the wireless installed correctly. I just dont know how...

There are several "unknowns" in the device manager...again not knowledgeable enough to correct the issues YET!

I can use Ubuntu for connecting to the internet using a cable just fine. I mainly boot Ubuntu to experiment and learn Linux

I must admit that I must use windows to do flash and photoshop.
I also have VMware windows but I dont like how it works in Linux as I can access my USB thumb drive...and a few other things as well, eg. can't get at my shared fat32 partition...OH well

Live 'n Learn

Peace

---

### Post by Sef on 2006-07-23
> The machine will be exclusively Kubuntu linux, not dual-booting.

There was a thread, not sure if here or elsewhere recently where the person was told to keep XP on if they wanted to have their computer fixed while it was under warranty.  I would check with HP and see what their policy is.

---

### Post by nrwilk on 2006-07-23
@Sef If you mean this thread: [http://ubuntuforums.org/showthread.php?t=205565](http://ubuntuforums.org/showthread.php?t=205565)

Yes, I know about it.  I called HP and also emailed them asking what their deal is.  I was worried because I've also run across people who were told by HP that installing another OS will void the warranty.  Thank you for giving me the heads up, though!

@BKK Thanks for the run down!  I was really hoping that the scroll area on the touchpad would work.  Oh well.

:D

---

### Post by firstc624 on 2006-07-24
I have a dv5000 as well.  Ubuntu did install just fine once i partitioned my drive w/ gpart.  that said though i did have problems w/ a few things

1.  i could not get teh wireless working on my model, apparently the broadcom chipset i have 4318(9) is so new that the linux driver will not work w/ it and ndiswrapper wouldn't work for me as well, even using my windows driver...go figure.

When ever i installed the drivers and such i would end up locking my pc out and have to reinstall  ubuntu all over again, i must have reinstalled it about 30 times before i got fed up w/ tring to get the wireless working.

2.  the touchpad for me was very touchy.  It would constitaly act like i have held the left mouse button down, making it very hard to navagate thru the menus and such.

3.  Unistalling / removing ubuntu totally screwed up my hard drive.  I ened losing my entire hda.  somehow it messed up the boot partiton....very possible a mistake on my end.

4.  I really liked using ubuntu, just in my case, it is not ready for such a new laptop w/ teh chipsets i have.   It did a fabulous job w/ detecting my windows partion and setting it up so i didnt' have to edit the fstab and get to see it.


Good Luck to you.  And if you gt it working or if anyone w/ the same model gets theirs working please let me know as i would love to be able to dump windows for good.

firstc624

---

### Post by gregh on 2006-07-25
I have a dv5000 and Dapper (exclusivly) is just fine on it.
The wireless (in my case 3945) works with the drivers from 3945.sourceforge.net.

Hibernate and suspend dont work properly, but that is not an issue for me.
Screen, drives etc no problem at all.

Card reader I dont know, it does not appear in the devices, but I dont have a sd card to try so maybe it would if there was a memory card inserted.

All in all, for me, no show stoppers at all, just a couple of minor niggles (much improved on my old Tashiba A70)

-Greg

---

### Post by Sef on 2006-07-25
> @Sef If you mean this thread: [http://ubuntuforums.org/showthread.php?t=205565](http://ubuntuforums.org/showthread.php?t=205565)

Yes that was the thread.

---

