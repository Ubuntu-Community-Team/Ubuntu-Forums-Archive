---
title: "Upgrading ram"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by Ranko95 on 2009-04-21
Hey um i need more ram and im a noob at linux stuff so this may sound stupid. I want to use virtualbox and i figure that requires alot more ram, (I also want more for compiz stuff). anyways, there is this thing on vista and win 7 called ready boost. I enables you to use a flash drive for ram memory. I have never tried this before. I dual boot win7 and ubuntu intrepid. If i use ready boost on win 7 and then delete the windows partition will this effect still apply? also what drawbacks are there to ready boost. Oh and could i use ready boost from the virtual box if that will work better?

Thanks for your time and patience.

---

### Post by lisati on 2009-04-21
I think "ready boost" is a Windows (Vista) thing. I'm not aware of an Ubuntu-friendly equivalent, but other forum users might be able to enlighten us.

---

### Post by Ranko95 on 2009-04-21
no, im saying if i use in vista then will it effect ubuntu? (it should right?) and im asking if i can delete the win 7 partitition afterward and keep the ready boost effect.

---

### Post by lisati on 2009-04-21
> **Ranko95 said:**
> no, im saying if i use in vista then will it effect ubuntu? (it should right?) and im asking if i can delete the win 7 partitition afterward and keep the ready boost effect.
Ubuntu usually makes its own arrangements for managing memory and any gadgets you have plugged in. There are probably one or two exceptions which are hardware based, but changing the settings on one operating system usually doesn't directly affect the settings on another.

---

### Post by saidinesh5 on 2009-04-21
incase you directly want your answers, directly jump to the next paragraph, skipping this one :
from what i guess, ready boost simply uses the flash drive for the virtual memory thing. (basically your ram isnt big enough to hold all the programs you are running, so the operating system only loads the CURRENTLY USED files onto the ram and it stores the remaining files that are in use on the hard disk in  this place). In windows it is done using a file called pagefile , n is generally put in your c: drive. since USB drives are considerably faster than hard drives, the readyboost would try to store a part of this file on the pen drive hoping for a better performance. :) in linux this is why you dedicate a swap partition.

NOW coming to your questions :
obviously when you wipe out windows , infact ,even when you shut it down, your pen drive will be as good as a normal pen drive. it wont magically act as your ram.

n as far as drawbacks , i dunno wht to expect out here
n didnt understand your virtual box question.

---

### Post by Ranko95 on 2009-04-21
so then what if i deleted win 7 and loaded it up on virtual box? If i used ready boost would it be like having extra ram? Also is there a linux based program similar to this?

---

### Post by lisati on 2009-04-21
The best way of increasing your RAM is to actually open up your machine and install extra RAM.

---

### Post by saidinesh5 on 2009-04-21
well if you meant that if you install windows 7 on a virtual box in ubuntu , and then ask it to use readyboost, then basically it MIGHT(i am not sure about it) help improving ONLY the performance of your windows 7 in your virtual box. in NO WAY will it help change your ubuntu's performance.

if you want to know why: when setting up virtual box, you actually say that use this much of ram to run virtual box . and thats it: so much amount of ram in ubuntu is eaten by virtual box. now you are saying to the windows in the virtual box to store whatever excess data in the ram that you ve allocated to virtual box in your usb drive,instead of your hard drive. so obviously it makes no difference to ubuntu, cuz you have already told it to give so much of ram to virtual box.

I dont know of any software like ready boost for linux. but may be you could ask it to use your pendrive as the swap partition. Even i am googling for it. so if i find out about it, i'll tell you :)

and even i agree with lisati. thats the cheapest and easiest way to get a huge performance difference (Y)

---

### Post by upchucky on 2009-04-21
if you really want to free up ram without buying more ram, get rid of windows it hogs around 1.2 gigs, just imagine what you can do with that much free ram.

---

### Post by saidinesh5 on 2009-04-21
> **upchucky said:**
> if you really want to free up ram without buying more ram, get rid of windows it hogs around 1.2 gigs, just imagine what you can do with that much free ram.


correction: dude, windows eats ram only when its running : in no way will an installed copy of windows affect a person running ubuntu . its just lying on your hard disk, at the most slowing down the file access times. i felt it was a necessary correction to make, cuz some of my friends had this misconception that installing ubuntu makes their windows run slower!!!

---

### Post by upchucky on 2009-04-21
> **saidinesh5 said:**
> correction: dude, windows eats ram only when its running : in no way will an installed copy of windows affect a person running ubuntu . its just lying on your hard disk, at the most slowing down the file access times. i felt it was a necessary correction to make, cuz some of my friends had this misconception that installing ubuntu makes their windows run slower!!!

Umm.. did he not say he was running windows in virtual box? are they not both running at the same time?

---

### Post by saidinesh5 on 2009-04-27
Oh am sry.. i thought you meant the otherway : its a loooooong story out here... n many times people ask me the same thing: wont my windows slow down when i install linux ... 
:)

---

