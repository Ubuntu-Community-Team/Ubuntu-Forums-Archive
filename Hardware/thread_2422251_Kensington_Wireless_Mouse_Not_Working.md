---
title: "Kensington Wireless Mouse Not Working"
date: 2019-07-04
forum: Hardware
---

### Post by rogerpolo on 2019-07-04
Hello everyone, I'm new here and I really need your help to fix this issue.

I'm using Xubuntu right now on my laptop but I can't get my Kensington Wireless Three-Button Mouse to work. I've seen that the mouse is detected by the system, in fact it is shown in the "Mouse" section and I can even change its settings. However, even if plugged in, it won't respond at all.

What should I do? 

Thanks for your help :D

---

### Post by him610 on 2019-07-04
Does your trackpad work as it should?
Do you have fresh batteries installed in mouse?
Please show results of *xinput* and* lsusb* within the code tags.
> However, even if plugged in...
What part of wireless mouse is plugged in?

---

### Post by rogerpolo on 2019-07-09
First of all thanks for your reply. You'll find the logs in the attached screenshot.  Answering to your question, I have plugged in the wifi receiver of the mouse. However I'm also using a wired one in the meantime, as stated in the logs.

---

### Post by VMC on 2019-07-09
Since your using a laptop I'm sure your close enough, but on my desktop, I needed to reorient my receiver closer to my wireless device. Try plugging the receiver into another usb slot too be sure.
If the wireless keyboard works then its the mouse that's the issue. As stated above, check batteries.

---

### Post by him610 on 2019-07-09
Your mouse was manufactured by Logitech for Kensington who marketed under its brand. Post #4 by VMC has recommended a good course of action. I don't know how long you have had your wireless mouse, but sometimes electronic devices go bad. I am about to trash a fairly new bluetooth mouse after using it only a few months.

---

### Post by VMC on 2019-07-09
Interesting;Logitech. That's what I have. What I did was use a usb extender and put the transceiver in the air. I was having issues until then.

---

### Post by him610 on 2019-07-09
@VMC
Logitech wireless mice - I have five of them attached to different computers. Never had any problems with them. I use a couple of Logitech wireless keyboards together with mice using the Unifying Receiver. The defective bluetooth mouse that died was a Technet that I had ordered from Amazon.
You might be interested in this link, [http://www.linux-usb.org/usb.ids]("http://www.linux-usb.org/usb.ids") that lists most USB devices and manufacturers using the USB identification code you see when running *lsusb*.

---

### Post by rogerpolo on 2019-07-10
Sorry for that bit of a mess I made here. Some claryfing is needed lol. I have both a Logitech and a Kensington wireless mouse and they act the same way (wireless receiver plugged in, but no response from the mouse).  At the time the screenshot was taken, I was also trying to use the Logitech one.  For what concerns your questions: - Does your trackpad work as it should?  Yes, it does. - Do you have fresh batteries installed in mouse? Yes, both of them.  I even tried using different USB ports, but that's not solving the issue.   However these mouses are working fine on other Windows PCs.

---

### Post by him610 on 2019-07-10
You may be picking up some RFI from the laptop itself. Post #6 had another good suggestion, try an extender. I purchased a Logitech K400r wireless keyboard that even came with an extender, about 1-1/2 inches long, so the RFI issue does exist.
By the way, when displaying characteristics about your system using xinput or lsusb for others to analyze, it helps to only have the suspect device plugged, ie: only one mouse.
Code tags on your coded text can be applied from the Advanced page using the crunch (#) icon.

---

### Post by VMC on 2019-07-10
> **him610 said:**
> ...
You might be interested in this link, [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids) that lists most USB devices and manufacturers using the USB identification code you see when running *lsusb*.
Yes, that's a interesting and a good link to remember, thanks!

---

