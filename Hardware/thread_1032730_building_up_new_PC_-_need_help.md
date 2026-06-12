---
title: "building up new PC - need help"
date: 2009-01-06
forum: Hardware
---

### Post by dmurat on 2009-01-06
hi there =) 
I have used Ubuntu 8.04 4-5 months ago for the first time and had a good experience but unfortunately had to remove it due to dependencies on windows vista (about my university).

I had it installed on my laptop, Toshiba Satellite L-40, which was actually designed for Windows Vista. Though I had not much problems neither installing Ubuntu nor using it.

Anyway, now I am trying to build up a new Desktop PC and willing to use Ubuntu again! I will have both Windows Vista and Ubuntu. Windows for only video games, and Ubuntu for everything else (programming/coding, surfing, research, chat etc etc...)
The system I am planning to build is as follows:

Sapphire Radeon HD 4850 512MB DDR2 - video card
Kingston Dual 2GB DDR2-1066 HyperX - ram 
AMD Phenom X4Quad 9850 2.50Ghz - cpu   
Gigabyte MA770-DS3 AM2+ AMD  - main board
and
Cooler Master RC-690-KKP2-GP 460W

Plus a 22inch LCD monitor (probably LG or Phillips or BENQ)
and a hdd (probably Maxtor or Seagate)

Can you please comment generally on the system's performance and its compatibility with Ubuntu? 
Is it possible that I can experience problems regarding hardware? If so, what part of the hardware pieces should I change to make it fully-compatible with Ubuntu?
Should I choose Intel instead of AMD. Would it be better for both gaming and other performances and compatibility with Ubuntu? (Otherwise, why pay 150-250 dollars more?)

Moreover, should I install a 32-bit or a 64-bit version? (I don't know the difference much though)

I appreciate all comments, suggestions and advices. Thanks!

---

### Post by Rohan Kapoor on 2009-01-06
> **dmurat said:**
> hi there =) 
I have used Ubuntu 8.04 4-5 months ago for the first time and had a good experience but unfortunately had to remove it due to dependencies on windows vista (about my university).

I had it installed on my laptop, Toshiba Satellite L-40, which was actually designed for Windows Vista. Though I had not much problems neither installing Ubuntu nor using it.

Anyway, now I am trying to build up a new Desktop PC and willing to use Ubuntu again! I will have both Windows Vista and Ubuntu. Windows for only video games, and Ubuntu for everything else (programming/coding, surfing, research, chat etc etc...)
The system I am planning to build is as follows:

Sapphire Radeon HD 4850 512MB DDR2 - video card
Kingston Dual 2GB DDR2-1066 HyperX - ram 
AMD Phenom X4Quad 9850 2.50Ghz - cpu   
Gigabyte MA770-DS3 AM2+ AMD  - main board
and
Cooler Master RC-690-KKP2-GP 460W

Plus a 22inch LCD monitor (probably LG or Phillips or BENQ)
and a hdd (probably Maxtor or Seagate)

Can you please comment generally on the system's performance and its compatibility with Ubuntu? 
Is it possible that I can experience problems regarding hardware? If so, what part of the hardware pieces should I change to make it fully-compatible with Ubuntu?
Should I choose Intel instead of AMD. Would it be better for both gaming and other performances and compatibility with Ubuntu? (Otherwise, why pay 150-250 dollars more?)

Moreover, should I install a 32-bit or a 64-bit version? (I don't know the difference much though)

I appreciate all comments, suggestions and advices. Thanks!
Overall the system looks good! You may want to exchange the video card with one made by Nvidia for better compatibilty.

---

### Post by teaker1s on 2009-01-06
if your not worried about skype a couple of other 32bit proprietary applications,64 bit will give much better utilisation of hardware. 
Secondly if you will be using possibly over 3gb of ram at any stage use 64bit.
Lastly amd/ati support has come on leaps and bounds, my opinion is nvidia suffers less bugs and more support-others will choose to disagree on my last statement I'm sure.

---

### Post by dmurat on 2009-01-06
can you suggest me a nvidia equivalent of Sapphire Radeon HD 4850 512MB DDR2 that will be ok with the system I wrote above?

---

### Post by jolx on 2009-01-06
> **dmurat said:**
> can you suggest me a nvidia equivalent of Sapphire Radeon HD 4850 512MB DDR2 that will be ok with the system I wrote above?

Perhaps a 9800GT?

---

### Post by dmurat on 2009-01-06
9800GT sounds cool =) 
is there any problems with the cpu being AMD or the mainboard? or any other suggestions?

---

### Post by Rohan Kapoor on 2009-01-06
> **dmurat said:**
> 9800GT sounds cool =) 
is there any problems with the cpu being AMD or the mainboard? or any other suggestions?
Nope no problems with anything else!

---

### Post by dmurat on 2009-01-06
alright then thank you all! =) 

i ve got one more question then. if all these well known hardwares i wrote above has no problems with linux, why does everybody keep whining about compatibility issues? is it the webcams, printers etc. more than things like video card, cpu, main board, ram etc.? or what is it?

---

### Post by Rohan Kapoor on 2009-01-06
> **dmurat said:**
> alright then thank you all! =) 

i ve got one more question then. if all these well known hardwares i wrote above has no problems with linux, why does everybody keep whining about compatibility issues? is it the webcams, printers etc. more than things like video card, cpu, main board, ram etc.? or what is it?
Mostly the webcams, printers, etc cause problems! Additionally some people have reported problems with the GPU and certain motherboards. Also the Asus laptops have certain problems with their RAM configurations!

Edit: As far as I can tell you should have some smooth sailing!

---

### Post by teaker1s on 2009-01-06
via creative and other companies are not linux friendly.
 Also people look at a model of wireless for example and don't realize that a revision in model could be totally different hardware.

Some times a branded product from a small company may use known hardware. two top commands for you
```
lspci -v
``` will query   pci hardware

```
lsusb
``` usb hardware which product id and description will help with driver issues eg.
[COLOR="Red"]ID 046d:08af Logitech, Inc. QuickCam Easy/Cool[/COLOR]

check a product with forum search or use ubuntu or linux followed by product name in google search

---

### Post by theozzlives on 2009-01-06
> **dmurat said:**
> alright then thank you all! =) 

i ve got one more question then. if all these well known hardwares i wrote above has no problems with linux, why does everybody keep whining about compatibility issues? is it the webcams, printers etc. more than things like video card, cpu, main board, ram etc.? or what is it?

I have found a lot of nvidea, and Creative Labs probs

---

