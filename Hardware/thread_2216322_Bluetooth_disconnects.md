---
title: "Bluetooth disconnects"
date: 2014-04-11
forum: Hardware
---

### Post by daniel-clement on 2014-04-11
Hello,

I have a new Dell XPS 13 laptop which came with Ubuntu 12.04 Precise pre-installed. It has an Intel 7260 WiFi+Bluetooth wireless chipset. 

The Bluetooth mouse frequently disconnects and I'm thinking of a power management issue, because
- the same BT mouse has no problem on other laptops;
- this seems to happen only when the laptop is running on battery.

This is generally solved by manually disabling and re-enabling wireless (with the Fn key).

First, I'd like to try and disable all power management for this wireless card, but I don't know how.

TIA for any help - best regards, Daniel

---

### Post by trag on 2014-04-15
Is this a Logitech Mouse?,The open source driver for Logitech's unifying reciever is called 'Solaar' and it may help with your connection problems.[COLOR=#4F4F4F][FONT=Lato]Installing Solaar on Ubuntu requires the addition of the [/FONT][/COLOR][following PPA]("https://launchpad.net/~daniel.pavel/+archive/solaar")[COLOR=#4F4F4F][FONT=Lato]. It provides packages for Ubuntu 12.04 LTS up to 13.10.[/FONT][/COLOR]sudo add-apt-repository [FONT=inherit !important]ppa:daniel.pavel/solaar[/FONT]sudo apt-get update && sudo apt-get install solaar[COLOR=#4F4F4F][FONT=Lato]Those using GNOME Shell should swap the last command for:[/FONT][/COLOR]
sudo apt-get update && sudo apt-get install solaar-gnome3[COLOR=#4F4F4F][FONT=Lato]Pre-built packages for other distributions, including Arch, OpenSUSE and Mageia, are also available from the project&#8217;s GitHub page.[/FONT][/COLOR]
[COLOR=#4F4F4F][FONT=Lato]Once installed, Solaar can be launched from the Dash. You may need to remove and reinsert the receiver before it is detected by Solaar. Go tohttp://pwr.github.io/Solaar/devices.html for list of supported devices.
good luck
trag[/FONT][/COLOR]

---

### Post by daniel-clement on 2014-04-16
No, it's a Bluetooth mouse (Dell). Actually I suspected the mouse first, so I tested another one. But since I get the same behavior (while the mice work very reliably on other PCs), I'm bound to blame this laptop's built-in Bluetooth card.

However, 
1) thank you for pointing me to the Solaar PPA; I've been tempted by Logitech Unifying devices before but I've always been deterred by the lack of Linux support;
2) perhaps the Intel 7260 chipset is a tad new for Precise? From some testing with a Live-USB key, I'm pretty confident Trusty will solve that...

---

### Post by willbradley on 2014-09-23
> **daniel-clement said:**
> Hello,

I have a new Dell XPS 13 laptop which came with Ubuntu 12.04 Precise pre-installed. It has an Intel 7260 WiFi+Bluetooth wireless chipset.

Daniel, did you ever get a fix for this? I have this laptop and just got a bluetooth mouse as well, and I also suspect power management issues. The mouse disconnects after I lock my computer and leave for a few minutes. I'm wondering if it's the mouse or just an idle timeout. My problem is solved by reconnecting via the sync button on the mouse and clicking "On" in the Ubuntu 14.04 bluetooth menu for the mouse, as if it has un-paired. (I also was having issues with the mouse pointer lagging, though that could've just been high 2.4ghz noise in the area. I applied a few fixes for this problem, not sure if related.)

---

