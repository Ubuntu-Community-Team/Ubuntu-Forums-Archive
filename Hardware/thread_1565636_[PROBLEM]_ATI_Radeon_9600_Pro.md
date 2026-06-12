---
title: "[PROBLEM] ATI Radeon 9600 Pro"
date: 2010-09-01
forum: Hardware
---

### Post by Carlos Leocádio on 2010-09-01
I have installed the new Ubuntu 10.04 on my desktop. But until now I haven't been capable of installing the correct ATI drivers for my ATI Radeon 9600 Pro.

I have tried many things, but never works.
When I try to run the aticonfig, the prompt tells me that "aticonfig: No supported adapters detected".

Please help me. It's very important to make this computer works properly, and as soon as possible.

Leocadio

Note: (lspci command)
[...]
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
[...]

---

### Post by realzippy on 2010-09-01
The newer ATI/fglrx driver does not support old cards on newer Xorg versions..stay with the free driver or downgrade to Ubuntu 8.10.
Or get a newer graphics card...

---

### Post by Carlos Leocádio on 2010-09-01
> **realzippy said:**
> The newer ATI/fglrx driver does not support old cards on newer Xorg versions..stay with the free driver or downgrade to Ubuntu 8.10.
Or get a newer graphics card...

What graphic cards are supported for Ubuntu 10.04? The HD series from ATI are?

---

### Post by realzippy on 2010-09-01
Mostly any nvidia card...even an old 6600 GT would do a good job.
Do not know if there are problems with HD cards,generally the fglrx driver should be installable on Lucid.

ATI users out there?

---

### Post by Tracy177 on 2010-09-01
> **Carlos Leocádio said:**
> What graphic cards are supported for Ubuntu 10.04? The HD series from ATI are?


ati hd4850 together with the latest catalyst 10.8 work perfect

---

### Post by Carlos Leocádio on 2010-09-02
Could you recommend me an AGP card compatible with ubuntu 10.04?

nVidia maybe a better choice not?

---

### Post by Tracy177 on 2010-09-02
> **Carlos Leocádio said:**
> Could you recommend me an AGP card compatible with ubuntu 10.04?

nVidia maybe a better choice not?


buy ati it work great in ubuntu 10.04 

also it is able to show you gpu load and gpu temp in conky or terminal

and your card should work in ubuntu perfect i dont know what driver do you have but i would advice u to install this one

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

after u install it reboot sometimes u need to install it two times so do it 

when u boot ubuntu and everything is ok right resolution etc u can check what driver u got by typing in terminal fglrxinfo 

if the driver is installed properly u will be able to use aticonfig


i just found something if u use lucid lynx than u have a problem :)

mean u driver from amd wont work it will work with ubuntu 9.10 but it wont work in lucid 

so one choice u got is to install open source driver and i dont know if it is working or not u can go to sysstem administration hardware drivers and check up if the driver for your card is installed if not install it/.

and i dont think open source does support aticonfig

---

### Post by Carlos Leocádio on 2010-09-02
Are you telling me that ATI Radeon 9600 Pro should work on ubuntu 10.04? 

When I install the property driver, and go to System > Administration > Hardware Drivers, nothing appears to activate.

---

### Post by Tracy177 on 2010-09-02
> **Carlos Leocádio said:**
> Are you telling me that ATI Radeon 9600 Pro should work on ubuntu 10.04? 

When I install the property driver, and go to System > Administration > Hardware Drivers, nothing appears to activate.


im saying there is two types of driver for your card one is from AMD the package is called catalyst but i checked and it isnt working in lucid it will in karmic.

other type of the driver is the open source thats the one from system administration hardware 

and if u didnt try to install catalyst before than it mean your open source driver is already installed and it should work. on my pc the open source didnt work very well im talking about 3d and also u cant check gpu temp or gpu load open source driver doesnt support aticonfig command mean u type in terminal aticonfig and u get nothing.

u could join irc channel #radeon to ask anything u want about open source driver and available commands etc.

as i said at the moment there is no driver for your card from AMD that work in lucid.

stick with open source for sometime and in few days or weeks u will see on here 
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

new driver for your card than download it install it and enjoy it :)

---

### Post by realzippy on 2010-09-02
*Tracy* messes things up and gives wrong instructions,do **not** try to install the
linked driver on 10.04 **nor** on 9.10
..the 9.3 catalyst driver will **only** work with your card *until 8.10*....
it does not support the newer Xserver version used  since 9.04...

