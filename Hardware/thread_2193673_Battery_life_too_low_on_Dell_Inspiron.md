---
title: "Battery life too low on Dell Inspiron"
date: 2013-12-14
forum: Hardware
---

### Post by davy jones on 2013-12-14
I use Ubuntu 12.04 LTS on a Dell Inspiron 3521, and my battery drains in about 2.5 hours as opposed to over 5 hours on Windows 8. I'd read that this happens even before I bought this laptop due to some issue with dual graphics, but my usage is very light and does not require much from the graphics, and yet the fan seems to be always on while I'm using Ubuntu. Does anyone have a solution to this problem?

---

### Post by asus-user on 2013-12-14
> **davy jones said:**
> I use Ubuntu 12.04 LTS on a Dell Inspiron 3521, and my battery drains in about 2.5 hours as opposed to over 5 hours on Windows 8. I'd read that this happens even before I bought this laptop due to some issue with dual graphics, but my usage is very light and does not require much from the graphics, and yet the fan seems to be always on while I'm using Ubuntu. Does anyone have a solution to this problem?

I am using Asus u30j, and I have the same problem (4h on ubuntu 12.04 while 9h on windows 7 , medium use). and it contains dual vga, intel and nvidia.

---

### Post by davy jones on 2013-12-18
Any idea if there's a way around it?

---

### Post by fyfe54 on 2013-12-18
I had success with tlp on my Inspiron 1545.  It's in the repos.

---

### Post by asus-user on 2013-12-18
I am using jupiter, slightly better than nothing.

---

### Post by go.harrison on 2013-12-31
When I was digging around to install 12.04 on my 3521 I found out that those with the ATI Radeon graphics will have a lot of fan issues thus decreasing battery life.
Why? I believe it is because when the OS is running, both the integrated graphics and the Radeon graphics's fans are running which hurts battery life.
There isn't a lot of driver support for newly released video cards so I guess it is best to disable the Radeon graphics card and use Intel's integrated graphics or use it on demand.
Rajesh KSV appears to have some success. Whether or not it works I'm not sure. But give it a try.[URL="http://rajeshksv.blogspot.com/2013/06/ubuntu-1304-on-dell-inspiron-3521.html"]
http://rajeshksv.blogspot.com/2013/06/ubuntu-1304-on-dell-inspiron-3521.html[/URL]

---

### Post by davy jones on 2014-01-01
I don't know how to implement this. The tutorial on [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450) is not working for me.

---

### Post by davy jones on 2014-01-03
I had gotten stuck on the step that is supposed to let you download the AMD catalyst driver from the terminal because you cannot download it from any other site now. I downloaded it from the AMD site, and managed to install it, followed by Catalyst Control Centre and voila! I can switch between graphics cards now. Switched to the integrated one and battery life has doubled. Around 5 to 5.5 hours now as opposed to 2.5 earlier. (Although it says 7, but that's fine since it said 4 earlier)

---

