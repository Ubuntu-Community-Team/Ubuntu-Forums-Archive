---
title: "unreliable CPU thermal sensor; monitoring disabled ..."
date: 2014-05-05
forum: Hardware
---

### Post by jarinek on 2014-05-05
Hi,

I just installed Ubuntu 14.04 and get an error on boot: "unreliable CPU thermal sensor; monitoring disabled ..."
Is there a fix for this message?

When I try to find a solution, all ends on [https://wiki.archlinux.org/index.php...K10Temp_Module](https://wiki.archlinux.org/index.php...K10Temp_Module). But the file /etc/modprobe.d/k10temp.confis not existing and I have no rights to create it. What can I exactly do to solve this? I'm beginner in Ubuntu --> sorry for replaying old thread..

---

### Post by Yellow Pasque on 2014-05-05
Try this command:
```
sudo modprobe k10temp force=1
sensors
```

Don't be surprised if sensors reports garbage (like 0 degrees or 102 degrees). If the output seems reasonable, then you can make it permanent:
```
echo "k10temp" | sudo tee -a /etc/modules
echo "options k10temp force=1" | tee /etc/modprobe.d/k10temp.conf
```

---

### Post by JKyleOKC on 2014-08-19
I've had a similar problem for years now on this machine and finally today decided to search for a solution. Unfortunately, here's what I get when I follow the suggestion:```
jk@mehitabel:~$ sudo modprobe k10temp force=1
jk@mehitabel:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +40.0°C  (crit = +75.0°C)

jk@mehitabel:~$ man k10temp

```Apparently I need to do a bit more than simply force the k10temp module. The acpitz reports 40 degrees at all times, regardless of the actual CPU load. If I look at the temperature using BIOS, it varies from time to time -- but to do that I must reboot, and I avoid rebooting as much as possible since this is Linux, not Windows.

Next step?

---

### Post by QIII on 2014-08-19
Here's my take on this:  it doesn't matter what you do, so ignore it the warning.

AMD's internal sensor does not ever return an actual temperature.  In their infinite wisdom, AMD has decided that what is reported is some odd value representing some value relative to when your AMD processor begins to set off your home smoke alarms.

"  Tctl is the processor temperature control value, used by the platform to   control cooling systems. Tctl is a non-physical temperature on an   arbitrary scale measured in degrees. It does _not_ represent an actual   physical temperature like die or case temperature. Instead, it specifies   the processor temperature relative to the point at which the system must   supply the maximum cooling for the processor's specified maximum case   temperature and maximum thermal power dissipation."

You can see why the kernel developers might stick a warning in there that says the k10temp temperature reading is unreliable.  It is.  It's hocus pocus, the best the developers can do to make sense of a ridiculous reading.

See [this]("https://www.kernel.org/doc/Documentation/hwmon/k10temp").

For my conky, I have a script that adds 10 degrees to the temperature reported by the motherboard.   Supposedly as the temperature goes up the discrepancy between this meaningless relative value an the actual temperature diminishes.  If you look at k10temp at idle, you'll sometimes notice that the temperature reported is *below *ambient (about -10 from the actual physical temperature of the die), which we know is not reasonable.

---

### Post by JKyleOKC on 2014-08-19
Many thanks for the rapid response! So does this mean that there's no way to actually monitor CPU temperature with this mobo/chip? I'm running the panel applet (for Xubuntu's Thunar) to watch temperature for both CPU and HDD, so that I can throttle back and try to hold it below critical levels when doing CPU-intensive tasks. Since the BIOS display does seem to vary from time to time, that seems to imply that monitoring is indeed possible. The sensors-detect program has added a different driver, f77882fg, to /etc/modules but that one does NOT get loaded at boot, and modprobe errors out when I try to insert it manually.

Would blacklisting k10temp be a possible solution and allow the f77882fg driver detected by sensors-detect to be used? Or is this simply an undesired side effect of my preference for AMD processors? None of my other AMDs seem to have this problem.

---

### Post by QIII on 2014-08-19
Short of a dedicated probe and a bay device with a readout, I'm not sure there is much to be done about it.  This was a problem 10 years ago.  I think it was about that time that hardwaresecrets threw up their hands and started doing HSF testing with their own in-house "thermal load simulators" to get reasonable and comparable results from Intel and AMD setups.  They apparently make physical replicas of each that they can crank to any desired wattage output to test the actual performance of the coolers.  If you cruise the Windows forums, you will still find all sorts of posts with people saying just to assume the temperature is 10C higher than reported.  k8temp was the same way.

I use conky and put the CPU temp and the fan speed right next to each other.  I can get a "best guess" that way.

Interestingly, the hottest I can get my 1100T to under any circumstances is roughly 50C +/- 2 (adjusted by my script) with a Noctua NH-D14.  If the ambient temperature changes, the CPU temp still goes to 50C under full load.  But on a hotter day the fan speed is higher.  This summer I have been able to experiment quite a bit, since it has been approaching 100 degrees and our air conditioner is out (OUCH!) until the repairman comes on Friday (and the forecast temperature drops, wouldn't you know!).  It has gotten as high as 85F in the house.  But the reported temperature from the die is solid at 50C -- and the HSF fans spin a lot faster.

So the system they have works in its own inscrutable way.  It's just irritating to not have an actual temperature.  Why not just make it an actual temperature and design the chips for the motherboard to react to that?

Addendum:

Got a bit sidetracked by work!  :)

I do have a machine with a motherboard that simply does not support k10temp.  It does, however, report socket temperature.  Since the socket temp is typically about 5C cooler than the die, I just at 5.  The results seem reasonable.  Roughly 30C at idle with an ambient temperature of 20C. 55-ish under full load (Phenom II x4 Black Edition).  That one has a Cooler Master Hyper 212 Evo HSF.

Maybe you could research  your motherboard's specs and see if you get socket temp?  The board on the other machine with the 1100T reports die temp +10 at idle, which is always within 1 or 2 degrees of my "corrected" k10temp.

---

### Post by JKyleOKC on 2014-08-19
> **QIII said:**
> If you cruise the Windows forums, you will still find all sorts of posts with people saying just to assume the temperature is 10C higher than reported.  k8temp was the same way.

...snip...

So the system they have works in its own inscrutable way.  It's just irritating to not have an actual temperature.  Why not just make it an actual temperature and design the chips for the motherboard to react to that?We may have been "talking" past each other! I'm not seriously concerned about a lack of accuracy in the reading; what concerns me is that the reading absolutely NEVER varies even a tenth of a degree from 40.0 C. I get the impression that this "virtual sensor" is simply reporting a hard-coded value and actually no sensor at all is taking part.

I could live comfortably with an inaccurate reading, so long as it let me know when the chips were beginning to approach the frying point. The message in dmesg implied to me that the sensor was being totally ignored.

I'm also concerned that the f71882fg chip driver added into /etc/modules isn't being loaded, while k10temp IS. Makes me wonder whether there's more wrong here than I originally thought.

I just installed psensor in hopes that it might find other sensors -- and launched it from a terminal window in order to have a bit of control over it while learning its quirks. It immediately filled the window with one-line error messages that it was unable to contact the NVidia GPU0 sensor, and I found no way to keep it from trying to do so. My video in the system is a GeForce chip on the ASUS mobo; I've never been concerned about the GPU so never looked for a sensor there. The box itself is a low-end Compaq that predates Win7; it came from the factory with Vista on it but I replaced the HD almost immediately and installed only Xubuntu.

It did show that my HDD temp was holding steady at 41.0 while the Temp1 reading from the virtual sensor was at 40.0, exactly what the sensor applet in my top panel says...

---

### Post by QIII on 2014-08-19
Ah.  Sticky dial guage, so to speak?

---

### Post by Luis_A._Diaz on 2014-09-28
> **JKyleOKC said:**
> I've had a similar problem for years now on this machine and finally today decided to search for a solution. Unfortunately, here's what I get when I follow the suggestion:```
jk@mehitabel:~$ sudo modprobe k10temp force=1
jk@mehitabel:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +40.0°C  (crit = +75.0°C)

jk@mehitabel:~$ man k10temp

```Apparently I need to do a bit more than simply force the k10temp module. The acpitz reports 40 degrees at all times, regardless of the actual CPU load. If I look at the temperature using BIOS, it varies from time to time -- but to do that I must reboot, and I avoid rebooting as much as possible since this is Linux, not Windows.

Next step?
Manual temperature cant be access and freezes while in desktop

---

