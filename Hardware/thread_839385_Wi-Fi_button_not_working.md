---
title: "Wi-Fi button not working"
date: 2008-06-24
forum: Hardware
---

### Post by Alexis Phoenix on 2008-06-24
Hi, I wonder if anyone can help me?
I have a Dell Inspiron 1501, dual core AMD 64 bit.  I have Hardy Heron installed on it and it works a treat.  One thing that used to work with Feisty and now doesn't work however, is the Fn-F2 key to turn on/off the wireless card (which works fine with the B43 driver, btw).  With the rfkill and rfkill-input modules loaded, I can toggle the state of the card with:
echo 1 > /sys/class/rfkill/rfkill0/state 
or
echo 0 > /sys/class/rfkill/rfkill0/state
Also,
cat /dev/input/event1
gives me some gobbledygook when Fn-F2 is pressed.
So something between the event2 and rfkill0/state is not working (I'm guessing it's a HAL issue).

So err, any suggestions, anyone?

Thanks in advance,
Alexis Phoenix

---

