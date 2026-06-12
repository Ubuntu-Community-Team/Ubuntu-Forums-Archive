---
title: "Lenovo ThinkBook 15G2 problem with touchpad"
date: 2024-06-22
forum: Hardware
---

### Post by georgesgiralt on 2024-06-22
Hello Guys,
I run Ubuntu 22.04.4 LTS on this laptop. 
I've set org.gnome.desktop.peripherals.touchpad send-events to "disabled-on-external-mouse" in order to have my touchpad disabled when I connect a mouse either with USB or Bluetooth. It is not the first time I use this as I've other laptop running Ubuntu where I use this successfully. 
Alas, on this laptop it is not working : 
When I set up the Gnome property, when I connect a mouse, the touchpad get disabled properly. But when I unplug the mouse, the touchpad stays disabled and if I look at the properties, the touchpad is disabled. 
If I log out and in, the Gnome property is set at disabled and the touchpad is not working because it is disabled .
As this is working fine in two other machines of my network which run the very same Ubuntu version I wonder if there is something related to a bad setting/permission on files or to the particular touchpad this laptop uses ? 
More info :
The laptops run Wayland server. 
the Touchpad is SYNA2BA6:00 06CB:CE2D Touchpad 
I use two mouse a Delux m618mini Vertical mouse (Bluetooth) or a Targus AMU76EU (USB mouse).
The later runs well on the others laptop and the switch between the touchpad and the mouse works well.
So all help you will provide will be greatly appreciated !
Many thanks in advance for this.

---

### Post by him610 on 2024-06-22
I am unfamiliar with Ubuntu as I use Xubuntu 22.04.4. 
My spouse has a laptop with a trackpad and everytime I use it my lazy hands touch the trackpad inadvertently. My solution was the use of a terminal and aliases.
```

# Do you want to disable the trackpad
# get input
# yes
# synclient TouchpadOff=1
# no
synclient TouchpadOff=0
#quit()

```

I never followed though with writing the code; I found it was simpler to define a couple of aliases.

---

### Post by georgesgiralt on 2024-06-23
Thank you him610 for your response, but as I run Wayland, synclient does not work. 
So I'm left with my touch pad problem.
Have a nice and bright day

---

