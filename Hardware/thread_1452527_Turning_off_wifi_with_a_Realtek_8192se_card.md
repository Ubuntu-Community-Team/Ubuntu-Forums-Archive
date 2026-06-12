---
title: "Turning off wifi with a Realtek 8192se card"
date: 2010-04-12
forum: Hardware
---

### Post by cyberslayer on 2010-04-12
I have a realtek 8192se wireless card and I can't turn off the wireless card  to decrease power usage.  I'm using the Realtek linux driver provided on the Realtek webpage.  I've tried
sudo ifconfig wlan0 down
sudo iwconfig wlan0 txpower off
but niether command turned the wifi card off.  "sudo iwconfig wlan0 txpower off" results in the error message "
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported."

Anyone know of any other ways to turn it off?

Thanks.

---

