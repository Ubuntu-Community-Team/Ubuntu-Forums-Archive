---
title: "asus k52jt touchpad"
date: 2015-05-02
forum: Hardware
---

### Post by Seth-666 on 2015-05-02
How can i activate mouse1/left mouse click?  asus k52jt. I search over the internet for tutorials and verified the installed driver and its ok i think... but can't fiind a button to enable it or install it ? 
pls help :( i

---

### Post by Pilot6 on 2015-05-03
What to you mean by "activate left mouse click"?
What touchpad do you have? Please give output of

xinput
dmesg | grep pnp

---

### Post by Seth-666 on 2015-05-03
i "repaire" it by eneble in bios uefi .

Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=9	[slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons               	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

[    0.371147] pnp: PnP ACPI init
[    0.371405] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.371504] pnp 00:03: Plug and Play ACPI device, IDs ETD0001 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.371544] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.373888] pnp: PnP ACPI: found 6 devices
is this ok ? what do you think ?

---

### Post by Pilot6 on 2015-05-03
You have an Elantech touchpad. It is supported by current Ubuntu versions.
Which Ubuntu version do you have and what is the issue?

---

### Post by Seth-666 on 2015-05-03
last ubuntu 14.04 . now only the video issue ... ati radeon 6370M, this mode of laptop has many bugs for linux ...

---

