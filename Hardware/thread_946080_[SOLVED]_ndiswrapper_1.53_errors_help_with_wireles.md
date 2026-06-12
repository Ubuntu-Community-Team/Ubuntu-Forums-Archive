---
title: "[SOLVED] ndiswrapper 1.53 errors help with wireless"
date: 2008-10-13
forum: Hardware
---

### Post by otz070 on 2008-10-13
running a v6000presario laptop
broadcomwireless 4311
ubuntu 8.04/XPPro (using xp now for web)

trying to get ndiswrapper 1.53 installed getting errors 
Trouble with getting wireless to work. any advice, is appreciated.

Thanks.:)

---

### Post by cariboo on 2008-10-13
Ndiswrapper-utils, ndiswrapper-common and ndisgtk are located on the LiveCD. They are located in /pool/main/n on the cd.

Jim

---

### Post by Bucky Ball on 2008-10-13
You would need to blacklist or remove all ndiswrapper to do this. I have the same card and use the Broadcom b43 driver which can be found under:

System->Administration->Hardware Drivers

Certainly a lot simpler than ndiswrapper which I screwed with for months until installing Hardy and this restricted driver. I had my wireless up in 5 minutes.

You can also have a look here:

[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

ndiswrapper can be problematic with these cards and is slowly being superceded (b43 and wl drivers).

---

### Post by otz070 on 2008-10-15
Tried that Still couldnt get it to work.
I'm thinking you use the live cd?

either way I get error messages about unable to connect to the internet to download something like you must be connected to the internet to download to continue.

Do I have to download the drivers using xp, copy to a sdcard, then to vista? If so where are the drivers? :confused:

Also not sure if this is relavant but I am using 64bit version.

Thanks.:)

---

### Post by Ayuthia on 2008-10-15
> **otz070 said:**
> Tried that Still couldnt get it to work.
I'm thinking you use the live cd?

either way I get error messages about unable to connect to the internet to download something like you must be connected to the internet to download to continue.

Do I have to download the drivers using xp, copy to a sdcard, then to vista? If so where are the drivers? :confused:

Also not sure if this is relavant but I am using 64bit version.

Thanks.:)

Which revision of the 4311 card do you have?  If you are not sure, can you post the results of lspci -nn from the Terminal?

