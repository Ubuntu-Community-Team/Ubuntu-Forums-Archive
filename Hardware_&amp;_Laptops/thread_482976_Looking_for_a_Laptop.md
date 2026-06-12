---
title: "Looking for a Laptop"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by /dev/clast on 2007-06-24
Hi everybody,
as i'm gonna be moving out of the house soon i'm in need of a Laptop.

of course i wanna run Ubuntu on it...preferably everything should work out of the box.
Acutally i'm looking for some advice here, from people who are using Ubuntu on laptops.

I'm looking for a device with specs something like this:

[LIST]
[*]around 1200€ (1 600 US$)
[*]intel core 2 duo processor
[*]at least 1GB ram
[*]preferably an nvidia graphics chip (performance and drivers!), but i guess intel would be okay too, NO ATI
[*]screen smaller than 17"
[*]w-lan (i guess intel chips are the way to go here)
[*]as much disk space as possible
[/LIST]

besides that...i have no idea what's cool and hip for laptops these days, but i'm open for suggestions :)

thanks in advance :)

clast

---

### Post by bigken on 2007-06-24
dell inspirons

---

### Post by /dev/clast on 2007-06-24
i'll take a look at those, thanks.

what about this: 	

Acer Aspire 5920G-302G16N (LX.AGW0X.120)

---

### Post by Ziox on 2007-06-24
try HP Pavillion dv6000 series.  No problem with mine yet (been using since January with 3 different versions of Ubuntu)

Sound, wireless, media buttons, and screen resolutions work out-of-box.  when I bought it, it costed about $1500, but I'm sure it is much cheaper now.

---

### Post by EnolaGay on 2007-06-24
Gigabyte W251U works fine except the Webcam, is cheap and has no Windows tax :)

---

### Post by bigken on 2007-06-24
acer are a nice cheap laptop but I have had no experience with linux on acer systems where as inspirons every thing just works

---

### Post by juanvicfer on 2007-06-24
Have you compared prices for ACER Laptops? I think they are pretty cheap for their performance.
I hope you can get the laptop you are looking for, for less than 1000 €. Asus is selling good price/performance laptops as well.

Good Luck!

---

