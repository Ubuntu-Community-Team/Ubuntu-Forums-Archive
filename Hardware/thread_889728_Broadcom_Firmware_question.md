---
title: "Broadcom Firmware question"
date: 2008-08-14
forum: Hardware
---

### Post by PhantomOG on 2008-08-14
So I'm a complete noob who's trying out ubuntu on my laptop (HP dv9500z).  I shrank my Vista partition down by 20GB, installed ubuntu on the new free space and everything seems OK.  Now I'm trying to get all of my devices working.  First and most important is the Wifi.  I plan on following the documentation here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

which says I will need to install firmware in order for it to work. 

My question is whether installing the firmware will have any (negative) effects on my Vista usage?  I want to Wifi to work on both Vista and Ubuntu obviously.  Also, am I on the right track as far as getting things to work?  I admit to being a bit overwhelmed when reading all the documentation.

---

### Post by pwnprog on 2008-08-14
hey man. i was once in your shoes. same computer, same installation method, same problem, same n00bie-ness. 

unlike me however, you don't have to spend hours hunting for the answer cause i'll point you to it! this worked for me in one shot. ----->  [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

just follow the directions in the original post and you'll be good to go. worked like a charm for me on the first try! only takes about 5 or 10 minutes. you'll never drop a connection or anything like that either. very well written how-to.

to answer your question about the vista partition, i also dual boot and haven't had a single problem using wireless in my vista partition. i dont know if it does anything to the insides of your wireless adaptor. all i know is that wireless still works reliably and strongly on both partitions after 4 months of ubuntu.

hope this helps!! let me know if you run into any trouble.

---

### Post by Ayuthia on 2008-08-14
> **PhantomOG said:**
> So I'm a complete noob who's trying out ubuntu on my laptop (HP dv9500z).  I shrank my Vista partition down by 20GB, installed ubuntu on the new free space and everything seems OK.  Now I'm trying to get all of my devices working.  First and most important is the Wifi.  I plan on following the documentation here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

which says I will need to install firmware in order for it to work. 

My question is whether installing the firmware will have any (negative) effects on my Vista usage?  I want to Wifi to work on both Vista and Ubuntu obviously.  Also, am I on the right track as far as getting things to work?  I admit to being a bit overwhelmed when reading all the documentation.
The firmware that you are downloading is not going to do anything to Vista.  The b43 driver just needs some of the information from the firmware to make it work.  

You are on the right track on getting it to work.  The Broadcom cards now have a few driver options: the b43/b43legacy driver, the bcm43xx depreciated driver, ndiswrapper, and the new wl driver from Broadcom.  Which one you decide to use is up to you.  In my opinion, the b43 driver is the easiest to try first.  It does not require anything, but installing the firmware.  Here is a link on how to get the firmware installed:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

The ndiswrapper option has more steps and will require you to blacklist (block out) the other wireless drivers.  I prefer to do this as the next option after trying the b43 driver mainly because it is harder to troubleshoot when something goes wrong during the install.  You can use the link that pwnprog provided.  It seems to work pretty well with HP laptops.

The bcm43xx driver is also another option, but it is depreciated because of the new b43/b43legacy drivers.  It can be used in certain situations where some of the older cards are not working with the b43 card.

The wl driver is a new driver from Broadcom.  The downside to it is that some of the Broadcom cards do not work with them yet.  However, the ones that do seem to work pretty well and it does not require any firmware.

---

### Post by PhantomOG on 2008-08-14
Thank you so much.  I can't wait to get home from work and try it out.  Thank goodness that link is very explicit with line by line instructions.  Alot of the documentation seems to assume a base level of knowledge that apparently I don't have yet.

I hope you don't mind me PM'ing you for more info since you have the same laptop.  Did you install the 64 bit version as well?

---

### Post by maaxberg on 2008-08-14
Hello there,

Recently I installed Ubuntu 8.04 the hardy Heron released April 2008 on my mac power bookG4 PPC. Pls. I need so help... from where I may download??? codecs? plugins 4 firefox? yahoo messenger? skype? everything is working fine this is the best version of linux I installed on mac ppc, really amazing! broadcom installed the wrong driver... from where I can get the driver?:guitar: thanks very much!!! AL

---

### Post by pwnprog on 2008-08-14
> **PhantomOG said:**
> Thank you so much.  I can't wait to get home from work and try it out.  Thank goodness that link is very explicit with line by line instructions.  Alot of the documentation seems to assume a base level of knowledge that apparently I don't have yet.

I hope you don't mind me PM'ing you for more info since you have the same laptop.  Did you install the 64 bit version as well?

hey duder. i guess our laptops aren't the "same", but they are the same series i suppose (hp pavillion dvxxx). mine is not 64 bit, so i can't say i've tried that.

however, i have the peace of mind in knowing that i've suggested following this how-to to a few other people owning pavillion laptops with broadcom chips, and it's worked every time. 

feel free to pm me and let me know how it worked out! hopefully i saved you a little bit of digging.

---

