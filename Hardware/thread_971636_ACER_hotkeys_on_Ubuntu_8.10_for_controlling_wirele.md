---
title: "ACER hotkeys on Ubuntu 8.10 for controlling wireless led"
date: 2008-11-05
forum: Hardware
---

### Post by vtom80 on 2008-11-05
Hello, 
to whom could be concerned:

this is a small help for people having an ACER laptop with buttons to switch on/off the wireless controller. In almost all cases a led blinks when the controller is searching for a wireless network, or shines continuously when connected to one, or does not shine when it is switched off. This is programmed by acer only for windows, and thus for ubuntu users this can become dramatic, and yes, even a reason to remove ubuntu from your system. It is sometimes very hard to find out if your wireless card is switched on or not, and gives rise to many frustrations. Luckily a solution exists by acerhk (acer hot keys, [http://www.cakey.de/acerhk/]("http://www.cakey.de/acerhk/")). In the newest versions of ubuntu, no installation of acerhk is needed anymore, as it is already present. It just needs to be activated:

[http://insidethebrackets.blogspot.com/2008/02/acerhk-and-ubuntu-update.html]("http://insidethebrackets.blogspot.com/2008/02/acerhk-and-ubuntu-update.html")

I tested it for an ACER TravelMate 4000 series (4001WLMi). It didn't work by default. 

if using 
```
sudo modprobe acerhk
```
followed by:
```
echo 1 > /proc/driver/acerhk/wirelessled 
```
gives no result (no led blinking), try the following:
```

sudo modprobe -r ipw2200
sudo modprobe -r acerhk
sudo modprobe acerhk force_series=290 usedritek=1 verbose=1
echo 1 | sudo tee /proc/driver/acerhk/wirelessled
sudo modprobe ipw2200 led=1

```
and we have a led blinking!!!

To make it also work at startup, do following
[(http://ubuntuforums.org/showthread.php?t=524429)]("http://ubuntuforums.org/showthread.php?t=524429")

check if no acerhk in  /etc/modules

```
echo "options ipw2200 led=1" | sudo tee -a /etc/modprobe.d/options
```


hope this helps/inspires some ACER users for which acerhk is not working directly... Try also to play with the force_series parameter (check google on this)

cheers, tom

---

### Post by arm-c on 2009-02-02
I thought I would post a link to a python/gui utility that I created to turn on/off the wireless/bluetooth hardware. It requires the AcerHK driver.

[http://acerhkgui.sourceforge.net](http://acerhkgui.sourceforge.net)

Hope it helps someone. Any suggestions/contributions, please let me know.

-- As for Ubuntu 8.10, the wireless worked out of box, but no LED functionality.  I didn't have to do any of the above post except add LED=1 to the /etc/modprobe.d/options file as indicated above.

-- Bluetooth was another issue.  It wouldn't turn on from the keys.  I started this app primarily for the bluetooth radio but added wireless in case would be helpful.

---

### Post by Ubangi on 2009-02-08
My LED is still as dead as a dodo, despite trying all these conflicting hacks....

For example,why does not the official Ubuntu Acer One thread even mention acerhk, but instead gives totally different and equally non working instructions, if acerhk is installed by default??

I am lost and heading back for linpus....

---

### Post by Ubangi on 2009-02-09
Don't even think about trying any of these dangerous hacks!
I tried the fan control thing and the leds.
The leds still don't work and now my touchpad is totally screwed
(it freezes up) and my Acer has become useless!
You had been warned!

---

