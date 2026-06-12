---
title: "d250-1613 aspire one acpi problems, cpu temp too low etc"
date: 2009-12-04
forum: Hardware
---

### Post by vajorie on 2009-12-04
I'm having some weird problems with my brand new Aspire One (model: aod250-1613, the one that comes with Android). Briefly: 

(1) battery is reported to have "last full capacity" 5500mAh (design capacity is 5800mAh)

(2) cpu reports its heat around 25-27C even when it is very hot to the touch (by "acpi -V" as well as by files under /sys/... and /proc/acpi/battery/...)

(3) acerhdf and acer_wmi modules do not work (error: no such device)

Is anyone else with a d250 having these issues? I am wondering whether I have bad hardware or whether this is because of the BIOS or some such thing common to all aspire ones of model aod250-1613 or such... 

I have no idea what to do: use the laptop as is (but what if the hardware is failing), or try to get it fixed at Acer (they seem not very good at fixing things), or try to return it to Newegg (what if the new one has the same issues -assuming newegg accepts the return). And I worked really hard and long to set it up the way I wanted :(

I also sent an email to the kernel list (for item 2), so here it is for reference purposes (I don't have experience with filing bugs with the kernel, so they probably won't respond me because of some mistake I did in reporting the issue): [http://www.spinics.net/lists/linux-acpi/msg26078.html](http://www.spinics.net/lists/linux-acpi/msg26078.html)

What do you think? 

PS. I have Karmic (uptodate) and Arch (uptodate, kernel: 2.6.31) installed and both have the same problem.

update: also see [http://bugzilla.kernel.org/show_bug.cgi?id=11161](http://bugzilla.kernel.org/show_bug.cgi?id=11161) and [http://bugzilla.kernel.org/show_bug.cgi?id=14991](http://bugzilla.kernel.org/show_bug.cgi?id=14991)

---

### Post by fipeflip on 2009-12-26
I have exactly the same problems in Acer Aspire One d250 -1530 . No idea how to solve them.

---

### Post by vajorie on 2009-12-27
> **fipeflip said:**
> I have exactly the same problems in Acer Aspire One d250 -1530 . No idea how to solve them.

The other stuff should solve itself out with time, but I'm surprised you have the battery problem as well... I thought my motherboard or something was bad (replaced battery under warranty, still reports the same number). Huh..

---

### Post by fipeflip on 2009-12-28
> **vajorie said:**
> The other stuff should solve itself out with time, but I'm surprised you have the battery problem as well... I thought my motherboard or something was bad (replaced battery under warranty, still reports the same number). Huh..

Yes, I have the same battery issue since I bought the netbook and installed Ubuntu. By the way, do you know a an alternative way to control the temperature? Maybe by the BIOS?
Greetings.

---

### Post by vajorie on 2009-12-29
> **fipeflip said:**
> Yes, I have the same battery issue since I bought the netbook and installed Ubuntu. By the way, do you know a an alternative way to control the temperature? Maybe by the BIOS?
Greetings.

Nope... No way to control it (neither in windows nor in linux it seems) nor to check it (hwmonitors can see cpu temperature in windows).

By the way, I'm pretty sure the battery issue too is a hardware quirk --battery is reported to have lower full capacity than design capacity there as well (I used hwmonitor).

---

### Post by kenlegaspo on 2010-11-20
I know this is an old thread but I finally found something that worked for me. 

if you don't already have it installed, you'll have to install lm-sensors

```
sudo apt-get install lm-sensors
```

then 

```
sudo sensors-detect
```

some warnings.. but I said yes to all the Yes/No questions

The scan should find your cpu sensor and and will pick the correct module for you to load.

After I restarted,

I can just type ```
sensors
```

and this pops up:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +43.0°C  (crit = +90.0°C)   

The second temperature reading is the correct one.

---