### Post by joe.turion64x2 on 2007-06-24
My Acer Aspire laptop (5102WLMi) although not similar to what you are requesting runs Ubuntu 7.04 quite well.
AMD Turion 64 X2 TL50
1GB DDR2
120GB HD
128/256MB ATI Radeon Xpress 1100
Atheros wireless (in fact this is better than Intel's).
Price: $980 (tax included).

Everything works (except the webcam but it does not have drivers yet) and it is really easy to get the drivers (Restricted Drivers Manager). Although it is somewhat tricky to set up Beryl (with XGL, the only available method), once set up it performs amazingly well. In fact I am still astonished of how well Beryl works.

Of course I am not trying to change your mind about the specs your machine should have, the only suggestion I can make you is to get an Atheros wireless chip on it.

Joe.

---

### Post by steveneddy on 2007-06-24
Go to system76 and take a look at their laptops.

Also, Dell has some good laptops, especially the one with Ubuntu preinstalled.

---

### Post by /dev/clast on 2007-06-24
thing is, we can't get those dells with ubuntu preinstalled in Germany.

the acer i was looking at, is around 1100&#8364; here.

thanks for all the other responses

---

### Post by EnolaGay on 2007-06-27
The Gigabyte W251U is much more cheaper. If you come from Germany you can check prices here [http://geizhals.at/deutschland/?fs=Gigabyte+W251U&x=0&y=0&in=](http://geizhals.at/deutschland/?fs=Gigabyte+W251U&x=0&y=0&in=) .
As I mentioned above the only thing that I don't got to work is the Webcam. If you don't need it it is  a great price imho.
If you want a test report [http://www.minitechnet.de/gigabyte_w251u_1.html](http://www.minitechnet.de/gigabyte_w251u_1.html) .

---

### Post by roncrump on 2007-06-27
I have a Dell XPS M1210: small, sexy and works well.

I believe there are some hibernate/sleep issues (I tend to shut it down completely) - but I think they are related to the nvidia card/driver so may be apply across machines and I think someone had trouble with a microphone - but again that is a feature I haven't tried to use, and may apply to other similarly equipped boxes.

I love it. Set up to dual boot with Vista (in case I need to do soem Windows work, but I hate it so rarelyboot that), managed to keep the Dell MediaDirect stuff working too.

Ron.

---

### Post by /dev/clast on 2007-07-07
alright guys, so i got myself the afore mentioned Acer Aspire 5920G-302G16N. it's a really nice laptop as fas as i can tell ;)
neither the feisty nor gutsy live cds are able to boot...they stop with some initframfs error. that's okay though, because i was able to install gutsy tribe 2 with the alternate cd.
thanks to the new nv driver the xserver came up right away and i was able to install the latest nvidia driver sucessfully :) on the bad side of things...it didn't recognize the wireless adapter at all, sound didn't work and it feels like I/O operations are painfully slow. starting a program takes way to long...i think it took gnome-terminal more than 10 seconds to load.

any suggestions? the next thing i wanna do is try installing feisty with the alternate cd, because it's a stable release...however i'm not sure if i'm gonna have any luck with that.

---

### Post by strabes on 2007-07-07
Why did you go with a laptop that has iffy hardware support? Why didn't you just go with a big OEM whose hardware is 100% supported like dell with nvidia? Broadcom wireless support is crap in linux but Intel PRO/Wireless is perfect.

---

### Post by joe.turion64x2 on 2007-07-07
> **strabes said:**
> Why did you go with a laptop that has iffy hardware support? Why didn't you just go with a big OEM whose hardware is 100% supported like dell with nvidia? Broadcom wireless support is crap in linux but Intel PRO/Wireless is perfect.
What you say is not necessarily true. Small manufactures uses standard parts too, or saying it another why, the fact that the machine comes from a 'big' OEM does not instantly mean everything will be supported (the day they start selling "Designed for Linux" machines will be different).

My laptop is an Acer Aspire 5102WLMi and works quite well, the Atheros wifi card works out of the box with Feisty (other Linux's needs madwifi to be installed but it is very easy), the Realtek sound card works like a charm (once ALSA is properly configured) and the machine is very fast and responsive (in fact it was the best performance/price ratio). The only problems I have are with 'eye candy' devices such as the webcam (its manufacturer has not released specs, nor drivers) and the integrated card reader (same case, but easily solved with an external USB one). The other 'problem' is Beryl not working very well (Ok, it is not easy to configure) because of the ATI card (but many other OEM sell machines with that ATI card too).

A cousin bought an Acer Aspire 3690, a budget machine and almost EVERYTHING worked out of the box with Linux (even the BROADCOM wireless card). Since it does not have webcam that is no longer a problem to configure, and since it has the same card reader that does not work either. The fact it has Intel graphics meant Beryl worked out of the box as well.

Joe.

EDIT: By the way, the machine /dev/clast got has Intel Wireless.
[http://www.backoffice.be/shop/information.asp?partid=LX.AGS0X.071](http://www.backoffice.be/shop/information.asp?partid=LX.AGS0X.071)

---

### Post by /dev/clast on 2007-07-08
okay, so I installed feisty, it worked very well once i set up the latest nvidia driver again :) it's faster than gutsy (those weird I/O delays are gone). most of those special keys worked out of the box. right now i'm in the process of getting the wireless chip to work...yes it is an intel chip and there are drivers...well we'll see.
it's not all that bad so far :)

---

### Post by grace.misery on 2007-07-14
I have the same laptop, just started downloading the feisty alternate cd. 
Could you please update, did you get the wireless card to work and how?

I'm pretty new in Ubuntu, so any help is much appreciated!!!

---

### Post by Stijn1985 on 2007-08-11
Hi, I also bought this laptop a few days ago and I'm looking around how I can install ubuntu on this laptop.
I've heard rumors that vista won't work when installing ubuntu, a problem with the GRUB bootloader because vista is preinstalled...

I'm new to ubuntu and I would like to keep vista working on my laptop next to ubuntu...

Now my question is: 
1. does vista still works after your installation of ubuntu 7? And did you have any problems with the GRUB bootloader?

I already made my partitions using paragon partition manager:
I made D:\ logical and created
1GB swap2
24 GB ext3
42 GB Fat32 (for sharing my files with vista)

2. will this partition configuration work?

Stijn.

---

### Post by joe.turion64x2 on 2007-08-12
> **Stijn1985 said:**
> Hi, I also bought this laptop a few days ago and I'm looking around how I can install ubuntu on this laptop.
I've heard rumors that vista won't work when installing ubuntu, a problem with the GRUB bootloader because vista is preinstalled...

I'm new to ubuntu and I would like to keep vista working on my laptop next to ubuntu...

Now my question is: 
1. does vista still works after your installation of ubuntu 7? And did you have any problems with the GRUB bootloader?

I already made my partitions using paragon partition manager:
I made D:\ logical and created
1GB swap2
24 GB ext3
42 GB Fat32 (for sharing my files with vista)

2. will this partition configuration work?

Stijn.
I installed Ubuntu 7.04 in a Vista laptop recently. It is an Acer Aspire 5050 with relatively mainstream components (they have been around for a while; for instance the chipset is the same used in my 1 year old laptop). The version of Vista installed was Home Basic.

The way Acer bundles its systems made things easier for me because the machine had 3 partitions (system, data, and recovery) so I just had to delete one of them to make room for Ubuntu (it is strongly recommended to let Vista resize itself (it is called Shrink filesystem) instead of using any 3rd party partition tool).

After Ubuntu's installation Windows Vista continued working as usual (it was automatically added to the grub menu).

The partitions you created should be quite enough.

Joe.

---

### Post by OldTimeTech on 2007-08-12
Have an Acer 9300-5005, Nvidia, 2 GB, 120GB HD, Dual Write DVD, installed Fiesty after using the shrink filesystem and everything automatically worked without a problem..

---

### Post by Stijn1985 on 2007-08-14
Hi, I have installed ubuntu 7 onto my laptop ( Acer 5920G ), installation was smooth using the alternate install CD, Only the video card wasn't supported. The laptop gave an error and started linux terminal. But this problem is already known I'm sure and probably can be solved by downloading and installing the latest nvidea driver for this card. 

The GRUB bootloader works fine for me, Windows vista keeps working after I let it change the bootloader on the c:\ drive.

Thanx for the info!

Stijn

---

