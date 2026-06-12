---
title: "Start Up"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by Raymond Jasinski on 2007-09-16
I've installed Ubuntu 7 onto my Dell Inspiron 1100 laptop. Th program runs in the center of my screen, with a nominally 2 inch black border around it. How do I get the program to fill the screen? ("maximize" doen't dp anything).

rj

---

### Post by w4ett on 2007-09-16
You will have to select a different resolution to fill the available screen area:
> 
System>Preferences>Screen Resolution

if the desired resolution is not available you will have to reconfigure your xorg.conf.

From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select your video driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

<Ctrl> <Alt> <Backspace>

This will reset X and get you back to  to a GUI desktop....then reset your resolution like before and tic the box to select it as your default screen resolution.

Good Luck

---

### Post by Raymond Jasinski on 2007-09-17
I solved the problem. On a Ubunto documentation page there is a command-line solution for my specific computer - which will allow changing the screen resolution.

---

### Post by kellemes on 2007-09-17
> **Raymond Jasinski said:**
> I solved the problem. On a Ubunto documentation page there is a command-line solution for my specific computer - which will allow changing the screen resolution.

Please provide a link for those having the same problem..

---

### Post by w4ett on 2007-09-17
> **kellemes said:**
> Please provide a link for those having the same problem..

And please mark the thread "Solved".

---

