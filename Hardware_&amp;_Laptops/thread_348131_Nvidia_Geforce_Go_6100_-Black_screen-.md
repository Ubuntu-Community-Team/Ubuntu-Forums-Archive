---
title: "Nvidia Geforce Go 6100 -Black screen-"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by mangaeva on 2007-01-28
I start this topic again cause I had to reinstall my linux.

So I have an MSI Megabook M670 laptop with AMD Sempron 1.8 Ghz processor, 1GB RAM, Nvidia Geforce Go 6100 and wide screen. I was really happy that i could start to use Linux. Im really new for everything and first i thought that the problem is in me when i tried to install the nvidia driver. but after i found automatix i realized that its not cause me that i get a black screen when i could sign in. I hear the drums and such just cant see anything. I tried out things i found on the net but non of them seemed to work.

I attached the right xorg.conf this time. 

Every idea is Welcome, i really dont know why i cant fix it, tho cause im really new to this all, im not really knowing what im doing, but im really sad about it that i couldnt make it alone.

Hope one of you guys can help me. I fee like a noob, but im reading about linux in the past 2 days. So i hope that i will get better.

Thanks for every help. Hope that finnaly i will be able to use the nvidia and the wide screen resolution.

---

### Post by alfo_uy on 2007-01-28
do you have the eeprom module loaded?

generally you should have seen it in the setup of lm sensors, am i right? 

(unload it)

good luck.


i don't know if you did it or not, but just in case, first search and then ask.
and welcome to ubuntu.

---

### Post by mangaeva on 2007-01-28
> **alfo_uy said:**
> do you have the eeprom module loaded?

generally you should have seen it in the setup of lm sensors, am i right? 

(unload it)

good luck.


i don't know if you did it or not, but just in case, first search and then ask.
and welcome to ubuntu.

Hi there. I did search for methodes to correct this problam, just non of them worked... 

Hope my questions wont bother you:

What is an Eeprom module, and how can i unload it?
And i dont know what you mean by this "generally you should have seen it in the setup of lm sensors, am i right?" I use Automatix 2 to install the driver. 

Im going to search for the Eemprom on net, but im interested in your answers. Cause it can help more.

Thanks a lot for the tip!

Bálint Szabados

---

### Post by jackrobinson on 2007-01-30
> **mangaeva said:**
> I start this topic again cause I had to reinstall my linux.

So I have an MSI Megabook M670 laptop with AMD Sempron 1.8 Ghz processor, 1GB RAM, Nvidia Geforce Go 6100 and wide screen. I was really happy that i could start to use Linux. Im really new for everything and first i thought that the problem is in me when i tried to install the nvidia driver. but after i found automatix i realized that its not cause me that i get a black screen when i could sign in. I hear the drums and such just cant see anything. I tried out things i found on the net but non of them seemed to work.

I attached the right xorg.conf this time. 

Every idea is Welcome, i really dont know why i cant fix it, tho cause im really new to this all, im not really knowing what im doing, but im really sad about it that i couldnt make it alone.

Hope one of you guys can help me. I fee like a noob, but im reading about linux in the past 2 days. So i hope that i will get better.

Thanks for every help. Hope that finnaly i will be able to use the nvidia and the wide screen resolution.
well it sounds like a refresh rate/resolution issue (most probably refresh rate). This is what I suggest you do. For starters open up your xorg.conf and change the word "nvidia" to "nv"  under the Devices section.
you could open the file thusly:
```
sudo nano /etc/X11/xorg.conf
```
and make the changes. Hit ctrl-X and Y to save and exit. Then restart your computer and you should get your display back.
when you do get it back, do the following:
From inside Ubuntu, hit Ctrl-Alt-F1 to go to console and the do the following:
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
```
This will reconfigure your refresh rates/resolution and then when you are done, restart your computer and when you log back in, replace "nv" with "nvidia" again in xorg.conf

---

### Post by alfo_uy on 2007-02-03
> **mangaeva said:**
> Hi there. I did search for methodes to correct this problam, just non of them worked... 

Hope my questions wont bother you:

What is an Eeprom module, and how can i unload it?
And i dont know what you mean by this "generally you should have seen it in the setup of lm sensors, am i right?" I use Automatix 2 to install the driver. 

Im going to search for the Eemprom on net, but im interested in your answers. Cause it can help more.

Thanks a lot for the tip!

Bálint Szabados

the eeprom module, i don't exactly know what it does. BUT i do know that causes the black screen problem with nvidia drv for linux, (at least in some friends and my pc and others millions, because i googled it.)

you can go to with a text editor and a beloved sudo command before it to /etc/modules

there the modules you load to your kernel at startup should be. in the case eeprom module figures in that list, erase it, but knowing that with the unload some apps would not work properly. if you installed an app to monitor your pc sensors, usually the eeprom module is loaded but not always needed.

at any case, just coment the line, its like this # in the first char of the line, meaning that the line will be ignored. (probably the best solution)

reboot and you should technically be able to "see" the difference.

if not, you can uncomment that line (remove #) and you are back at point zero. and black screen.

remember that you should have the nv  driver blocked to avoid problems with the nvidia drv.


--
on boot after you hear the sounds of the loggin press ctrl+alt+F2 and you should open a console, loggin.

do something like sudo nano /etc/modules

if you do not have the nano console text editor, do before that an sudo apt-get install nano

and then the modules list should reveal itself showing the loaded modules.

after that, do the # thingy

save with ctrl+o    (nano)
exit with ctrl+x      (nano)

and just for the fun off it write sudo shutdown -r now

you should by now "see" the difference. i hope so. good luck!!

---

