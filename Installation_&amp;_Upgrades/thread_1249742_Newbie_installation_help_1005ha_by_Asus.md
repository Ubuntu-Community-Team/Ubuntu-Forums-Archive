---
title: "Newbie installation help? 1005ha by Asus"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by madarieder on 2009-08-25
I want to download UNR. I've done the live boot test. My wireless doesn't work. I've read about how to fix it, but I honestly have no clue where to start. I don't want to install an new OS if I can't access the internet. So, can somebody explain to me what I need to do in simple terms, please? xD

---

### Post by darksniper404 on 2009-08-25
You can simply dual boot and have both your OS's on the same computer so you can go back any time. To fix the wireless:
> This is easy — you just need to install the driver back-ported from the next Ubuntu release. 
 First, enable the backports repository: Administration > Software Sources > Updates and enable “Unsupported Updates (jaunty-backports)”.
 Then, open Synaptic Package Manager, find the package linux-backports-modules-jaunty, and install it.

from [http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

Good luck!

---

### Post by madarieder on 2009-08-25
How do I dual boot?

---

### Post by darksniper404 on 2009-08-25
> **madarieder said:**
> How do I dual boot?
During the setup you will have the option to dual boot, I believe its when you first start the installation but I have never installed the remix.

---

### Post by madarieder on 2009-08-25
> **darksniper404 said:**
> During the setup you will have the option to dual boot, I believe its when you first start the installation but I have never installed the remix.


Okay. I'll attempt it. xD

---

### Post by madarieder on 2009-08-25
So, I'm trying to do the tutorial provided here [http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/) . I get to the enabling wireless part 
> After install, the first thing you’ll notice is that ethernet and wireless networking aren’t working. Fortunately, they’re easy to fix.
On a computer with working networking, download this file:
atheros-wired-driver-1005ha-linux
Open the zip file (double-click it), and extract it to the location of your choice. Then, in a terminal, navigate (’cd’) to the ’src’ directory of the unpacked files, and type:

make
sudo make install
sudo insmod atl1e.ko
If you receive an error after the first line, and you’re not running Ubuntu Jaunty UNR, ensure you have the linux headers package installed for your kernel — you’ll need to find and download the appropriate .deb and install it. Information is here.
Until Ubuntu Karmic is released, every time you do a kernel update, you will need to re-run the last two steps (preceded by a sudo rmmod atl1e.ko).
You now have ethernet network — so plug yourself in to a network cable and set up wireless…

and I'm completely lost. I am new and have no clue what I'm doing.

Help?

---

### Post by madarieder on 2009-08-25
Anybody? Really?

---

