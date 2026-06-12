---
title: "Bluetooth at start-up"
date: 2014-04-13
forum: Hardware
---

### Post by c-m on 2014-04-13
I'm on 13.10 and recently connected a bluetooth mouse and keyboard. 

I was shocked to find that on rebooting neither the mouse or keyboard connected, leaving me unable to log into the system.

Once logged in I could then open the bluetooth settings and connect them, but surely there must be a better way than having to do this every time I restart my machine.

---

### Post by trag on 2014-04-15
Switch to auto log on for the time being, is this a logitech setup? you may need logitech's unifying reciever driver. [COLOR=#4F4F4F][FONT=Lato]Installing Solaar on Ubuntu requires the addition of the [/FONT][/COLOR][following PPA]("https://launchpad.net/~daniel.pavel/+archive/solaar")[COLOR=#4F4F4F][FONT=Lato]. It provides packages for Ubuntu 12.04 LTS up to 13.10.[/FONT][/COLOR]sudo add-apt-repository [FONT=inherit !important]ppa:daniel.pavel/solaar[/FONT]sudo apt-get update && sudo apt-get install solaar[COLOR=#4F4F4F][FONT=Lato]Those using GNOME Shell should swap the last command for:[/FONT][/COLOR]
sudo apt-get update && sudo apt-get install solaar-gnome3[COLOR=#4F4F4F][FONT=Lato]Pre-built packages for other distributions, including Arch, OpenSUSE and Mageia, are also available from the project&#8217;s GitHub page.[/FONT][/COLOR]
[COLOR=#4F4F4F][FONT=Lato]Once installed, Solaar can be launched from the Dash. You may need to remove and reinsert the receiver before it is detected by Solaar. Go to [http://pwr.github.io/Solaar/devices.html](http://pwr.github.io/Solaar/devices.html) for list of supported hardware
good luck
trag[/FONT][/COLOR]

---