Why not grabbing e.g. an old nvidia 7600 GT AGP  from second hand market?


@ tracy:

[I]and in few days or weeks u will see on here
[http://support.amd.com/us/gpudownloa...2&lang=English](http://support.amd.com/us/gpudownloa...2&lang=English)[/I]

Never,this is called "Waiting for Godot"  ;)

---

### Post by Carlos Leocádio on 2010-09-02
> **realzippy said:**
> *Tracy* messes things up and gives wrong instructions,do **not** try to install the
linked driver on 10.04 **nor** on 9.10
..the 9.3 catalyst driver will **only** work with your card *until 8.10*....
it does not support the newer Xorg version used  since 9.04...

Why not grabbing e.g. an old nvidia 7600 GT AGP  from second hand market?


@ tracy:

[I]and in few days or weeks u will see on here
[http://support.amd.com/us/gpudownloa...2&lang=English](http://support.amd.com/us/gpudownloa...2&lang=English)[/I]

Never,this is called "Waiting for Godot"  ;)


I'm thinking buying that card, the 7600 GT... But I don't wish to spend money on these old pc... And on my country it's difficult to find that card, or another similar AGP, even an used one...

---

### Post by mastablasta on 2010-09-02
I have ATI Radeon 9600 XT and it works ok with opensource drivers that are already installed with the instalation. why are you trying to install proprietary ones? are you having a problem in playing games or what?
 
also if you want you can get new AGP cards (well the tech on them is a bit older but stil...)

---

### Post by Tracy177 on 2010-09-02
> **realzippy said:**
> *Tracy* messes things up and gives wrong instructions,do **not** try to install the
linked driver on 10.04 **nor** on 9.10
..the 9.3 catalyst driver will **only** work with your card *until 8.10*....
it does not support the newer Xorg version used  since 9.04...

Why not grabbing e.g. an old nvidia 7600 GT AGP  from second hand market?


@ tracy:

[I]and in few days or weeks u will see on here
[http://support.amd.com/us/gpudownloa...2&lang=English](http://support.amd.com/us/gpudownloa...2&lang=English)[/I]

Never,this is called "Waiting for Godot"  ;)


i dont know what are u talking about but u probably know not much about ati cards open source and fglrx right?


fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4850
OpenGL version string: 3.3.10151 Compatibility Profile Context

aticonfig --adapter=0 --od-getclocks

Adapter 0 - ATI Mobility Radeon HD 4850
                            Core (MHz)    Memory (MHz)
           Current Clocks :    500           850
             Current Peak :    500           850
  Configurable Peak Range : [500-550]     [850-900]
                 GPU load :    0%

aticonfig --adapter=0 --od-gettemperature

Adapter 0 - ATI Mobility Radeon HD 4850
            Sensor 0: Temperature - 55.50 C

uname -a
Linux matrix 2.6.35-19-generic #25~lucid1-Ubuntu SMP Wed Aug 25 04:24:28 UTC 2010 i686 GNU/Linux


SO CAN U DO THAT WITH YOUR NVIDIA OR OPEN SOURCE FOR ATI ? NAAH 

this guy he dont need to upgrade to to nvidia or anything he has to wait few week for his propper driver from AMD and his card will work

dont advice people wrongly it isnt good to change from new card to new card !!!!

---

### Post by Tracy177 on 2010-09-02
> **mastablasta said:**
> I have ATI Radeon 9600 XT and it works ok with opensource drivers that are already installed with the instalation. why are you trying to install proprietary ones? are you having a problem in playing games or what?
 
also if you want you can get new AGP cards (well the tech on them is a bit older but stil...)


do you know why? why fglrx ? cuz when u install propper catalyst your gpu will be used from 0 to 2 with compiz and all effects and also cuz of this 

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4850
OpenGL version string: 3.3.10151 Compatibility Profile Context

aticonfig --adapter=0 --od-getclocks

Adapter 0 - ATI Mobility Radeon HD 4850
                            Core (MHz)    Memory (MHz)
           Current Clocks :    500           850
             Current Peak :    500           850
  Configurable Peak Range : [500-550]     [850-900]
                 GPU load :    0%

aticonfig --adapter=0 --od-gettemperature

Adapter 0 - ATI Mobility Radeon HD 4850
            Sensor 0: Temperature - 55.50 C

uname -a
Linux matrix 2.6.35-19-generic #25~lucid1-Ubuntu SMP Wed Aug 25 04:24:28 UTC 2010 i686 GNU/Linux


