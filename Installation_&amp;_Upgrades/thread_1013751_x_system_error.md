---
title: "x system error?"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by Spitz13 on 2008-12-17
I am completely new to ubuntu and linux in general so please brace with me. I recently decided to install linux and have a dual boot system. So i procedeed to download Mandriva 2009 (the problem is really about ubuntu) but after creating a 5 gigabyte ext3 partition and a 1 gigabite swap partition ( i have 1 gigabyte of RAM) i installed it. but when i tried to boot to it, i would get a corrupted screen, in other words, a bunch of pink and yellows on top of a green background. i rebooted to it, and i pressed cntrl+alt+f1 and i found a command line, in witch i could log in to the account i had created. but i couldn't manage to get into a desktop view of mandriva. Not being able to deal with this problem, i formated the ext3 partition and the swap partition and i installed ubuntu 5.10 only to find it would lead to the same problem, minus the corrupted screen (the one with colors) after booting to ubuntu, i would get a command line, in witch i could log into ubuntu, but i couldn't get to a desktop. Also, before i got to the command line, i got an error about x system (GMD grafical interface) not being able to load. i am so sorry if i cannot express myself in a more advanced way, but i've been using windows my entire life, so i'm new to all this kinda stuff, so please brace with me.

cheers.

---

### Post by joff13 on 2008-12-17
Hi,

please help us understand more:

[LIST]
[*]what pc ?
[*]download and use ubuntu 8.04.1 Desktop edition 
[/LIST]

try to run the live CD and tell us whether it works or not
if not, edit the grub entry and add xforcevesa

---

### Post by Spitz13 on 2008-12-17
The pc I'm trying to run ubuntu on is an HP Pavilion dv9008nr:
Processor:1.6 GHz AMD Turion&#8482; 64 X2 Dual-Core
Ram: 1gb DDR2
Video: NVIDIA GeForce Go 6150 (UMA)  [I think this might have something to do with the corrupted screen I got on mandriva]

Also, I kinda thought downloading another ubuntu would be a waste of time because since mandriva also gave me an error, I really doubted it was something having to do with ubuntu.. but then again, I don't know anything about linux, so if you recommend that, I'll get to it :)

thanks.


EDIT: I'm running the live cd of ubuntu 5.10 now, I'll post a response with the result in a bit.

---

### Post by joff13 on 2008-12-17
> **Spitz13 said:**
> 
EDIT: I'm running the live cd of ubuntu 5.10 now, I'll post a response with the result in a bit.

this is really old... I suggest 8.04.1 because there are 3 years of new technology... and, I know that you have a 64bit processor, but try with i386

again, try adding xfocevesa. $I think your problem is just a matter of setting in you xorg.conf file

---

### Post by Spitz13 on 2008-12-17
I tried running the live cd, and after loading everything, I got a black screen that lasted over 10 minutes, so I guess that didn't work either (unless its supposed to do that). About my older version, once I get this ubuntu to work I'll download a newer one, I just want to have this one working before I download a newer one, just so I know it won't give me the same response at ubuntu 5.10 and mandriva 2009..

also, sorry but I don't know anything about linux yet, but how would I go about doing this?

[quote=joff13]again, try adding xfocevesa. $I think your problem is just a matter of setting in you xorg.conf file[/quote]

 :-?

---

### Post by lovelyvik293 on 2008-12-17
To add the "xfocevesa" 
```

gksudo gedit /boot/grub/menu.lst

```
And add "xfocevesa" in the end of ubuntu kernel you want to use.

---

### Post by joff13 on 2008-12-17
> **Spitz13 said:**
> 
also, sorry but I don't know anything about linux yet, but how would I go about doing this?



 :-?

Sorry, by heart i do not remember exactly how the boot menu of the live CD is done, but press F1

usually you can edit a grub entry ba pressing "e" on the desired line

---

### Post by Spitz13 on 2008-12-17
> **lovelyvik293 said:**
> To add the "xfocevesa" 
```

gksudo gedit /boot/grub/menu.lst

```
And add "xfocevesa" in the end of ubuntu kernel you want to use.

Do I enter this in the command line once I get into ubuntu(the command line without the desktop), or is it another command line?
Sorry for the really nooby questions.

---

### Post by joff13 on 2008-12-17
> **Spitz13 said:**
> Do I enter this in the command line once I get into ubuntu(the command line without the desktop), or is it another command line?
Sorry for the really nooby questions.


you cannot use this command
[LIST=1]
[*]no x running
[*]live CD
[/LIST]

you have to give the instruction to grub at boot time as i explained

---

### Post by Spitz13 on 2008-12-17
> **joff13 said:**
> you cannot use this command
[LIST=1]
[*]no x running
[*]live CD
[/LIST]

you have to give the instruction to grub at boot time as i explained

One last question before I try this, when I press e on the ubuntu kernel, i get four command lines, that I can choose to edit, delete, or create a new one, the last one being boot if I remember correctly, at the end of witch command line do I add "xfoceversa" to?

Sorry if theese questions are stupid, but I'm really new

---

### Post by Spitz13 on 2008-12-17
So I added xfoceversa to the line in GRUB that started with "kernel" (I believe it was the second one). And I had the same problem, also, I managed to read the xsystem error diagnosis and it said:

Fatal Error:
no screens were found
(if I remember correctly)

I'm at the moment downloading ubuntu 8.04, in hopes it'll magicaly work(despite ubuntu 5.10 and mandriva 2009 not working).

but yeah, please tell me if I did the xfoceversa thing wrong.. or any other solutions you guys can come up with, and once again, sorry for being so new and not knowing anything :P

cheers.

---

### Post by joff13 on 2008-12-17
> **Spitz13 said:**
> So I added xfoceversa to the line in GRUB that started with "kernel" (I believe it was the second one). 


on the kernel one is correct 

> 
And I had the same problem, also, I managed to read the xsystem error diagnosis and it said:

Fatal Error:
no screens were found
(if I remember correctly)


It seems that it's unable to find your screen
> 
I'm at the moment downloading ubuntu 8.04, in hopes it'll magicaly work(despite ubuntu 5.10 and mandriva 2009 not working).

but yeah, please tell me if I did the xfoceversa thing wrong.. or any other solutions you guys can come up with, and once again, sorry for being so new and not knowing anything :P

cheers.

good idea, but 8.04.1 not 8.04 
actually there is 8.10 to, but I had some other problems, and also, 8.04.1 is the LTS one

good luck

---

### Post by Spitz13 on 2008-12-17
> **joff13 said:**
> 
good idea, but 8.04.1 not 8.04 
actually there is 8.10 to, but I had some other problems, and also, 8.04.1 is the LTS one

good luck

Well I downloaded ubuntu 8.04.1 and I ran it without change to my hard disc, it booted to it, but once again, right where my desktop should be, is just a bunch of flashing colors, this is the third version of linux this happens with.. I don't think its linux, maybee just something with my computer, but I really have no idea, maybee its not picking up my video card? I don't know, you guys tell me..

cheers.

---

