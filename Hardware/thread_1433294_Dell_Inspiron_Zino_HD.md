---
title: "Dell Inspiron Zino HD"
date: 2010-03-18
forum: Hardware
---

### Post by IanH on 2010-03-18
I have a couple of these mini computers that I'm trying to set up as thin clients (edubuntu) for our lab. I've already gotten some of our old towers running as clients, so I know the server is running, but I can't make these work with either network boot or an etherboot cd. An Ubuntu live cd boots, but shows no network devices (Windows is able to connect to the Edubuntu server), making me think there's a driver problem (network card is a Broadcom Netlink gigabit ethernet card).

So: has anyone gotten these things working? Any suggestions on what to try next?

---

### Post by rpared01 on 2010-03-18
here an idea. here me out:

install ubuntu 9.10 on any pc that can connect to the internet, next download dells "Create recovery media" software, next copy the broadcom drivers that come with the stock ubuntu cd. Next run the Dell Recovery media cd creator and as you are creating the media add the drivers during the media creator process. See if that works.

---

### Post by IanH on 2010-04-01
Just in case someone else is having this problem and digs up this thread, here's the solution: In the bios, go to "advanced settings". Select "network card", and you'll see an "enable boot rom" option which is off by default. Enable this, and set the computer to boot from the network. Once I got this, the setup works perfectly (except for compositing (which I'm hoping may be fixed in 10.04).

---

