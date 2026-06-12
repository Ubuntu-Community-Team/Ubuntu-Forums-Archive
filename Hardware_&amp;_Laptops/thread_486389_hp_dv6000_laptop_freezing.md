---
title: "hp dv6000 laptop freezing"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by dfreer on 2007-06-27
Hi everyone,
  I'm currently running Ubuntu 7.04 AMD64 on my hp dv6000 laptop, core 2 duo, nvidia geforce go 7400 with 1 GB of RAM. I'm using the nvidia-glx-new driver, along with beryl. I am experience random freezing, where nothing works EXCEPT the mouse, which moves fine. Weird, huh? The mouse cannot click on anything, and the system does not respond to keyboard input (including <Ctrl><Alt><Backspace>). I have to hold down the power button for the system to hard reboot. Any ideas, or ways to troubleshoot?

---

### Post by Ayuthia on 2007-06-28
My two thoughts is that it could be either beryl or your laptop is getting to hot.  You might get a temperature applet to monitor the temp or you could turn off beryl and see what happens.

---

### Post by sureinlux on 2007-06-28
Hi there,
 I also had the same experiences with Compaq Presario V3000au. Experienced the same random freezes, but now rock solid with the boot options:
```
idle=poll
```

---

### Post by dfreer on 2007-06-29
> **sureinlux said:**
> Hi there,
 I also had the same experiences with Compaq Presario V3000au. Experienced the same random freezes, but now rock solid with the boot options:
```
idle=poll
```

hmmm, well since hp owns compaq, maybe this will help out. I'll give it a try, but since the freezes are random it may be awhile till I can prove it works lol. Where did you get the idea to do this from, do you remember (and what does it do)?

---

