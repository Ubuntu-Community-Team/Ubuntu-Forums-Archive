---
title: "Xubuntu 8.10 Login Screen resolution, bypass solution"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by salariua on 2008-12-19
I have been trying to install Xubuntu 8.10 on an old pc I have around and I wasn't able to get to the login screen. I have an hyundai lcd and it just goes "screen not supported" or something similar. Got an even older crt monitor and after plugging it in I was able to login and use the system. Tryed the sudo dpkg-reconfigure xserver-xorg and it seems that xserver will not handle the graphics anymore. 

One of the solution might be [here]("https://answers.launchpad.net/ubuntu/+source/xorg/+question/20476") but even after changing the settings in the Applications/Settings Manager/Display I couldn't make it work at next reboot.

The above solution didn't work for me and so the login screen is coming in a "way to high" resolution for my lcd.

So I am posting this in case somebody has a better solution of in case someone decides to use mine. 

My solution was to tel the Applications/Settings/Login Window/Security to login automatically the main user therefore skipping the login screen.

If anybody has a better solution plese let me know since there might be more users for this computer and the login screen will be nice to have.

---

### Post by cariboo on 2008-12-19
It would help if you told us what type of graphics adapter you are using. If you aren't sure, in a terminal type:

```
sudo lshw -C video
```

This will tell you what display adapter you are using and what driver is installed.

Jim

---

### Post by salariua on 2008-12-19
Here it is, cariboo907:

*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: RV280 [Radeon 9200 SE]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=64 mingnt=8
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200 SE] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 mingnt=8

The problem is that I can't use the network on that pc also cause the wireless card isn't working, but I am copying all results on memory stick for you.

That's a nice command you've just pulled out of your hat.

I'm glad I started this thread.

---

