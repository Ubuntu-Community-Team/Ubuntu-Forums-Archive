---
title: "From Raspberry Pi to Ubuntu hardware"
date: 2014-06-30
forum: Hardware
---

### Post by micwit2 on 2014-06-30
I am currently getting a raspberry pi set up as a server, and have come across a few things that I think would work better on a full desktop install of Ubuntu. For example, there is no dropbox support for arm hardware, but dropbox works well on the Ubuntu desktop. SMB shares on the Pi could not be accessed in Ubuntu desktops (although they were fine on windows machines!). Running some things in LAMP can be a bit slow (like logging into PHPmyAdmin), I think it would benefit with a little more ram and a slightly faster CPU.

I need the solution to be cheap, and not chew much power (10w or so) and I was thinking maybe an old laptop with a broken screen that someone doesn't want (if I could pick one up cheap), or maybe if there is a tablet that runs Ubuntu desktop and would let me plug in a USB HDD? At the moment the Pi is such a great option as it is $35 for the entire thing, it runs silent, and on about 3w! If there was a dropbox installer for it and the web server ran a little faster, it would be great (I can just use NFS instead of SMB if need be).

Any ideas?

Thanks

---

### Post by squakie on 2014-06-30
Which OS are you running on the Pi?  I don't just mean "linux", but instead which variant?  What server software are you trying to use?  Do you want this to be a media server?  

Also - I have NO idea what the status of it is now, but there was a product - I believe it was called PCDuino - that you could run Ubuntu on.  Not much more than a Pi - around $65-$70 if I remember correctly.  It's small, low power consumption, quiet, etc..  It might be worth looking at.

---

### Post by micwit2 on 2014-06-30
I am running raspbian on the pi, cant remember which version, within the last 6 months though. The server software I am using is Apache, mysql, php, PHPmyAdmin, rsync etc.

