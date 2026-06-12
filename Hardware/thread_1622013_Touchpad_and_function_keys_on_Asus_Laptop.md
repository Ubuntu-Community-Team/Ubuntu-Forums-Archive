---
title: "Touchpad and function keys on Asus Laptop"
date: 2010-11-14
forum: Hardware
---

### Post by bucky79 on 2010-11-14
Hello,

I'm brand new to Ubuntu and this is my first forum post.  So I have an Asus G73 laptop and I do not particularly like the touchpad so I usually use a trackball.  The FN-F9 hotkey on my keyboard worked in windows but does not work in Ubuntu.  I'm wondering if there is a way to get the laptop function keys working in Ubuntu, (touchpad enable/disable, volume control, keyboard brightness...etc).  I tried downloading the pointing devices package and have had some limited success with that.  Specifically I told it to disable touchpad when other devices are plugged in but it only seem to work intermittently.

Thanks,

Cory Buchholz

---

### Post by mul14 on 2010-12-31
If your laptop or netbook doesn't already have a key to toggle the touchpad on/off (or it doesn't work - as it seems there are issues with the Fn keys on some devices), you'll be glad to know that Touchpad Indicator now has an option to set a hotkey for quickly enabling / disabling the touchpad.

To set it, simply click the [Touchpad Indicator]("http://www.webupd8.org/2010/11/touchpad-indicator-lets-you-quickly.html"), select *Shortcut > Set Shortcut* and then enter a letter (it will be used with Ctrl + ALT - you can't change those).

To install Touchpad Indicator in Ubuntu 10.10, use the following commands:
```
sudo add-apt-repository ppa:lorenzo-carbonell/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator
```

Once installed, you'll find it under *Applications > Accessories > Touchpad Indicator*

Source: [http://www.webupd8.org/2010/12/touchpad-indicator-update-brings.html](http://www.webupd8.org/2010/12/touchpad-indicator-update-brings.html).

---

