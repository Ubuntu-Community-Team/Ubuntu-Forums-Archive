---
title: "Sempron LE-1250 steep learning curve, help please"
date: 2011-10-19
forum: Hardware
---

### Post by kansasnoob on 2011-10-19
This is my first AMD CPU and the learning curve is kicking me in the pants a bit :D

First a couple of links to basic specs:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103189](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103189)

[http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=135](http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=135)

I think I have the frequency scaling thing at least partly figured out, but I'm not sure. In the accompanying screenshot you can see I've installed the scaling monitor in the panel. 

I have NOT changed any settings! But I can see that change from 1GHz to 1.8, 2, or 2.2 under various loads, such as full screen flash videos. But I'm just curious if I need to install any additional kernel modules, etc :confused:

Also in that screenshot you can see that the sensors applet displays three temps:

temp1
Core0 temp
Core1 temp

But Core1 temp always shows a negative ridiculously low temp, and AFAIK that CPU is a single core processor. So I assume lm-sensors is just reading a temp from the MoBo that's actually nonsense :confused:

Click on the screenshot below please:

[ATTACH]204836[/ATTACH]

So my three questions are:

#1: Do I need to install any additional kernel modules or anything to deal with frequency scaling, or was that a thing of the past?

#2: Do you think it's safe to disable that Core1 temp sensor in the sensors applet?

#3: Do you think this CPU will handle 64bit Oneiric or would you recommend sticking with 32bit?

I'm actually quite happy with the performance. It's downright awesome along with an Nvidia GeForce 7025 for all of my purposes, so I'm a bit loathe to fiddle with perfection.

NOTE: I'm currently using Natty in classic w/o effects mode just to get a handle on the new hardware. I'm still learning gnome 3 w/unity (Oneiric) and I prefer one challenge at a time.

---

### Post by 2F4U on 2011-10-19
> #1: Do I need to install any additional kernel modules or anything to  deal with frequency scaling, or was that a thing of the past?

Usually, everything is covered by running sensors-detect. It would tell you if anything is missing.

> But Core1 temp always shows a negative ridiculously low temp, and AFAIK  that CPU is a single core processor. So I assume lm-sensors is just  reading a temp from the MoBo that's actually nonsense

> #3: Do you think this CPU will handle 64bit Oneiric or would you recommend sticking with 32bit?

Is that  a 64 bit CPU. I couldn't find that piece of information on the links.
Nonsense numbers usually indicate that a sensor is not present.

---

### Post by kansasnoob on 2011-10-19
> Usually, everything is covered by running sensors-detect. It would tell you if anything is missing.


Awesome, it told me to add the following to /etc/modules:

```
# Chip drivers
it87

```

Doing so and rebooting got the plymouth splash working properly which I hadn't yet been able to figure out ;)

I'll have to run this through some more tests to see if there were any other performance changes. I didn't even know you could do that :D

> Is that a 64 bit CPU

Both Newegg and AMD say yes so I guess I'll give it a try and see what happens.

> Nonsense numbers usually indicate that a sensor is not present. 

That's what I thought also.

Many thanks for the sensors-detect hint :D

---

### Post by kansasnoob on 2011-10-19
I'm marking this solved but I will comment further once I test Oneiric 64bit.

Gnome 3, regardless of UI (Unity, gnome-shell, or fallback-session), presents a number of problems so it may be a while.

For those who may say, "what problems", I'd submit:

#1: Poor screensaver and power management. I tested 11.10 extensively and followed Ubuntu+1, and this was a common complaint. Who wants an OS where you can't control the screen blanking out while watching a video? Even Ubuntu-studio switched to xfce ;)

#2: Many well known and simple gnome panel applets and the goodies they bring to user friendliness are no longer available for the panel in gnome 3. And some of the replacement goodies for Unity based on gnome 2 no longer work in Oneiric :cry:

#2a: Most specifically the inhibit applet and the aforementioned frequency scaling applet, but there are also others :)

Regardless I'm a multi-booter (you almost must be if you're going to be a serious tester) so I'll likely end up with a mix of 32 and 64 bit Ubuntu derivatives on here before I'm done :guitar:

Thanks again for the help. New hardware is always fun.

---