The main thing that is the issue on the pi is the lack of support from dropbox (they don't support ARM). I believe that the PCDuinos are also running ARM processors, and don't believe they have dropbox support either. I don't think they run Ubuntu, I think they run their own variant of Lbuntu, which Im guessing would not run a normal x86 or 64bit apps. As far as I can tell, the CPU would have to be on one of these architectures (or be compatible somehow with x86 at least).

---

### Post by grahammechanical on 2014-06-30
Are you saying that the Ubuntu developers should produce a Raspberry Pi version of Ubuntu? Such a Pi Ubuntu would be limited by the Raspberry Pi hardware. Just as the present OS for Raspberry Pi is limited. Ubuntu is open source and any developer who is interested can take the source code and port it to the Raspberry Pi. 

It is my understand that the Raspberry Pi board was developed at such a low cost so that schools could use it to get children involved in computer programming without breaking their school budgets.

[http://www.raspberrypi.org/](http://www.raspberrypi.org/)

Regards.

---

### Post by micwit2 on 2014-06-30
lol, not at all! Im just wondering if there is something out there kind of like the pi, but that runs an x86 or x86_64 architecture that I could run the full desktop Ubuntu and any x86 software with, something low powered and silent though (prefer no fans). Also something cheap (doesn't have to be the $35 like the pi, but not heaps more).

---

### Post by squakie on 2014-06-30
Perhaps this will help.  This was linked to by other sites about using DropBox on the Pi.  It's supposed to be cross-platform, but I've never had a need for that so I don't know how it works - just passing it along it case it can help you:

[https://github.com/andreafabrizi/Dropbox-Uploader](https://github.com/andreafabrizi/Dropbox-Uploader)

---

### Post by micwit2 on 2014-06-30
I have seen that. Its for uploading files, not syncing them. I actually created a sync program in python, but the api (at least the python one) has soooooo many bugs! Not worth using.

---

### Post by squakie on 2014-06-30
And if you don't already know - a Pi, a powered USB hub, an external hard drive (plug into the hub), and possibly a flash drive to do all the booting from except for the very initial call (still have to have the SD card for that), makes a GREAT media center!   Very inexpensive - can run raspbmc (sp?), OpenELEC (I use that) and more wth XBMC.  I have a cheap IR receiver I bought used off Ebay plugged in to the hub and set the AUX on my remote to Microsoft XBox and it's just a push of buttons on my universal remote to do what ever I need to.  I also have my tablet set up with XBMC for Android and simply point it to SMB on the Pi and can play all my media wirelessly throughout the house.

Yep - developed for the purpose you stated.  Since people found out how good a media center they make, the demand has just skyrocketed.  I'm surprised they can keep up with the production and still keep the cost so low.

I've also used raspian on another Pi just to "goof around with".  Can get on the net, etc., but of course limited by speed and what is supported.  But it is an amazing little box.  Remember back to the old days of paying $500-$600 for a bare motherboard, getting and soldering all the components on, making your own cables, building from scratch and writing the CP/M drivers for disks, making your own power supply, etc. (heck I even had a keyboard that came as a bare board and a bag of parts!) ??  I think about how much it cost back then for something that couldn't do anything like the Pi, let alone for under $50.

I may try setting one up as a server myself just to have some more fun goofing around.

> **grahammechanical said:**
> Are you saying that the Ubuntu developers should produce a Raspberry Pi version of Ubuntu? Such a Pi Ubuntu would be limited by the Raspberry Pi hardware. Just as the present OS for Raspberry Pi is limited. Ubuntu is open source and any developer who is interested can take the source code and port it to the Raspberry Pi. 

It is my understand that the Raspberry Pi board was developed at such a low cost so that schools could use it to get children involved in computer programming without breaking their school budgets.

[http://www.raspberrypi.org/](http://www.raspberrypi.org/)

Regards.

---

### Post by squakie on 2014-06-30
Thanks for the info!  I may just need to get another and play with it as a server and see what I find out.  Never done it with a Pi yet. Any chance of a C program to do the syncing?  I have NO idea what is involved.  If you could point me to some sort of docs for programming the syncing I could look into it.

> **micwit2 said:**
> I have seen that. Its for uploading files, not syncing them. I actually created a sync program in python, but the api (at least the python one) has soooooo many bugs! Not worth using.

---

### Post by micwit2 on 2014-06-30
> **squakie said:**
> Thanks for the info!  I may just need to get another and play with it as a server and see what I find out.  Never done it with a Pi yet. Any chance of a C program to do the syncing?  I have NO idea what is involved.  If you could point me to some sort of docs for programming the syncing I could look into it.

No worries, the core API (the one you want for syncing) is here: [https://www.dropbox.com/developers/core](https://www.dropbox.com/developers/core) - This includes some basic tutorials etc, then you just need to look at the calls etc required.

You will need to go to [https://www.dropbox.com/developers/apps/create](https://www.dropbox.com/developers/apps/create) to register an app and get your key and secret. As part of the app, you will need to then allow this through your account (can be the same account you registered the app through, or a different one).

The main calls are at [https://www.dropbox.com/developers/core/docs](https://www.dropbox.com/developers/core/docs)

The main 3 issues I had with the python API were:
1) Capitalisation - It sometimes had the path as capitals, sometimes it didn't. This meant that when you went to delete files, it couldn't find them if there was a capital anywhere in the path! I did get around this, but it was a pain-in-the-butt! It is a known issue with dropbox that having the same named file with capitals and lower case causes problems, these are just expanded in the API as it doesn't even stick to a standard.
2) File sync errors - Another issue was that the error reporting was not too good, it would just print to screen and kill the program. Sometimes it would send some kind of an error back without killing the program, but other times it would just print an error and kill the program (so if running in the background, you wouldn't realise it had stopped syncing, and thats a BIG problem). The errors it would print were so bland anyhow, that you wouldn't even know how to fix them!
3) Random files with issues - I found that there was a particular file that wouldn't sync one time. No particular reason, other files in that folder would sync fine, and files in other folders with exactly the same name would sync fine, just that particular file wouldn't sync!

So as I said, quite a few bugs still in the API! I decided to be on the safe side, I would just not worry about it on the pi, and share a folder on my media centre (windows) running dropbox to get around it for now. If I could find the right hardware to run desktop ubuntu, that would rock for what I want to do.

---

### Post by squakie on 2014-06-30
Hey - I know this thing doesn't look great, but so far at least it's cheap and should be able to do what you want:

[http://www.ebay.com/itm/HP-Mini-110-Intel-Atom-1-66GHz-1GB-RAM-160GB-HDD-948-3/351102923679?hash=item51bf5d739f](http://www.ebay.com/itm/HP-Mini-110-Intel-Atom-1-66GHz-1GB-RAM-160GB-HDD-948-3/351102923679?hash=item51bf5d739f)

---

### Post by squakie on 2014-06-30
Hey - I know this thing doesn't look great, but so far at least it's cheap and should be able to do what you want:

[http://www.ebay.com/itm/HP-Mini-110-Intel-Atom-1-66GHz-1GB-RAM-160GB-HDD-948-3/351102923679?hash=item51bf5d739f](http://www.ebay.com/itm/HP-Mini-110-Intel-Atom-1-66GHz-1GB-RAM-160GB-HDD-948-3/351102923679?hash=item51bf5d739f)

---

### Post by squakie on 2014-06-30
Ooooppppsss- forget this post - somehow I dup'ed the one above......

---

### Post by micwit2 on 2014-06-30
Thats an interesting idea. So are the Atom chips x86 arch? are all of them x86? I was thinking a little Atom of some description if they work. That particular item has a fair bit for postage, and being a bid item Im guessing it will go up towards the end anyhow.

There has to be some little atom computer produced thats not a laptop (no screen etc attached) that would be cheap as!

---

### Post by squakie on 2014-06-30
Hummm.....never looked for a headless atom product.  I think they are x86 as I had a netbook a few years ago and just installed what was normal ubuntu to it in those days.   I did see someones headless item on ebay for $39, but it's arm based.  I think I'll do a little checking myself.  I just had the weird idea that you might be able to pick up something like that relatively cheaply if you watch the auctions closely.  Some are what I call out of their mind priced, others are to me just priced to high for the product.  Heck, I bought mine new back then for like $199.  I wouldn't even think about anything much over $50 if I had it and was selling it today.

I'll keep this idea in mind a let you know if I see something else that's reasonably priced, x86, that might work for you.

Dave

---

### Post by micwit2 on 2014-06-30
Cool, thanks. Yeh, considering new price, they seem to want a lot for them!

---

### Post by squakie on 2014-07-01
Hey - here's something that may be what you need - it's used, relatively small hard drive, headless (or at least it appears it can be) running a Celeron.  Just a touch over $50 including shipping!

---

### Post by micwit2 on 2014-07-01
That could be cool, got a link?

---

### Post by squakie on 2014-07-01
Sorry - I forgot the link!

Hey - here's something that may be what you need - it's used, relatively small hard drive, headless (or at least it appears it can be) running a Celeron.  Just a touch over $50 including shipping!

[http://www.ebay.com/itm/AOpen-MP915-X-Mini-Desktop-PC-Computer-Intel-Celeron-M-CPU/291073834850?_trksid=p2047675.c100005.m1851&_trkparms=aid%3D222007%26algo%3DSIC.MBE%26ao%3D1%26asc%3D23823%26meid%3D7998822596205851303%26pid%3D100005%26prg%3D10177%26rk%3D4%26rkt%3D6%26sd%3D271523893489&rt=nc](http://www.ebay.com/itm/AOpen-MP915-X-Mini-Desktop-PC-Computer-Intel-Celeron-M-CPU/291073834850?_trksid=p2047675.c100005.m1851&_trkparms=aid%3D222007%26algo%3DSIC.MBE%26ao%3D1%26asc%3D23823%26meid%3D7998822596205851303%26pid%3D100005%26prg%3D10177%26rk%3D4%26rkt%3D6%26sd%3D271523893489&rt=nc)

---

### Post by micwit2 on 2014-07-01
Cool, but wont post to Australia. And I notice it says it uses 19V and 3.5A, thats 66.5W! Seems a bit extreme for something like that!

---

### Post by squakie on 2014-07-01
It's probably the Celeron and the hard disk that bump the wattage up.   I didn't realize you were in Australia!  I'll change my searching criteria and keep you posted!

Dave ;)

EDI:  BTW- I missed the part about a $15 surcharge international shipping.  But you never know:  Pi, power supply, case, SD card - over $55 U.S..  At $65, this still might not be a bad idea, however I truely understand financial limits - I'm on disability so I just can't go out on jump on things like this myself!

---

### Post by micwit2 on 2014-07-01
Haha, thanks. Yeh, the best would be something like the pi but with an atom instead of an arm cpu. I just looked on the pi site, where are the tech specs on the new site???

---

### Post by squakie on 2014-07-01
I did just find something else - its says L55, so not really knowing I assume that's 55 British pounds?  Haven't look yet, but perhaps a used one can be found.

[http://robosavvy.com/store/product_info.php/products_id/1704?osCsid=a64d0381e158bf40d82bd753f4d1636b](http://robosavvy.com/store/product_info.php/products_id/1704?osCsid=a64d0381e158bf40d82bd753f4d1636b)

---

### Post by micwit2 on 2014-07-01
10W, thats more like it! I wonder if you can add 512 ram to the onboard ram. NOT cheap on ebay ([http://www.ebay.com.au/itm/DMP-eBox-3350MX-x86-Compact-PC-/141326044718?pt=LH_DefaultDomain_15&hash=item20e7b04e2e&_uhb=1](http://www.ebay.com.au/itm/DMP-eBox-3350MX-x86-Compact-PC-/141326044718?pt=LH_DefaultDomain_15&hash=item20e7b04e2e&_uhb=1))

---

### Post by squakie on 2014-07-01
Perhaps this would work?

[http://www.ebay.com.au/itm/Asus-Eee-PC-R105-10-1-inch-netbook-/131226762637?pt=AU_comp_laptop&hash=item1e8db97d8d](http://www.ebay.com.au/itm/Asus-Eee-PC-R105-10-1-inch-netbook-/131226762637?pt=AU_comp_laptop&hash=item1e8db97d8d)

---

### Post by micwit2 on 2014-07-01
I was looking at that one, I think for now I may leave it and see if my mate who works at a computer shop has anything come in. For gear like that, there has to be a way of getting one with a broken screen or something.

---

### Post by squakie on 2014-07-01
I don't know anything about Australia postal codes, so I have no Idea on the shipping - but something like this could even work - just set power options to ignore lid closed.  It's also relatively cheap!!

[http://www.ebay.com.au/itm/COMPAQ-PRESARIO-V2000-AMD-SEMPRON-3000-640MB-RAM-128MB-ATI-GRAPHICS-/271534267901?pt=AU_comp_laptop&hash=item3f38b41dfd](http://www.ebay.com.au/itm/COMPAQ-PRESARIO-V2000-AMD-SEMPRON-3000-640MB-RAM-128MB-ATI-GRAPHICS-/271534267901?pt=AU_comp_laptop&hash=item3f38b41dfd)

---

### Post by micwit2 on 2014-07-01
Thats pretty cool, but doesnt come with charger, and the charger is more than the laptop lol

---

