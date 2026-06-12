---
title: "HP LaserJet printer not recognized on Ubuntu 20.04"
date: 2020-11-04
forum: Hardware
---

### Post by wmrp on 2020-11-04
HPLIP installed. Tried multiple usb printer cables, different ports. 

lsusb lists all devices, but not the printer (HP LaserJet Pro MFP M148fdw). With HP Device Manager no usb devices are detected. 

HP setup with HP Device Manager, Terminal has been showing the following:
Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb

---

### Post by CelticWarrior on 2020-11-04
Have you tried in another computer? And other USB devices in that one?

---

### Post by wmrp on 2020-11-04
Yes to both

---

### Post by CelticWarrior on 2020-11-04
And the results were...?

---

### Post by wmrp on 2020-11-04
Same. Printer does not show up

---

### Post by CelticWarrior on 2020-11-04
Then why didn't you reach the obvious conclusion the printer is defective yet?

---

### Post by wmrp on 2020-11-04
Is it that obvious? Brand new, straight out the box. As a newbie I figured we are looking at a software issue.

---

### Post by CelticWarrior on 2020-11-04
Yes, it could be a (very rare) software issue. Printers may not work due to a missing or non-working driver. However, in those cases, the hardware would still be detected by lsusb.
When it isn't detected/listed in lsusb the printer could still be fine and the problem be in the USB ports, hence the second part of my question above.
Now, if other USB devices works in the same computer and the printer isn't detected in another computer then it become bloody obvious where the problem is.

The results of the troubleshooting you already did should have been posted in the OP. That would have saved us this unproductive back and forth.

If it's brand new ask for an under warranty replacement.

---

### Post by brian_p on 2020-11-04
> **wmrp said:**
> Is it that obvious? Brand new, straight out the box. As a newbie I figured we are looking at a software issue.

That's a possibility. You appear to have done all the right things - changing cables etc - and *lsusb* doesn't show anything. How do you fancy setting up a wireless connection with the LaserJet?

Incidentally: you do not need HPLIP with your device.

---

### Post by wmrp on 2020-11-04
I don't want a wireless connection, only usb

---

### Post by wmrp on 2020-11-04
Maybe not that rare of a software issue... [https://bugs.launchpad.net/hplip/+bug/1879719](https://bugs.launchpad.net/hplip/+bug/1879719)

---

### Post by brian_p on 2020-11-04
> **wmrp said:**
> I don't want a wireless connection, only usb

I don't really want to debug a USB connection when I know that getting your device printing and scanning with wireless is straightforward (assuming it is not defective).

---

### Post by CelticWarrior on 2020-11-04
From the bug description:

> [COLOR=#333333][FONT=monospace]After installing Ubuntu 20.04 on two different laptops the HP deskjet printers 2450 and 4502 **are recognized** (...) [/FONT][/COLOR]**[COLOR=#333333][FONT=monospace]Printing and scanning fails[/FONT][/COLOR]**

Now please re-read my previous post. Please understand this is NOT your issue.

---

### Post by brian_p on 2020-11-04
> **wmrp said:**
> Maybe not that rare of a software issue... [https://bugs.launchpad.net/hplip/+bug/1879719](https://bugs.launchpad.net/hplip/+bug/1879719)

Earlier you said > lsusb lists all devices, but not the printer... I do not think your link mentions users having that problem.

---

### Post by wmrp on 2020-11-04
Lots of scenarios there, but I am sure you are right.

---

### Post by wmrp on 2020-11-04
A friend from the U.S. helped me over the phone, and problem got solved. Thanks for your precious time guys.

---

### Post by brian_p on 2020-11-04
> **wmrp said:**
> Lots of scenarios there, but I am sure you are right.

I am very familiar with the situation described at [https://bugs.launchpad.net/hplip/+bug/1879719](https://bugs.launchpad.net/hplip/+bug/1879719) and know how to rectify it. If you follow through with the various links from that report you should find one of my posts with a solution (not the best solution) and maybe it works for you.

Being on wireless is up to you, but I'd be perturbed if it did not work.

---

### Post by brian_p on 2020-11-04
> **wmrp said:**
> A friend from the U.S. helped me over the phone, and problem got solved. Thanks for your precious time guys.

You are welcome to my time. But - how was the problem solved? Your response will help other users.

---

### Post by brian_p on 2020-11-05
> You are welcome to my time. But - how was the problem solved? Your response will help other users. 

[https://answers.launchpad.net/hplip/+question/693799](https://answers.launchpad.net/hplip/+question/693799)

---

### Post by unarver474 on 2021-06-16
I am also using the HP printer for 5 years but I didn't get any issue till now. I have just bought a new printer [COLOR=#1155CC][FONT=Arial][https://productz.com/en/hp-envy-5010/p/MzMB5](https://productz.com/en/hp-envy-5010/p/MzMB5)[/FONT][/COLOR] for my kids and installing it with my desktop. This printer print colors very nicely. My friend Anika suggested I buy this because she is using the same for 3 years. She is very much an expert in purchasing tech products.

---

