---
title: "Intel 915 Display"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by yeoheric on 2007-01-25
Hi,

My laptop is running one of those integrated Intel video chipset 915GM. I get it to display nicely by hacking the 915resolution config, so far so good. 

I'm just wondering. Is Ubuntu using only 8MB of RAM to render stuff or does it like Windows can use up to 128MB? I really don't mind coz I have 1GB of RAM.

I am just curious coz if like I need to install stuff or anything, what should I do? Somehow, the display in my XP (I dual-boot) seems better (e.g. I don't really get blurry if I scroll down a web page a little faster).

Thanks.

Eric

---

### Post by JohnPhys on 2007-01-25
In the xorg.conf file you can tell the server how much system ram (in KB) to use for vid ram, I believe.  It's one of the questions it asks if you reconfigure the xserver.

---

### Post by yeoheric on 2007-01-28
> **JohnPhys said:**
> In the xorg.conf file you can tell the server how much system ram (in KB) to use for vid ram, I believe.  It's one of the questions it asks if you reconfigure the xserver.

Thanks. I have put in the [FONT="Courier New"]VideoRam 131072[/FONT] directive in my xorg.conf file and my system boots into the GNOME desktop fine.

Sorry but another question, how do I know it has taken effect?

Thanks.

Eric

---

### Post by prytnar on 2007-01-29
I reconfigured xorg.conf and also put VideoRam 131072. Now when I'm running 'top' it says that 1.5% is used of 1gB . shouldn't it be like 10%    ????

---

### Post by JohnPhys on 2007-02-01
I'm not sure how to see if it has "taken effect", and I don't think that looking at "top" output is all that accurate for ram usage.

---

