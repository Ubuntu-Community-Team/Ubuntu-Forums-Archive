---
title: "Screen pixelated after upgrade to 12.10"
date: 2012-11-10
forum: Hardware
---

### Post by gentrymcc on 2012-11-10
I recently upgraded to 12.10 from 12.04. When I put my pc asleep, then wake up, the screen is completely pixellated. I have to reboot and then it comes up normal. Tried setting display in System Settings, but it says all the correct info: correctly identified the monitor. No special settings, it is set up properly. Yet the problem remains.

I have an nvidia geforce 6150se nforce 430 card.
Thanks

---

### Post by moma on 2012-11-10
EDIT: Sorry. This may not help in your case. Wrong answer, wrong place.

Can you re-install the driver. Run
$ [COLOR="DarkGreen"]sudo apt-get install linux-headers-generic[/COLOR]
$[COLOR="DarkGreen"] sudo apt-get install --reinstall nvidia-current nvidia-current-dev nvidia-settings[/COLOR]
$ [COLOR="DarkGreen"]sudo reboot[/COLOR]

---

