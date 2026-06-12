---
title: "[SOLVED] help atheros wireless not working"
date: 2008-07-17
forum: Hardware
---

### Post by xnostradamusx on 2008-07-17
i downloaded and installed the latest ubuntu as of today it 

seems all my hardware has no problem the only problem i cant 

solve is my wireless, i already tried some guides but i think i 

dont know if its compatible on my wireless card or im the one 

just doing something wrong. my wireless card is 

atheros AR5007 802.11b/g wifi adapter

i really wanted to use this OS

im using vista at the moment but i want to migrate in ubuntu

but if i cant solve my wireless problem i have no choice but to 

stick with my windows vista. :(

thanks who will be a good samaritan here to assist me here

---

### Post by Tigin on 2008-07-18
you have not mentioned anything about your system :) is it 64 bit or 32 ? 

there are tons of solution in forums . I'd try a search with some keywords to find a HOW-TO .

It may be a good start to give some info about your system .

PS :) there is more then one "latest ubuntu" , like ubuntu studio , ultimate etc.

---

### Post by kevmitch on 2008-07-18
This might be helpful:
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

---

### Post by xnostradamusx on 2008-07-18
thanks for the reply guys

i forgot to mention im using hp compaq presario c745EE 

and im using 32 bit..

i tried several guides already here but seems i cant make it to work... 

is there something already tried and works 100%?

---

### Post by Sealbhach on 2008-07-18
How about trying this?

[http://easylinuxwifi.org/](http://easylinuxwifi.org/)

It's automated ndiswrapper, it might help or at least point out what the problem is.


.

---

### Post by xnostradamusx on 2008-07-20
thanks 

@tigin it seems i dont have any idea where to find those other ubuntu release cause i download ubuntu from the official site

thanks

kevmitch

Sealbhach

will try your suggestions

---

### Post by Reiger on 2008-07-20
Having a Atheros AR5007EG myself, the only thing which apparently works atm is a propietary driver & ndiswrapper. I'm using ndiswrapper 1.5.1 and the 32 bit XP driver.

---

### Post by xnostradamusx on 2008-07-20
while i was connected in internet in my laptop (wired)

ive seen an availble download in add/remove of ubuntu for wireless drivers

but havent tried yet

will try first the above suggestions


@Reiger actually my wireless card is detected but restricted

it shows atheros hal and atheros wireless blah blah blah

did you manage to use your wireless?

cause actually this is my 1 and last problem

---

### Post by J A Smith on 2008-07-20
Using same wireless card myself, this might help:

[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

---

### Post by xnostradamusx on 2008-07-20
@J A Smith does it matter if my 5007 version is X i think the tutorial your refering me is only for 5007EG as per what i seen in one of those post

---

### Post by J A Smith on 2008-07-20
I am not sure - but I don't think so. Read around on the links everyone has provided and if one seems about right, give it a go, but do ask if you;re not sure- better then making a mistake!

---

### Post by xnostradamusx on 2008-07-20
i manage to install a driver combining ndiswrapper an windows xp driver and the easylinuxwifi posted by Sealbhach

i have the option to edit my wireless now only problem now how can 

scan for my wireless router like what im doing with my windows

---

### Post by xnostradamusx on 2008-07-21
@J A Smith thank you thank you thank you for the guide you give in this link [http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

it solved my problem heres what i did,

i reformated my hard disk and installed a fresh kubuntu latest from their website today then i followed exactly what the guide said.

now my wireless works but my wireless button is still orange but it doesnt matter.

i dont know if it can would be the same if i was using ubuntu cause now my os is kubuntu

---

### Post by xnostradamusx on 2008-07-21
ok i tried reinstalling ubuntu and doing the same thing i done in my kubuntu

but found out it doesnt work and some errors appear,

only in my kubuntu the guide works no problem i dont have a choice then i will be in kubuntu then i hope in the future updates wireless would fix

---

### Post by xnostradamusx on 2008-07-22
ok juz want to share i finally made my wireless work in ubuntu cause i tried it again for 1 more time, i used that guide from  with this link

there is something missing in the command there its sudo make

i noticed is only make then make install so add (sudo) on that make.

finally i can enjoy my ubuntu now with my wireless SWEeeeet :guitar:

---

