---
title: "can't turn the wireless on"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by davidbe on 2007-06-04
ok, i have that no name laptop (ODM is FIC)
with centrino M740 platform and ipw2200 wireless card

I've installed ubuntu 7.04 and the wireless is stated "RADIO OFF" 
I've tried everything i could find in this forum:

1. echo 1/0 to the rf_kill file -  it switch between 2 and 3
2. iwconfig eth1 powr on / iwconfig eth1 txpower on - i get an error "Input/output error"
3. try loading the following moduls:
          a. acerhk - won't load "couldn't allocate memory"
          b.fsaa1655g - doesn't work
          c.rfsam  -  "no bios signature found"
          d.rfswitch-1.1 - won't load
4. searched my BIOS 
5. tried to set the wireless key to a value (Use 'setkeycodes 6d <keycode>' to make it known) -   maybe i hadn't used the correct keycode? i tried varius and can't recall witch.

anyone have suggestions?

oh, also, for some strange reason the "down" key always bring the "ubuntu help center" up, how could i change it?

---

### Post by teaker1s on 2007-06-05
if your wireless is built in then you may find a bios setting to force it always on.
As for your second request.
Sounds as if shortcuts are wrong
System>preferences>keyboard shortcuts

---

### Post by darwin_te on 2007-07-16
Hi,

For 7.04 using the latest kernel 2.6.22, I found the following script responsible for setting rf_kill to 2 (hardware radio frequecny off):

/etc/init.d/acpi-support which called:
/usr/share/acpi-support/state-funcs

The script state-funcs checked /sys/class/net/$DEVICE/device/power/state, which has different directory structure in latest kernel, and will flag wireless state as disabled if not found, which in turn will set rf_kill to 2.

Just modify the script state-funcs and it will now work.

---

