---
title: "dv6000 shuts down when power is unplugged"
date: 2009-03-10
forum: Hardware
---

### Post by Caronj on 2009-03-10
Hi, im running Ubuntu intrepid on an hp dv6000 and everything has been running fine until I realized that when I unplug my power cable it powers down within 30 seconds. I have enabled laptop mode and played around with power settings and power.sh a little in an attempt to fix this but haven't found anything that worked. Any suggestions?

---

### Post by backtothefuture on 2009-03-10
Caronj i also have a dv6000 laptop and have been running Ubuntu with Intrepid Ibex with no problems. In fact had a power outage recently and was plugged into regular outlet with no ups attached, and the dv600 kept on going for several minutes. I shutdown ok with no problems and powered up again after the power came back on.
Does your battery indicate a full charge? I cab  dual boot between Vista and ubuntu and when in windows the battery icon in my tray shows 100% when i run it plugged into the power outlet.
Try taking out the battery and reseating it back in. Make sure you are fully charged. The battery condition could be getting bad and not holding a charge.

---

### Post by Caronj on 2009-03-10
I have several batteries and none of them charge, but all indicate 100% charge on the gnome power manager, I think this might be why it is not charging but I don't know how to adjust this. The LED on the AC cord lights up as well and everything otherwise seems normal

---

### Post by bigken on 2009-03-10
I have seen this before and it amounted to the mobo being faulty

---

### Post by Caronj on 2009-03-10
It charged fine from windows a week ago

---

### Post by bigken on 2009-03-10
so try it in windows now

---

### Post by Caronj on 2009-03-10
i no longer have windows other than in a virtualmachine but that wouldnt do me any good would it?

---

### Post by bigken on 2009-03-10
nope I had a hp dvXXXX wot ever model it was and would not charge battery so i replaced the mobo and all was well i think u need to install windows and eliminate its not ubuntu problem


process of elimination

---

### Post by Dark_Stang on 2009-03-10
What's your exact model? The dv60xx to dv64xx models do have a service alert on them because of motherboard issues. Normally it's only related to the wireless card not working correctly.

Go System > Preferences > Power management. Go to the On Battery Power tab. And set it to "Do Nothing" when "Battery Power is Critically Low."

While your battery is discharging run "acpi" several times in a terminal to see what it's reporting.

---

### Post by Caronj on 2009-03-10
it is a dv6200 CTO and you are right about the wireless card and I had that taken care of about 6 months ago when it was still under warranty so that is why I am reluctant to pursue a motherboard issue. 

Also I tried charging it with the power off briefly and this seemed to work as it held a charge for around 15 minutes or so. Also during this time i ran acpi -V and over the course of about 5 minutes it continued to tell me that it was discharging but maintained that it was 100% charged which is clearly wrong. It still does not seem to be able to charge while ubuntu is running

---

### Post by Dark_Stang on 2009-03-11
It's a 6200? Is it possible that your battery is bad? My laptop is a 6600 which is newer, and it's battery completely crapped out in January.

---

### Post by Caronj on 2009-03-11
ya its beginning to seem more and more likely to me that its a battery issue. I have a backup but ill have to wait to this weekend to get it and give it a try. Thank you for all of your help

---

### Post by Dark_Stang on 2009-03-14
How goes it?

---

