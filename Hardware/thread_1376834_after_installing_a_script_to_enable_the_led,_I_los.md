---
title: "after installing a script to enable the led, I lost the wireless connection"
date: 2010-01-09
forum: Hardware
---

### Post by leorolla on 2010-01-09
Hi all,

I was trying to enable the LED indicator of my wireless to know when it is on/off/connected, and perhaps also when there is data flow, and found the following:

[http://www.google.com/search?q=wireless+led+ubuntu](http://www.google.com/search?q=wireless+led+ubuntu)
||
||
V
[http://knowledge76.com/index.php?title=Wireless_LED_on_Ubuntu&oldid=14760](http://knowledge76.com/index.php?title=Wireless_LED_on_Ubuntu&oldid=14760)

After following the recommended procedures, I rebooted and lost wireless forever.

The proprietary driver control tells me that the driver is active but not in use.

Any guess of where the problem can be?

Thanks for the help!

---

### Post by leorolla on 2010-01-10
Here is the script
```
#!/bin/sh
#
# wled
#
WIRELESS_LED=/proc/acpi/asus/wled


# $IFACE is set by ifup/down, $PPP_IFACE by pppd
[ -n "$PPP_IFACE" ] && IFACE=$PPP_IFACE


[ -r $WIRELESS_LED ] || /sbin/modprobe asus_acpi


if [ -w $WIRELESS_LED ]; then
case $(dirname "$0") in
*/if-up.d)
if [ -d /sys/class/net/$IFACE/wireless ]; then
echo -n 1 > $WIRELESS_LED
fi
;;
*/if-down.d)
if [ -d /sys/class/net/$IFACE/wireless ]; then
echo -n 0 > $WIRELESS_LED
fi
;;
esac
fi

```
which I saved as 'wled' and then installed at```
sudo install -m 755 ~/wled /etc/network/if-up.d/
sudo install -m 755 ~/wled /etc/network/if-down.d/

```

No idea what made my wireless stop working...

Any help is welcome.

---

### Post by leorolla on 2010-01-10
Suddenly it is working again...

---

### Post by ajgreeny on 2010-01-10
> **leorolla said:**
> Suddenly it is working again...
And your wireless LEDs, what about them?

---

### Post by leorolla on 2010-01-10
Nope. Actually I deleted the scripts and I tried to keep track of the mess they could have done and I found nothing.

I have tried several many solutions found on blogs and tutorials, but either Karmic is much more recent or my hardware has a different setting... but so far none of the solutions I have found did work out.

---

