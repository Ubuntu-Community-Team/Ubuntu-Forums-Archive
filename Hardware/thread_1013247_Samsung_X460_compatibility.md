---
title: "Samsung X460 compatibility"
date: 2008-12-16
forum: Hardware
---

### Post by Dr.Utnubu on 2008-12-16
Has anybody tried to install Ubuntu on the Samsung X460 laptop?
I would like to know if there are any issues with hardware and drivers.
Is there a chance to get the fingerprint reader working?

I'm thinking about buying this laptop.

Please tell me your experiences.

Thanks in advance.

---

### Post by davey t on 2008-12-16
Yes

I'm writing this on a samsung x460 running Ubuntu right this second. Its great but for my eyes are killing me. The FN brightness control don't work and the screen is stuck on maximum brightness which rinses the battery and really hurts!

Most other stuff seems to work ok. Skype was having some problems with the sound card but it seemed to work fine for all other programs. Webcam seems to work. Graphics card drivers installed ok. Bluetooth is there but i haven't tried it yet. Not sure about hdmi. Anthing you want me to try just ask 

If you are thinking of buying an x460 then why don't you help my try to solve the brightness control problem. I'm going to have to revert back to windows otherwise because its just unusable at the moment. 

-dave

---

### Post by Dr.Utnubu on 2008-12-17
Hi Dave,
thanks for the information. My plan is to use the laptop generally with Vista. But after 1 or 2 years I will go to a new machine and use the old one (e.g. X460) with Ubuntu.
So there is plenty of time for the linux community to solve issues like the screen brightness.
Unfortunately I am not a linux guru, so my only chance is to look for solutions provided by others who are technically more linux savvy.

I think I'll buy the X460 soon. Hopefully I'll find the time to install Ubuntu as a 2. OS on the X460 next week.

But we can stay in touch on this topic.

regards,
Tom

---

### Post by Dr.Utnubu on 2008-12-19
Does anybody know how to switch to "silent mode" on Ubuntu?

---

### Post by terribletrouble on 2008-12-19
What is silent mode?

Volume off?

---

### Post by Dr.Utnubu on 2008-12-19
If you boot up the original Vista you can toggle with a FN key combination between different performance modes: silent, normal, speed.
in silent mode the cpu clock speed is reduced and therefore there is less fan noise.

---

### Post by except on 2009-04-17
I've been running Ubuntu on my X460 successfully over the past week. Brightness control does not work but you can use a little script to set the screen to whatever you want. This is the script I use:

```

#!/bin/sh
gksu chvt 2
if [ "$1" ]; then
  BRIGHT=$1
else
  BRIGHT=60
fi
echo $BRIGHT | sudo tee /proc/acpi/video/NVID/LCD/brightness
sudo chvt 7

```

This allows you to pass a value to the script like say "Brightness 80" and it will use 80, else it will use 60, a nice value.

Otherwise, the fan is on at all times but it's a quiet one, I hope to find a control for that one... the rest seems to work as intended.

---

### Post by Ioky on 2009-04-23
I wonder can you map your key manually to set the brightness. you know maybe right a problem yourself and do this.

---

### Post by lesscode on 2009-05-03
Dave: did you get brightness working yet? I am planing to buy this laptop soon. Please let me know.

Dr.Ubuntu: you plan to use your laptop in 1 or 2 years. Why bother to ask question know?

---

### Post by chavezsa on 2009-05-09
I'm a relatively new Ubuntu user; I have Ubuntu 9.04 as a dual boot option on my X460. Again, no Fn+up/down brightness control. Sound adjustment (Fn+left/right) works though.

I tried installing a newer driver from nVidia, but that removed brightness control altogether for me. Reverting to the original driver put me back to manual control via the brightness app.

No biometric support yet; I'd love to see this work eventually, but I'd be happy with Fn key brightness control.

---

### Post by lesscode on 2009-05-27
I found out another way to add brightness applet. 
Right click on your panel--> Add to panel --> Brightness Applet.

It works! Nice.

---

### Post by elrod on 2009-06-19
I'm having an issue with the keyboard sometimes, seemingly at random, pasting my copy buffer into the middle of something I'm typing. Or in a web form suddenly tabing to another input field. Anyone else see this? What keyboard model and layout are you using?

---

