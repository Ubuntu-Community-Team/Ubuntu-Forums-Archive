---
title: "dvd drive spinning too fast..."
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-08-20
Hi.
I have a problem with my dvd drive spinning  WAY too fast.
When i watch a dvd it reads at max speed when 2-3x does fine.

I use "nero drive speed controller" in wiindows to limit the read speed, this works great...
however in nerolinux there is no option for this (at leat in my version)
Is there a way to control the read speed with a program or linux itself??
thanx a bunch..

---

### Post by drizek on 2005-08-20
[QUOTE=floyd27]Hi.
I have a problem with my dvd drive spinning  WAY too fast.
When i watch a dvd it reads at max speed when 2-3x does fine.

I use "nero drive speed controller" in wiindows to limit the read speed, this works great...
however in nerolinux there is no option for this (at leat in my version)
Is there a way to control the read speed with a program or linux itself??
thanx a bunch..[/QUOTE]
 open a terminal and do

man hdparm

have fun

sorry, ive never used hte program before, so youll have to read up on how it works and how you can use it on your system. shouldnt be too hard. then just use 

hdparm

to set the speed

Edit: before reading he man pages, try doing 

hdparm -E4 /dev/cdrom

and see if it does anything

---

### Post by floyd27 on 2005-08-20
thanx for the code..
that seesm to be for HDD's aand not cd-rom dvd drives....
I didnt get to read it all (lots there), but i dont think it will work with the dvd drive.
thanx anyway though

---

### Post by drizek on 2005-08-20
[QUOTE=floyd27]thanx for the code..
that seesm to be for HDD's aand not cd-rom dvd drives....
I didnt get to read it all (lots there), but i dont think it will work with the dvd drive.
thanx anyway though[/QUOTE]
 ya, it does work with cdrom drives too.

i edited my above post

hdparm -E 3 /dev/cdrom

should work

your cdrom might be called something else though, like cdrom1

---

### Post by floyd27 on 2005-08-20
Hi..
that last one you put seesm to work...
havent actually tested it though
I assume i can change the 4 to whatever i wanted ?
like 1
lol
i dont like loud drives :)

thanx again

---

### Post by floyd27 on 2005-08-20
how would i go about finding what t is called?
thanx

---

### Post by drizek on 2005-08-20
np, and ya, the 4 is the speed

---

### Post by drizek on 2005-08-20
i dont know. lol. ive only been using gnome for a couple days. if you only have one drive though, htne it should just be cdrom

---

### Post by floyd27 on 2005-08-20
that worked out great.
quiet as can be....
thanx alot, iv nbeen messing with that for a while...

---

