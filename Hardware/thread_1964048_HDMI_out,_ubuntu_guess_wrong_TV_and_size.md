---
title: "HDMI out, ubuntu guess wrong TV and size"
date: 2012-04-23
forum: Hardware
---

### Post by hateregistering on 2012-04-23
I am running

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

How can I get Ubuntu to understand that I am using a Sony 46 inch external TV through my HDMI connector instead of a Pioneer 65 inch TV that it already has assumed in some way?

---

### Post by grahammechanical on 2012-04-23
What video card do you have and what video driver are you using?

If you are using a proprietary video driver perhaps you should open the settings utility that was installed with that driver and look for some way to tell the utility to Detect displays.

I could direct you if you had a Nvidia video card and were using the Nvidia driver. But as you do not give that information I cannot not help you.

If you are using an open source video driver than you can go to System Settings>Displays and launch that utility. It has a detect displays button but it little information about the make of the display.

The boot process of Ubuntu gets its display settings not from some written script or configuration file but directly from the monitor. Have you changed the external monitor that you use? Does Ubuntu know this?

Regards.

---

### Post by hateregistering on 2012-04-23
> **grahammechanical said:**
> What video card do you have and what video driver are you using?

I have a Sony Vaio VPCEB3S1E, so I guess it should be what it says [here]("http://www.nexus.com.cy/Sony-EB3S1E.html"), i.e. ATI Mobility Radeon HD 5650, 1024MB. And the driver I was using first was the default one.

> **grahammechanical said:**
> If you are using a proprietary video driver perhaps you should open the settings utility that was installed with that driver and look for some way to tell the utility to Detect displays.

I was suggested two drivers by the System Settings > Additional Drivers dialog. However, the worked even worse - they couldn't even make use of the whole TV screen - instead an error message appeared: "".

> **grahammechanical said:**
> I could direct you if you had a Nvidia video card and were using the Nvidia driver. But as you do not give that information I cannot not help you.

If you are using an open source video driver than you can go to System Settings>Displays and launch that utility. It has a detect displays button but it little information about the make of the display.

Nothing happens when pressing this button. My guess it that it will try to redetect the screens? It still is a Pioneer 65", while I have a Sony 46".

> **grahammechanical said:**
> The boot process of Ubuntu gets its display settings not from some written script or configuration file but directly from the monitor. Have you changed the external monitor that you use? Does Ubuntu know this?

Regards.

No, I have not changed the external monitor - this is the first time I am using an external monitor. Not sure if this is relevant, but my PC is dual boot with Windows 7.

Thanks!!

---

### Post by gordintoronto on 2012-04-23
The brand and model of TV are not very important, it's the resolution. You didn't provide the model of Sony TV, so we don't know its native resolution. Do you know what resolution is being displayed?

You could run Additional Drivers and see if it suggests an ATI driver, which should produce improved results.

---

