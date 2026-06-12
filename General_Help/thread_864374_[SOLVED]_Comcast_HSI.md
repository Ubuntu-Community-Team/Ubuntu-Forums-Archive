---
title: "[SOLVED] Comcast HSI"
date: 2008-07-19
forum: General Help
---

### Post by jbeaunaux on 2008-07-19
I'm not sure if this would be the right forum to pose this question - but here goes.

I'm dropping Verizon DSL and going with Comcast HSI; the installation tech is coming out in a few days. I asked Comcast if they support Ubuntu/Linux and their reply is that they don't, but that there shouldn't be any inherent compatibility issues. I'm not entirely convinced though after my ordeal with Verizon saying roughly the same thing. I've been browsing through different Ubuntu forums looking at others' experiences, and it seems like there's a mixed bag out there of people who've had no problems at all with Comcast and those that have.

Should I be anticipating any problems with installing Comcast and getting online? And if so, what can I do to get up and running?

---

### Post by warp99 on 2008-07-19
> **jbeaunaux said:**
> I'm not sure if this would be the right forum to pose this question - but here goes.

I'm dropping Verizon DSL and going with Comcast HSI; the installation tech is coming out in a few days. I asked Comcast if they support Ubuntu/Linux and their reply is that they don't, but that there shouldn't be any inherent compatibility issues. I'm not entirely convinced though after my ordeal with Verizon saying roughly the same thing. I've been browsing through different Ubuntu forums looking at others' experiences, and it seems like there's a mixed bag out there of people who've had no problems at all with Comcast and those that have.

Should I be anticipating any problems with installing Comcast and getting online? And if so, what can I do to get up and running?

No problems here except be prepared to put up with poor customer service and bandwidth throttling issues with seeding bittorrent. Whatever you do don't tell them you have multiple computers in the house since they will try to charge you an IP for each machine.

With Comcast the less they know about your computers the better off you are. Just let them do what they want then after they leave plug the cat5 cable into your router, set all of your machines to static IP addresses, then power cycle the cable modem. 

With my family sometimes I have three laptops, one desktop, one server, and two handhelds all sharing the same IP at the same time. :lolflag:

---

### Post by exploder on 2008-07-19
Comcast is who I have for an iSP, no problems here.

---

### Post by sports fan Matt on 2008-07-19
I personally went with at&t dsl, but thats cause comcast has poor cust. service for their tv as well...

---

### Post by Sinkingships7 on 2008-07-19
As long as you don't mind horrible upload speeds, you shouldn't have any problems with Comcast. That's my ISP.

---

### Post by fragos on 2008-07-19
Windows users self install and register their modem to Comcast with a Windows only program. For linux after pluging in the modem you're done on the Linux side. Once all setup, call their support and ask them to remotely register your modem. It is their policy to do so. If support doesn't understand what you want ask for another agent. In my area Comcast recently boosted the speed of uploads to about double what it was.

---

### Post by jbeaunaux on 2008-07-23
Thanks to all who replied - all of this info will definitely help me handle the Comcast installation guy!

---

### Post by tamoneya on 2008-07-23
here is how i deal with comcast techs.

1. never let them out of your sight.  Even when they are working outside the house on a cable or something.  They have been reported to just drive off sometimes.  

2. Make your computer setup look as simple as possible.  Take out the router and just give them one windows computer to work with if you can.

---

### Post by stay gold! on 2008-08-14
that's ironic guys, i just re-went with comcast a couple days back and have had no problems at all with their customer service or anything. in fact, i have an account on twitter, and started speaking through one of the higher ups in their hq about some issues we had with on demand and the internet dropping out. low and behold they had someone here the next day fixing whatever it was that needed fixed.

not to mention the tech was a huge nerd and played wow and collected comic books.

---

### Post by bengoza on 2008-10-13
When they come to do the installation, don't they have to install something in Windows? So if you only have Ubuntu they won't be able to install their software to make it work?

---

### Post by wfp on 2008-10-13
Comcast sucks in my opinon. I Had Dsl for about 7 years and through all those years i had maybe 2 or 3 issues that were resolved very fast. I just recently moved, and the new house has comcast. The first day i moved i had to go out and buy a wireless adapter no big deal, installed it and then connected to internet, man was really impressed with the speed, that speed lasted for a few days, the next 2 months have been hell, even as i am typing this i am getting about 120kbs on a line that is 6Mbs. We have had the techs out numerous times. Seems like there are too many people who are using cable in our neighborhood. That is there number 1 excuse they always use. . I am pissed. Sorry had to vent some. Any way the good news is were switching to dsl in two weeks. Thank God

---

### Post by fragos on 2008-10-13
> **bengoza said:**
> When they come to do the installation, don't they have to install something in Windows? So if you only have Ubuntu they won't be able to install their software to make it work?

They use a web site which only works with with IE to get your specific modem and Ethernet port MAC address registered for use. For Linux you call Comcast support and they will initiate the modem registration from their end. Your Comcast broadband will only work with the MAC address of that specific port. If you add a wireless router it won't work unless you clone the MAC address into the router. Then all wired or wireless users will have Internet access.

---

### Post by bengoza on 2008-10-17
> **wfp said:**
> Comcast sucks in my opinon. I Had Dsl for about 7 years and through all those years i had maybe 2 or 3 issues that were resolved very fast. I just recently moved, and the new house has comcast. The first day i moved i had to go out and buy a wireless adapter no big deal, installed it and then connected to internet, man was really impressed with the speed, that speed lasted for a few days, the next 2 months have been hell, even as i am typing this i am getting about 120kbs on a line that is 6Mbs. We have had the techs out numerous times. Seems like there are too many people who are using cable in our neighborhood. That is there number 1 excuse they always use. . I am pissed. Sorry had to vent some. Any way the good news is were switching to dsl in two weeks. Thank God

Yeah I tried to get DSL but it's not available in my area. :mad:

---

### Post by bengoza on 2008-10-17
> **fragos said:**
> They use a web site which only works with with IE to get your specific modem and Ethernet port MAC address registered for use. For Linux you call Comcast support and they will initiate the modem registration from their end. Your Comcast broadband will only work with the MAC address of that specific port. If you add a wireless router it won't work unless you clone the MAC address into the router. Then all wired or wireless users will have Internet access.

If I have a dual boot setup can I let them do it in Windows and then just use Ubuntu all the time like I do now?

---

### Post by fragos on 2008-10-17
> **bengoza said:**
> If I have a dual boot setup can I let them do it in Windows and then just use Ubuntu all the time like I do now?

Yes you. Once Comcast has registered your cable modem and the MAC address of the Ethernet port connected to the modem your good to go until one of those things changes. If you have a router and have cloned your PC's MAC address in the router any device that connects over your LAN has access to the Internet.

---

### Post by gpsmikey on 2008-10-17
At least in our area (Seattle, WA), Comcast didn't seem to notice when I changed routers a while back from my SMC to the Linksys.  Simply power cycled cable modem and the router and all was well.  No issues from either Windoze or Ubuntu as near as I can tell.  There is no additional software installed on any of my computers for Comcast.  Some years ago, when it was @home, they did install a branded browser, but I knew that was going to happen and simply gave them one of my test machines with a clean install of windoze 98 on it (after I had imaged the drive).  After they left, I reloaded the drive from the image and "poof" their software was gone.  Never heard any complaint from them.

mikey

---

