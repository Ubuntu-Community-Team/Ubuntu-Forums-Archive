---
title: "Easy guide to enable 3D on your ATI card"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by linuxownswindows on 2007-12-08
After doing extensive research I have figured out the easiest way to get full 3D effects on your ATI card. Please read below.

1st

Download ATI Catalyst 7.11 **[COLOR="black"][SIZE="5"](SAVE TO DESKTOP)[/SIZE][/COLOR]**
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-7-11-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-7-11-x86.x86_64.run)

2nd

Right click the file, select properties, select permissions, check "Allow executing file as program"

3rd

Open up terminal and type

> cd Desktop
sudo ./ati-driver-installer-7-11-x86.x86_64.run
Click through the installer

4th

Type in terminal 
> sudo gedit /etc/X11/xorg.conf
Scroll down to where it says "Device" and change "Driver" from "mesa" to "fglrx"
**[SIZE="5"]Click save[/SIZE]**

5th

Type in terminal
> sudo gedit /usr/bin/compiz
Scroll down to where it says WHITELIST="nvidia intel ati radeon i810" and change it to WHITELIST="fglrx nvidia intel ati radeon i810"
**[SIZE="5"]Click save[/SIZE]**

Reboot open up terminal and type:
> fglrxinfo
If it reads something like this:
> OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.1.7059 Release

ENJOY!!!

---

### Post by santiagoward2000 on 2007-12-08
Hi!
I have a question: Why not just use the **Restricted Drivers Manager** to install the drivers? It worked for me.

---

### Post by Yellow Pasque on 2007-12-08
> **santiagoward2000 said:**
> Hi!
I have a question: Why not just use the **Restricted Drivers Manager** to install the drivers? It worked for me.
The version from the Ubuntu repo doesn't support AIGLX/Compiz and that seems to be a big deal for a lot of people. However, if you can live without the eye candy, that's the best driver to use IMHO.

---

### Post by santiagoward2000 on 2007-12-08
> **Temüjin said:**
> The version from the Ubuntu repo doesn't support AIGLX/Compiz and that seems to be a big deal for a lot of people. However, if you can live without the eye candy, that's the best driver to use IMHO.

Well, but you can use Compiz with XGL, that's what I'm doing... Is there any performance improvement by using ATI's drivers with AIGLX?

---

### Post by jocko on 2007-12-08
There's a better guide [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually") (I think it's better because it describes how to make .deb packages, which makes it easier to uninstall).
Another thing: it's not true that you need the 7.11 version to be able to run compiz. compiz has always worked fine on my radeon 9600, but xserver-xgl has to be installed.
I have tried the 7.11 version and found a few serious problems that made me go back to the repo version (8.37.6):
First of all, video overlay with Xv is broken (flashing video).
The second problem is that it seems to break my dual head configuration, which I need in order to play movies on my tv.
Another problem is that scrolling gets extremely slow with aiglx/compiz enabled (scroll one step, wait a second or two for the picture to update).
None of these problems are present in the repo version, and I can't notice any difference in 3d performance between running compiz through xgl on 8.37.6 or through aiglx on 7.11.

---

