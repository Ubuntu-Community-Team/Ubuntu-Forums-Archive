---
title: "Recommendations regarding hardware needed for home server"
date: 2010-10-06
forum: Hardware
---

### Post by rashhashan on 2010-10-06
Hey, im wanting to build a home server. I dont want to spend a whole lot so i was wondering if you guys could give me some suggestions as to what hardware i should look into using.

 I dont need specifics just something like...1gHZ proc, 1 Gig of ram 80gig HDD....or you could go into more detail if you have a reason to such as...you should use two NiCs if you want to use your server for...ect.

Thanx guys,
Rashhashan

---

### Post by Yumi on 2010-10-06
I am interested in that too.
Michael

---

### Post by mastablasta on 2010-10-06
What will the server be used for. I would go for something with low power consumption. Some celeron or turion. how many people will connect to it?
 
if you don't plan to use monitor on it or desktop environment then definatelly some onboard graphics.
 
stuff in a bit of ram, hard disk, good PSU, maybe provide UPS... and you are good to go.
 
For me home server seemed too much money and time, so i rented it. maybe in the future i will get one of my own. i mean i pay 50 EUR/a year for 1GB and it includes plenty services. i could increase the storage if i had to but so far no need to. ahgome server would cost  probably about 250 EUR + electricity+bandwidth+maintenance (time, money...) ... just wasn't worth it.

---

### Post by Ryan-Robinson on 2010-10-06
I built my home server a few years ago, nothing fancy or expensive. I use it for a file server and a test bed for my web development with Apache, PHP and MySQL installed.

I went with a single core AMD 2.7GHz.

Entry level motherboard with onboard graphics

1GB RAM

320GB Hard drive

480W Power supply

Mid-sized case with a few cooling fans

DVD-RW

and that was it. It's running nicely on 10.4, and I also installed Windows 7 on it at one point and it was ok.

---

### Post by rashhashan on 2010-10-06
well i plan on either running ubuntu 64 bit server or freenas...i know that freenas isnt so hardware demanding..as in it can tun of 128mb i believe with <512 gb of ram and an 800mHZ proc lol.

but actually ill be running ubuntu server...and the only prerequisite i have is it must have a raid controller. Also what do you guys think about going with a Dell? just something cheap ya know...for like 50-100 bucks on ebay

---

### Post by cascade9 on 2010-10-07
> **mastablasta said:**
> What will the server be used for. I would go for something with low power consumption. Some celeron or turion. how many people will connect to it?
 
if you don't plan to use monitor on it or desktop environment then definatelly some onboard graphics.
 
stuff in a bit of ram, hard disk, good PSU, maybe provide UPS... and you are good to go.
 
For me home server seemed too much money and time, so i rented it. maybe in the future i will get one of my own. i mean i pay 50 EUR/a year for 1GB and it includes plenty services. i could increase the storage if i had to but so far no need to. ahgome server would cost probably about 250 EUR + electricity+bandwidth+maintenance (time, money...) ... just wasn't worth it.

Turion (apart from some pretty old socket 754 models) is laptop sockets only, and good luck finding a AMD laptop socket on a desktop motherobard. Its rare enough to find a laptop socket on an intel motherboard. 

Celerons arent that power efficient. The newer dual core versions are all 65watts TDP (73watts for the 'clarkdale'),a nd the single ores arent much better than a Semprons for TDP (35watts for the celeron, 45watts for the sempron), and the sempron is a lot faster, and possibly could be underclocked/undervoltaged to less TDP and power consumption than the celeron. 

I'd go for a Athlon II 160u (single core, 20watts TDP), X2 250u (dual core, 25watts TDP), X2 250e (dual core, 45watts TDP) or X4 615e (qaud core, 45wats TDP) myself. 

Renting server is all well and god if you want to run a website, but if its for file storage then it would be a bad idea. Unless you have an 'unlimited' connection, and dont mind waiting for your files to upload/download.

> **rashhashan said:**
> well i plan on either running ubuntu 64 bit server or freenas...i know that freenas isnt so hardware demanding..as in it can tun of 128mb i believe with <512 gb of ram and an 800mHZ proc lol.

but actually ill be running ubuntu server...and the only prerequisite i have is it must have a raid controller. Also what do you guys think about going with a Dell? just something cheap ya know...for like 50-100 bucks on ebay

Some of those old computers EAT power like you wouldnt believe. Old P4s are the worst for that. 

Dell, meh. Better of getting a nice 'white box' computer and avoiding all the possible dell pitfalls.

---

### Post by IcarusR on 2010-10-07
You still have not told us the most relevant thing yet...

What will the server be used for ? How many people will access it ?
Web server or home network server... file server ? multimedia server ?

Then we can be more specific with hardware suggestions.

---

### Post by PresenceofMind on 2010-10-07
> **IcarusR said:**
> You still have not told us the most relevant thing yet...

What will the server be used for ? How many people will access it ?
Web server or home network server... file server ? multimedia server ?

Then we can be more specific with hardware suggestions.

 I agree.....

---

### Post by rashhashan on 2010-10-13
ok please excuse my lack of knowledge but what is the difference in file server and multimedia server...i mean there both dealing with files right??

---

### Post by PresenceofMind on 2010-10-13
Yes, file server and multimedia server both deal with files, but the multimedia is more specialised in storing and delivering multimedia content (i.e. media files) such as Movies, Video-on-demand, Pictures, Music etc.

At a basic level, file servers are simply specialized in shared disk access (i.e. Lending their hard drives...)

---

### Post by rashhashan on 2010-10-13
ahh ok ty then def multimedia server...but it must have hardware RAID

---

### Post by lavinog on 2010-10-26
Why must it have hardware raid?
How many clients do you expect to be serving?

I used an old 1998 HP that was given to me as a file/web server.  I added a little more memory to it so it had a total of 256M of PC133 ram. It had a 120G Drive.
It was built to last.  It didn't have a processor fan, and it ran for 3 years with no problem until I finally replaced it with a windpc.

If you are needing raid for speed reasons, you might want to make sure you have as much memory as possible first.

If you are wanting raid for redundancy, and you are not expecting the contents of the drive to change much, you could also consider using rsync to mirror the drive to another every now and then.

If you never setup a home server before, I would suggest setting one up with whats available and get a feel for the basics of running a server.

Don't forget that there are energy costs associated with running a home server too.

---

### Post by rashhashan on 2010-10-28
> **lavinog said:**
> Why must it have hardware raid?
How many clients do you expect to be serving?

I used an old 1998 HP that was given to me as a file/web server.  I added a little more memory to it so it had a total of 256M of PC133 ram. It had a 120G Drive.
It was built to last.  It didn't have a processor fan, and it ran for 3 years with no problem until I finally replaced it with a windpc.

If you are needing raid for speed reasons, you might want to make sure you have as much memory as possible first.

If you are wanting raid for redundancy, and you are not expecting the contents of the drive to change much, you could also consider using rsync to mirror the drive to another every now and then.

If you never setup a home server before, I would suggest setting one up with whats available and get a feel for the basics of running a server.

Don't forget that there are energy costs associated with running a home server too.


TYVM for that, yes this will be my first home server so im kinda lost...i just want it to be fast, efficient, and ease of use

---

