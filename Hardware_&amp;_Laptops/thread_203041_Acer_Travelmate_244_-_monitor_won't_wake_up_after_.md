---
title: "Acer Travelmate 244 - monitor won't wake up after suspend to RAM"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by mhb on 2006-06-24
Hello everyone,
Ubuntu is working almost flawlessly on my Acer Travelmate 244FX laptop - and the only thing that troubles me is the wake up. I try the suspend to RAM (either using /etc/acpi/sleep.sh or /usr/share/hal/scripts/hal-system-power-suspend) and the machine gets suspended, but when I try to wake up the monitor won't wake up with it. The system itself wakes up (you can connect via ssh or so) but only a whole lot of vertical coloured lines 1px wide appear on the monitor. Switching to console won't help. I changed almost every single bit of configuration in /etc/default/acpi-support but with no luck. Has someone else encoutered such weird behaviour? Do you have any other suggestions that may solve this problem?

---

### Post by mikeoh on 2006-06-25
I have the same problem with a Acer Travelmate 2304.  Also hibernate doesn't work.  It will power down but on resume it just starts up normally instead of restoring the previous session.

---

### Post by hizaguchi on 2006-07-23
Same problem with an Aspire 5100 and acpi suspend.  Tried using apm, but just booting up with that enabled causes the computer to totally wig out in X.

---

### Post by Jorge on 2006-10-06
For that problem (and some other great tricks), go to:

[http://myy.helia.fi/~karte/acer_travelmate_3004wtmi_with_linux.html]("http://myy.helia.fi/~karte/acer_travelmate_3004wtmi_with_linux.html")

I hope it helps you, it did it for me. :)

---

### Post by isagani on 2007-10-11
I have an ACER Aspire 5570 and have exactly the same issue. My laptop suspends (just as it did pre-gutsy) and then wake up but with the display dead. It used to be fine pre-gutsy.

However hibernate (suspend-to-disk) does work properly.

---

### Post by zibi on 2008-07-04
I had the same problem in Hardy on a Travelamte 250. I solved it by substituting the /etc/default/acpi-support taken from an Acer Aspire with Gutsy to mine. Everything now is fine.

In case of need I can paste here the file.

Good Luck!

---

