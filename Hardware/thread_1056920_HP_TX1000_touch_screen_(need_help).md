---
title: "HP TX1000 touch screen (need help)"
date: 2009-02-01
forum: Hardware
---

### Post by Arqillions on 2009-02-01
**im using Ubuntu 8.10 on HP XT 1000 and i`ve already downloadad all the nessesery application for my touch screen but is there any other applications that i need to maximise the use of my touch screen, like virtual keyboard etc.....please help. thank you........**

---

### Post by PoHandle on 2009-02-04
To get your touchscreen working for the TX1000 in Intrepid Ibex, open a terminal, then enter:
```
sudo apt-get install xserver-xorg-input-evtouch

```

After that installs, run the calibration tool with:
```
gksu /usr/bin/calibrate_touchscreen
```
or you can find it in System > Administration > Calibrate touchscreen.

After calibrating your touchscreen, restart your xserver with CTRL+ALT+Backspace, and you should now be able to utilize the touchscreen.  If not, reboot the computer.

For input, I use CellWriter
```
sudo apt-get install cellwriter
```
It has hand-writing recognition, but you have to train it before you can use it.

Another useful tool that I use is the Grab and Drag plugin for Firefox.  This allows you to click (touch) on a page, and dragging causes the page to scroll, much like on the iPhone.
[COLOR="DarkOrange"][https://addons.mozilla.org/en-US/firefox/addon/1250](https://addons.mozilla.org/en-US/firefox/addon/1250)[/COLOR]

There is a calibration bug with the touchscreen if your screen is rotated, and should be fixed if you install the latest version of xserver-xorg-input-evtouch ( 8.8 ), but I have not had any success with this.

I hope this helps.

---

### Post by stuckwi on 2009-02-05
Pohandle, Thanks for your instructions on the tx1000z,
you got the touch screen to work on the 64bit version?

Any word on the audio/mic jacks? do they work?

---

### Post by jpeddicord on 2009-02-05
This thread or post has been moved from the Desktop Effects & Customization forum as the posted content is considered off-topic.

Desktop Effects & Customization is a forum for discussing:
[LIST]
[*]Compositing managers such as Compiz
[*]Themes (window themes, widget themes, backgrounds, etc)
[*]Appearance preferences
[/LIST]
Your post did not fit any of these categories, so it has been moved.

Common types of off-topic threads include:
[LIST]
[*]GNOME/KDE/XFCE help in general
[*]Hardware problems not directly related to compositing
[/LIST]

---

