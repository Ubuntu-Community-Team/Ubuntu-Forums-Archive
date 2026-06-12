---
title: "Detection of battery status not working"
date: 2012-03-15
forum: Hardware
---

### Post by faabiioo on 2012-03-15
Hi,
what I'm experiencing these days has never happened before.

From the beginning: I have an Acer TravelMate 5730, which is 3 y.o., running 10.04 LTS. One year ago I changed the battery 'coz  the old one died. Since then, everything worked a charm.

Two days ago I was using my laptop running on battery; battery was charged up to 60%. Suddenly it shut down and for about 24h it was like the battery was totally broken: it didn't charge anymore and the '[FONT="Courier New"]upower --dump[/FONT]' said > state: critical
I was kind of resigned to buy a new battery, when suddenly the orange light became green: battery was charged and actually working.
But now, the battery indicator was staked to 100%. I tried again with '[FONT="Courier New"]upower --dump[/FONT]' or '[FONT="Courier New"]acpi -b[/FONT]' commands and it keeps saying battery is discharging, though maintaining the percentage to 100% and the energy to the top.

Right now I'm running on battery since 1 hour at least, and here it is:
> 
fabio@fabUntU:~$ upower --dump
...
Device: /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:06/PNP0C09:00/PNP0C0A:00/power_supply/BAT0
  vendor:               GW
  model:                CONIS51
  serial:               20626
  power supply:         yes
  updated:              Thu Mar 15 12:02:26 2012 (8 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    energy:              969.178 Wh
    energy-empty:        0 Wh
    energy-full:         969.178 Wh
    energy-full-design:  65.12 Wh
    energy-rate:         18.7516 W
    voltage:             14.536 V
    percentage:          100%
    capacity:            100%
    technology:          lithium-ion
  History (rate):
    1331809346	18.752	discharging
    1331809316	18.470	discharging
    1331809286	18.752	discharging
    1331809255	19.344	discharging

Daemon:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      yes
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes


I tried to use IBAM and it says '[FONT="Courier New"]No apm data available[/FONT]'; '[FONT="Courier New"]acpi -b[/FONT]' reports > Battery 0: Discharging, 100%, 49:43:22 remaining

'acpitool -B' says more or less the same.

I don't really know what else can I do, except count the hours I use it and try to avoid it to shut down.
ANY help is appreciated

Actually I'd like to know if this problem might be related to some hardware issues or, rather, ubuntu's daemon has stopped working properly or some other reasons.
I also forgot to mention that installing the battery-status package didn't change much: it keeps saying the battery is fully charged but discharging!

---

### Post by trundlenut on 2012-03-15
I think this is likely to be a problem with the battery.  I have a extra battery on my hp laptop which I picked for peanuts, it gives around 2 hours of power but the stats in ubuntu are sooo wrong.  Like yours it reports that it has 900 odd wh of power and calculates running times of several days.  If I boot into windows and use the hp battery checker utility it tells me it is knackered and needs replacing.

Fortunately I have the main battery as well so I don't get sudden shut downs.

---

### Post by faabiioo on 2012-03-16
> **trundlenut said:**
> I think this is likely to be a problem with the battery.  I have a extra battery on my hp laptop which I picked for peanuts, it gives around 2 hours of power but the stats in ubuntu are sooo wrong.  Like yours it reports that it has 900 odd wh of power and calculates running times of several days.  If I boot into windows and use the hp battery checker utility it tells me it is knackered and needs replacing.

Fortunately I have the main battery as well so I don't get sudden shut downs.

uhm...
actually my battery is really working fine, as it lasts up to 3 hours just like it was brand new.

what fails is the "estimate" of percentage of charge - actually it is totally messed up - as it always says it is at 100% and it is going to last forever, even though I've been running on battery for 2 hours.

btw, I checked this behaviour booting WinXP and the problem persists: battery is 100% charged and is going to last forever (which might sound amazing, though!)

up to this point I'm inclined to think that it is not an "Ubuntu's something" problem: It might be the BIOS gone messed up, or some other sensors or circuits devoted to tell the OS about battery status that are freaking out!

it would be nice to know how I could check whether these assumptions are true or not, and in case, how to act in order to fix it.

---

### Post by trundlenut on 2012-03-16
It will be the circuitry in the battery itself which is the problem which is why it occurs in both Ubuntu and WinXP.

---

### Post by faabiioo on 2012-03-16
> **trundlenut said:**
> It will be the circuitry in the battery itself which is the problem which is why it occurs in both Ubuntu and WinXP.

so you mean within the battery there's something that is in charge to tell the OS about battery status. and that is ****** up now!
well that's really annoying because the battery really works fine - so no reason to change it - but there's no way to know when it is going to be empty and save the pc from a brute shut down!

or... is there one? like some counter that keeps records of how long the laptop has been running (taking into account also stand-bys).
that would be nice!

---

### Post by trundlenut on 2012-03-16
> **faabiioo said:**
> so you mean within the battery there's something that is in charge to tell the OS about battery status. and that is ****** up now!
well that's really annoying because the battery really works fine - so no reason to change it - but there's no way to know when it is going to be empty and save the pc from a brute shut down!

or... is there one? like some counter that keeps records of how long the laptop has been running (taking into account also stand-bys).
that would be nice!

Type "uptime" into a terminal!

---

### Post by faabiioo on 2012-03-16
> **trundlenut said:**
> Type "uptime" into a terminal!

cool! and it considers the standby time

now just some scripting that will remembers me when ~180 minutes have expired!

I don't feel like I want to mark this thread as SOLVED! but it's a reasonable workaround.

thank you trundlenut

---

### Post by trundlenut on 2012-03-16
> **faabiioo said:**
> cool! and it considers the standby time

now just some scripting that will remembers me when ~180 minutes have expired!

I don't feel like I want to mark this thread as SOLVED! but it's a reasonable workaround.

thank you trundlenut

Conky could be a good way to give you a visible display on the desktop.  My setup just displays the uptime, but with a little fiddling you should be able to give you the remaining time based on a three hour capacity.

---

