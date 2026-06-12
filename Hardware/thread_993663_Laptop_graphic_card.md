---
title: "Laptop graphic card"
date: 2008-11-26
forum: Hardware
---

### Post by Micromat on 2008-11-26
Hello,
i have a problem with driver ... my graphic card work but i think than not install because many graphic option are block...

check this and explain to me...

i use Ubuntu 8.10

My laptop is HP pavillion DV6827CA

[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=fr&cc=fr&product=3695072&lang=fr](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=fr&cc=fr&product=3695072&lang=fr)

»  	Mobile Intel 965 Express Chipset Family Video Driver
»  	NVIDIA GeForce Series Video Driver 

how to check if driver exist for linux and how to install...
sorry i am a real newbie on linux ... but i am open to change my windows to linux...

thanks
Micromat

---

### Post by CholericKoala on 2008-11-26
First you would need to find which video card you have:  Intel or Nvidia.  If you have Nvidia, drivers are not a problem.  You can download envyng and it will do it for you, or download the nvidia driver from the nvidia website.  In terminal, do "sh <executable file here.sh>" and it'll be automatic from there.

I'm not sure if Intel has drivers needed to be installed.

---

### Post by vandorjw on 2008-11-26
[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2800&OSFullName=Linux%2A&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2800&OSFullName=Linux%2A&lang=eng&strOSs=39&submit=Go%21)

Go there if you need the intel driver.

if have have an Nvidia card, open up the terminal (command prompt) and type this.

sudo apt-get install envyng-core envyng-qt

this program will install the lastest drivers for ATI and Nvidia cards.
(except for the ati X1050 because it sucks)

---

