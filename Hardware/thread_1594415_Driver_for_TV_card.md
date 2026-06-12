---
title: "Driver for TV card"
date: 2010-10-12
forum: Hardware
---

### Post by bsuton on 2010-10-12
Hi,

I am using Ubuntu 10.10 and i can not find drivers for this TV CARD 
items DVB-T Hybrid Digital/Analog TV, Video IN, USB 2,0 / ITV-721
Does anyone know how i can make that this card works under Ubuntu OS?

Thanks

---

### Post by bsuton on 2010-10-13
Does anyone have some idea?

---

### Post by PaulReaver on 2010-10-13
is this a itv 721 usb tv tuner?

like [[COLOR="Red"]this[/COLOR]]("http://www.tv-cards.com/model.php?modelid=236")

doesn't look good,  best hope would be try find what chipset this uses...

---

### Post by bsuton on 2010-10-13
thanks
yes it is
and how i can found out which chipset have my TV card?

---

### Post by PaulReaver on 2010-10-13
I went on [http://www.itemstech.com.tw/](http://www.itemstech.com.tw/) and couldn't find any drivers for ubuntu
even tried google to find which chipset this tuner uses but had no luck.

sorry... I tried but...I don't think you'll be able to get this working any time soon.



hopefully someone else has some useful ideas?


you could maybe do "dmesg" (without the quotes) in a terminal,  and look for any mention of dvb hardware

---

### Post by bsuton on 2010-10-13
I have tried "dmesg" and i have found those lines
[10.705825] [drm] nouveau 0000:01:00.0: Detected a TV connector
[10.707513] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 1)

---

### Post by IcarusR on 2010-10-13
Description of the hardware is a tad lacking, given the question.

In a terminal run

```
lsusb
```

Then you will be able to find the id, then you can look for info on that.
Suggest you start here ...

[http://linuxtv.org/wiki/index.php/Main_Page]("http://linuxtv.org/wiki/index.php/Main_Page")

If you had done a google search for "linux usb tv drivers" this site would have come up first !

---

### Post by bsuton on 2010-10-13
thnks for replay i have used "lsusb" and i have found this line
 Bus 001 Device 004: ID 6000:0001
that is usb where is connect my tv card but i cannot find anything with this id

---

### Post by halj32 on 2010-10-13
this is copied from one of my older posts

first have you installed "linux-firmware-nonfree" as this is needed
next you need to use a media player like Kaffeine which can detect your tv card and scan for channels
also make sure you have the codecs installed like ffmpeg, xine etc, also you may need w-scan.
look in Synaptic Package Manager

also you may have to use Kaffeine to watch tv as this is the only player that would work

good luck

---

### Post by bsuton on 2010-10-13
I have tried this but Kaffeine does not detect my TV card.
any other solution?

---

### Post by bsuton on 2010-10-13
i have installed MythTV and when i click on TV i get this message
ERROR: MythTV is using all inputs, but there are no active records.

Does someone knows how to fix this problem?

---

### Post by logoonlinepros on 2010-10-13
I think there is some problem with your cable try to check you cable and then try it.
I hope you find a better result after change the cable.

---

### Post by bsuton on 2010-10-13
it does not have any cable directly goes to usb.
And under windows xp works  without any problems.

---

### Post by IcarusR on 2010-10-13
bsuton

You'd do better posting on the MythTV forums rather than on this thread.

Check your setup & file permissions.

Is there anything relevant in the log file ?

Are you using the latest version of MythTV ?

---

### Post by bsuton on 2010-10-13
That is not problem with MythTV only, there no card detect by Kaffein and Me TV also.
I think that is problem because i do not have right drivers for Ubuntu, and i cannot find it anywhere. 
And  no one do not know where to find them.

---

### Post by IcarusR on 2010-10-13
> Bus 001 Device 004: ID 6000:0001

Never seen a usb id like that before ! Not normally so many 0s.

I think it is unlikely to be supported. May be better to get a new one that is in this list as supported...

[http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices]("http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices")

---

### Post by bsuton on 2010-10-13
Yes it seems that is only solution.
I see that on this list is not any usb TV card from Items Tech. 
do u know why?

---

### Post by IcarusR on 2010-10-13
Maybe they are 'wierd & wonderful' unknown chipset or are a rare item ? 

The id 6000:0001 is suspicious to me, maybe they don't follow any protocols ??

Just my spin on it.

---

### Post by HandeH on 2010-12-13
There is a bug report: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311659](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311659)

and another forum thread: [http://ubuntuforums.org/showthread.php?t=1401960](http://ubuntuforums.org/showthread.php?t=1401960)

Edit: and also a Brainstorm: [http://brainstorm.ubuntu.com/idea/15749/](http://brainstorm.ubuntu.com/idea/15749/)

The common denominator for different brand names is TRIDENT TM6000 (and maybe also TM5600/TM6010) Chip: [http://linuxtv.org/wiki/index.php/Trident_TM6000](http://linuxtv.org/wiki/index.php/Trident_TM6000)

---

### Post by halj32 on 2010-12-26
if your still having trouble have a look here it may help

[http://linuxtv.org/wiki/index.php/Trident_TM6000](http://linuxtv.org/wiki/index.php/Trident_TM6000)

---

