---
title: "Fan control on Lenovo Thinkpad X1 Carbon"
date: 2012-10-24
forum: Hardware
---

### Post by l8arrival on 2012-10-24
I am running 64-bit Quantal on my new Lenovo Thinkpad X1 Carbon, and everything works great, but the whine  from the fan is driving me crazy. If I do nothing at all, the fan stays  off (I'm using xsensors to see the speed ). Almost any real activity,  even light web browsing, turns the fan on and it quickly goes to 3200-3500  rpm. At these speeds, the actual noise level is not incredibly loud, but there is a very annoying high pitched whine along with the lower pitched base noise, which is driving me crazy.

So far, I have not been able to control the fan in any way. pwmconfig tells me that that manual control mode is not supported (there are no usable Pwm outputs), while thinkfan doesn't seem to be able to read the current temperature.

Has anybody been able to control the fan speed in Ubuntu 12.10?

Regards,
Colin

---

### Post by Tohasu on 2012-10-25
I have 12.04 on a mac mini and came across this fan utility.  Of course it is probably specific to mac hardware, 
but it cooled the mini down and then dropped the fan speed to something appropriate.  

The URL and instructions for getting it are below.   It can be configured and creates a logfile.


[http://mac.linux.be/content/fan-control-script-ubuntu-prevent-overheating](http://mac.linux.be/content/fan-control-script-ubuntu-prevent-overheating)

sudo apt-add-repository ppa:mactel-support/ppa
sudo apt-get update
sudo apt-get install macfanctld

---

