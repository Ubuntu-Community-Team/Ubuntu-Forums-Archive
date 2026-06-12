---
title: "Nvidia high level powermizer problem"
date: 2020-09-05
forum: Hardware
---

### Post by mm1379 on 2020-09-05
On kubuntu and ubuntu 20.04 and kubuntu 18.04,  I installed nvidia 390 driver.
When I change gpu to nvidia dgpu (The other one is intel) and make a little a change in desktop such as moving the cursor or a window,  nvidia setting shows rising clock speed and higher powermizer level that causes high power consumption and more heat.
If I do not do anything with my laptop (not to moving cursor and etc.) The two factors i mentioned above (clock speed and powermizer level) will reduce.
This clockspeed shouldn't be normal in idle mode.formerly nvidia diver itself could understand when change the power.
What can I do?
Thanks in advance

---

### Post by mm1379 on 2020-09-08
Any idea?

---

### Post by Yellow Pasque on 2020-09-09
I don't see a problem. From your description, the GPU ramps up when it's doing work and returns to idle state when it's not. What did you expect to happen?

---

### Post by mm1379 on 2020-09-09
> I don't see a problem. From your description, the GPU ramps up when it's doing work and returns to idle state when it's not. What did you expect to happen?

Thanks for reply.
Moving cursor cause nvidia gpu power and clock jumps is that normal?

---

### Post by Yellow Pasque on 2020-09-10
I don't know. Sometimes, my Nvidia desktop card will stay at the highest state for a bit when seemingly nothing is changing on the screen.
Out of curiosity, what specific GPU(s) are we dealing with here?

---

### Post by mm1379 on 2020-09-10
Nvidia gt 525m /Intel hd 1000

---

