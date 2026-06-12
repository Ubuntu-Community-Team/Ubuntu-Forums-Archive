---
title: "Suspend, Hibernate, Sound and Wireless problems in gusty"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by thegrimgod on 2007-11-28
I just bought a new asus laptop, best computer i had in ma life hardware wise :)
And after downloading gusty, erasing vista in a blink of an eye, here are all my problems:
1. I can not suspend or hibernate, I read about having something to do with ati , on the ubuntu web page, well my graphics card is nvidia 8600 GT so thats not it.It's not a compiz problem , since it doesnt work with or without. Tried different suggestions , on changing acpi-support etc, etc , well one worked, but whenever i wake up , my wireless is gone , when i try to reboot , my laptop freezes ,so i have to manually reboot , so i really don't like that.
2. Hibernate is almost the same issue , except sometimes it works , sometimes it doesn't, depends on the mood of the laptop, i read about the swap, i have 2gb ddr2 ram ,and 3gb swap , i'm sure thats enough since my ram never gets filled, i don't do fancy stuff , and further more , the swap is never used , i've launched office , totem , dictionary mozilla, like a ton of programs ,swap never gets used , note my ram is not filled yet :)
3. my sound works :) , but here is the bad news ,it always works , if i plug in my headphones , i still have sound in my speakers, i read about the hdaintel issue , more about people complaining , i have bad googling skills, all i find is people with the same issue and some odd fix , that never really fixes anything.
4. wireless, i boot up , its easy to start , to connect to access point with WEP 64/128 bit ascii , but boy when it goes down it goes down good , sometimes iwconfig will get it back on track with the corect essid and key , sometimes ifconfig doesnt even show my wlan0 interface ,im so confused , i dont see any logic.
So what i have to add to everybody's problems is this, i'm one of the many who complain , but it would be nice if a search on the ubuntuforums website would give an official post saying this is the status of the problem , it has been solved or not , this is what you can do to help: pray or actually do something (im not that experienced so i'll pray). the bugs.launchpad website is similar , all that i see people with the same problem, some odd fix , that i have no clue what does , and most of the time does not work, or partially works ,but breaks something else.
So the irony of the story , my best computer is so far my worst , feisty worked like a charm on an old amd pc, and yes i have tried to install feisty on this , doesnt work, gives me a error about tty or something , i can find it lol, its here in the forums , again people with a problem , and no solution that i can see.
Please feel free to ask for more details if u need , and help me out if you can, im just new , so you might want to talk to me in a not so technical language, thank you, have a nice day.

---

### Post by thegrimgod on 2007-11-29
Bump , currently writing from vista :( i'll get to installing gentoo tomorrow with fluxbox , just to test , see if i can get everything working, btw tested the headphones speakers , its not a hardware problem , for all those that say it is.
In any case , if i could solve the sound , wireless and suspend problems, i would be back to ubuntu in a sec, best os ive used in the last 2 years , sept it actually worked on ma old pc , just doesnt here..., ill still install it in a small partition , see if  i can figure it out ,but some real answers would be the best, surely there are smart people there that have figured this out , enlighten me too!!

---

### Post by happypup on 2008-03-15
Q 3

Ok I had the same sound issue on my computer It was an easy fix double click on the volume control > Edit > Preferences > click on Line Jack sense.

It will now shut your speakers off when you plug your head phones in.

Q4

> [QUOTE]One more issue with suspend/hibernate… the wifi network. Sometimes it works, sometimes it doesn’t. If it’s down, the only way to get it back seems to be through restarting the dbus subsystem:

sudo /etc/init.d/dbus restart.

Clipped from [http://polishlinux.org/linux/ubuntu/ubuntu-710-gutsy-gibbon-critical-review/](http://polishlinux.org/linux/ubuntu/ubuntu-710-gutsy-gibbon-critical-review/)[/QUOTE]

---

### Post by Giacecco on 2008-03-23
Hi thegrimgod,
did you get back to Ubuntu lately? I have the same problem as you with the wireless network dying after suspend.

Giacecco

---

