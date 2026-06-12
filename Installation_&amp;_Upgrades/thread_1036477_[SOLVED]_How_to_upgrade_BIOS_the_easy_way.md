---
title: "[SOLVED] How to upgrade BIOS the easy way?"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by BazookaAce on 2009-01-10
Hi, 

I'm trying to upgrade my BIOS on my Acer Aspire One A150 with Ubuntu 8.10, but it ain't that easy. I've downloaded and installed Unetbootin, made a bootable USB-stick with the DOS-thing (don't remember the name), rebooted, and then, i'm stuck. 

So, my question is; is there an easier way to upgrade my BIOS in Ubuntu? In Windows, we can use Winflash, that makes BIOS-flashing very easy, but the thing is, i don't have Windows. 

So, does it exist a program that will do the same thing in Ubuntu? 

Please help me. I really  need to upgrade the BIOS :)

---

### Post by Shazaam on 2009-01-10
Found this...
[http://ubuntuforums.org/showthread.php?t=694513](http://ubuntuforums.org/showthread.php?t=694513)

---

### Post by oilchangeguy on 2009-01-10
> **BazookaAce said:**
> Hi, 

I'm trying to upgrade my BIOS on my Acer Aspire One A150 with Ubuntu 8.10, but it ain't that easy. I've downloaded and installed Unetbootin, made a bootable USB-stick with the DOS-thing (don't remember the name), rebooted, and then, i'm stuck. 

So, my question is; is there an easier way to upgrade my BIOS in Ubuntu? In Windows, we can use Winflash, that makes BIOS-flashing very easy, but the thing is, i don't have Windows. 

So, does it exist a program that will do the same thing in Ubuntu? 

Please help me. I really  need to upgrade the BIOS :)

why do you think you need to upgrade the bios?

---

### Post by abn91c on 2009-01-10
just so you are aware if you mess up the bios flash you will turn your laptop into a paperweight. It will be nearly impossible to undo.

---

### Post by BazookaAce on 2009-01-10
I need to upgrade it because of Acer. The current BIOS has a critical error, that's causing Acer Aspire One's with BIOS version 3301, getting black screens, and then making them useless. It happened me once, and it won't happen again. I hope. The screen is also flickering in Ubuntu, and i've heard that it's the BIOS who's doing it. 

So, i'm thinking i'm going to upgrade it now, and then i'm finished with it. No more anoying flickering and black-screen-of-death. ;)

------------------

The link that's provided in this thread is nice, but it doesn't work. So.. i don't know what i can do now. I did try to use WinFlash when accessing XP with Virtualbox in Ubuntu, but it says it can't find the drivers. It's the same story when i'm trying to do it in Wine. I've read that it's a known problem in the "real" XP and Vista, and i don't know the solution to this problem.  

The problem i'm having with the FreeDOS(?)-method is that i don't know what drive my USB-stick is, cause when i'm making it bootable with Unetbootin, it says that my USB is drive "sdb1". Ok, but i don't think it will work with "CD:/sdb1 in DOS. Sorry, i've tried. I've also tried drive A, B, C, D, E, F, G, and so on. It won't boot. :(

---

### Post by oilchangeguy on 2009-01-11
> **BazookaAce said:**
> I need to upgrade it because of Acer. The current BIOS has a critical error, that's causing Acer Aspire One's with BIOS version 3301, getting black screens, and then making them useless. It happened me once, and it won't happen again. I hope. The screen is also flickering in Ubuntu, and i've heard that it's the BIOS who's doing it. 

So, i'm thinking i'm going to upgrade it now, and then i'm finished with it. No more anoying flickering and black-screen-of-death. ;)

------------------

The link that's provided in this thread is nice, but it doesn't work. So.. i don't know what i can do now. I did try to use WinFlash when accessing XP with Virtualbox in Ubuntu, but it says it can't find the drivers. It's the same story when i'm trying to do it in Wine. I've read that it's a known problem in the "real" XP and Vista, and i don't know the solution to this problem.  

The problem i'm having with the FreeDOS(?)-method is that i don't know what drive my USB-stick is, cause when i'm making it bootable with Unetbootin, it says that my USB is drive "sdb1". Ok, but i don't think it will work with "CD:/sdb1 in DOS. Sorry, i've tried. I've also tried drive A, B, C, D, E, F, G, and so on. It won't boot. :(

