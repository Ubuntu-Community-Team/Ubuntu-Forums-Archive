---
title: "Driver for ATI Radeon IGP 345 video card"
date: 2013-02-20
forum: Hardware
---

### Post by franrc on 2013-02-20
Hi, 

  I have an old Compaq Presario with ATI Radeon IGP 345 video card. I have just installed Lubuntu 12 but the improvement is still slow. I have read a little about I think the system is using "Radeon" open source driver and acceleration is not working properly.

  I have thought about installing "Catalyst" driver but my video card is not supported by the driver version for Lubuntu 12, what can I do? May I have to install Ubuntu 8? Is there any other way to make my video card working properly?

  Thanks in advance.

---

### Post by Yellow Pasque on 2013-02-20
What are the other components of your machine? HOw much RAM, etc.

What is output of glxinfo?
```
sudo apt-get install mesa-utils
glxinfo
```

---

### Post by ajgreeny on 2013-02-20
The open source driver that was installed and used when you installed the OS is your only option with that old ATI card.

**DO NOT ATTEMPT TO USE THE CATALYST DRIVER**.  That will make matters worse as it does not support that card, as you say, and you will have to uninstall it anyway.

What exactly do you mean by "acceleration is not working properly"?  I run Lubuntu 12.04 om an old Acer Travelmate with celeron cpu, ATI 9000M card, and 512MB ram, and that runs fine; not a speedy machine I agree, but very usable.

---

### Post by Yellow Pasque on 2013-02-20
> **ajgreeny said:**
> You are stuck with the open source driver.
Poor choice of words. The open source driver works just fine for a card this old...

---

### Post by ajgreeny on 2013-02-20
> **Temüjin said:**
> Poor choice of words. The open source driver works just fine for a card this old...
Actually, you're right, it was a very bad choice of words!

As well as the laptop I spoke of I also have an old desktop machine with an ATI 9200SE card for which the open source driver is the only option, and it is great for everything that card is capable of doing.

I am also aware that some users of new AMD cards are using the radeon driver and not the proprietary driver as they find it is much less trouble, and if they are not gamers it is absolutely fine.

Original post of mine now amended accordingly to sound somewhat better!

---

### Post by franrc on 2013-02-21
Well, the fact is that my PC is working better using a privative O.S. that we all know than using my dear Ubuntu...
The response is quite slower in Ubuntu and the CPU usage is normally at 80%
I thought that installing Catalyst driver would make ubuntu to have a better performance.
Any help??

---

### Post by Yellow Pasque on 2013-02-21
> Any help??
[http://ubuntuforums.org/showpost.php?p=12519864&postcount=2](http://ubuntuforums.org/showpost.php?p=12519864&postcount=2)

---

### Post by franrc on 2013-02-21
Sorry Temüjin :)
Here is attached the exit of glxinfo
Thanks in advance

---

### Post by Yellow Pasque on 2013-02-21
The glxinfo looks good.
> the system is using "Radeon" open source driver and acceleration is not working properly.
How do you know it's not working properly?

---

### Post by franrc on 2013-02-22
I said it's not working fine because the response to user events is slow and because the CPU usage is always at 70-80%
Something's going wrong, I thinks it's a problem of Radeon Driver with my video card so I wanted to install the propietary driver.
May I tune driver configuration? Is there any guide about it?
If it is not a problem of the video card, what can be causing the problem?

---

### Post by franrc on 2013-02-26
Any idea? How can I increase the improvement?
Practically I can't use Abiword, it works reaaaally slow...

---

