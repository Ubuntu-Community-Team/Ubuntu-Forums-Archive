---
title: "Adding a second 'monitor'"
date: 2021-04-05
forum: Hardware
---

### Post by makem2 on 2021-04-05
I use a Dell XPS13 9300 running xubuntu and also have a Samsung Tab A tablet. I would like to use the tablet as a second screen to avoid the need to 'Alt + tab to swap current views on the laptop.

Both machines have USB C connections and I have one adapter which can output HDMI from the tablet.

Before I invest in another adapter for the laptop and a connecting cable, is it possible? Will it work as I want or should I be looking for a cheap/free small tv/monitor with HDMI?

---

### Post by CelticWarrior on 2021-04-05
No, not possible.

---

### Post by makem2 on 2021-04-05
Using scrcpy and connecting both machines via a usb c to usbc cable I can view and control the tablet on the linux desktop. However, it does not register as another 'display' so does not appear if the linux display settings.

Any ideas on how to configure this? 

EDIT: I prepared this post before seeing the previous reply. I take it that still applies?
[COLOR=#FFFFFF][FONT=Consolas]


[/FONT][/COLOR]

---

### Post by CelticWarrior on 2021-04-05
[COLOR=#000000]Scrcpy is screen mirroring software via network. It has nothing to do with cables. It is not another display and can't be configured as such and regarding control it merely allows what KDEConnect/GSConnect does but in reverse.[/COLOR]

---

### Post by makem2 on 2021-04-05
Thanks for helping to not waste my time :)

---

### Post by makem2 on 2021-04-05
Thanks for helping to not waste my time :)

Is there any monitor available which would allow usb to usb connectiing or must it be via hdmi to have two effective displays?

---

### Post by CelticWarrior on 2021-04-05
There are DisplayLink based USB adapters that are supported in Linux, mainly Ubuntu (with additional drivers).

---

### Post by makem2 on 2021-04-05
> **CelticWarrior said:**
> There are DisplayLink based USB adapters that are supported in Linux, mainly Ubuntu (with additional drivers).


I have this:

[https://www.samsung.com/uk/mobile-accessories/multiport-adapter-p3200-ee-p3200bjegww/](https://www.samsung.com/uk/mobile-accessories/multiport-adapter-p3200-ee-p3200bjegww/)

Is that what you refer to as a Displaylink?

---

### Post by CelticWarrior on 2021-04-05
> **makem2 said:**
> I have this:

[https://www.samsung.com/uk/mobile-accessories/multiport-adapter-p3200-ee-p3200bjegww/](https://www.samsung.com/uk/mobile-accessories/multiport-adapter-p3200-ee-p3200bjegww/)

Is that what you refer to as a Displaylink?

No.
DisplayLink based adapters are and were used many years before the new USB-C protocol with Thunderbold allowed connecting additional monitors via the USB-C port.
Before further considerations please understand that not all USB-C ports support this. Unless such feature is explicitly mentioned by the manufacturer, users should assume it doesn't. If yours explicitly supports than yes, you can add additional monitors with it, but, again, this has nothing to do with your original question which is about using a tablet for that purpose.

DisplayLink based adapters already worked with the old USB2.0 ports (some resolution and refresh rate limitations may apply). Thanks to its proprietary drivers they can "emulate" an additional video output routed via the USB port. DisplayLink devices aren't required if there's a USB-C with that capability already and that USB-C capability has nothing to do and doesn't depend on anything DisplayLink related.

The Samsung adapter in your link is targeted to specific Samsung TABLETS although it should work fine with any other tablets or notebooks or desktop computers that have USB-C ports with the aforementioned display support. The adapter itself is passive, i.e., not a converter. it has a power connection to allow charging the tablet while in use, not to power any electronics inside.

[B]In any case you need to understand the difference between INPUT and OUTPUT and also the difference between MIRRORED and EXTENDED desktop. 
[/B]This is your original question: > [COLOR=#000000]I would like to use the tablet as a second screen to avoid the need to 'Alt + tab to swap current views on the laptop.[/COLOR]
Your question implies the usage of a second monitor to extend the desktop in order to have different views (mirrored, as the name implies, it's the same view on all monitors). 
The Samsung adapter provides a HDMI OUTPUT to the tablet (or other). Meaning: It allows connecting the tablet to any HDMI enabled monitor. It can't be used the other way around.

---

### Post by makem2 on 2021-04-05
Yes my question has involved and perhaps I should have stated why I want to attach a tablet.

I desire to have a display of for example a YouTube 'how to' on an external source which I can pause while I use the laptop to 'make' something using the 'how to'.

I can do this if I control the tablet with a Bluetooth mouse but, I, knowing there was a facility of workspaces in Linux, I wanted to use one mouse.

The adapter supplied by Samsung does in fact mimic the Linux desktop on a tv via HDMI but that is not what I want. I bought the adapter to allow HDMI input/output and connection of a USB memory stick to my mobile phone, not the tablet.

My son who uses windows, has two monitors and I used to use two many years ago when I was only using windows.

That is what I would like to achieve.

I need to consult my son and refresh what I have forgotten!

Thank you for your help and explanations.

EDIT: This is what I NEED lol:

[https://www.youtube.com/watch?v=ODOeu3NMM8Q](https://www.youtube.com/watch?v=ODOeu3NMM8Q)

---

