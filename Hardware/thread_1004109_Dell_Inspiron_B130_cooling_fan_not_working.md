---
title: "Dell Inspiron B130 cooling fan not working"
date: 2008-12-06
forum: Hardware
---

### Post by pcfixer on 2008-12-06
I am using version 8.10. I can not get the cooling fan to run like it does in Windows. What do I need to make this happen?:KS

---

### Post by frankleeee on 2008-12-06
in synaptics is i8k and gkrellm if you install both you can control the fans and the temps. this link will help you do everything but the 5th command then open gkrellm and look for plugins click on i8k and this should work. I have gkrellm in the sessions startup to auto start the fan monitoring. You could just follow the links instructions and add the swallow applet but I found it to be unreliable on my computer, in that the 5th command has set temps that I am not familiar enough with to mess with whereas gkrellm is pretty straight forward once you figure it out.

---

### Post by pcfixer on 2008-12-07
Found the apps and installed them. The fan will run now. It comes on around 138F and cuts out at 120F. Is this normal or should it run cooler? And if so how can I adjust it? Thanks a million.

---

### Post by frankleeee on 2008-12-07
> **pcfixer said:**
> Found the apps and installed them. The fan will run now. It comes on around 138F and cuts out at 120F. Is this normal or should it run cooler? And if so how can I adjust it? Thanks a million.

If you installed gkrellm open it right click on it and click on configure if in top area if the fans and temps are showing just a right click will open the config gui go to plugins-i8k-setup should be in Celsius then go to temp and adjust to you hearts content, make sure you read the about stuff. You have to mess around with this application to understand it, since it offers a lot of things, the THM portion which I don't remember how I got working will display in Fahrenheit, but keep the fan controls on Celsius unless you adjust the fan temp sensors to read Fahrenheit. If you want to have gkrellm auto open on boot up go to sessions and just put gkrellm in the name and command and I put Monitor for Cpu, memory, disks, network, mail in the comment. I have the fans set to come on at 35c low and 40c high lower then is generally needed but the laptop doesn't run hot in general. the temps you have are okay I believe but I like mine a little lower.

---

