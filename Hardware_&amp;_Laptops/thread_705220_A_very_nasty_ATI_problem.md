---
title: "A very nasty ATI problem"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by KOTAPAKA on 2008-02-23
Hello folks I have a very nasty problem. First my configuration:
In order of install:
1.Windows
2. Ubuntu
3. Debian

Now I usually install ATI drivers for my X1400 card the ATI way. I go to the dir the driver is in and do ```
sh ./NAMEOFDRIVER
```

I has always worked for me. When I open the restricted drivers manager it says ATI accelerated graphics driver -> in use(and has the green light is on). BUT it didn't say Enabled so yesterday I decided to tick this enabled and what happened was that now when I log in I get a message saying that my monitor has to be run in low graphics mode and I have 3 options:
Configure                         Shut Down                     Continue
I press configure and I have a menu to chose LCD model and ATI chipset model. I have chosen various nothing fixes it( i can still log into the system but I am sick of this poping up on reboot). So I pressed Again on Enable to untick it and now ATI accelerated graphics driver is not in use and I cannot turn it on but this thing still bothers me at startup.Please NOTE that after pressing Enable it installed packages xserver-xorg-video-ati and xorg-driver-fglrx. And must tell you that even though it says my computer has to be run in low graphics it still runs it in native resolution 1680x1050 but I cannot open ATI Catalyst Control Centre any more.

PS OK I think I know what I've done - I have installed the proprietary driver(from ati.com) and the open source one. How do I fix it?

---

