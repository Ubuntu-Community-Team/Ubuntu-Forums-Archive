---
title: "Command to switch displays?"
date: 2008-11-02
forum: General Help
---

### Post by Aimevous on 2008-11-02
Hi,

I am running Ubuntu 8.10 on a laptop and I have an external 22" LCD connected to it.

Is there a command/script I can use to switch my display to the external LCD?

The reason is that when I get home and plug my laptop to my external display and switch on, it still uses my laptop's display.

If I use the default button for my laptop for toggling displays (Fn + F8), the display resolution would follow my laptop's default, which is wrong. 

Laptop = 1280 x 800
LCD = 1680 x 1050

What I'm doing now every boot up is to run the Nvidia X Server Settings and 
1. Enable Twin View on external display
2. Disable laptop display
3. Apply.

Kinda slow like this.

So is there a script that I can use to do all that above? Or even better, can it auto detect on boot up and switch automatically?

Thanks all in advance!

---

### Post by chino_sti on 2008-11-03
I have basically the same setup and question - am curious to see if this has been answered... I've tried searching a bit and haven't found a solution.  My laptop is almost always docked and it would be beautiful if it could auto-detect the displays and use my external monitors instead of the laptop display.

---

### Post by capput on 2008-11-20
I too am interested to find a way to auto-detect the external display and then disable the laptop's screen if connected.

Aimevous, I may be able to help a bit.  Instead of running Nvidia X Server Settings every time you start up, open a terminal and type:

 sudo nvidia-settings


Make the changes that you usually make and now the changes should remain after you reboot.

---

### Post by Aimevous on 2008-11-20
Oh.. if I set that and when I boot in without the LCD connected, will there be any problems?

---