NDISwrapper can be installed by using the live CD:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```
You will need to download an XP driver for your card.  You can find one using this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

However, if you have the rev 01 card, you can try the following link:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
Go to Option 2 and it will tell you where to download the firmware that you need and how to install it.

EDIT:
By the way, if you are trying to compile ndiswrapper 1.53, you will need to install build-essential.  That is also on the live CD.

---

### Post by otz070 on 2008-10-15
Don't Quote me on this as I am not at my laptop right now but I THINK that it is rev 2.0? 

I really don't care which version of ndiswrapper gets Installed just so I have a bug free working internet

Thanks.:)

---

### Post by Yellow Pasque on 2008-10-15
If you're using 64-bit, you'll need an XP-64 driver.

---

### Post by otz070 on 2008-10-19
Where do I get an Xp64bit driver for my system?


I tried hp's website (They suck they don't fully support my computer with XP, they want you to use vista:() I actually had to use drivers for a different computer just to get most of my stuff working.
This was suggested by an hp technition on the hp buisness forum.

Finally found an OS that works efficiently(Ubuntu!:)). Now I just need to get all of the hardware working. 

(Note I find it odd that when using different linux Nearly all of the hardware on my system was atomaticly detected and working, when I still can't get it working (right) with xp or vista:()

---

### Post by Bucky Ball on 2008-10-19
> **otz070 said:**
> 

I tried hp's website (They suck they don't fully support my computer with XP, they want you to use vista:() I actually had to use drivers for a different computer just to get most of my stuff working.
This was suggested by an hp technition on the hp buisness forum.

Finally found an OS that works efficiently(Ubuntu!:)). Now I just need to get all of the hardware working. 

(Note I find it odd that when using different linux Nearly all of the hardware on my system was atomaticly detected and working, when I still can't get it working (right) with xp or vista:()

Slightly off topic, but when I bought my laptop, the first thing I did was delete Vista and install XP. Appeared fine but nothing worked! After a little research, I discover that this is a *Vista machine*, and indeed, they do not even make drivers to support XP for my machine!!! The wisdom of HP, hey? So, a tiny partition for Vista and 1 program that I need to use in Windoze, the rest devoted to my beloved Ubuntu.

This kind of manipulation of consumer choice should be outlawed IMHO.

Incidentally, you will notice I have the same card and am using the Broadcom B43 Driver found in System->Admin->Hardware Drivers as I spent months trying to get the card to work with ndiswrapper in Gutsy with no success. Installed Hardy and had it up in 5 minutes with this driver.

---

### Post by otz070 on 2008-10-21
> Slightly off topic, but when I bought my laptop, the first thing I did was delete Vista and install XP. Appeared fine but nothing worked! After a little research, I discover that this is a Vista machine, and indeed, they do not even make drivers to support XP for my machine!!! The wisdom of HP, hey? So, a tiny partition for Vista and 1 program that I need to use in Windoze, the rest devoted to my beloved Ubuntu.

This kind of manipulation of consumer choice should be outlawed IMHO.

Actually you can get the xp drivers even though hp considers it "Vista machine" it just takes some time and tinkering (the hardest to get (for me was the audio driver) you just have to use drivers from older hp systems with the same or similar hardware! (_Don't use the bios and other key drivers,unless you are intentionally wanting to fry your system!:)_)
You could also ask for help in the buisness forum on hp, as many buisness owners REFUSE to switch to vista, well for obvious reasons, and require XP/XPPro. Fortunatly there is still a way to get things to work the way you need them to, even if it's not the easy route.

(Now back on topic:))
> Incidentally, you will notice I have the same card and am using the Broadcom B43 Driver found in System->Admin->Hardware Drivers as I spent months trying to get the card to work with ndiswrapper in Gutsy with no success. Installed Hardy and had it up in 5 minutes with this driver.

Do you use 32bit or 64bit? I'm using 64bit.
By Hardy I take it you mean 8.04? (I'm new to linux, but I do learn fast fortunatly!:))
I gave up on ndiswrapper and tried the other ways as suggested, but I guess I'm not being clear on the problem which is (Now)
I don't quite understand how to do this. Could anyone please explain more clearly? 

Thanks for reading/help:)

---

### Post by Bucky Ball on 2008-10-21
> **otz070 said:**
> 
Do you use 32bit or 64bit? I'm using 64bit.
By Hardy I take it you mean 8.04? (I'm new to linux, but I do learn fast fortunatly!:))
I gave up on ndiswrapper and tried the other ways as suggested, but I guess I'm not being clear on the problem which is (Now)
I don't quite understand how to do this. Could anyone please explain more clearly? 

Thanks for reading/help:)

My computer details are my signature.

Now, can you get online with an ethernet cable? If so, download updates and find:

ubuntu-restricted-extras

by searching in:

System->Administration->Synaptics Package Manager

You should now have an icon in the right hand top toolbar, alerting you to the fact you have a restricted driver available. So;

System->Administration->Hardware Drivers

There you should find the 'Broadcom B43 Driver'. Tick it to enable it and follow your nose. You will be asked to download a few things and you should be online with wireless. Check to see if the blue light comes up on your card. It may ask you to restart after this, but pull the ethernet plug, restart and see if your wireless light comes up during the boot process (after the login screen). If so, you should be good to go. Let us know how you go. :)

ps: I use Windoze for one program a couple times a week, and usually on my desktop, so thanks for the info but doesn't really bother me nowadays. \\:D/

---

### Post by otz070 on 2008-10-21
> Now, can you get online with an ethernet cable?

Ah there it is the solution (That's one thing I am good at making simple things complicated) No seriously I never even thought of that, I'll try it later when I get on my laptop (right now I'm using the family desktop).

Thanks.:)

(I don't yet consider this solved as I can't get windows to work with an ethernet cable, so I might need an alternate way, I'll check later.)

---

### Post by Bucky Ball on 2008-10-21
Plug it in, boot into Ubuntu and see what happens. Might just do the trick. If you can't get online with a cable and windoze either, maybe it is the router setup. That is all working, online light happening on the router?

---

### Post by otz070 on 2008-10-21
I am now posting using ubuntu+firefox (in other words it worked:))
Thanks Bucky Ball, I had everything right before the only reason it wasn't working was because I had no internet connection to download drivers (I kept thinking that I was supposed to use the cd) I plugged the ethernet cord in and got all my stuff to work (now I'm not stuck with minimum resolution because of lack of graphics drivers)
It's odd though that with every one of my computers I could never get windows to work with ethernet, (A technition I called from the ISP actually told me that my ethernet card on the computer was broken, Now I'm curious. I'm going to install ubuntu on that computer sooner or later and see if it works.)

Anyway Problem solved I'm happy now Thanks again!!!:biggrin:

---

### Post by Bucky Ball on 2008-10-21
Excellent news! I take it you are talking wireless also is up? You can mark your thread as solved from 'Thread Tools' in the upper right of the window here. Others might be able to get some ideas or a fix from our dialogue. See, you're learning new things about Windoze already! Give that other machine a try.

Welcome and don't forget to post a new thread if this happens ... ](*,)

:)

---

### Post by otz070 on 2008-10-22
Thanks Again:)
Also for the pointer for marking As "SOLVED"

---

