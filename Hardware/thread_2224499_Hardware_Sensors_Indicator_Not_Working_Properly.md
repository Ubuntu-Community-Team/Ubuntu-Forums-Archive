---
title: "Hardware Sensors Indicator Not Working Properly"
date: 2014-05-16
forum: Hardware
---

### Post by HaffaWaffle on 2014-05-16
I downloaded Hardware Sensors Indicator to get my temperatures of my PC. When I open the app, It says "No Active Sensors". I also found that I needed an app called "Im-Sensors" so that the Hardware Indicator app could read the sensors, but to no avail, I still cant read the sensors. I have been looking all over the place for an answer but everyone says something different.

I have a dual-core Gateway laptop with 4GB of RAM running the newest Ubuntu distribution from the site.

Can anyone help me get the app "Hardware Sensors Indicator" working properly?

---

### Post by deadflowr on 2014-05-16
Thread moved to  ***Hardware***

---

### Post by HaffaWaffle on 2014-05-16
Thanks, Im a NOOB at this forum.

---

### Post by gifford on 2014-05-16
Run sensors-detect in your terminal and choose yes to all.
Did you also install the Hdd sensor? If so, you must enable it by the following:
[COLOR=#333333][FONT=UbuntuRegular]edit /etc/default/hddtemp, replace RUN_DAEMON="false" by RUN_DAEMON="true" and reboot.[/FONT][/COLOR]

---

### Post by grahammechanical on 2014-05-16
did you install Indicator Sensors through the trusty (1404) PPA? It has only been available since 08/05/2014. Sometimes earlier versions work with a new release of Ubuntu. sometimes we have to wait until the developer brings out a version suitable for the new release of Ubuntu.

[https://launchpad.net/~alexmurray/+archive/indicator-sensors-daily](https://launchpad.net/~alexmurray/+archive/indicator-sensors-daily)

Notice this bug report and the reply by the developer.

[https://bugs.launchpad.net/indicator-sensors/+bug/1317001](https://bugs.launchpad.net/indicator-sensors/+bug/1317001)

The Ubuntu Software Centre also has Psensor which does similar things and I have had no problem with it on 14.04.

Regards.

---

### Post by HaffaWaffle on 2014-05-16
I will try both of your suggestions when I get off work in an hour.

---

### Post by HaffaWaffle on 2014-05-18
I ended up just installing Psensor and it does exactly what I needed, Thanks [ 						 							]("http://ubuntuforums.org/member.php?u=1087323")[**[COLOR=#000000]Grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323").
And thank you both for your help.

---

