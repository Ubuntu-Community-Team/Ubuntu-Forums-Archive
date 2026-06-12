---
title: "Power saving mode for WiFI adapter Intel 4865AGN does not work in Jaunty"
date: 2009-04-21
forum: Hardware
---

### Post by KMK_ECS on 2009-04-21
Hi,

After apgrading my Thinkpad T61 to Jaunty the idle power consumption increased by nearly 1 watt :(. The cause is the Intel WiFi adapter 4865AGN. In Intrepid I could switch the adapter to power saving mode with the follwoing command:

```
echo 5 > /sys/bus/pci/drivers/iwlagn/*/power_level
```

After this command the idle power consumption with lowest display brightness was 12.5 watt (1400x1050 nvidia graphic). Turning wireless lan off did not change that.

Unfortunately, changing the power level does not work with Jaunty. Although the above command initially changes the power level to 5 and reduces power consumption...

```
kmk@t61:~$ sudo cat /sys/bus/pci/drivers/iwlagn/0000\:03\:00.0/power_level 
SYSTEM:auto	MODE:fixed	INDEX:5
```

... it switches back to level 0 shortly afterwards:	

```
kmk@t61:~$ sudo cat /sys/bus/pci/drivers/iwlagn/0000\:03\:00.0/power_level 
SYSTEM:auto	MODE:fixed	INDEX:0
```

I would greatly appreciate if someone could let me know whether there is a way to change the power level in Jaunty permanently.

Many thanks and best wishes

Karl Martin

---

### Post by cyprusxr3 on 2009-04-28
I seem to be having the same problem, again with the 4865agn. So... bump :)

---

### Post by KMK_ECS on 2009-05-17
Hi,

I have reported this bug at Launchpad. If you also experience this problem could you please let them know here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/377484]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/377484")

Many thanks and best wishes

Karl Martin

---

### Post by KMK_ECS on 2009-05-23
Apparently, it is possible to use iwconfig again in Jaunty to activate the power saving mode of the iwl4965:

```
sudo iwconfig wlan0 power on
```

This command permanently changes the power level to 3:

```
kmk@t61:~$ sudo cat /sys/bus/pci/drivers/iwlagn/0000\:03\:00.0/power_level
SYSTEM:auto	MODE:fixed	INDEX:3
```

However, I have not yet found a way to change the power level to 5 even though idle power consumption is now back to 12.5 watts.

Best wishes

Karl Martin

---

