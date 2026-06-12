---
title: "Genius Tablet Cursor jumping to upper left"
date: 2011-04-19
forum: Hardware
---

### Post by Ae-Cha on 2011-04-19
So I'm not really that much of a tech person, as far as understanding it when people get technical about things, so I am really confused as to how to go about this problem. I have a Genius tablet, I believe a wizardpen or something to that effect, that my parents bought me a few years back. It worked fine with Windows XP but when I switched I found it would still pick up but the cursor would jump to the upper left hand corner and click my applications tab.

Now my question would be if anyone can tell me how to get this to work so I can start drawing again. Like I said earlier, I am easily confused by software matters so I would need basic instructions. Thank you to anyone who can help me.

---

### Post by Favux on 2011-04-19
Hi Ae-Cha,

Welcome to Ubuntu forums!

When the pointer arrow jumps to the upper left corner that usually means whatever X driver your tablet needs is not getting any input.

So first what Ubuntu release are you using?  Lucid or Maverick or ...?

Next open a terminal and enter the following in it:
```
lsusb
```
And post the output.  That will tell us what type of tablet the system sees and that will tell us which X driver to use.

---

### Post by Ae-Cha on 2011-04-19
My release is Maverick, as I just found out. And as follows is what came up when I typed the code into the terminal.

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:08af Logitech, Inc. QuickCam Easy/Cool
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 5543:0005 UC-Logic Technology Corp. Genius MousePen 8x6 Tablet
Bus 001 Device 005: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 001 Device 004: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Favux on 2011-04-19
OK.  And your tablet is a:
> Bus 001 Device 006: ID 5543:0005 UC-Logic Technology Corp. Genius MousePen 8x6 Tablet
And you were right, UC-Logic tablets use the WizardPen driver.  So check in Synaptic Package Manager or the Software Center if you have the package that contains it, xserver-xorg-input-wizardpen, installed.

---

### Post by Ae-Cha on 2011-04-19
I tried copying and pasting the xserver name into the search of the synaptic package manager and it doesn't have it.

---

### Post by Favux on 2011-04-19
Huh, you are correct.  I'm wondering if Lucid was the last with it or has it recently been removed.  Oh well, it doesn't matter because we were probably going to end up having to install it from DoctorMO's PPA (personal package archive) anyway:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages](https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages)

Either open a terminal and run (copy paste and hit enter) these commands:
```
sudo add-apt-repository ppa:doctormo/xorg-wizardpen

sudo apt-get update

sudo apt-get install xserver-xorg-input-wizardpen 
```
Or download the deb for your kernel architecture and double click on it.

After it is installed reboot.

---

### Post by Ae-Cha on 2011-04-19
Thank you so much. It works very well now and I can go back to working on some drawings. Thank you again.

---

