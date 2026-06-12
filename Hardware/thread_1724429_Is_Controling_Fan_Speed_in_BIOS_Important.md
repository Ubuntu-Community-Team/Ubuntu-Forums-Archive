---
title: "Is Controling Fan Speed in BIOS Important?"
date: 2011-04-08
forum: Hardware
---

### Post by uss on 2011-04-08
Hi,

I want to buy a new PC and I don't know what motherboard to choose. I have two choices: [ASUS P8P67 Deluxe]("http://www.asus.com/product.aspx?P_ID=FpufhQASBFHNvccl") and [ASROCK P67 Extreme6]("http://www.asrock.com/mb/overview.asp?Model=P67%20Extreme6"). It appears that ASROCK has more features. But there is something that worried me: According to [this page]("http://www.overclockers.com/asrock-p67-extreme-6-motherboard-review/") Extreme6 doesn't have any fan control in BIOS and you could control them through a Windows program:

> The fan controls are not automatic and are not fine-grained. For better  fan control, you’ll have to use ASRock’s software from within windows.  In BIOS, you can select a speed but that’s about it.
But P8P67 Deluxe allow you to control fan speed through BIOS (see [this page]("http://www.legitreviews.com/article/1500/5/")):

> ASUS has also placed all of the fan control options here. The CPU Fan  minimum can be set as low as 200RPM and you can place a maximum speed of  20% to 100%. For example, if you set the CPU upper temperature at 60  degrees Celsius and the CPU Fan maximum duty cycle at 40%, once the CPU  hits the 60 degrees Celsius the fan will run at 40% until the CPU hits  75 degrees Celsius where the fan will operate at 100%. Is it important? Is it worth because of this feature I buy the ASUS one? I want a silent PC so It's important for me that fans doesn't work at full speed all the time when I'm in Linux. Does anybody have a good or bad experience about these MB? I know there are some programs in GNU/Linux that can control fan speed but I didn't work with them.

---

### Post by Grenage on 2011-04-08
Personally, I'd take the BIOS automatic fan control over software, and buy a board that offered such (the Asus).

---

### Post by uss on 2011-04-08
> **Grenage said:**
> Personally, I'd take the BIOS automatic fan control over software, and buy a board that offered such (the Asus).
Thanks for your quick reply. It's grateful.

---

### Post by Grenage on 2011-04-08
No problem; I've had a few Asus Deluxe boards, and I've been very happy with all of them.

---

### Post by uss on 2011-04-08
Thanks again. Now I don't have any hesitation. I will buy ASUS.

---

### Post by Yellow Pasque on 2011-04-08
> According to this page Extreme6 doesn't have any fan control in BIOS 
I don't believe the article is saying it has absolutely no fan control, but it does have fan control that you have to set yourself and no easy auto-tune/profiling.
If the sensor chip on the Asrock board was supported in lm-sensors (not a safe assumption with such a new board), one could probably turn off the BIOS fan control and tune the fan using the pwm-config script in Linux just like the proprietary Windows software allows.

I just wanted to add that for the sake of those Googling..

---

