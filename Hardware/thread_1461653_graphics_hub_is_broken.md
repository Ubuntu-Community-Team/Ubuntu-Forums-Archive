---
title: "graphics hub is broken"
date: 2010-04-24
forum: Hardware
---

### Post by termin on 2010-04-24
okay so the other day, i had to format the system because of another problem. but all of a sudden, my monitor blinked and then it said "no signal" so i went to the back of my PC and saw the monitor plug and i pulled it to the other hub but now it says "Ubuntu is running in low graphics" and it slows down my PC a lot. also, i can't enjoy my games and videos because of this. so please help me. i tried 

lspci | grep VGA 

and it says:
 " 00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
02:04.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)"

i am currently running the nvidia thing. if i cant fix the hub, can i at least make the graphics compatible now? 


Thanks!

---

### Post by Mewshi on 2010-04-24
By "Hub" I'm assuming you mean a VGA plug?

If that's the case, and you switched to the NVidia port, then installing the nvidia drivers SHOULD fix it :)  Let me know how it works out!

---

### Post by jerome1232 on 2010-04-24
So which vga port is your monitor cable plugged into now?

The integrated graphics (will be higher up, closer to your power supply than the other one) or your nvidia card (lower down where there are alot of horizontal metal slots where other cards could stick out)

---

### Post by termin on 2010-05-03
guys i fixed it. i just needed to install the driver and then change the BIOS configuration so the video display is PCI thanks for your help

---

