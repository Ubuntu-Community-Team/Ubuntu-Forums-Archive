---
title: "Touchpad Disabled Can't Enable Again"
date: 2011-03-15
forum: Hardware
---

### Post by nukethewhalesagain on 2011-03-15
I'm kind of still a beginner but I figured this would be a better place for this than the Beginner forum.

I have a Samsung QX410 laptop.  I'm running Ubuntu 10.10 on it and it was mostly working fine until I used the FN+F10 keys to disable my touchpad while I typed something out. At first it worked fine but now I can't get the touchpad to work again.

Now when I try FN+F10 the indicator on Ubuntu will tell me the opposite of the lights on the physical touchpad.  If the lights are indicating the touchpad is working, the indicator on Ubuntu will tell me that its not and vice versa.

Anyone have any ideas how I may fix this?

---

### Post by nukethewhalesagain on 2011-03-16
bump

---

### Post by nukethewhalesagain on 2011-03-16
To solve this problem I ended up using Touchpad-Indicator.  That worked to reset my touchpad back but I had to wait till I had access to an external mouse.

It can be installed using these command:
```
sudo add-apt-repository ppa:lorenzo-carbonell/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator
```

I did some research into how Touchpad-Indicator works and found the gconftool and this command which will work if you don't have access to an external mouse:
```
gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

---

