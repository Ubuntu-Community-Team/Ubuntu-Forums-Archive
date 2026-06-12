---
title: "Cursor misbehaves on first boot up"
date: 2010-03-19
forum: Hardware
---

### Post by NB Iona on 2010-03-19
Hi folks.  This is my first ever post on my second ever forum so I'm feeling a tad nervous.  I'm very new to Ubuntu - my son convinced me to switch from Vista to Ubuntu a while ago (can't remember why but he wore me down eventually!)  I've found the answers to problems so far via the search facility and have found this forum very helpful, unfortunately I can't seem to find the right search phrase to find the solution to my current problem, so I've had to bite the bullet and join up.

I'm on Ubuntu Karmic Koala using an Acer Aspire laptop, permanently dangling from a dongle because I live on a narrowboat.  Every time I fire up the laptop the cursor misbehaves - it opens up menus on the screen and jumps from place to place.  It's become a bit of game - I chase it around and eventually catch it quickly enough to get the lappy to restart, then it behaves impeccably.

I'm not sure if it's linked, but when the laptop restarts and the cursor is behaving itself I have a fight with the internet to get it started.  I click on the mobile internet option, it tells me I'm connected with a very good signal, but I can't get on the internet.  I then spend a while disconnecting then re-connecting over and over again, and then it suddenly works and I have no further problems until I shut the computer down.

Sorry if this is a bit long-winded - I had to have a few glasses of wine to pluck up the courage to post and I waffle after a few drinks!

Thanks in advance for any help

Ange

---

### Post by NB Iona on 2010-03-20
Just checking - did I receive no replies because no-one knows the answer, or because I've posted my question wrong / in the wrong place?  I'm not sure where else to go for help.

Thanks
Ange

---

### Post by xifer on 2010-03-20
> **NB Iona said:**
> Just checking - did I receive no replies because no-one knows the answer, or because I've posted my question wrong / in the wrong place?  I'm not sure where else to go for help.

Thanks
Ange

i'm guessing no one is sure enough to post. when you say cursor you mean the mouse pointer?  so i'm wondering what type of device is it? one of those touchpads or a stick thing?  Do you get the same behaviour if you boot with an external mouse plugged in?

your internet problem might be dns or dhcp related - those are the services that run on your network to give you an internet address and tell your internet requests where the websites are and how to access them.  Can you access your router to reboot it when this happens?  what sort of router is it - often they can be the issue?  Have you changed any setting in config files etc relating to network at all or installed special drivers or is everything being done automatically?

---

### Post by NB Iona on 2010-03-20
> **xifer said:**
> i'm guessing no one is sure enough to post. when you say cursor you mean the mouse pointer?  so i'm wondering what type of device is it? one of those touchpads or a stick thing?  Do you get the same behaviour if you boot with an external mouse plugged in?

your internet problem might be dns or dhcp related - those are the services that run on your network to give you an internet address and tell your internet requests where the websites are and how to access them.  Can you access your router to reboot it when this happens?  what sort of router is it - often they can be the issue?  Have you changed any setting in config files etc relating to network at all or installed special drivers or is everything being done automatically?

Hya - thanks for the reply.  Yes I do mean mouse pointer when I say cursor - getting that wrong probably didn't help did it!  I use a touchpad - I haven't got an external mouse so haven't tested it with one plugged in.

Re the internet - I don't have a router.  I live on a narrowboat so I use a dongle - not sure if this makes a difference.  I've only just installed Ubuntu so haven't changed anything.

Both issues are an annoyance more than anything, but it'd be nice to get them sorted.

Ange

---

### Post by xifer on 2010-03-20
> **NB Iona said:**
> Hya - thanks for the reply.  Yes I do mean mouse pointer when I say cursor - getting that wrong probably didn't help did it!  I use a touchpad - I haven't got an external mouse so haven't tested it with one plugged in.

Re the internet - I don't have a router.  I live on a narrowboat so I use a dongle - not sure if this makes a difference.  I've only just installed Ubuntu so haven't changed anything.

Both issues are an annoyance more than anything, but it'd be nice to get them sorted.

Ange

Hi

I'd try and get an external mouse - there could be a hardware error or weird compatibility problem.  


ok, well if you haven't changed anything the internet should ''just work'' :-)

This is a wireless mobile dongle rather than a local area connection to a router then?  not used one myself but it will have to provide certain info to your pc like ip address and default gateway - that's your route to the internet.

If the machine is stable to enough to get a terminal window open then type in the command :

> ifconfig

it should show you the details for your connection - probably labelled wlan0
you should see an inet addr and bcast line - if those numbers are correct then your dhcp is working - that's stage one.

next type this

> route


and the last line printed should say default and another IP number that's your default gateway if that is correct then you would seem to be connected ok to your ISP.

> ping <default gateway IPNumber>

should give you a response if it does try another website like

> ping [www.bbc.co.uk](www.bbc.co.uk)

if that works then your internet connection is fine and your browser is stuffed.

depends where it's going wrong - see how it goes - it doesn't seem like the trouble is on your PC but the network managers sometimes do mess up.

---

