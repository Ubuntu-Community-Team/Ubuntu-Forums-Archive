---
title: "Please help! Ubuntu 9.04 display not working"
date: 2009-04-23
forum: Hardware
---

### Post by necr0mancer on 2009-04-23
Hi all, let me first start by saying im a complete noob with linux, i just started learning it today, I download Ubuntu 9.04 Jaunty Jackalope Final today and installed it. Everything was fine until I started doing updates which ubuntu kept asking me to do. So i started doing the updates, and when i got to the ATI/AMD driver, i installed it (I have a radeon hd4870x2) then it asked me to restart my computer which i did, and now all of a sudden i have no display. It's all messed up and i cannot see or do anything. Is there a way for me to re roll to the previous driver and fix up my ubuntu properly. Dont forget, im a complete noob, so I dont know the commands, im assuming i would have to go to the recovery options and then to the command line console and type in something there to restore my drivers. Does any1 know how to fix this? Please help.

---

### Post by Johan de Jong on 2009-04-24
1. Reboot your computer and at the GRUB boot menu, choose 'recovery mode'. The system loads and you will be dropped at the prompt as root. For the next steps, make sure you are online (check this by entering 'ping [www.google.com]("http://www.google.com") -c5', control+C)

2. Use the apt-tool by entering:
apt-get remove --purge fglrx*
apt-get remove --purge xserver-xorg-video-ati
apt-get remove --purge xserver-xorg-video-radeon
apt-get install xserver-xorg-video-ati
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

In any case that works for me (also an owner of the ATI Radeon HD4870X2).

---

### Post by rtlong on 2009-04-27
> **Johan de Jong said:**
> 1. Reboot your computer and at the GRUB boot menu, choose 'recovery mode'. The system loads and you will be dropped at the prompt as root. For the next steps, make sure you are online (check this by entering 'ping [www.google.com]("http://www.google.com") -c5', control+C)

2. Use the apt-tool by entering:
apt-get remove --purge fglrx*
apt-get remove --purge xserver-xorg-video-ati
apt-get remove --purge xserver-xorg-video-radeon
apt-get install xserver-xorg-video-ati
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

In any case that works for me (also an owner of the ATI Radeon HD4870X2).

Thank you so much! Would you mind explaining a little of what that did? Was fglrx causing the problem?

---

### Post by Ed_496 on 2009-07-24
GREAT.   It worked also for me after looking at many other solutions.  Thanks a lot.   By the way, I have an ATI HD4850 512Mo.

For beginners like me, I can give some details. On the safe mode, you choose "Shell Prompt with Networking" and at the end of the process, just type "reboot" in the command line to reboot. And this time, choose the normal startup.

---

### Post by meshashiranjan on 2009-10-23
Hi,
I downloaded Ubuntu 9.04 and installed on Acer TravelMate 4050 laptop. I have LG 23" monitor attached to the laptop. The default resolution was low after installation. So I increased to the highest in the drop down menu of the Display Settings. It asked me that The virtual Display Area needs to be created. I said yes.
Then I rebooted. Now I get a white screen after full boot.
Please help. I want to 1st restore to the default original setting and then to the highest possible resolution to the screen.

Thanks in advance.
Regards,
Shashi.

---

### Post by swoody on 2009-10-23
meshashiranjan, welcome to the forum ):P

When you have a question that's not directly related to the thread at hand, please start a thread of your own. This will help keep things organized, as well as make sure your question gets the attention it deserves.

Thanks :)

---

