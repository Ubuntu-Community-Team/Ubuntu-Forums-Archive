---
title: "Panasonic toughbook CF-31 bluetooth adapter not found"
date: 2014-12-30
forum: Hardware
---

### Post by 4-null-nan on 2014-12-30
In the bios, I see bluetooth in the advanced/networking tab.  It is enabled.
However, after I setup the bluetooth and have the service running according to this:

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

> hcitool dev <enter> or
> sudo hcitool dev <enter> would return nothing, other than the label "Devices".

I restarted the computer and still see nothing.

Is there a way to manually configure this?  How do I find out what chip is behind it, or anyway to start this?

> sudo lshw | grep blue
> sudo lshw | grep Blue

returns nothing.  same as:

sudo  cat /proc/devices  | grep tooth

---

