---
title: "Ubuntu Live CD on flash drive problem"
date: 2012-07-10
forum: Hardware
---

### Post by Hydera5 on 2012-07-10
Hello, I am currently running Ubuntu on a 16 GB flash drive.  I had to run out and do some errands so I closed the lid of my "Toshiba Satellite Computer" and left.  When I got back and opened the lid, the desktop loaded up with some error windows.  I cannot remember exactly what they said but it was something along the lines of not being able to connect to the casper -rw, the system, and HDD.  I then proceeded to log off of the account and I was met with a black screen with some error text.  I then had to hold down the power button to restart the computer.

Is there any way to change this from happening?  I would like to conserve a bit more power when I close the lid rather than running Ununtu full throttle.

Thanks!

---

### Post by gopherkiler9 on 2012-07-12
well you should be able to always go up to the start menu and hit postpone or something of the sort in order to make it sleep. I'll tell you now though, i've had my deal of issues getting my computer's 'personality' to work well with flashdrive linux. You may find that you'll run into problems a bit more often than if it was hard installed. 

I don't really have a suggestion as to where in the ubuntu terminal you should go and what codes to hit, but you would obviously need to create a queue to tell the computer that closing the lid means go to sleep. (not sure if thats a gui setting option or not yet)

my past experience with shutting my lid with various forms of linux has resulted in my computer never going to sleep and it actually crashing because of a dead battery. Odds are though, is your computer may have attempted to go into sleep mode, which caused a mis-communication with the usb ports. and since your entire OS is based off that drive, you lost contact with many important drive files. Kinda like losing the paths to the system 32 folder in windows while its running.



was everything hunky dory when you reboot the next time? all run smooth?

---

### Post by Hydera5 on 2012-07-12
> **gopherkiler9 said:**
> well you should be able to always go up to the start menu and hit postpone or something of the sort in order to make it sleep. I'll tell you now though, i've had my deal of issues getting my computer's 'personality' to work well with flashdrive linux. You may find that you'll run into problems a bit more often than if it was hard installed. 

I don't really have a suggestion as to where in the ubuntu terminal you should go and what codes to hit, but you would obviously need to create a queue to tell the computer that closing the lid means go to sleep. (not sure if thats a gui setting option or not yet)

my past experience with shutting my lid with various forms of linux has resulted in my computer never going to sleep and it actually crashing because of a dead battery. Odds are though, is your computer may have attempted to go into sleep mode, which caused a mis-communication with the usb ports. and since your entire OS is based off that drive, you lost contact with many important drive files. Kinda like losing the paths to the system 32 folder in windows while its running.



was everything hunky dory when you reboot the next time? all run smooth?

Yes, everything is fine after a reboot. I believe the computer unmounted the flash drive when it went to sleep/closed the lid. I guess I just have to keep it awake.

---

