---
title: "Which piece of hardware is likely to be faulty?...."
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by junior aspirin on 2005-09-01
I built up my own pc, quite high spec, but am experiencing random crashes, 1 every day or so. i would like to point out this is not a lunux/ubutu problem, it is definatly hardware related as i get crashes and or bsod in windows.

hardware:
ati radeon 9800se
1gig ram 2 512 sticks
asus k8v se delux mobo
amd64 3000+

and a few other things.

in my opinion i think it is a falty graphics card. i have run memtest - nicely included with ubuntu  ;-) and no problems there.

the lockups are realy random, occurs in games, when only firefox open, when going into screensaver, and also did it when loging in. it doesnt do it at the same point in a game, it seems totaly random. the whole machine freezes, cannot use mouse or keyboard, sound (usualy) dies and display freezes too. nothing shows in system log in ubuntu or windowz.

is there any nice diagnosic tools i could use to test my graphics card and other hardware. or has anyone got any ideas on what the problem could be and how to solve.

---

### Post by az on 2005-09-01
memtest86 is on your ubuntu system, just boot into it from the grub menu.

there is also cpuburn
[http://packages.ubuntu.com/hoary/misc/cpuburn](http://packages.ubuntu.com/hoary/misc/cpuburn)

That is a start.

---

### Post by junior aspirin on 2005-09-01
thanks, dont think it os a cpu issue. just ran cpuburn, and my oc is still fine. i realy am very impressed with linux. at 100% cpu usage everything is very responsive, ie i can drag windows around and open up apps at no similar startup times to when no cpu is used. i didnt get this in windows. used to be real laggy.

anything to test my graphics card at all?

---

### Post by mcduck on 2005-09-01
It could also be a power problem. Altough Asus uses quality condensators, you should check that none your motherboards condensators is distended or bleeding brown stuff. That would sure cause some problems, and i've seen it way too often in fairly new motherboards lately.

Also what power source do you have in your machine?

---

### Post by junior aspirin on 2005-09-01
Power supply: Antec atx12v soluton series - was recommender by a mate - i dont know much about hardware, although i beat him on getting comfotable with linux, but thats another story.

will have a look at the mobo and see if it is damaged. oh and temperature is not an issue, i have got masive fans in my pc!

is there an app similar to [everest](http://www.lavalys.hu/products/overview.php?pid=1&lang=en) for linux? it displays temps and various other stuff. that showd that my voltages were stable and temperatures are fine.

---

### Post by mcduck on 2005-09-01
Well, Antec makes pretty descent powers so I don't think that would be the problem then. Of course it may be broken, so if nothing else comes up, you might want to borrow a PSU from some friend and test with it..

As for Everest-like program, I don't know is there is any single program in linux that would give you all that info, but for temps, fan speeds and voltages you should install lm_sensors, and gkrellm or gDesklets to provide you with a nice GUI on your desktop..

---

### Post by junior aspirin on 2005-09-01
oh yar, iv been meaning to setup gdesklets for ages now.

im preaty sure its a graphics card problem (sapphire ati radeon 9800 se 256mb) i just need something to prove that its the case. wouldnt have gone for an ati if i knew about the bad driver support. thanks for all your help btw. just wish i could recreate the crashes grrrr

---

### Post by mcduck on 2005-09-01
I think we have already PSU, CPU, Memory and MoBo counted out..

I don't know any good way to test your graphics card. Some heavy games could work, but you said you get crashes even with no games.. If some of your friends has an Ati card, you could borrow it and try if another card would solve the problem. Or if it's a new card you could take it back to where you bought it and ask them to test it, but then they would propably want some money if the card is working..

To check it's not you HD that's causing these problems you could remove its cables and try running Ubuntu Live.. Hope you don't have Maxtor DiamondMax9, they have a lot of problems. Next time your system freezes, try to listen if you can hear your HDD stopping. That would mean it could be causing your troubles.

Basicly, only way to test these things is to replace one component, test if problems still exist and then try again with some other component until you find the broken one..

---

### Post by junior aspirin on 2005-09-01
i have 2 80gig seagate barracuda hD's. i doubt very much that they are the problem eather as ubuntu and windows xp are installed on different drives. boath have 2 partitions 20gig for each os and then 60gig for music and another for docs and stuff.

think its gotta be the gfx card den, as i thought all along. seems strange how it happens so random, even though just loging in, or opening a media player. btw also have a belkin network card - doubt that would be an issue. did have a tv card too, but took that out as i thought it was causing the problems.

i know half life 2 randomly crashes often, so im conviced. time to contact the lovely people at ebuyer - i hate tech report ppl, especialy when u have to do it in the form of an email - they dont have a tel number!

thanks for all your help people ;p

---

