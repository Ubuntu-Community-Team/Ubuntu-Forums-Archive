---
title: "asus eee pc 1000he issues"
date: 2009-06-07
forum: Hardware
---

### Post by ratdude747 on 2009-06-07
yay just got a new 1000he

swapped xp for ubuntu 9.04, installed eee-control, almost everything works

first, the fn+f3 (touchpad control) is not detected when i went to set it. any way of being able to use it?

also, my eee storage (10gb) is not detected. any reason for this?

last, what is the fn+space supposed to do? not in manual, but an icon is there (fn color, running man with energy symbol for legs) and what does it do?

other than than, runs so much faster than the demo unit running xp did

---

### Post by hibliss on 2009-06-07
I have this same machine. The function keys have improved over time with Ubuntu and the eee (they used to not work at all), but they are not perfect yet.

The trackpad on/off function key is a known bug, not sure if there is a fix yet. edit: seems like this is one of the options of eee control.

fn+spacebar toggles between preset power management modes in the preinstalled XP. It will auto overclock the CPU by 5% in super performance mode, and it also changes the screen brightness. Power saver mode is pretty much where my model lives in XP.

I have been thinking about installing Ubuntu Netbook Remix on my 1000he, is this the version you used?

---

### Post by ratdude747 on 2009-06-07
no

strait up ubuntu

like the feel of it

eee control has that as a command, but can i add the button combo?

---

### Post by Flash858 on 2009-06-07
The Array kernel will take care of most of the issues you are having. It is native to eeebuntu and a few other distros, or you can just install the kernel in UNR (what I did).

It runs great on my 1000HE, and it ran just as well on my old 701 prior to that.
I can't wait to see what will happen when that 2gb memory module I just ordered gets here... :)


[http://array.org/ubuntu/](http://array.org/ubuntu/)

---

### Post by ratdude747 on 2009-06-07
last i checked, 9.04 had all of array's features built in (or eee-control fixed it)

---

### Post by ratdude747 on 2009-06-07
i tried array just 4 kicks, big  mistake

made half of my hotkeys go dead

switched it so it boots normal kernel now

---

### Post by hibliss on 2009-06-08
I just installed eeebuntu and it seems great. No issues, everything works out of the box except for the trackpad and spacebar function keys. 

The latest version is using the Ubuntu 9.04 kernel and has been tailor made for the eee. Give it a shot if you have any issues with your current install.

---

### Post by ratdude747 on 2009-06-08
> **hibliss said:**
> I just installed eeebuntu and it seems great. No issues, everything works out of the box except for the trackpad and spacebar function keys. 

does your 10gb eee storage show up? mine says it has it (hybrid storage sticker) but no show in my vanilla 9.04 installation with eee-control

i donk like the desktop of eeebuntu- maybe ill try it... post back and ill see

---

### Post by hibliss on 2009-06-10
> **ratdude747 said:**
> 
i donk like the desktop of eeebuntu- maybe ill try it... post back and ill see

What do you not like about it? The dock? Other than the dock, it is identical to the standard install. All the dock does is give more screen real estate on such a cramped screen.

The eee storage is just a weblink, so you need the address from the Windows side (in the properties of the desktop shortcut). To be honest, I have not even thought about using it, 160gb is plenty of storage for me on this type of device, and I am not using it as my primary computer. I can test it out tonight and try to get eee storage working on the Ubuntu side. It acts like a local drive because Asus has it setup to map it automatically, I am sure the same can be done in Ubuntu with some work.

---

### Post by ratdude747 on 2009-06-10
oh iget it

i thought they were refurring to an ssd

since mine ws not partitioned, i have no xp install

the dock in vanillia ubuntu is fine on mine

i just use menus/drawers on my menu bar

i think "eee storage" is a deceptive name

btw, do the "bugged" keys (f3 fn/ space fn) work in eeebuntu?

---

### Post by hibliss on 2009-06-11
Those two function keys will not map properly no matter what I do. I went in to the config file for the Eee tray app and made some changes, uncommenting what was needed to identify the keys in question, but they were already set properly.

The spacebar function key is easily replaced by fn+f5, which dims the screen. As far as Power settings in power saving mode, screen brightness is the biggest factor. The only other major change is the small change to the clock speed on the processor, but the brightness definitely effects the battery much more.

As far as the trackpad is concerned, I cannot get mine to turn off at all, and in fact the tray app says that it is alreayd off and that it cannot be enabled. That doesn't bother me much, but I can see how it might get in your way while typing.

---

### Post by ratdude747 on 2009-06-11
i just re-mapped fn+f7 for touchpad, and fn+f9 for power

the screen dims automatically when on battery (when power consumption is key


oh andi tried easy peasy- didnt like it- kept what i had

---

### Post by hibliss on 2009-06-11
> **ratdude747 said:**
> i just re-mapped fn+f7 for touchpad, and fn+f9 for power


What if you need to turn off the screen :lolflag:

I think the fn+f9 key is valuable, being a shortcut to Process Monitor.

---

### Post by ratdude747 on 2009-06-11
> **hibliss said:**
> What if you need to turn off the screen :lolflag:

I think the fn+f9 key is valuable, being a shortcut to Process Monitor.

i have the system manger wiget on my top menubar so i click that if i need more than just cpu info

for the screen, i shut the lid:lolflag:

---