you do NOT need to flash the bios. the bios is NOT the cause of your problems. since it seems you don't understand what the bios is. and what it does. you should read this:
[http://www.informit.com/articles/article.aspx?p=332850](http://www.informit.com/articles/article.aspx?p=332850)

---

### Post by BazookaAce on 2009-01-11
It's the BIOS who's causing the "black-screen-of-death". Hundreds of people on the Aspire One-forum had the BSOD, and like me, we had to do a BIOS-recovery. So yes, i know it's the BIOS. 

I also read on THIS forum, that people with the Aspire One having "problems" with flickering screen, and after upgrading the BIOS, the problem is gone. So, i'm going to upgrade it regardless the links and stuff you're posting. Read a little about the problems with Aspire One first. 

But if you're "sure" that it's not the BIOS, then please, tell me what's wrong.

---

### Post by oilchangeguy on 2009-01-11
> **BazookaAce said:**
> It's the BIOS who's causing the "black-screen-of-death". Hundreds of people on the Aspire One-forum had the BSOD, and like me, we had to do a BIOS-recovery. So yes, i know it's the BIOS. 

I also read on THIS forum, that people with the Aspire One having "problems" with flickering screen, and after upgrading the BIOS, the problem is gone. So, i'm going to upgrade it regardless the links and stuff you're posting. Read a little about the problems with Aspire One first. 

But if you're "sure" that it's not the BIOS, then please, tell me what's wrong.

then reload your computer to factory specs (reinstall windows) and go to acers website. they should have bios updates for your model. do it the correct way. then you won't need to do it the "easy" way.

---

### Post by BazookaAce on 2009-01-11
Yeah, but the "funny" thing is that re-installing XP on the computer isn't that easy as if i had an eksternal-CD/DVD-ROM. And i really don't want to re-install XP just to upgrade the BIOS. So, i just think i must use my brain a little bit more, and come up with something "smart". Wish me luck. Hehe

---

### Post by Zeroberry on 2009-01-11
Checkout what form you can get the BIOS in, if you get can get the files themselves isn't it simply an issue of booting them off a disc? Your BIOS could have options to help you out in that.

---

### Post by BazookaAce on 2009-01-11
Here's the BIOS-files: 

3309.bat
flashit.exe
ZG5_3309.fd

Any idea?

---

### Post by oilchangeguy on 2009-01-11
read this:
[http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html](http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html)

it's amazing what you can find when you do a google search. i typed in acer one a150 bios update, and came up with this link, and there are many more. perhaps some research on your part is in order.

---

### Post by BazookaAce on 2009-01-11
I've already tried that. It's the "Macles-method" i tried the first time ;) It didn't work. I tried at least 5 times without any results. :(

---

### Post by oilchangeguy on 2009-01-11
> **BazookaAce said:**
> I've already tried that. It's the "Macles-method" i tried the first time ;) It didn't work. I tried at least 5 times without any results. :(

then take it to a computer shop. there's not much else this forum can do for you.

---

### Post by BazookaAce on 2009-01-11
Yeah, i think i'll do that. But i'm going to try the Macles-method one more time. But.. the new problem is that i can't mount my USB-stick! It worked yesterday! 

Sooo typical. I've tried different methods to make it mount, but it just won't do it. 


I'm laughing so much now! What's next?! Throw it on me! Do your best! You can't break me!! :D

---

### Post by BazookaAce on 2009-01-11
Wow..! It's.. working now.. :confused:

It just poped up on the desktop from nowhere! :D And i did't do anything special! I like it!

---

### Post by oilchangeguy on 2009-01-11
> **BazookaAce said:**
> Wow..! It's.. working now.. :confused:

It just poped up on the desktop from nowhere! :D And i did't do anything special! I like it!

ok, please use the thread tools to mark your thread solved.

---

### Post by boof1988 on 2009-01-11
> **oilchangeguy said:**
> read this:
[http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html](http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html)

it's amazing what you can find when you do a google search. i typed in acer one a150 bios update, and came up with this link, and there are many more. perhaps some research on your part is in order.

Perhaps less arrogance and rudeness on your part.

---

