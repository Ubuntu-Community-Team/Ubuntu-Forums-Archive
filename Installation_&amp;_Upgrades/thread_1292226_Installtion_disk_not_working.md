---
title: "Installtion disk not working"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by 2ndsayton on 2009-10-15
Ok so ive never used linux before and my harddrive is partitioned with vista ultimate as my current main OS.

I downloaded the 8.04 LTS x64 bit home version and wrote the iso to a disk. But when I try to install instead of coming to the installation screen its supposed to it loads into a sort of MS-DOS format and seems to be expecting me to type in commands. Something about Debian v1.1.4 or something.

What have I done wrong? and when I choose "check disk for errors" it results in the same screen

---

### Post by phillw on 2009-10-15
The most common cause of mis-behaving cd installs is that you need to write the cd at about 4X speed - the accuracy needed is far greater than a run of the mill audio cd - so 48X write speed is no good.

On the same vein - use a decent make of cd-r, and clean the lens on the burning cd-writer & the reading cd unit (if they are on 2 different machines).

Hope that helps,

Phill.

Get your iso image from here ....
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

An excellent how-to can be found here for popping ubuntu on with windows...
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)

Hope that helps,

Phill.

---

### Post by 2ndsayton on 2009-10-15
ah ok ill try re-doing the disk, hope it fixes it

edit: Opened a brand new disk and wrote and 2x speed. It still comes up with "Busy Box 1.1.3 (Debian v1.1.3........ some stuff about ubuntu etc)

 and wants MS-DOS style commands?? This is when I choose the "Demo without changing harddrive" and same for installation.


Also I did download from the above link

---

### Post by 2ndsayton on 2009-10-15
> **phillw said:**
> 
An excellent how-to can be found here for popping ubuntu on with windows...
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)


The installation doesn't even get that far - I choose install, then it goes to Ubuntu loading screen, then the DOS

---

### Post by phillw on 2009-10-16
Can you post the make & spec of your computer.

Thanks.

Phill.

---

### Post by invitingdopeman on 2009-10-16
try getting the actual disk in the mail thats what i did works wonders i didnt partion or anything just thought i would suggjest i had to completely put a new OS on my pc cuse windows was so ****** up aight well im rambling late INVITINGDOPEMAN

---

### Post by 2ndsayton on 2009-10-16
> **phillw said:**
> Can you post the make & spec of your computer.

Thanks.

Phill.

Yea sure, Im using a Q8200 2.33 Ghz Quad processor
                               Mostly intel stuff like the motherboard etc 
                               6 gig ram
                               Geforce 9800GT graghics card
 
PC was ready built so im not really 100% sure of exact makes of things, but the PC is only nearly 1 year old. If that helps.

---

### Post by phillw on 2009-10-16
Well, it's the correct architecture chip Vs ubuntu installation.

If you're sure you got the 64 bit one (it's 32 bit by default from the down-load page).

I'm afraid I'm stumped if you have got the image from that site, burned it at slow speed on a decent CD-R.

The only thing I could suggest would be to use a cd/dvd drive cleaning disk, as the tolerance on the iso image is quite tight.

If none of this works, go to a reasonably sized public library, computer section, linux section and borrow a book with a cd/dvd in the back (there's several at my local library) - Try one of those.

Failing that - yeah, order the disk - it can take 4 weeks :(  But, you do get some real kewl stickers.

If you PM or email me - I'll gladly burn a disk for you using the settings I use for installs. (Heck, I can afford a postage stamp ;-) )

Phill.

---

### Post by 2ndsayton on 2009-10-16
Could I install from the ISO by some how using a USB stick instead? to totally remove possible errors? Ive got a 16 gig one which would be easier. I never have much luck when it comes to disks.

And a huge thanks for the help by the way

---

### Post by phillw on 2009-10-16
Yeah, usb would be a kewl way !!

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Make sure you set your BIOS to boot off the USB stick :P

Phill.

---

### Post by 2ndsayton on 2009-10-16
reminds of trying to get vista to work :P but THAT is a story for another time. Ill post if I get it working.

Huge thanks again

---

### Post by presence1960 on 2009-10-16
if all else fails try the alternate text based installer. get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"). it will usually succeed where the Live Cd fails.

Also did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso before you burned it to disk? The hashes must match exactly or the iso is corrupted.

---

### Post by 2ndsayton on 2009-10-16
No worrys, its working from my USB. Only slight issue is that it only wants to install on the USB and not the harddrive but I'm sure when ive got rme later I can fix it


edit: bad phrasing - what I mean is the demo works perfectly and when I choose installtion its not picking up my hard drive

---

