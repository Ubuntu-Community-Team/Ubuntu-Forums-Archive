---
title: "lm-sensors issues..."
date: 2015-09-17
forum: Hardware
---

### Post by Mopar1973Man on 2015-09-17
First off I'm got two machines with Asus motherboards less that a year old. Both machines don't properly detect sensors. I've manage to upgrade lm-sensors once but now the web site seems to be gone. 

[www.lm-sensors.org]("http://www.lm-sensors.org")

Is there another solution to making lm-sensors work on newer hardware?

```

*-core
       description: Motherboard
       product: A78M-A
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev X.0x
       serial: 140323639003289
       slot: To be filled by O.E.M.

```

No power stats... Temperature is way off...
```

michael@michael:~$ sensors -f
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +36.0°F  (high = +158.0°F)
                       (crit = +158.0°F, hyst = +156.2°F)

radeon-pci-0008
Adapter: PCI adapter
temp1:        +35.6°F  (crit = +248.0°F, hyst = +194.0°F)

```

---

### Post by Yellow Pasque on 2015-09-17
> Temperature is way off

That's a known issue with Kaveri-based chips, especially at lower temps.
You should be able to also read the mobo's sensor chip, though you may need to manually specify a model for it87:
```
sudo modprobe -v it87
```
What model you specify depends on exactly which chip your mobo has. There's a chip in the lower left corner of the mobo that says "ITE", but I can't seem to find any images sharp enough to tell me what exact model it is.

BTW, what kernel are you running?
```
uname -a
```

---

### Post by QIII on 2015-09-17
The "low" temperatures are "normal" for k10temp.

This is from the k10temp module documentation:

> There is one temperature measurement value, available as temp1_input in
    sysfs. It is measured in degrees Celsius with a resolution of 1/8th degree.
    Please note that it is defined as a relative value; to quote the AMD manual:

    Tctl is the processor temperature control value, used by the platform to
    control cooling systems. Tctl is a non-physical temperature on an
    arbitrary scale measured in degrees. It does _not_ represent an actual
    physical temperature like die or case temperature. Instead, it specifies
    the processor temperature relative to the point at which the system must
    supply the maximum cooling for the processor's specified maximum case
    temperature and maximum thermal power dissipation.

    The maximum value for Tctl is available in the file temp1_max.

    If the BIOS has enabled hardware temperature control, the threshold at
    which the processor will throttle itself to avoid damage is available in
    temp1_crit and temp1_crit_hyst.

And from the lm-sensors wiki:

> coretemp returns unrealistic values

So, if the temperature value reported by coretemp is unrealistically low, all it means is that you are far away from the critical limit so your systems are running totally fine and cool and you don't have to worry at all. Unfortunately, there is no way to improve the readings, this is a hardware limitation.

Additionally, the critical limit value may be wrong on come CPU models. We may be able to address this problem over time, but again it's not really a problem in the first place. All that really matters is how far the measurement is from that limit. If the difference is above 40 pseudo degrees Celsius (again these are not real degrees Celsius!) then you're safe.

Anything you get from lm-sensors will be some arbitrary number of pseudo-degrees in Celsius units that serves the purpose of telling your cooling system how fast to run the fans, basically.  It's not a physical temperature.

[Here's]("http://theleftcoastgeek.net/index.php/general-interest/5-lm-sensors-conky-and-amd-temperatures") what I have to say about how I use k10temp with my conky.

---

### Post by Mopar1973Man on 2015-09-17
I do have ITE chip in both. Now if I modprobe it does show some value of temperature more realistic. But my thing is I want to update the second computer and lm-sensor site is down. So how do you get a update copy of the lm-sensor software like I've got on my first computer. Man I wished I kept the download files. (Bangin' head on desk!)

---

### Post by Yellow Pasque on 2015-09-18
For building it yourself? You can get it here: [https://launchpad.net/ubuntu/+archive/primary/+files/lm-sensors_3.4.0.orig.tar.bz2](https://launchpad.net/ubuntu/+archive/primary/+files/lm-sensors_3.4.0.orig.tar.bz2)

---

### Post by Mopar1973Man on 2015-09-22
Thanks I needed that! I'm glad to see there is a way to get a hold of the source code. So what's happening to the actual lm-sensors site? Is this end of lm-sensors?

Another quick question is there a way to get the IT87 module to load up every time? I'm doing something wrong and it not loading.

---

### Post by Yellow Pasque on 2015-09-22
> **Mopar1973Man said:**
> So what's happening to the actual lm-sensors site? Is this end of lm-sensors?
I doubt it.

> Is there a way to get the IT87 module to load up every time?
Put 'it87' in /etc/modules:
```
echo "it87" | sudo tee -a /etc/modules
```

---

### Post by Mopar1973Man on 2015-09-22
Thanks I give that a shot in the morning.

---

