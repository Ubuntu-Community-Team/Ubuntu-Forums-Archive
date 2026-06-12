---
title: "Medion MD97600 Intel 2200BG Wireless"
date: 2010-05-17
forum: Hardware
---

### Post by skozzy on 2010-05-17
I recently put in a new HDD in my laptop and put a fresh Ubuntu on it.

Long time ago, maybe 3 years I went through days of posts and trials to get my Wireless Enable Button working. Now I can't find any posts explaining it.

Anyhow, it's a Medion MD97600 Laptop with an Intel IPW2200BG wireless card, by default it is disabled and requires pressing the wireless button when using say Windows XP or Vista to turn on the LED on the laptop and also to enable the wireless card.

What I used to have on the old setup was a small script that enabled that button, I do remember making the script with some commands I got from peoples posts. Silly me didn't think about keeping that in a safe place.

What else I remember is I used some Acer Softkey program or code. Being 3 years at least and I don't have a clue what I did back then.

Can someone help me out.

---

### Post by noobquest on 2010-05-22
same problem... same exact laptop.. HELP:(

this is the post i found..but im a ultra noob and i have no idea what they talking about.. i dont even know where to start.

[http://ubuntuforums.org/showthread.php?t=517228&page=7](http://ubuntuforums.org/showthread.php?t=517228&page=7)



if you figure out what u did please let me know.

---

### Post by skozzy on 2010-05-23
I am using Ubuntu 9.04 (just in case it makes a difference)

I read a lot and tried a lot and this was the simplest solution.

1. From the Desktop click on Places
2. Click on Home Folder
3. Right Click inside Home Folder and Create Document - Empty File
4. Open the Empty File it called New File
5. Type the following inside it
sudo modprobe acerhk force_series=95400 autowlan0
sudo modprobe acerhk force_series=95400 usedritek=1 verbose=1
echo 1 > /proc/driver/acerhk/wirelessled

6. Save it as WIFI (or whatever you like)
7. Open Application then Accessories then Terminal
(you should be inside the home/yourname folder at this point, if not use the CD command to get there and type ls to list the files and you should see your wifi script there)
8. Now you make the file executable with
chmod +x wifi (or whatever name you used)

At this point you can double click the script to turn on the WIFI LED and the wireless will start several seconds later. You can also choose if you like to add a icon across the top of the menu bar to click on that runs the script or add it to the startup of Ubuntu if you like it on all the time. I don't have the time left to explain it yet, if you want to know that then let me know. The button you press in XP/Vista/Win7 isn't going to work with what I told you, there is a way to do it, but I long forgot it.

---

### Post by noobquest on 2010-05-23
/proc/driver/acerhk/wirelessled dose not exists. even though i installed acerhk threw software center. i cant find that directory.

---

### Post by skozzy on 2010-05-23
Im not going to be the best to debug stuff since I barely know what Im doing my self, but I mentioned about me using 9.04 cause I read somewhere that later some builtin stuff in the os was removed. Wish I could help you further.

---

### Post by skozzy on 2010-07-17
Well, im back again, upgrade from 9.04 to 9.10 and now it is broken again, wifi no longer works

now /proc/driver/acerhk/wirelessled doesn't exist. 

So painfull having a wireless card that has the radio disabled by default and no support for a wireless key that is fairly common on computers with the ipw2200BG card

---

### Post by noobquest on 2010-08-11
yeah i gave up with this.. for now im back to windows on this pc.. gonna stick to what works.

but i found this link if you can make sense of it let me know.. 

[http://forum.ubuntuusers.de/topic/wlan-hotkey-medion-md97600/](http://forum.ubuntuusers.de/topic/wlan-hotkey-medion-md97600/)

---

