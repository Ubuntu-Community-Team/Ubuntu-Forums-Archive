---
title: "Ubuntu thinks wireless keyboard is a laptop battery"
date: 2013-10-13
forum: Hardware
---

### Post by serendipitousus2 on 2013-10-13
Ubuntu thinks my wireless keyboard is a laptop battery. When pair my wireless keyboard with by ubuntu 12.10 desktop, the laptop battery monitor shows up. 

I'm having a host of issues with my wireless keyboard, and I think this might somehow be related, or even at the root of the problem. 

These problems include: 


[LIST]
[*]Turning keyboard on and off causes ubuntu to not recognize it.
[*]Frequent issues re-pairing the keyboard
[*]bluetooth-wizard sometimes hangs
[*]inconsistent status messages in the bluetooth menu in the top panel and bluetooth settings
[/LIST]

I'm wondering if ubuntu somehow understanding the keyboard's battery to be a laptop battery could be the cause or at least an obvious symptom. 

My current workaround for these issues is to restart the system with the bluetooth dongle removed, disable bluetooth, start bluetooth-wizard with sudo, and then re-pair the device. 

The keyboard is a Logitech DiNovo Edge. This is a relatively fresh install of 12.10. 

To get ubuntu to recognize and pair with the keyboard at all, I had to edit 

[B]/lib/udev/rules.d/97-bluetooth-hid2hci.rules

[/B]and change hiddev to hidraw (information found in [http://askubuntu.com/questions/125473/logitech-dinovo-edge-does-not-work-in-12-04/125936#125936](http://askubuntu.com/questions/125473/logitech-dinovo-edge-does-not-work-in-12-04/125936#125936)) 

The specific battery problem I'm facing sounds similar to that posted here [http://askubuntu.com/questions/283613/turning-off-battery-management-on-desktop](http://askubuntu.com/questions/283613/turning-off-battery-management-on-desktop) although I don't have the automatic power-off issue that poster was facing.

I'm not sure that removing the power-management feature is the correct response.

I'm hoping for: 

* A solution to keeping ubuntu from mistaking my wireless keyboard's battery as a laptop battery 
* Alleviate or solve the host of bluetooth connection issues.

---

