---
title: "laptop crashes when closing the lid"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by rares.pop on 2008-03-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196979](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/196979) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

I have the following configuration:
- HP Compaq 8510W laptop
- Dell 1908 FP external monitor
- docking station for plugging the laptop

I installed Ubuntu 7.10 Gutsy Gibbon (all updates installed) on this configuration and i'm facing a crash when i'm closing the lid of the laptop or i plug out the laptop from the docking station.

It's very interesting that if i'm using the laptop without the external monitor everything it's working perfectly, i can close the lid and plug out the laptop without crashing. But when i'm using the external monitor with or without the docking station, it's crashing.

I have installed NVIDIA Driver version: 169.07 and X Server Version: 1.3.0

Regards,
Rares

---

### Post by arimaniac on 2008-03-03
Hello there

I also have a 2 screen config (desktop):
2 X LG 1910S + Nvidia graphics.
Same happens when I press Suspend.

Do try to press Suspend and reply of what happens. :|

Just a notice: Keep in mind that support  of a dual screen config has been 
implemented on this very last release of Ubuntu. 
There is yet many work to be done.

Suspend problems are a known issue... :(

I would recommend to  to disable the Suspend when you close the 
lid if you haven't already done so.

Find it in **System>Screensaver>Power>General**

About the docking station I wouldn't know...

Hope this helps...:)

---

### Post by rares.pop on 2008-03-03
Hi arimaniac,

it happens the same when i suspend my laptop, it just crashes and i have to power it off.

I disabled suspend when i close my lid but the behaviour is still the same, the laptop crashes.

Thanks for trying to help,
Rares

---

### Post by arimaniac on 2008-03-03
Hi Rares

Glad to be able to help!

I also found this from other users

[http://ubuntuforums.org/archive/index.php/t-587390.html]("http://ubuntuforums.org/archive/index.php/t-587390.html")

Check it out...

---

### Post by rares.pop on 2008-03-03
arimaniac,

i followed the solution from the thread you send me, but none of them is working.
For my laptop it's working everything if don't have any external monitor attached.
If i attach an external monitor the trouble begins.

Thanks again for trying to offer solutions,
Rares

---

### Post by viocudinti on 2008-03-05
Hello,

I have the same exact model and the same exact issue.
One thing to mention is that it does not actually crash, just that the screen remains blank (or in some suspend state). I can connect with ssh on it though and it looks ok in the background.

---

