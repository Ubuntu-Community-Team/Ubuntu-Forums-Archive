---
title: "Poor performance with acer laptop (intel i5, gtx950m)"
date: 2020-03-22
forum: Hardware
---

### Post by nightfever on 2020-03-22
I'm getting poor performance with my acer f5 laptop on linux. It uses an intel i5 7th gen cpu and gtx950m graphics, with 8gb of ram. 
By poor performance I mean animations are choppy and actions are sometimes slow (like opening an app or menu). Youtube videos are pretty much unwatchable. Every app that uses hardware acceleration is slow.
Since I dual boot with windows 10, which works smoothly and without any of these issues, I pretty much excluded the possibility of a hardware issue. I do however notice that the cooling fan works harder on linux, on windows it's pretty much silent unless there's something intensive. Temps are ok, around 65C. I cleaned the fan and replaced the thermal paste just to be sure.
I have tried all the nvidia drivers, and switching to the intel integrated gpu. I've ran out of options.

---

### Post by crip720 on 2020-03-22
Would help if you mention which Linux and version, unless you have tried most of them.  65C is a bit up there, unless only when doing harder work or in a very warm room, would like to see it less.

---

### Post by nightfever on 2020-03-22
> **crip720 said:**
> Would help if you mention which Linux and version, unless you have tried most of them.  65C is a bit up there, unless only when doing harder work or in a very warm room, would like to see it less.
The linux version is pretty much irrelevant. I'm either working on ubuntu or arch (always the latest versions, updated). Currently on 19.10.

---

### Post by crip720 on 2020-03-22
Don't know enough, but have used both low end intel and am using a 4th gen i7 now and both have worked very well.  Would try googling with ubuntu and your cpu and/or computer model to see if any one else has had poor performance.

---

### Post by CelticWarrior on 2020-03-23
> **nightfever said:**
> I have tried all the nvidia drivers, and switching to the intel integrated gpu. I've ran out of options.

It would be interesting to know exactly HOW did you manage to try all the drivers... Anyway, even if you currently have a proper Nvidia driver installed (very unlikely) and yet you didn't disable Secure Boot (or used the specific tool to sign the drivers), the installed drivers are as good as no Nvidia drivers at all.

---

### Post by nightfever on 2020-03-24
Driver Manager gives me a few options: nvidia-435, nvidia-390, nvidia-430 and nouveau. So I tried them all. Eventually went back to 435 and even switched to the intel integrated graphics. Secure boot is disabled.
However I noticed a strange thing when I monitored the resources with htop. I get high cpu usage with one of the cores (almost 100%) while the others are sitting at lower values, around 10% or less. This is with firefox open, writing comments on facebook (with severe lag).

---

