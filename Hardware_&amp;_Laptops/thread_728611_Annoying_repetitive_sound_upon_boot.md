---
title: "Annoying repetitive sound upon boot"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by alzwded on 2008-03-19
Yeah, so i i've been with ubuntu for a while now, and i just got Gutsy. Unlike the previous versions i used, this one has pretty annoying issues, be it booting from the live cd or after installing. 

First of all, right after the bootloader screen, i get a <dunnowhat>eth0 bug warning message then goes into the start up screen. (Internet otherwise works fine, i'm posting from the live cd right now)

But the weird part comes after loading gnome - the clicky sound keeps looping over and over and over... and it's not just that, i tried playing with the setting in the sound setting in gnome and when i pushed `test' the sound again went into loop and the sound window froze. (had to force quit) But, from the hard drive installation, it won't go passed the login screen, and again i get the looped clicky sound.

Does anyone know why the sound malfunctions, to say so? And why everything sound related freezes and loops after one second? Please help, i really need a linux really soon and in the past ubuntu has been the only one without any issues.

(I got a Fujitsu-Siemens amilo notebook L1310G, celeron m, realtek ac97 onboard sound card, realtek fast ethernet 10/100mb network card)

EDIT:
Okay, I've just been to the twilight zone and I'm now in the zone-where-normal-things-don't-happen-very-often... so, i was curious and booted the cd with the oem install option (if i'm not allowed to do this let me know and i'll remove it) and now it works. Then i was curious again and booted the cd once more with the start and install option and it still loops the clickety sound. Weird.... Anyway, for my common knowledge can someone please explain what's the problem with my notebook and the first boot option on the cd?

If it helps, I have had no problems with hoary and dapper, but fiesty did the same thing, but i've only tried the latter the day it was released so i thought it was just a bug. Yet, seeing this carry on to gutsy puzzles me... i am confused. :|

---

### Post by LeoSolaris on 2008-03-19
I have no real idea, but I have a couple of theories...

It may be a glitch in your sound card interfacing with the Linux driver..

It may be that you have a slightly off copy of Ubuntu...  check the md5sum.

It may be that you will have to make some alterations to the sound settings before installing Ubuntu to make it work, but I don't know exactly what to change.

What hardware are you running? Have you checked launchpad for any known bugs?

I have found that the "OEM" setting makes it a hell of a lot easier to install on other people's computers. I used it on my girlfriend's computer. (I actually used it on mine by accident and had to put all of the passwords back when I logged in for the first time, it was sort of amusing/annoying, but it let me learn.)

Leo

---

### Post by alzwded on 2008-03-19
Well, it would be wrong to have a faulty copy of ubuntu since i ordered it...

And i checked launchpad for a while but nothing really caught my eye. 

Anyway, all seems to be working now, yet it is beyond my comprehension as to why with the normal boot option it doesn't work right, yet works fine with the oem option. weird...

---

### Post by LeoSolaris on 2008-03-19
Quite strange indeed. There should be a check CD option in the boot menu... might be worth it to pop it back in and check it, even though you have the system up and running now.

What a strange glitch.
Leo

---

### Post by alzwded on 2008-04-26
Well, i'm not sure but i think it has something to do with the ati drivers, but i don't know how. I remember back when Edgy came out (which had the drivers included on the cd) it did something similiar in addition to the fan not working. Maybe they didn't fix all of the bugs related to that. Eh well, life's tough :P until i'll have the knowledge to write my own drivers i can't really complain, at least in the end everything works right, and i appreciate that. :D

---

### Post by em08 on 2008-05-09
Hallo everybody,
my name is manuel and I type from Italy. I have your same problem at the startup, with the annoying sound. I didn't found answers in italian bulletins, so here I am. Thanks for your help.
I give you same info about my system. Till yesterday I worked very well with 7.04, but yesterday I had the bad idea to change the system and pass to 7.10. First problem with the loop sound at the startup. I had the following idea: "maybe is my dvd a little bit corrupted, it will be better with the 8.04". I downloaded and... surprise: SAME PROBLEM!! Every 3or 4 reboot i can access normally to the system, but it is always a chance. 
My pc: MSI VR320, ATI RADEON (maybe here the problem??), Intel Core Duo. I do not have other sys installed. Ireally do not know what is important to find out which can be the problem, but if someone of you can do it, please ask me the data that are important to find a solution. Really annoying that after 5 betas, here we are with such a discussion...

Thank you. I hope we're going to solve the problem.

---

### Post by alzwded on 2008-06-02
Might indeed be the ATI card, a while back in dapper i remember having installed the official drivers and my computer would barely work anymore. I feel i need to ask - have you tried all combinations of boot options? Have you tried installing in oem mode? Have you tried removing the ATI driver? If so, then i join you in waiting for someone to come up with an explanation / solution.

---

