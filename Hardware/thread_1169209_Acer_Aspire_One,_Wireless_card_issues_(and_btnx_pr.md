---
title: "Acer Aspire One, Wireless card issues (and btnx problems)"
date: 2009-05-24
forum: Hardware
---

### Post by Snow Keld on 2009-05-24
alright [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16834115552) is the exact thing that i got.

i'm running ubuntu 9.04 (i didnt like the netbook remix's desktop and the regular ubuntu version works exactly the same as far as hardware goes, the wireless card had the same issues with UNR

the wireless card doesnt want to work very well, it starts and stops working for no reason.

this is what it says for specs, WLAN = 802.11b/g Wireless LAN
i opened it up and there is a sticker on it that says atheros...

i've tried using the atheros driver, but then it doesnt work at all.

anyone have any ideas? or a defective card? if its a defected card i hope they dont care that windows is gone (deleted it the day i got this :P )


the other thing is btnx program to be able to edit what my mouse buttons do, i got a logitec wireless 6 button notebook mouse, it comes up with an error, i took a screenshot of it which is bellow.

thank you in advance for anyone who can help, the btnx is a minor issue, but my wireless card NEEDS to work better.

---

### Post by Snow Keld on 2009-05-25
if anyone has any thoughts on my wireless card issues or some kind of troubleshooting command so you can get a better idea of whats going on i would be very happy.

i'm using this acer cuz its an upgrade from my desktop, but all i have is wireless here and i have to turn my desktop on and connect to wireless on it then rout from my desktop to this acer to use it :(




but more about the problem.

i've connected to a couple modems with no problems at all, but many have had issues (esp the one at my house and my friend robs house :( ).

simply it connects but then doesnt want to load, at all, and has trouble connecting, i can sit right next to my wireless at home and it will STILL do this, because originally i thought it may have been an issue of a bad signal cuz i am far away.


also, if there is another card i could buy (preferably wireless N) that will both fit inside this comp and work very well with ubuntu, i will would probably buy it, i've had trouble finding one thats as small as this one + i really dont know much about wireless so i'm kind of searching in the dark.



again, help is VERY much appreciated :D

---

### Post by Funnel Weaver on 2009-05-25
I posted this in my thread as well, but I wanted to make sure that you saw it. Hope it helps.

[http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html](http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html)

---

### Post by Steelmourne on 2009-05-25
I have the same laptop and the wireless is an Atheros 5700EG. The key is to get ndis wrapper and the .inf file that allows ndiswrapper to set up your card.

---

### Post by Snow Keld on 2009-05-26
> **Steelmourne said:**
> I have the same laptop and the wireless is an Atheros 5700EG. The key is to get ndis wrapper and the .inf file that allows ndiswrapper to set up your card.

i dont entirely understand :(

could you explain for me please?


also, thx tunnel weaver, wifi indicator works perfectly now.

---

### Post by Snow Keld on 2009-05-27
ok, how i see this by reading other peoples issues with the same thing, i need to use the windows driver for it.

but i cannot find it ANYWHERE and anyone who has a download link it is now not there (been deleted)

i dont know where to go from here, but maybe an expert in this kind of thing is needed.



as soon as i find a way i will be posting clear cut directions for those who have this same problem after me.

---

### Post by Snow Keld on 2009-05-28
i just had to re-install for prolly the 6th time.

anyone who has fixed their wireless on an acer aspire one d150, i would really love to know exactly how you did it :D

---

### Post by Snow Keld on 2009-05-29
i'm considering buying a replacement card.

Intel Wireless WiFi Link 4965AGN - Network adapter - PCI Express Mini Card - 802.11b, 802.11a, 802.11g, 802.11n

i did some research and everything i found said it works fine with the aspire one.

i also was looking up for compatibility with ubuntu, i found some people saying it doesnt work, but its all 5 + months old, anyone know for sure?


>what i found says it works fine with windows drivers, but wireless N would not work.

so if anyone knows thats would be cool, if it works good, or if there is a fix to make it work good (something i can follow and be able to do.. i can do anything i'm given good/clear directions for)

even if this one worked fine i was considering getting a wireless N card anyway (as long as it was compatible) and its only $30 off amazon buying it new.



btw, i am very grateful for those who have helped me so far :D


EDIT:

i just ordered that wireless card, hopefully i have a better time with that one.

---

### Post by Snow Keld on 2009-05-31
ok, for whatever reason its working better now, too bad i already ordered the other card :(

oh well, the other one is better.



[just for clarification, this is running ubuntu 9.04 (netbook remix should work the same in with this) and this is the acer aspire one d150 which comes with the Atheros 5700EG wireless card (b/g)]

i'm not entirely sure how or why this card is working better, but the only things that i imagine could have effected it are...


```
sudo apt-get install linux-backports-modules-jaunty
```
(this was to fix wireless LED indicator, but it also seemed to help me see wireless networks, meaning it was receiving packets better, but still not sending them well, your comp will need a restart for it to be effective)

next, i grabbed one of my favorite little programs, and the only one i ever took the time to learn to run in a terminal (cuz it doesnt have a GUI)

go to synaptic package manager and install "aircrack-ng" its not the program itself that would change anything, but there is another required package, i dont remember what it is though, i assume it mods the wireless setup to allow packet attacks, which is changing how your wireless card sends packets.


this seems to have fixed the wireless to a usable extent, while trying to find a fix for this wireless card i came across lots of people having issues with it while running the preloaded win xp and the preloaded drivers, apperantly there are two issues with this, it could be one of them, or both.

first, acer or etheros, whoever makes the drivers (windows drivers) never released one meant for this wireless card, which is stupid, but apparently they used a driver meant for another card for this one, which works, but not well.

and second, i found people saying that even with drivers working well and a good connection, the wireless card itself has problems, where it will work well, and not work well other times, and it seems to be more of a hardware issue.

i cant say that the reasons for this card not working well are from great sources, but i was finding different people complaining about the same problems everywhere, and these 2 explanations i found several times in different places, mainly drivers being the issue, but how can you know your driver is good if the card has hardware problems? it would seem that the driver is not working right even if it is.


i hope i have helped others who find this, if you get it to this point (gets a low signal and low transfer rates, but works consistently) you will probably find that you may want a better card anyway, i'll post back here again with info on the intel card to let people know how well that works :D

---

