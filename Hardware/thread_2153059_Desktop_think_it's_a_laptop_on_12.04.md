---
title: "Desktop think it's a laptop on 12.04"
date: 2013-06-10
forum: Hardware
---

### Post by jasonplund on 2013-06-10
I am a moderate user that just installed ubunutu 12.04 on my desktop. I did a format and full install.

My issue is that it is a desktop but ubunutu thinks it's a laptop. It functions perfectly besides that. Normally I wouldn't mind and would just ignore it but it also thinks it's not plugged in and gradually loses battery. So eventually it suspends the os which doesn't work very well when I use this as a media server. Not to mention it forgets my bluetooth keyboard and I have to repair it every time. As a relative beginner to ubuntu I'm not quite sure how to troubleshoot this. Here are the system specs:

[COLOR=#333333][FONT=Verdana]Intel Core i3-2120[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Gigabyte GA-H61N-USB3 Intel H61[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]4 GB DDR3 1333[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]1 TB Western Digital Caviar Black[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]GIGABYTE ATI Radeon HD6850[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]LG Electronics WH12LS39K Blu-Ray rewriter

I installed the drivers for the video card that poped up. I am running my monitor through hdmi to my tv. That's about all I can think of. Other than that it is set up like a normal desktop. If you need any more info just ask.

I searched for this issue in previous posts but most of them ended up being the video card wasn't installed which I did.

Please help  :([/FONT][/COLOR]

---

### Post by ohnonot on 2013-06-10
that's a funny issue and you might want to do some research yourself.
however, there's a power manager installed on your system and you can adjust it so it never suspends or even warns however low it thinks your non-existent battery to be.

---

### Post by jasonplund on 2013-06-10
I already set the power settings to never suspend but I guess it still does it because it freaks out and a suspend on battery that "low" is built into the system. Standard feature if it actually was running on laptop battery.

---

### Post by ohnonot on 2013-06-12
i logged into a ubuntu install the other day - you're right, the power manager does not allow for the kind of settings i suggested.

i have no idea how to tell ubuntu that it's *not* running on a laptop - maybe uninstalling laptop-mode-tools would be enough?

however for the previous mentioned workaround, you could install [this]("http://www.webupd8.org/2013/03/unity-tweak-tool-available-in-ubuntu.html").
if that doesn't help you could take a look at [this]("https://sites.google.com/site/easylinuxtipsproject/alternative") and see if you could install xfce4-power-manager instead.

---

