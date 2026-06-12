---
title: "Tap-to-click not working in Lubuntu 14.04"
date: 2014-04-22
forum: Hardware
---

### Post by xdya57 on 2014-04-22
Hello, I have quite a strange problem.
My sister upgraded her Lubuntu yesterday to 14.04 and everything went alright. After some reboots though (she said she hadn't done anything except for messing with the look and feel settings) the tap-to-click on the touchpad suddenly stopped working. Scrolling works alright.
What I've done:
1) Checked the mouse options. Everything was fine.
2) Logged in as guest. Tap-to-click worked just fine.
3) Put in the line "Option         "TapButton1" "1"" into the inputclass section of 50-synaptics.conf. After rebooting/logging out nothing has changed.
4) Tried synclient tapbutton1=1. That works in the current session.
5) Put in the xorg.conf folder a new configuration file.
Still, I wasn't able to fix the problem permanently. I couldn't find any other solutions apart from the one described in 3).
I would be really thankful for any suggestions :)

---

### Post by vasa1 on 2014-04-22
Take a look at these links in case they give you some pointers:
[http://ubuntuforums.org/showthread.php?t=2192864&p=12870711#post12870711](http://ubuntuforums.org/showthread.php?t=2192864&p=12870711#post12870711)
[http://askubuntu.com/questions/391102/configuring-lubuntu-to-run-a-script-when-lxde-starts](http://askubuntu.com/questions/391102/configuring-lubuntu-to-run-a-script-when-lxde-starts)

---

