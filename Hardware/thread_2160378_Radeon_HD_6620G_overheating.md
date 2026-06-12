---
title: "Radeon HD 6620G overheating"
date: 2013-07-06
forum: Hardware
---

### Post by ephryn on 2013-07-06
Hi, I have a HP Pavilion dv7-6184ca Entertainment Notebook. The PC runs hot all the time, I've tried the drivers from AMD and fglrx no matter what I do it keeps running hot. I followed the guide from [Noobs Lab]("http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html") the laptop has the following:

Processor:	AMD Quad-Core A8-3530MX VISION A8 Technology from AMD
RAM:	6 GB DDR3
	AMD Radeon HD 6755G2 Dual GPU

Running Ubuntu 13.04 64-bit


let me know if more info is needed thanks for your help.

---

### Post by Jake_Gardner on 2014-02-18
I have the same problem.
Did you end up fixing this?

---

### Post by mastablasta on 2014-02-18
try 13.10 or perhaps even 14.04 (just try, since it's still under heavy development)

---

### Post by Jake_Gardner on 2014-02-18
I am trying 13.10 it has the same problem.

---

### Post by mastablasta on 2014-02-19
you might need latest beta (6.2) eventhough i htink A8 was supported by 13.10 kernel as wlel as opensource drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

why are you following 3rd party sites to install thing instead of official wiki?

by the way the overheating solution or energy management is in new kernel that will be in 14.04.but that goes mostly for opensource drivers. while if you use fglrx it should work in 13.10. if nothing else in AMD Beta drivers

---

### Post by soum_axetuirk on 2014-02-20
First of all i want you to explain about overheating reasons.
1.Uncontrolled GPU use
2.Uncontrolled CPU use

Sollution:
1.For laptops BEst is to use "Jupiter" for processor controlled use.hence the Developement is stopped for Jupiter.its not supported for 13.10.
You should use TLP on ubuntu 13.10
Install TLP first by terminal.then configure it for optimised laptop use.
[B] install TLP using the following commands:
[/B]```

sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw

```
Now reboot your system.
2.Then for graphics card you should install proper driver.
for AMD Radeon HD 6755G2 or any AMD Hybrid Graphics
(you may call it dual graphics or switcable graphics -AMD 6000 , 7000 series)
Install by this command on terminal
```
sudo apt-get install fglrx fglrx-pxpress
```
wait until catalyst control centre is installed.
3.Now open catalyst control centre in super user mode.(you cant change GPU in normal mode.)
Now change graphics card to Intel HD.then reboot your system.
[ATTACH=CONFIG]250531[/ATTACH]

We are done now.you wont get any over heating problem.I tested after 6 hour of use laptop stays cool.

---

