---
title: "Laptop freezes when I plug in USB mouse, while on battery power."
date: 2011-02-21
forum: Hardware
---

### Post by megaman732 on 2011-02-21
I have a rather weird dilemma, I just got a new laptop (Toshiba Portege R700-P35) two days ago and Im dual booting Windows 7 Pro and Ubuntu 10.10. Ive noticed that the laptop freezes in Ubuntu, under weird circumstances.

Whenever I plug in my USB mouse, the laptop freezes. No input or response and the processor and fan really start whirring and make lots of noise, also laptop gets hot. The funny thing is, this seems to only happen on battery power (unplugged), and it does not happen at all in Windows.

Also, Im not entirely sure this is a USB mouse issue, as its happened when I plugged in my external USB hard drive as well.

Do you guys have any idea what the issue is, and how I should go about fixing/debugging the problem.

Thanks

---

### Post by megaman732 on 2011-02-22
I've got some more info. The issue happens so fast that there is almost no warning of it. One minute all is well, and the next, the mouse stops and then the party begins. I just checked if the same issue would happen while running on the install disc, and I get the same issue there.

---

### Post by megaman732 on 2011-02-22
Im not yet sure if these are correlated, but I just changed my power settings, and it seems to work fine now.

Where it was previously checked to spin down hard disks when possible, I unchecked it (on battery mode). Now it seems to work fine.

Does anybody know what effects this would have on my computer freezing, I'm rather interested to learn how/why this helped.

Thanks

---

### Post by megaman732 on 2011-02-23
i guess I spoke too soon. I have no idea why this keeps happening, its VERY annoying, because I hate to use the touchpad all the time.

Does anybody have any idea why this keeps happening, or where I should look to find out why this keeps happening?

---

### Post by megaman732 on 2011-02-28
This is still an issue. I've since discovered that the issue occurs whenever I plug in an external device through usb, regardless of the device. If the computer is plugged in, it works fine, however, when the computer is running off of battery power, it freezes at this point only allowing a hard reboot. Any thoughts?

What does the usb drive have to do with the computer power?

---

### Post by megaman732 on 2011-03-01
Found the problem. After updating the BIOS from version 1.70 to 1.80, this issue is resolved.

---

### Post by Arbayong on 2011-05-09
Megaman, i have similar problem. i had that problem when i was using ubuntu 10.10. last week i upg so raESR RESULT IS 80mmfall/hr. call 0382023150 if any prob or let patient come downded to Natty Narwhal and now the frequency of the freezes seem to have increased. In 10.10, when the computer freezes and the mouse pointer fails to move, all i have to do is hit ctrl alt + arrow key to move to a new workspace. Now this approach does work in Natty Narwhal.
I bought by Toshiba satellite l455d in november last year and updated the bios to the latest in february 2011 so i don't know whats wrong here. Now even the keyboard doesn't respond.

---

### Post by RonnieRoyce on 2011-07-06
Had the same problem. Here's how to fix it:

sudo nano /etc/laptop-mode/conf.d/usb-autosuspend.conf 

and then change from BATT_SUSPEND_USB=1 to BATT_SUSPEND_USB=0.

Problem solved. :)

---

### Post by amont on 2011-07-28
> **RonnieRoyce said:**
> Had the same problem. Here's how to fix it:

sudo nano /etc/laptop-mode/conf.d/usb-autosuspend.conf 

and then change from BATT_SUSPEND_USB=1 to BATT_SUSPEND_USB=0.

Problem solved. :)

Thank you RonniRoyce, had the same problem and this solved it. However, I have a similar problem with ethernet and wireless interfaces. Tried to adjust files /etc/laptop-mode/conf.d/ethernet.conf and wireless-power.conf, but no way. Any ideas?

Thanks,
Toni

---

