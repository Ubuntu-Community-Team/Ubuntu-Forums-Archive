---
title: "How to get Microdia SN9C201 Webcam to work on Ubuntu 8.10?"
date: 2009-03-16
forum: Hardware
---

### Post by adnansh on 2009-03-16
I have an Acer Aspire 5051 laptop and have been trying to get my webcam to work for the past couple of days have looked at many forums and have installed git with microdia but it still does not work. when I do lsusb I get 
adnan@adnan-laptop:~$ lsusb
Bus 003 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:6260 Microdia PC Camera (SN9C201)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Well after I followed instructions to install the driver...however the instructions say that there should to insert microdia.ko but there is no such file in my folder instead there is a sn9c20x.ko
so I changed the command to sudo insmod ./sn9c20x.ko but nothing seems to happen. Also earlier I found No Device when I tried to configure video settings on Skype...but now it does acknowledge that I have SN9C201 2.0 Webcam Driver but when I test it...no video..anyone can help me to check if my driver is actually installed or if it is the right one...I'm a newbie to linux so I don't know much coding...please let me know what I need to do step by step if possible...thanks!

---

### Post by restless on 2009-04-12
I have the same camera, and i tried the procedure you described, also without success...

thing is that the camera was working properly in ubuntu 8.04....makes me wonder...

anyone has solved this problem??
thanx
lor

---

### Post by bladerunnerfast on 2009-08-25
> **restless said:**
> I have the same camera, and i tried the procedure you described, also without success...

thing is that the camera was working properly in ubuntu 8.04....makes me wonder...

anyone has solved this problem??
thanx
lor

ive got an problem with mine also 
i got it to work on cheese but only inverted and i cannot undo it
its not the cheese effects tho
i tryed to get it to work on skype but i just got a blank output

---

### Post by tim.rittman on 2009-11-14
This website should be able to help you: [https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

---

