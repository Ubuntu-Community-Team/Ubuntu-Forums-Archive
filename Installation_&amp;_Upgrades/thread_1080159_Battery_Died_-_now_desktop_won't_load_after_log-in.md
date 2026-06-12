---
title: "Battery Died - now desktop won't load after log-in"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by Reloaded on 2009-02-25
I have Intrepid 8.10 and am having a problem at some people appear to have after they upgraded to 8.10, but I've been running 8.10 from a clean install. I was using my laptop just fine earlier today and I let the battery run out. When I plugged it back in, this problem blessed me with its presence *sigh*. I log in and then I am just at an orangish-peach screen. It appears that the system is in a state between the login screen and a loaded desktop. I can use the mouse just fine and CTRL ALT BCKSPC logs me back out. Fortunately for me I also had previously given the terminal a hot key, CNTRL SHIFT A. So I can bring the terminal up and even start firefox(with no internet) or any other program I want to start, but I cannot seem to get my desktop to load. 

I've tried starting in recovery mode and fixing Xserver or whatnot.
Please Help! Thanks!

---

### Post by Reloaded on 2009-02-27
I was able to fix my problem. First I tried:

```
gnome-panel
```

This gave me limited access to what I could already access via the terminal. I still could not connect wirelessly though so I plugged an ethernet cable into my computer and the following command fixed my problems:

```
sudo apt-get install ubuntu-desktop
```

Hope this helps anyone else with a similar problem.
Note: I had to reinstall my proprietary video drivers afterwards.

---

