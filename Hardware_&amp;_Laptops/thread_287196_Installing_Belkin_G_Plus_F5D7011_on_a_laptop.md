---
title: "Installing Belkin G Plus F5D7011 on a laptop"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by Wolf_Silentheart on 2006-10-28
I have a Gateway solo 9500 and I am trying to install a Belkin G+ F5D7011 PCMCIA card on a Breezy badger system. I really need this system online asap. Any info would help. I am unable to locate drivers for it and am not sure on how to install drivers in linux, (linux noob) Please feel free to email me at [email]Wolf_Silentheart@sbcglobal.net[/email] or better yet just post here. I'm not even sure if there are drivers for this device available for linux. I was also wondering, are the linux drivers universal or specific to the distro or kernal? Thnx in advance.

---

### Post by NE Key on 2006-11-08
I see no one has answered you after a week.

I am trying to do the same thing - my laptop with Belkin F5D7011 card works absolutely fine out of the box with Linspire but I cannot get it going in Ubuntu (also have no idea where to start) - and as the lack of replies suggests, perhaps it won't work.

 Hang on - forum search has produced the answer --- things are looking up....

---

### Post by 164747 on 2006-11-21
Having the same problem. My F5D7011 worked fine on FC2 with ndiswrapper. Now I have installed kubuntu 6.10 and used the exact same installation procedure (standard ndiswrapper) and using the file bcmwl5.inf.

Everything seems to be working fine, BUT when I write modprobe ndiswrapper, the card does not light up. However, once it did ?!? (after approx. 1 min) and I could access the wireless network. 

My card shows up with lspci, and is able to restract much info about the card. I think this is indipendent from ndiswrapper, but I am not sure what to do with this info.

I also think there is a solution to the problem, because there are people are claming to have their F5D7011 working with (k)ubuntu. Dont know what they did. 

Why is Linux so hard =)

---

### Post by 164747 on 2006-11-21
I have solved my problem, the file bcmwl5.inf that came with the installatiobn cd from belkin worked perfectly with ndiswrapper and FC2, but looking at 

[http://home.nc.rr.com/thehinnants/stuff/drivers/](http://home.nc.rr.com/thehinnants/stuff/drivers/)  (the zip-fil)

I found that the file bcmwl5.inf differed from the previos (old/wrong)

md5sum: OLD/WRONG worked for me using FC2
b19da13eeba8333fe7f43761e9f6078d  bcmwl5.inf
52d67c5465c01913b03b7daca0cc4077  bcmwl5.sys

md5sum: The ones that worked for me using kubuntu 6.10
02e93649508d68e60c4919fda92c2273  bcmwl5.inf
ebf36d658d0da5b1ea667fa403919c26  bcmwl5.sys
 
the installation is simple and is described at
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)


I hope that someone that understand theese issues with the wireless cards for Linux, structures the everything up, and makes it much more transparent and easy to use.

---

