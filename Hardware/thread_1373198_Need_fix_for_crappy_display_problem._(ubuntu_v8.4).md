---
title: "Need fix for crappy display problem. (ubuntu v8.4)"
date: 2010-01-05
forum: Hardware
---

### Post by aschulz90 on 2010-01-05
Hi all, I'm pretty new to linux, or just restarting, I have pretty close to no idea about all the commands associated with the terminal but enough excuses I need some help with a problem. I installed an old FX 5900 Agp 8x into my comp earlier today and the automated "install proprietary driver" thing came up. I installed restarted and it seemed to be working very well other than **the refresh rate being limited to 50 or 51 htz.** I went online and found this
[http://www.kuxas.com/38/installing-proprietary-nvidia-drivers-on-ubuntu-linux.html](http://www.kuxas.com/38/installing-proprietary-nvidia-drivers-on-ubuntu-linux.html)

I ran the script and it pretty much failed after it turned the gdm off. so now whenever I start the computer I get this really sh**y looking display at 800x600 (funny thing though is it's running at 60htz). I really don't know what I did but i'd like to fix it. and maybe if possible, get the hardware acceleration of this card and refresh rate it can put out (75htz and I'm sure that's its max refresh rate). Thanks for any help, I look forward to becoming a more active member of the community.

---

### Post by aschulz90 on 2010-01-05
As an additional note I just did the following:
removed previous drivers.
rebooted.
hit ctrl + F1 and logged in as root.
typed in sh graphics.run (the driver install file renamed)
and I received this: "Can't open graphics.run"

---

### Post by sliketymo on 2010-01-05
Check to make sure you are using the correct drivers for your particular grafics card.A good place to start would be : System>Administration>Hardware Drivers.Try turning off Visual Effects ,and see what happens.

---

### Post by aschulz90 on 2010-01-05
The device is not recognized you see, it's not listed in the hardware drivers. 

I had the whole system working then I executed the following commands and I came upon this low graphics mode problem. 

I'm thinking about cutting my losses and installing 9.10.

---

### Post by aschulz90 on 2010-01-05
So I just installed 9.10, I'd like to leave this post open in case I find the same initial problem with the refresh rate.

---

### Post by sliketymo on 2010-01-05
> **aschulz90 said:**
> The device is not recognized you see, it's not listed in the hardware drivers. 

I had the whole system working then I executed the following commands and I came upon this low graphics mode problem. 

I'm thinking about cutting my losses and installing 9.10.

That does not mean that it is not recognized.It was meant to check if you were maybe missing something,like maybe the correct driver for your card ? Maybe you will have better luck with your fresh installation.

---

### Post by aschulz90 on 2010-01-05
With 9.10 the newest drivers and some kind of Nvidia app was installed, it's working brilliantly.

---

