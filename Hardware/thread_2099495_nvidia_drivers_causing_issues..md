---
title: "nvidia drivers causing issues."
date: 2012-12-29
forum: Hardware
---

### Post by Steinklatre on 2012-12-29
Ok history.

Installed ubuntu 12.10 64bit on my desktop yesterday.

Setup:

P55 SLI motherboard
I5 CPU 64bit
4GB RAM
NVIDIA GeForce 9800 GTX+ (2) - SLI
1- SSD 60GB
2- HDD 500GB
2 monitors

Installed last night and EVERYTHING works except the nvidia drivers.

The only driver that works is the nouveau driver but I don't have the ability to enable SLI (which as far as I know makes my second video card a paperweight) or more importantly control the GPU fan speeds. They are running at warp speed!:KS

When I change the driver to the 310, 304, current-updates, or current and reboot I am left my main screen only showing AND only the background image showing and no menu screens.

Similar to the image below but without the settings window.

[IMG]http://i.stack.imgur.com/FVA5e.png[/IMG]

I would love some help on this! I want to get away from windows but this will hold me back.....:(

---

### Post by bogan on 2012-12-29
Hi!, **Steinklatre**,

Most probably a known bug which fails to install the necessary linux-header files in 12.10

See this Thread, Posts #1 & #4 substituting the nvidia driver package names with what you have presently installed:
[http://ubuntuforums.org/showthread.php?t=2098984](http://ubuntuforums.org/showthread.php?t=2098984)

In the blank Desktop Screen you should be able to get a Terminal or Console with one of these: 'Ctrl+Alt+t', 'Alt+F2' plus 'term', or 'Ctrl+Alt_F1'.

Chao!,** bogan.**

---

### Post by Steinklatre on 2012-12-29
bogan,

   I have tried to no avail..... no change whatsoever.

---

### Post by bogan on 2012-12-30
Hi!, **Steinklatre,**

What shows from: ```
echo $DESKTOP_SESSION # should be "ubuntu"
```Try: ```
sudo apt-get install --reinstall ubuntu-desktop # then reboot
# If that does not help try:
setsid unity # then reboot
```Do those alter things?

If you run: ```
sudo nvidia-settings # or:
gksudo gedit
``` Does anything happen, or do you get a 'Cant open display' message??

Chao!,** bogan.**

---

