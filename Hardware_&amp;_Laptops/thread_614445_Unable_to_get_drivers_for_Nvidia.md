---
title: "Unable to get drivers for Nvidia"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by xracer on 2007-11-15
Hello,

I have just installed Ubuntu in a sony laptop, and after a few bumps on the road everything is running smoothly, however there is only one minor problem i can't get my graphics card drivers NVIDIA GeForce 8400M GT, does any one knows where i can get them or how to configure it so that i can get off this 800x600 res :(

Please do take this with a grain of salt I am kind of new to Ubuntu and Linux overall. just got tired of Vista and went this way.

THanks for your help.

Xracer

---

### Post by Daelyn on 2007-11-16
> **xracer said:**
> Hello,

I have just installed Ubuntu in a sony laptop, and after a few bumps on the road everything is running smoothly, however there is only one minor problem i can't get my graphics card drivers NVIDIA GeForce 8400M GT, does any one knows where i can get them or how to configure it so that i can get off this 800x600 res :(

Please do take this with a grain of salt I am kind of new to Ubuntu and Linux overall. just got tired of Vista and went this way.

THanks for your help.

Xracer

Before we get down and dirty.
Tip1: Read some HOW-TO's and configure some easy stuff to get familiar with commands. You need it!
Tip2: Search the forum for any known issues you might currently experiencing.

Solution to your GFX issue.

Drop to console:
```
 sudo apt-get install nvidia-glx-new 
```
to get the nvidia driver.
```
 sudo nvidia-glx-configure enable 
```
to enable the use nvidia driver.

Restart X by pressing CTRL+ALT+2xBACKSPACE 

```
 sudo nvidia-settings 
``` 
and chose applicable resolutions/frequencies etc.

---

