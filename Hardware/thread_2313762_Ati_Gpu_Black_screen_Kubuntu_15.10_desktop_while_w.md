---
title: "Ati Gpu Black screen Kubuntu 15.10 desktop while working"
date: 2016-02-15
forum: Hardware
---

### Post by nigro.orlando on 2016-02-15
Hi!
I'm running ubuntu 15.10 and I'm having this problem that then Gui freezes suddenly and the only thing I can do is to restart. 
I have a radeon r9 390 and I'm using open-source driver. I tried the proprietary ones but they have other similar problems. 
I hope someone can help me with this issues! I know Radeons driver aren't the best but beside this problem they work fine.

---

### Post by QIII on 2016-02-15
Hello!

As of a few months ago, the open source driver had not caught up to this new generation of adapters.  I recommend using the proprietary driver until this happens -- which I am sure it will.  "Aren't the best" is an understatement with regard to the Radeon driver and the R9 series.  Non-functional is more like it.  You can see what I found almost a year ago in this [blog article]("http://theleftcoastgeek.net/index.php/categories/2-amd-s-r9-290x-tested-on-ubuntu").

Exactly what problems were you having with the proprietary driver?  The more detail, the better.

---

### Post by nigro.orlando on 2016-02-16
Hello and thank you for your answer. You're right, that was very limited information :). "aren't the best" is a very unclear statement. 
I meant that from what I have read is radeon open-source not as good as Nvidia, or as proprietary Radeon. That's why I started using the proprietary as well but then after a while I had the same problem I'm having now: desktop freezing which was slightly different from now because it was  more like getting all black suddenly. I tried using CTRL+ALT+F1 to restart the GUI but it didn't work.

That's why I switched back to open-source which led to all desktop effects not working and I also noticed that if a watch a movie full screen with VLC then the CPU temperature increases up to 40/45 degrees, but this didn't happen before with the proprietary. I could live with these issues but then it started freezing again. The difference now is that it's not a black screen I get but it just freezes and ctrl+alt+f1 doesn't work now neither.

I have been using Ubuntus drivers manager to install and unistall both drivers but maybe there could be other ways to install proprietary in a better fashion? I must try proprietary one more time and see if I get that problem again.

---

### Post by QIII on 2016-02-16
If you have look at the driver wiki link in my signature, I've put some clear instructions for installing via the terminal in section 3.1.  I also describe adding hardware acceleration in section 5.

---

### Post by nigro.orlando on 2016-02-16
I'll follow the guidelines in the section. I have just noticed that I don't have a xorg.conf, is it normal? I guess the the difference between fglrx and fglrx-updates is that the second automatically checks for update. Is it then to prefer?

---

### Post by Mark Phelps on 2016-02-16
> **nigro.orlando said:**
> I'll follow the guidelines in the section. I have just noticed that I don't have a xorg.conf, is it normal? I guess the the difference between fglrx and fglrx-updates is that the second automatically checks for update. Is it then to prefer?

In answer - NO -- the second does NOT check for updates.

These two are there to provide different fglrx versions to select from -- but if you look closely, you'll often see that they are exactly the same version.

There have been problems in the past where folks selected fglrx-updates, but I don't use fglrx anymore, so I don't know if that's still true.

---

### Post by nigro.orlando on 2016-02-16
thank you, I'll go for the normal fglrx then. What should I do about the xorg.conf file? Just don't care and keep following the guidelines from the wiki?

I did the installation and everything worked fine. Now I'm using the fglrx and I will let you know if I encounter those problems again. Thank you for the good tips!

Hi again. I had the same problem now. I left the computer on for a while and I turned off the monitor. When I got back and turned the monitor on the desktop was frozen. Nothing helped but restart. 
It seems to be an issue both with open-source then with proprietary drivers. What to do?

Hello again :), an other symptom for the problem is that when the monitor shuts itself down, I can't get kubuntu back online. I only get black screen as if the monitor wasn't connected to the computer. Only restart is the cure but I'm doing this restart so often that this can't be good for the computer. 
The problems seems most of the time to be connected with inactivity. I mean that the problem occurs (almost) always when I return to the computer after a while.

By the way, this it the response from fglrxinfo:

```
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon (TM) R9 390 Series 
OpenGL version string: 4.5.13399 Compatibility Profile Context 15.201.1151

```


I must correct what I wrote above. Now it freezed twice while I was using it. First while watching a youtube clip, just 10 minuts after starting the Pc. And later while looking a movie

---

### Post by nigro.orlando on 2016-03-20
Hi, I have some news. I reinstalled kubuntu 15.10, and also the kernel 4.4 since I read the it should help with AMD graphic cards. I didn't install the fglrx, I would like to make the open source work. My problem now has nothing to do with performance, since the open source work very good, but I got black screen all the time. Not at boot but while using kubuntu. Why?

---

### Post by nigro.orlando on 2016-03-22
news again, I hope this can help others. Now I'm running debian Jessie. I installed the kernel 4.3, the newest mesa (which is default in ubuntu) and a package called firmware-amd-graphics. All from the backports. That made the open source driver work pretty nice with Gnome-shell. But I still had the freezing problem. What I'm testing now is to use this:

echo 'low' > '/sys/class/drm/card0/device/power_dpm_force_performance_level'

or 

echo 'high' > '/sys/class/drm/card0/device/power_dpm_force_performance_level'

I tried both yesterday and it didn't freeze. If it is so that this is the right solution then the bug is the "auto" level and maybe there was nothing wrong with the drivers. I mean **maybe** ubuntu with kernel 4.2 and open source driver from the install were fine and I only needed to do this to make it work.

---