SO CAN U DO THAT WITH YOUR NVIDIA OR OPEN SOURCE FOR ATI ? NAAH 

this guy he dont need to upgrade to to nvidia or anything he has to wait  few week for his propper driver from AMD and his card will work

u cant do it with open source your not able to check if there is anythign wrong woith your card 

i tested open source too it doesnt work good in 3d and use more power



open source driver is for people who dont have choice.

for people who have choice is catalyst fglrx

---

### Post by Tracy177 on 2010-09-02
> **carlos leocádio said:**
> i'm thinking buying that card, the 7600 gt... But i don't wish to spend money on these old pc... And on my country it's difficult to find that card, or another similar agp, even an used one...


i say wait !!!!!!!!!!!! Dont waste money u got a good card !!!! 

You have got open source driver installed already in your ubuntu lucid 

aticonfig commands wont work 

wait for proper driver from amd few weeks or maybe days

---

### Post by Carlos Leocádio on 2010-09-02
> **Tracy177 said:**
> i say wait !!!!!!!!!!!! Dont waste money u got a good card !!!! 

You have got open source driver installed already in your ubuntu lucid 

aticonfig commands wont work 

wait for proper driver from amd few weeks or maybe days

ok. So please, put where some information, when that new driver came out from AMD. And a tutorial for installing correctly would be nice.

---

### Post by Carlos Leocádio on 2010-09-02
> **mastablasta said:**
> I have ATI Radeon 9600 XT and it works ok with opensource drivers that are already installed with the instalation. why are you trying to install proprietary ones? are you having a problem in playing games or what?
 
also if you want you can get new AGP cards (well the tech on them is a bit older but stil...)

The 3D and desktop effects don't work, and the games also don't. Even a simple game like Hedgewars. And i want to install steam on it.

I want this pc working 100% with ubuntu...

---

### Post by Tracy177 on 2010-09-02
> **Carlos Leocádio said:**
> The 3D and desktop effects don't work, and the games also don't. Even a simple game like Hedgewars. And i want to install steam on it.

I want this pc working 100% with ubuntu...


it wont cuz u have open source driver a bit buggy 

to get everything work properly u need propper driver with propper 3d support 

i dont say open source is total rubbish but it isnt as good as the driver AMD make.

and as i said u have to wait a bit when AMD release driver for your card then install it and everything will work 100%.

or other option if u cant wait u need to upgrade your card to for example hd4850 

or other option go back to ubuntu 9.10 there ADM driver will work with your card without problem

---

### Post by realzippy on 2010-09-02
@ tracy

Please stop posting nonsense.

"*or other option go back to ubuntu 9.10 there ADM driver will work with your card without problem*"

No,it will **NOT** work  on 9.10 and not with 9.04  it works until 8.10..

BTW,you know that fglrx = catalyst ???

And,your language makes tired.No need for SMS slang here....

---

### Post by Tracy177 on 2010-09-02
> **realzippy said:**
> @ tracy

Please stop posting nonsense.

"*or other option go back to ubuntu 9.10 there ADM driver will work with your card without problem*"

No,it will **NOT** work  on 9.10 and not with 9.04  it works until 8.10..

BTW,you know that fglrx = catalyst ???

And,your language makes tired.No need for SMS slang here....


to help you i took it from AMD 

and no i dont know what youre saying rude man !!!!

  9600    [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)
 X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4   ubuntu 9.10 = 7.4
 
ati hd4850mobile [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx) 
 X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, 7.4, or 7.5  ubuntu9.10 = 7.4 ubuntu 10.04 = 7.5


youre wrong or AMD is wrong ?

and if something make you tired why dont u stop read it instead being rude ?

---

### Post by mastablasta on 2010-09-02
> **Tracy177 said:**
> 

this guy he dont need to upgrade to to nvidia or anything he has to wait few week for his propper driver from AMD and his card will work

dont advice people wrongly it isnt good to change from new card to new card !!!!

How can i put this.... Radeon 9600 is an old card and according to ATI it moved into legacy support:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

now this driver only supports until X.org 7.4, while it doesn't support the 7.5 which Ubuntu 10.04 uses. so **ATI Catalyst&#8482; 9.3 Proprietary Linux x86 Display Driver **is the last one available and it seems it won't work with Ubuntu.

>  All future ATI Catalyst&#8482; releases made available past the ATI Catalyst&#8482;  9.3 release will not include support for the legacy products listed  above [*this inlcudes Radeon 9600 series*] or any of the features associated with those legacy products.-----------

