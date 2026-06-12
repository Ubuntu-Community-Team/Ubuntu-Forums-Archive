---
title: "intel centrino N 1030 wireless issue"
date: 2011-08-05
forum: Hardware
---

### Post by Arijit_Kundu on 2011-08-05
Hi guys,

i am a regular linux user. I recently bought a notebook which has intel centrino N-1030 wifi card. This is configured right out of the box in ubuntu, but gives a strange problem. When i am connected to a fast wifi connection (>30 mbps), it works perfectly. But, when i am connected to a quite slow connection (i dont know why, but this connection sucks) ~ 2mbps, it almost stops working. But i can browse/ download from my other laptop, which has a broadcom card. 

what i tried already: tried to set the speed for wireless manually using "sudo iwconfig wlan0 rate 2M".

is this related to problems with "N" cards?

dmesg gives no obvious errors and the driver used is iwlagn. My kernel is 2.6.38-10, 64 bit ubuntu 11.04

thanks in advance!

---

### Post by Vega on 2011-09-01
Just an fyi this card has performance issues on Windows 7 x64, it's probably too new with a lot bugs.

I hope you find a solution, thought you'd might like to know.

---

### Post by Vega on 2011-09-12
Any luck on getting it to work?

---

### Post by silageman on 2011-10-03
hey i think i might be able to sort it out i had the same problem i think it's down to power management settings just do a:

iwconfig

look for your device, look for power management if it says it's turned on (Power Management: on)this may be your problem.

If so:

open terminal and paste this in:
sudo gedit /usr/lib/pm-utils/power.d/wireless

when that opens just change every "power on" you see to "power off"
and then save it
thats it, it worked for me mite be worth a try its only power management settings it wont do any harm anyways.

let me know how you get on.

---

### Post by Vega on 2011-11-08
well strange thing is that power management was off for this card same thing on windows.

I'm still getting 2 bars instead of 5 on my wireless icon on the menu bar.

---

### Post by silageman on 2011-11-08
what laptop have you got? mine is a dell inspiron N5010, with intel centrino N 1030, my card worked perfectly under windows7, but never worked under any linux distro.But what i suggested above sorted that out, How far are you away from the router and it mite be worth while opening the laptop up and check the antenna's connected rite. other than that check update the firmware on your router it mite not support N speeds. After that i just dont know man.

---

### Post by collisionystm on 2011-11-08
> **silageman said:**
> what laptop have you got? mine is a dell inspiron N5010, with intel centrino N 1030, my card worked perfectly under windows7, but never worked under any linux distro.But what i suggested above sorted that out, How far are you away from the router and it mite be worth while opening the laptop up and check the antenna's connected rite. other than that check update the firmware on your router it mite not support N speeds. After that i just dont know man.


I have the same card. My problem was opposite! Horrible in windows and perfect in linux.

I disabled power management in windows and it worked great.

vostro 3750

---

### Post by silageman on 2011-11-08
> **Vega said:**
> well strange thing is that power management was off for this card same thing on windows.

I'm still getting 2 bars instead of 5 on my wireless icon on the menu bar.

Also make sure you'r charger is plugged out when checking the iwconfig or else it will show "power management off" when charging and "power management on" when not plugged in

---

