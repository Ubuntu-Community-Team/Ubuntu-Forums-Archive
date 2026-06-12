---
title: "Screensaver scrambles screen pixels and locks up computer"
date: 2015-04-23
forum: Hardware
---

### Post by rick_pizzi on 2015-04-23
Hi,

I have recently installed Ubuntu 14.04.

The screen saver suspends screen then locks up. I restart computer and scrambled screen shows up. I have to then re-boot to get anything to work. See screenshot for computer details and messed up screen. I note that in the computer info there is no mention of my NVIDEA card.

Also I can't get anything to stick to the desktop. I hope this is not a permanent thing. I now have a huge long list of programs on the left side of the screen. Very annoying to have to scroll thru these to find a program!!!

Would greatly appreciate help to solve this.

R.

---

### Post by pepsifx357 on 2015-04-23
I ran into this exact issue when I got an ATI card.  Which Nvidia driver are you using, the nouveau driver that comes with it, or did you install the proprietary Nvidia driver?  Just switch to whatever driver you are not using and the problem is likely to go away. If you go to "Software & Updates" and click on the "Additional Drivers" tab, it will tell you what you're using and allow you to install and remove drivers for your Nvidia card.

I just saw the picture with the "Gallium Graphics" listed.  If you do indeed have an Nvidia card, you need to install the Proprietary driver.

---

### Post by rick_pizzi on 2015-04-25
Thanks [**[COLOR=#000000]pepsifx357[/COLOR]**]("http://ubuntuforums.org/member.php?u=520476"),

I figured out how to get Gnome Classic to work and also how to install the NVIDIA driver. I'll use it a while and see if all goes well.

R

---

### Post by rick_pizzi on 2015-04-27
> **rick_pizzi said:**
> Thanks [**[COLOR=#000000]pepsifx357[/COLOR]**]("http://ubuntuforums.org/member.php?u=520476"),

I figured out how to get Gnome Classic to work and also how to install the NVIDIA driver. I'll use it a while and see if all goes well.

R

[SOLVED] :p

Thanks again [**[COLOR=#000000]pepsifx357[/COLOR]**]("http://ubuntuforums.org/member.php?u=520476"),

I have been using the new setup for a day or so and it works fine. I think the solution was to get the NVIDIA driver'

R.

---

