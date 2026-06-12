---
title: "Reset Bios Setup to Default, and ow ubuntu wont load???"
date: 2012-09-04
forum: Hardware
---

### Post by rfraser08 on 2012-09-04
I reset my NB200s bios to default by pressing f9. I was following a post I read in a forum saying this could help re-enable wifi.

After resetting the bios to default settings Ubuntu wont load. this doesnt make any sense to me! What might I need to change to make ubuntu work again?

thx

rob

---

### Post by cbanakis on 2012-09-04
I would focus on Boot order, and hard drive modes.

---

### Post by rfraser08 on 2012-09-06
Solved the problem. I turned off wifi in the bios. Only one disk in boot order anyways. Have my OS back, but still can't enable wifi.... 

Thx for the help!

---

### Post by Incarnadine on 2012-09-06
> **rfraser08 said:**
> Solved the problem. I turned off wifi in the bios. Only one disk in boot order anyways. Have my OS back, but still can't enable wifi.... 

Thx for the help!

Why did you turn your WiFi off in your BIOS? You need to have your WiFi enabled in your BIOS for Ubuntu to see and use it. Your WiFi setting should have no effect on the boot settings of your motherboard.

---

### Post by rfraser08 on 2012-09-09
I went back to the bios to try putting wifi on. Ubuntu still loads fine.

I experimented a little, and apparently it is when I changes the bios setting "Dynamic CPU Frequency Mode" to "dynamic" that Ubuntu seems to not load (perhaps it just takes a REALLY long time, and I lose patience before it loads). When I change "Dynamic CPU Frequency Mode" to "always low" Ubuntu loads just fine.


Will try and solve the wifi problem in another forum. 

Thx for the help

---

