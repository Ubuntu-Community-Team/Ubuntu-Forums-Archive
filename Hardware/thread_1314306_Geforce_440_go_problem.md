---
title: "Geforce 440 go problem"
date: 2009-11-04
forum: Hardware
---

### Post by Computecam on 2009-11-04
Okay I think this has been asked before but I haven't found a step by step guide to fix the problem so I am asking the question myself.


The question has to do with a problem that happens after I install the proprietary drivers for the nvidia Geforce 440 go GPU on my laptop (running ubuntu 9.10), after performing a restart ubuntu boots but the laptops screen is blank,
from my understanding the problem is that the driver is defaulting to the VGA out port,and from what I have read supposedly editing the “xorg.conf” can fix the problem.


The problem is I haven't quite figured out what to change in the “xorg.conf” and how to save what was changed in the “xorg.conf”, so if someone could help me that would be great, thanks!

---

### Post by Computecam on 2009-11-04
If you need any information let me know.

---

### Post by Computecam on 2009-11-04
Can anyone help?

---

### Post by heyho on 2009-11-04
I am by no means an expert in this area (or any), but as you've had no replies so far, I would suggest using the nvidia-settings manger to configure your xorg.conf, rather than making changes yourself.

I think 9.10 doesn't use an xorg.conf by default, but it will if it finds one.

Make sure you run the settings manger as root, otherwise it will not be able to make any permanent changes.

---

### Post by Computecam on 2009-11-04
How do I go about running nvidia-settings manager as root?

---

### Post by heyho on 2009-11-04
> **Computecam said:**
> How do I go about running nvidia-settings manager as root?

open up a terminal and enter:

> sudo nvidia-settings

---

### Post by Computecam on 2009-11-04
Ok, I got that far but I have no idea what to do, it says "ERROR: the control display is undefined; please run "nvidia-settings --help" for usage information"

---

### Post by heyho on 2009-11-04
Well, from memory, the settings manager is fairly self explanatory, but as I don't have an nvidia system here, I'm afraid I can't shed any more light on this problem for you, but hopefully somebody will come along who can.

---

### Post by gordintoronto on 2009-11-04
What is the brand and model of your laptop?

Have you searched the forums for the model number?

Does your laptop have a button for switching the video output?

Have you looked at "X Server Display Configuration" in the Nvidia X Server settings manager?

---

### Post by Computecam on 2009-11-04
It's a Toshiba Satilite 1955-S803, I searched it in the fourms and one person reported the same problem but their were no replys or solutions. 
 
The laptop does have a key comand to switch outputs but it's not working. 
 
I'm still quite new to linux so I don't fully understand some of the things about it yet

---

### Post by flusheDData on 2009-11-15
boot in console, login and type:

sudo nano /etc/X11/xorg.conf

Under the Screen section add this...

Option   "UseDisplayDevice"   "DFP"

Save, reboot and done.
Enjoy,
Miguel

---

