---
title: "Ipod doesn't display songs"
date: 2008-10-11
forum: Hardware
---

### Post by laplace/d on 2008-10-11
I was transfering songs using rhythmbox when it suddenly shuted down. After that i remounted the ipod and neither rhythmbox nor gtkpod recognized my music library (they did recognize the ipod though)... gtkpod displayed the following message:

----
Could not open "(null)" for reading extended info.
Extended info will not be used.
iPod Database Import Failed: 'iTunesDB '/media/SIMI/iPod_Control/iTunes/iTunesDB' corrupt: mhsd expected at 2818630.'

Newly mounted iPod at '/media/SIMI' could not be loaded into gtkpod.
----
is there anyway i can solve this whith out having to restore the device? (it's an ipod photo btw)
if in fact i have to restore it, is there anyway i can do it from ubuntu???
i can find a friend with xp or vista, but i rather learn how to do it here!!!!

needless to say, when i turn on my ipod, it doesn't display any songs eventhough they are on the hard drive.

HEEEELLPPP!!!
S.O.S.

---

### Post by laplace/d on 2008-10-11
i also tried banshee's option 'rebuild ipod's database' but it crahes after a while

---

### Post by laplace/d on 2008-10-11
now i tried banshee in debug mode (if anyone is having the same problem, that means to run banshee from the terminal by typing  banshee --debug )... i finally found why banshee cannot rebuild the library and that is because for some reason, the ipod is mounted as "read-only device".... i cannot change that... so now that's the issue...i've been looking around on some forums but i couldn't find anything that helped.

---

### Post by laplace/d on 2008-10-11
I SOLVED IT!!! 
here's what i did:
given that the problem was that i didn't have writing permission on my ipod, i checked where it was mounted...

i typed the following on terminal:

cat /etc/mtab
i looked for the line wher it said " /media/NAMEOFMYIPOD "
before that it said it's location " /dev/sdb2 

repaired the ipod's MS-DOS file system:
dosfsck /dev/sdb2 -a

i rebooted and i could read & write...
i ran banshee and rebuilt the database

works like a charm


DISCLAIMER: i'm a newbie, before trying any of these start your new thread or wait to read more responses.... for anyone who actually knows about ubuntu i'll be pleased to hear if i did something wrong here.

---