So much for this... As for having STEAM on linux i don't think there is a linux client...
as for hedgewars i do not know how they work with opensource. so fat i treid tux racer and a few more simpler ones and they all work on mine.

EDIT: i just tried hedgewars and works well with open source drivers on my maschine which is nothing special really...

---

### Post by mastablasta on 2010-09-02
> **Tracy177 said:**
> 
open source driver is for people who dont have choice.

for people who have choice is catalyst fglrx

ofcourse proprietary should be beter. they almost always are but in this case he doesn't have a choice if he want's to use 10.04. And neither do i.

---

### Post by Tracy177 on 2010-09-02
> **mastablasta said:**
> ofcourse proprietary should be beter. they almost always are but in this case he doesn't have a choice if he want's to use 10.04. And neither do i.


i asked on AMD forum and someone told me they will try to talk to developers to make driver from other card work with 9600 so if u will wait for sometime you maybe will get driver from AMD if not you will need to use OS driver. thats all i can say.

one thing more guys they also told me to try this driver in ubuntu 10.04 

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12%E2%8C%A9=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12%E2%8C%A9=English)

it is designed for 7.4 but someone said it may may not work need some testing and i dont have 9600.

so someone please test it and replay with results.

u dont need to uninstall OS driver just download that one install it reboot then if after reboot it will boot in low resolution boot in low resolution than install this driver again and again reboot. if again will boot in low resolution. install back OS driver from hardware drivers.

but report it here so i can tell to those guys it worked or not .

tnx

---

### Post by realzippy on 2010-09-02
> **Tracy177 said:**
> to help you i took it from AMD 

and no i dont know what youre saying rude man !!!!

  9600    [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)
 X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4   ubuntu 9.10 = 7.4
 
ati hd4850mobile [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx) 
 X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, 7.4, or 7.5  ubuntu9.10 = 7.4 ubuntu 10.04 = 7.5


youre wrong or AMD is wrong ?

and if something make you tired why dont u stop read it instead being rude ?


AMD is right and I am right and you are wrong.Catalyst 9.3 needs xserver < 1.6 ;which is given in Intrepid.End of discussion.

I *have* to read your stuff since you jumped in the thread -I have subscribed- talking nonsense.That is not rude,that simply is true.
But anyway,you might be the very first person that will make it on my ignore list;congrats,after being 3 days in the forum...

---

### Post by realzippy on 2010-09-02
> **Tracy177 said:**
> i asked on AMD forum and someone told me they will try to talk to developers to make driver from other card work with 9600 so if u will wait for sometime you maybe will get driver from AMD if not you will need to use OS driver. thats all i can say.

one thing more guys they also told me to try this driver in ubuntu 10.04 

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12%E2%8C%A9=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12%E2%8C%A9=English)

it is designed for 7.4 but someone said it may may not work need some testing and i dont have 9600.

so someone please test it and replay with results.

u dont need to uninstall OS driver just download that one install it reboot then if after reboot it will boot in low resolution boot in low resolution than install this driver again and again reboot. if again will boot in low resolution. install back OS driver from hardware drivers.

but report it here so i can tell to those guys it worked or not .

tnx

No.NOT AGAIN PLEASE!!

---

### Post by Tracy177 on 2010-09-02
> **realzippy said:**
> No.NOT AGAIN PLEASE!!


did u try it already ?

---

### Post by cariboo on 2010-09-02
This thread seems to be going nowhere, due conflicting solutions. have a look [here]("https://help.ubuntu.com/community/RadeonDriver") for supported ATI/AMD video cards.

---

### Post by Carlos Leocádio on 2010-09-04
I'm going to buy a new video card.

Asus Geforce 6600 GT

This would work properly on Ubuntu 10.04??

The 3D effects and all stuff will work?

---

### Post by realzippy on 2010-09-04
I used to own one under Edgy;worked great...

wondering that such an old card (AGP) is still available.If you had an PCIE slot on your mainboard,
you could get my old Geforce GT 7950 256Mb for free;although I don't know where you live and if it is possible to send a package there...

---

### Post by Carlos Leocádio on 2010-11-05
Finally I bought an used **XFX NVidia GeForce 6800 extreme 256 ddr3 AGP.**

Could you please put where a complete guide abaout How to install this graphic card on Ubuntu 10.04.

I want to use all the potencial of this XFX video card. Is that possible?

---

### Post by mastablasta on 2010-11-05
if drivers for Ubuntu 10.04 exist they will be under hardware drivers and they only need to be enabled.

---

