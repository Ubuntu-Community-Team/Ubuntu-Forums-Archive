---
title: "hp elitebook 6930p: wireless switch not working"
date: 2008-12-15
forum: Hardware
---

### Post by suxen on 2008-12-15
hi there, 
i got a new hp6930p laptop. after installation (fan-always on disabled in bios) of ubuntu 8.10 amd64 alternate most things work, except wireless.
console screenshot:

>sudo ifconfig wlan0 down
>sudo ifconfig wlan0 up
>sudo iwlist wlan0 scanning
wlan0   No scan results
>dmesg
...
[ 2924.348129] iwlagn 0000:02:00.0: PCI INT A disabled
[ 2933.320469] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2933.320714] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[ 2933.328139] iwlagn: Radio disabled by HW RF Kill switch
[ 2933.348308] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2985.864068] CE: hpet increasing min_delta_ns to 15000 nsec

the wireless touchbutton/switch above the keyboard is always colored orange which, reading the manual, means "off". does not change when i touch it.


how can i activate the wireless-switch?

thank you in advance,
suxen

---

### Post by suxen on 2009-04-05
here is the solution i found to work:

-reboot and enter setup (presse esc-key)
-make a list of your bios configuration settings (in particular device settings, like the ahci/ide/raid setting)
-navigate to "restore defaults" in bios menu
-save changes
-re-apply your individual settings
-save and exit

after the next boot, your wireless led should change upon touching it and connecting to a wireless network should work.

good luck!

---

### Post by Kandi07 on 2009-06-16
worked for me!

Best regards,
Kandi07

---

### Post by maa3856 on 2009-06-20
Worked for me too!!  Thank you

---

### Post by zeroseven0183 on 2010-08-20
One year later... this thread is still helping other users. :)

Anyway, this should be mark as SOLVED.

---

### Post by cybermeid on 2010-10-24
I tried doing the sam what you told,but still its not working.Also wireless was working till last week,now all of a sudden,its not working,Can someone help me out with this.
O'm using an HP laptop.Its HP Pavillion dv6-3123cl
Also even if I connect to ethernet cable its  not working,it shows networking device not ready.

---

### Post by yugo4k on 2011-05-01
I've been battling with drivers for hours trying to fix the wireless that stopped working after I installed Ubuntu 10.04...
... the solution in this thread is over 5 years old and solved my problems in less than 5 minutes!

Thanks!

---

### Post by ervinodsingh on 2012-09-26
works great...

---

