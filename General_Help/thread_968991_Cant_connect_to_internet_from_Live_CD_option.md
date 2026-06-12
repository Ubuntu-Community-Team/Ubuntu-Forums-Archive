---
title: "Cant connect to internet from Live CD option?"
date: 2008-11-03
forum: General Help
---

### Post by Ghot on 2008-11-03
Burned .iso to CD no problem, rebooted, Ubuntu LIVE CD option, no problem.....I get to Ubuntu desktop and click the Firefox icon and in about 15-20 seconds I get notice (in upper right corner of desktop) that I have been disconnected.

1. I have 20Mb/s // 20Mb/s FIOS connection (Verizon)
2. I have no router or modem...I have Cat5e running straight from
   the ONT (Optical Network Terminal) which is like a telco box
   mounted outside.
3. Firefox works fine in Windows XP

Question:  Do I NEED to **INSTALL** Ubuntu 8.10 to achieve a working internet connection?

**Is it even possible to have a working internet connection from only the "Live CD" option?**

I know this is a noob question, but it is very important to me as I (at this time) have to log off the Live CD and back onto Windows XP to even ask for help on the forums.

I dont know if it matters, but I have a ASUS M2N32-SLI Deluxe WiFi motherboard (the wireless is disabled in the BIOS, on purpose) AMD X2 64 CPU and a GTX280 vid card.

The motherboard has NVIDIA nForce 590 SLI MCP built-in dual Gigabit MAC with external Marvell PHY.

I just checked the BIOS and there is NO boot AV.

Almost forgot....in Windows XP I run Zonealarm firewall....could this be preventing internet connection form Live CD Ubuntu 8.10?

---

### Post by Ghot on 2008-11-03
I'm absolutely new to Ubuntu, even tho i have all the copies since 5.10

I really need an answer to this question please.

---

### Post by thestig_992 on 2008-11-03
You dont need to install ubuntu to get internet connection, however, your drivers for your wifi might not work in the live cd. this does not mean that they wont work in the real install, i had the same issue, and a real install fixed everything. Check your wireless card on google to see if it is compatible with ubuntu.
In the meantime, however, an ethernet cable should give you a connection.

Also, zonealarm cannot block your ubuntu wireless, windows is not running at all.

---

### Post by mixmaster on 2008-11-03
You should be able to connect to the internet from a live CD.

I had exactly the same problem with the RC beta and I never could get the thing to work.  It basically refused to offer me an eth0 device. 

I haven't had a chance to try the final release yet.

---

### Post by Ghot on 2008-11-03
**I'm not using the wireless.....it is disabled in the BIOS by me**....I am using a hardwired connection (CAT5e) straight from the verizon exterior box (ONT) to the back of my computer.  When I click the Firefox icon in Ubuntu it goes to the Ubuntu page then the little icon in upper right corner of desktop says:  Your internet is now disconnected.

Every time since 5.10 that i've tried the Live CD option i've had this same problem.....on different comps too...but all had NVIDIA chipsets and were ASUS.

I tried eth 0, eth 1 and even tried Wired....no joy.

This is a stand alone non-networked comp.  I read the entire help file concerning internet problems and again ...no joy.

Without knowing what I was doing I tried to edit the Wired connection option and even put in the MAC address for my LAN chip...no joy.

Also, as per the help file i opened the terminal and typed ifconfig eth 0, or w/e it told me to type  and the results from that command didnt match what the help file said I should see.

---

### Post by Ghot on 2008-11-04
bump.....I need help with this...after all I've only had ONE cup of linux so far  :)

---

### Post by ugm6hr on 2008-11-04
Does this "disconnected" message only appear when you start Firefox (i.e does network manager suggest you are connected until then)?

If so - boot from LiveCD (with cat5 cable connected):
```
ifconfig
lshw -class network
lspci
```

Copy & paste the responses here.

---

