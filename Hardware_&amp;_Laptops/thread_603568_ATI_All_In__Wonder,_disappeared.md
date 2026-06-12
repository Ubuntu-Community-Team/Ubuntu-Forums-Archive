---
title: "ATI All In  Wonder, disappeared"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by singlewc on 2007-11-05
When the install for v7.10  finished, there was a message about my ATI All In Wonder card drivers being proprietary, and I chose to install them. That was early on in the process, and everything was find. I rebooted a number of times for all kinds of reasons during the day, and went to bed thinking I had done good.

This AM, I boot up Ubuntu, and it says my video card is incompatible, and I get VESA and 800X600. Tried to change to the ATI driver, and checked the okay box, but when I rebooted... VESA.

In addition, my desktop came up different, in that the application bar is now at the bottom, and the other bar, is across the top. They were opposite that last night. 

Last night I turned off the system sounds. Today they are back on.

Why did Ubuntu eat my system that I worked so hard to set up?

Gotta have the video back for sure. If Ubuntu doesn't like the ATI drivers, how do I set up my system to work with the ATI AIW card. I don't really care about the features, I need the resolutions and refresh rates to match my needs.

I don't know how to deal with changing the video. Am I supposed to drop out of  xwindow, and run some sort of configuration utility? Please help me get back in. I was sure looking forward to working with Ubuntu today.

Thanks a lot,

John

---

### Post by khughitt on 2007-11-05
Hi John,

A couple quick things:

When you open the restricted drivers manager, does it show a check box / "enabled" next to the driver for your ATI driver?

Also, with 7.10 there is now a "screen and graphics card" configuration manager (under either system->prefs or system->admin). When you open that up, what does it show as the driver being used under the graphics card tab?

---

### Post by singlewc on 2007-11-05
> **pwnedd said:**
> Hi John,

A couple quick things:

When you open the restricted drivers manager, does it show a check box / "enabled" next to the driver for your ATI driver?

Also, with 7.10 there is now a "screen and graphics card" configuration manager (under either system->prefs or system->admin). When you open that up, what does it show as the driver being used under the graphics card tab?

First thing this AM, it was  unchecked, so I checked it, and rebooted. Now its checked, and it still refuses to load the driver, and all I get is VESA

The configuration manager says its a VESA generic driver. I try to change it to ATI Radeon, and when I press TEST, it gives me a plaid screen, no graphics on it, I say OKAY, and it comes back to the VESA driver.

Is there an app I can run from the shell to set up something different? I have seen xorgconfig, xvesa, and such, but with Ubuntu, when I drop out of xwindows, none of them work

When I first installed, the display was working, in the sense that I got the resolution I wanted. Then I did the proprietary drivers install, and its been a bummer ever since :-)

How do I get back to whatever it was that was loaded by default during the initial install?

Thanks very much for any help.

John

---

### Post by khughitt on 2007-11-05
Try running dpkg-reconfigure:

```
sudo dpkg-reconfigure xserver-xorg
```

and then restart x-windows.

If that doesn't do it,  instead of using the radeon driver, you can also try "fglrx" and "ati." You may have better luck with one of those.

---

