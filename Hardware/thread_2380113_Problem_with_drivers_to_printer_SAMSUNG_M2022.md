---
title: "Problem with drivers to printer SAMSUNG M2022"
date: 2017-12-13
forum: Hardware
---

### Post by mrowa2 on 2017-12-13
Hello.

Few months ago I installed drivers for my printer SAMSUNG M2022. Everything have been working great for months. One day it just stopped working without reason. Printer works correctly on another computer.The problem is on my Linux Ubuntu. 

I wanted to repair this problem by myself:
- I installed again drivers but in terminal i see: "The same version of Print driver is already installed"
- I deleted manually printer from "Printers". So actually my "Printers" are empty. When I click "add" button I don't see my printer (of course it is connected to my laptop and turned on)

Could you help me please?

---

### Post by ajgreeny on 2017-12-13
Network or USB printer? If network printer you may need to add the printer's IP somewhere in the setup for it to be detected, and it is worth giving it a static IP, as without that the problem you have seen is possible if the router is rebooted or loses power.

Have you tried going to cups installation at [http://localhost:631/](http://localhost:631/) which may be able to figure this out

---

### Post by mrowa2 on 2017-12-13
It's USB printer

---

