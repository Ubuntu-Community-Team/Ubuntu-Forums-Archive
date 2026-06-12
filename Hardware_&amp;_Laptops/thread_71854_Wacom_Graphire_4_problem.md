---
title: "Wacom Graphire 4 problem"
date: 2005-10-04
forum: Hardware &amp; Laptops
---

### Post by icenine on 2005-10-04
Hello to everyone. This is my first post here, though I spent a lot of time reading the forums. 

First of all, i want to thank all the people that helped me in this forums, making my transition to ubuntu easier and nicer.

Then, to the problem. I bought a Wacom Graphire 4, hoping to get it working in linux, since my Trust Tablet was not working and i heard that there was support for wacoms, in linux.

So I searched for informations and basically i had 2 ways to go:
1 -[http://ubuntuforums.org/showthread.php?t=25151&highlight=graphire]("http://ubuntuforums.org/showthread.php?t=25151&highlight=graphire")
2-[http://linuxwacom.sourceforge.net/]("http://linuxwacom.sourceforge.net/")

i followed the 1-approach, and i got nothing (i mean, the tablet is working but there is no pressure management etc)

regarding the 2-approach, it is actually scaring me, since i have a fine ubuntu system now, and i fear to break somthing; most important, i wonder if i have to go that way, since some people in my situation managed to solve the problem so easily!

my question is : what should i do to get the pressure etc working? i read everything wacom-related in ubuntuforums and still i cant get it to work!

does anybody know if there is a special problem with the graphire4 ?

i hope someone can help me, since this damned tablet is the only thing keeping windows installed on my pc

greetings and thanks in advance,
icenine.

---

### Post by miatapaul on 2005-10-04
If you notice the sourceforge site it does not say they support the Wacom Graphire 4. to quote them:
[INDENT]**Supported USB Devices**   [LIST]
[*]PenPartner 1
[*]Graphire 1, 2, & 3
[*]P4 Cintiq & CintiqPartner
[*]Intuos 1, 2, & 3
[*]Cintiq 21UX
[*]Volito 1 and 2   [/LIST] [/INDENT] 
I am thinking I may get a Graphire 3 from B&H as they seemed to have a really good deal on them and it may at this point be better supported in Linux. I know I have seen posts where people have them working. The other thing I have read is that you may need to use a newer version of The Gimp.

---

### Post by icenine on 2005-10-05
thanks for answering, miatapaul

the graphire4 should behave just like a 3, since they have the same technical specs... only difference is that the 4 has a pad with a wheel and 2 buttons, like the intuos

---

i'm pretty frustrated for this tablet, and i hope to get it working, since i need it for my job; the funny (funny?) thing is that it works in Gimp, under XP, while in linux it never shows to recognize pressure

beside that, i noticed that when i reboot the machine, the event number of the tablet changes (and i have not it plugged into an hub); sometimes the tablet is not even assigned to an event; i have mouse, keyboard and tablet on usb

please help me getting this tablet working! i am getting used to linux again, and i dont want to get back to it when i work at home!

your,
icenine.

---

### Post by icenine on 2005-10-05
now the situation is even stranger :

- from the led on the tablet i can see the signals are being received (the led is blue when in stand by, meaning the usb connection is active, and it gets green if i move the stylus over the tablet, meaning it is processing the input)

- i do "sudo cat" in /dev/input and i see that moving the sylus over the tablet produces garbage on screen for event4 and mouse1 too! (now i have the mouse switched from mice to mouse0)

- apart from those outputs, i get no onscreen movement of the pointer, nor in gnomedm nor in applications like gimp

anyone can help me?

---

### Post by icenine on 2005-10-06
i am trying to do all the linuxwacom stuff again, but after
./configure --enable-wacom
when i try a 
make 
i get this :
/home/ice9/linuxwacom-0.7.0/src/2.6.10/wacom.c: In function `wacom_intuos_inout':
/home/ice9/linuxwacom-0.7.0/src/2.6.10/wacom.c:427: error: syntax error before ')' token
/home/ice9/linuxwacom-0.7.0/src/2.6.10/wacom.c:432: error: break statement not within loop or switch
/home/ice9/linuxwacom-0.7.0/src/2.6.10/wacom.c:433: confused by earlier errors, bailing out
make[5]: *** [/home/ice9/linuxwacom-0.7.0/src/2.6.10/wacom.o] Error 1
make[4]: *** [_module_/home/ice9/linuxwacom-0.7.0/src/2.6.10] Error 2
make[3]: *** [all] Error 2
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
anybody can help?
fixed : at line 427 of wacom.c there is an error, it seems... a doubled ")"  ... i removed it and it compiles... strange

---

### Post by kxs on 2005-10-12
so your graphire.4 works or not? i`m going to buy one, but will it work under linux?

---

### Post by icenine on 2005-10-17
the support for the graphire4 will probably be in the next release of linuxwacom drivers, this is what the coder of the project said to me

so at the moment the tablet is not working in ubuntu, and i have to use it in windowsxp

anyway, the thing will be fixed soon, it seems.. let's hope :)

ice9

---

### Post by dadoprom on 2006-08-05
It works perfektly for me: Graphire 4 - Gimp, Inkscape :D

---

### Post by cywhale on 2006-08-05
This thread is from Oct 2005 , Ubuntu Hoary board !?

For anyone getting into this thread via the board search for "wacom" or "graphire4" like me or something similar - got it working for _dapper_:

Ubuntu Dapper, Wacom Graphire4

Simply followed the instructions given at [http://www.ubuntuforums.org/showpost.php?p=1264856&postcount=98](http://www.ubuntuforums.org/showpost.php?p=1264856&postcount=98) .
Had to reinstall ubuntu a few times, worked perfectly every time.
Good luck with this.

---

