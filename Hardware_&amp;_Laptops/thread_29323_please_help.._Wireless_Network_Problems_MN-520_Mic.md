---
title: "please help.. Wireless Network Problems MN-520 Microsoft Card"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by coreyb on 2005-04-23
Hi,

First off I just installed ubuntu today, after previous failures with other distros on my rather archaic IBM Thinkpad 600E.

I have a Microsoft MN-520 Wireless 802.11b network card for this laptop. Today I ran out and bought myself a nice Belkin wireless router. I have two other comps in my home that are hard wired to this router (my means of posing this).

Being a complete newbie to Linux itself I am pretty much at a loss on how to make it work! I have read through the forum and found somethings interesting, but I always ran into some sort of problem while trying to follow the directions. 

I am in need of complete, step-by-step, help to install and get on the internet with my network card. 

I am comfortable with the terminal, but I lack the command knowledge to give you information in order to help you help me. 

I can tell you that I am sure that the card is functioning because it was working perfect while the laptop was running Windows XP. 

Any and all help is appreciated.   :neutral:  ](*,) 

Thanks in Advance,
Corey

---

### Post by Mat10 on 2005-04-24
On install of Ubuntu did you allow the internet detection or skip it ?  Also did you install the nic after installing Ubuntu ?   If the card install was after your initial install of Ubuntu you might have to reinstall and let it detect your card.  If it doesn't see it , then it probably is not a compatible card.  Note I mean reinstall of Ubuntu not the nic.

If it is not supported with a driver then the only hope would be to try the ndiswrapper solution and  build a driver module that uses windows XP drivers. The best advice is to find a nic that will work, it has to be something two or three years old.  Most wireless USB and nics don't have drivers as yet and may never have them, for Linux.  The makers won't release the infomation needed to build good drivers.  

Cabling to the router with a standard nic is probably your best alternative , at least you can get on line and use Ubuntu.  This is a real sweet operating system once it is online and the tools that it has available are just great for doing all the work of downloading and installing new programs.  It just works what more can you say.  All the others have similar tools such as YaST in suse and they do the same task, but I like this manager much better.  Today it took three minutes to download and install the same program I had installed on suse 9.1 and it took me two days to figure out how to do that.

So I hope you find a good card that will work for you.  By the way before I forget, just about every Linux distro out there has pretty much the same data base as far as drivers for wireless and nics.  So don't waste a lot of your time trying different distros just to get on the net, been there and done that and it is a waste.  Go with the CAT5 cable for now and eventually you will find the right card doing the research.   It takes a lot of studying and trial and error to compile new kernels just for one driver,,    ndiswrapper

Tom

---

