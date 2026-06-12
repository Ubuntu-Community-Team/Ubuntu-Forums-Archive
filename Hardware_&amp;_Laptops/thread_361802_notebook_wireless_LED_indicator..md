---
title: "notebook wireless LED indicator."
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2007-02-14
Is there a way to enable the wireless indicator? my fn+f2 works to enable and disable the transmitter, but no led.

i understand that is it disabled by default, but an attempt to enable it just tells me permission denied:

ech0 1 > /sys/bus/pci/drivers/ipw2200/*/led

any ideas?

thanks.

---

### Post by mra122 on 2007-11-01
I have the same problem, only in my case the bluetooth led indicator is also blinking when the wireless is on...
HELP!!!

---

### Post by nikogawa on 2007-11-01
The following worked for me:

```
sudo gedit /etc/modprobe.d/wireless-led
```

then put this in the text file:

```
options ipw2200 led=1
```

Save, and restart your computer.

---

### Post by NET WT on 2007-11-01
I was also having a problem with my wireless LED. My wireless button works, but the LED would not light up. That fixed it though.

---

### Post by mra122 on 2007-11-10
mra122.

Works great..:) Thanks a lot!!!
Btw, you wouldn't happen to know how to turn off the bluetooth adapter? (besides the obvious option which is to switch it off with Fn+F2 which also switches off the Wifi)..

Edit:
Found it:

If you want to shut down the bluetooth just enter:
sudo hciconfig hci0 down
sudo rmmod hci_usb
and it will switch off. If you want it back on just turn it on the usual way (Fn+F2)...



Thanks,
mra122.

> **nikogawa said:**
> The following worked for me:

```
sudo gedit /etc/modprobe.d/wireless-led
```

then put this in the text file:

```
options ipw2200 led=1
```

Save, and restart your computer.

---

### Post by Offoffoff on 2007-11-12
That's fine - we all can turn led on, BUT how to turn led off when my wifi-card is off? My wifi-card is successfully turning off with wifi-button,  but light is still on. I use HP Compaq nc4000 with ipw2200.

---

### Post by GioShareITA on 2007-11-22
> **nikogawa said:**
> The following worked for me:

```
sudo gedit /etc/modprobe.d/wireless-led
```

then put this in the text file:

```
options ipw2200 led=1
```

Save, and restart your computer.

Thanks  :)

Work fine with Acer TravelMate 4060 ( Gusty )

---

### Post by Mike Armstrong on 2007-11-22
Just for info the HP laptops have an LED that is Wifi and bluetooth enabled. The softswitch is designed to turn both on and off to provide an "airplane " mode. If either bluetooth or wifi or both are enabled the LED is on.

---

### Post by bluedragon436 on 2007-11-26
Well darn for some reason this didn't work for me...was hoping it would...Oh well....at least my wireless does work....Well it picks up on networks, now as far as connecting...that is yet to be confirmed....

---

### Post by chiefrocka on 2007-12-06
> **nikogawa said:**
> The following worked for me:

```
sudo gedit /etc/modprobe.d/wireless-led
```

then put this in the text file:

```
options ipw2200 led=1
```

Save, and restart your computer.
nikogawa, how did you know to create that file in that location and set that option? I have some other LED indicator lights that are not working, and wonder if a related solution might work.

Btw, thanks, the setting worked for my Compaq Presario V2140US blue wireless indicator light. It was much easier than commenting lines in the source code of the ipw2200 driver.

---

### Post by shuttleworthwannabe on 2007-12-07
Confirm it works on HP compaq nw8240--thanks a million!

---

### Post by davidgianfran on 2008-03-21
I have an acer travemate 4060 and can't get my bluetooth to turn on (or maybe it's just not seeing my device as it says no device when i press the button). When i go to control panel to allow devices to see it, it gives me an error saying the setting could not be saved. Will something similar to the  sudo gedit /etc/modprobe.d/wireless-led work on bluetooth and if so what is it and where is it - i have no idea where you are talking about when entering this information...thanks

---

### Post by hobo on 2008-03-26
Doesn't work for me running Hardy amd64 on a r61e Thinkpad. Has anyone got this to work with this hdw config?

---

