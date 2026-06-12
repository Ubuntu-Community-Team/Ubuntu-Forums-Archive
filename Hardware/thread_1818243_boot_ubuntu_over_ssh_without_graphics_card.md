---
title: "boot ubuntu over ssh without graphics card"
date: 2011-08-04
forum: Hardware
---

### Post by umairalipathan on 2011-08-04
Hi,

Is it possible to boot ubuntu over ssh (from another pc) by disabling the graphics card? If yes, what should be a better way to disable graphics card?

---

### Post by Beacon11 on 2011-08-04
> **umairalipathan said:**
> Hi,

Is it possible to boot ubuntu over ssh (from another pc) by disabling the graphics card? If yes, what should be a better way to disable graphics card?

Wait... what? I'm sorry, I don't quite understand. SSH is a Linux program and as such isn't running until the computer is already booted, thus you can't ask a computer to boot via SSH (you might want to look at Wake-On-LAN). What are you asking about the video card?

---

### Post by umairalipathan on 2011-08-05
I want to measure the power consumption of a PC. Since graphics card is a measure source of power consumption, I want to completely disconnect it and access it over ssh from another PC. I will then measure the power consumption after the system is completely booted without the graphics card support. This is the only way I could get some idea how much the graphics card contribute to the power consumption.

---

### Post by Beacon11 on 2011-08-06
Ah, okay. Hmm... I'm not sure your motherboard will even boot without a video card connected, but you can try completely disconnecting the video card and booting. Assuming you have openssh-server installed, it will be running as soon as the computer finishes booting.

---

### Post by umairalipathan on 2011-08-07
The problem is that I cannot physically detach the video card on this board. The processor and the graphics cards are embedded into a single package. Is there any other way to disable the graphics card from linux? so that at the next boot, it doesn't load the graphics card?

---

### Post by IcarusR on 2011-08-08
Your system will not boot without graphics card even if you could disable it.
You may be able to ssh into it then unload the graphics module (linux equivalent of driver) but the card will still consume power.
You need to switch it off, which I don't think is possible.

---

### Post by umairalipathan on 2011-08-08
You are right. Is there any way to measure the power consumption of individual system components (e.g., processor, graphics card, network card etc)?

---

### Post by mikeyb5753 on 2012-04-28
> **IcarusR said:**
> Your system will not boot without graphics card even if you could disable it.
You may be able to ssh into it then unload the graphics module (linux equivalent of driver) but the card will still consume power.
You need to switch it off, which I don't think is possible.
 
Some motherboards will boot without a videocard attached.  I have done this in the past using smoothwall.  i'm not sure if ALL motherboards will let you do it though.  An onboard videocard will not consume much power anyway.

---

