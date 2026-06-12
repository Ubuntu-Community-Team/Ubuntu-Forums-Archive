---
title: "Unable to connect to the internet."
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by subhas123 on 2009-09-08
I have installed Ubuntu 9.04 in my system. The installation is successfully completed. But I am unable to connect to the internet. Please let me know the procedure about how to connect to the internet.

Thanks 
Subhas.

---

### Post by -Robert- on 2009-09-08
Did you read this documentation: [https://help.ubuntu.com/9.04/internet/C/index.html](https://help.ubuntu.com/9.04/internet/C/index.html)
Hopefully you can find the solution there.

---

### Post by tommcd on 2009-09-09
> **subhas123 said:**
> But I am unable to connect to the internet. Please let me know the procedure about how to connect to the internet.

You will have to give us more information. Are you using a wired or wireless internet connection? If it is wired, is it DSL, cable, dialup, or something else?
If it is wireless, tell us the name of the wireless card you are using and what wireless chip it uses. Also, if wireless, are you using encryption? If so, is it WEP or WPA encryption?
Open a terminal (applications > accessories > terminal) and post the output of these commands:
```
lspci
```
and
```
lsmod
```
The first will tell us about your hardware. The second will list the modules you have running. 
Telling us how you connect to the internet and the output of those 2 commands will help us be able to help you to get online.

And welcome to the Ubuntu forums!

---

