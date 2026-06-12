---
title: "Lenovo T590 Thinkpad not charging"
date: 2021-04-21
forum: Hardware
---

### Post by Tupaq on 2021-04-21
Hello,

I have a Lenovo T590 Thinkpad with Ubuntu 20.04 installed on it. Today, when I unplugged the laptop to move it, I realized it would not charge once I plug it back in. I troubleshooted the obvious potential issues — different outlets, cord not fully connected, etc. — but nothing worked. I did a quick DuckDuckGo search and found [this link]("https://askubuntu.com/questions/1051209/battery-not-charging-but-detected"). I followed the instructions to turn off my laptop, enter BIOS, and turn off the built-in battery in "config". When I left BIOS, I thought everything was fine. My laptop immediately resumed charging, and I could move my laptop to other outlets and it would still start to charge again. However, after I took it out of suspend after a few minutes of inactivity, the same issue, not charging, occurred again. So I had to go back into BIOS again, and I saw that the "built-in battery" settings were still on, and that the laptop had not saved my original change. Thus, I am currently writing this on my laptop that is charging, but I cannot go into suspend else I have to shutdown and then reenter BIOS.

I was wondering if anyone knows how to force my T590 laptop to save my settings. For the record, I purchased my laptop with Windows pre-installed, but I install Ubuntu 20.04 on it immediately upon receiving it in the post from Amazon, so I never setup Windows. Another piece of information that might be of interest is that, not long after I started using my new laptop, the BIOS settings attempted — and failed — to update; however, the BIOS have never attempted to update again, and since I have no other issues with this laptop, I ignored the issue.

---

### Post by Tupaq on 2021-04-21
I have further information, in the form of an output from the terminal when I input ```
upower -i /org/freedesktop/UPower/devices/battery_BAT0
```.

```
  native-path:          BAT0
  vendor:               SMP
  model:                02DL012
  serial:               559
  power supply:         yes
  updated:              Wed 21 Apr 2021 03:27:12 PM PDT (44 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    warning-level:       none
    energy:              54.17 Wh
    energy-empty:        0 Wh
    energy-full:         57.02 Wh
    energy-full-design:  57.02 Wh
    energy-rate:         0 W
    voltage:             12.822 V
    percentage:          95%
    capacity:            100%
    technology:          lithium-polymer
    icon-name:          'battery-full-charged-symbolic'


```

---

### Post by Tupaq on 2021-04-21
And this is the output I get now that I've woke the laptop after suspend:

```
  native-path:          BAT0
  vendor:               SMP
  model:                02DL012
  serial:               559
  power supply:         yes
  updated:              Wed 21 Apr 2021 03:34:47 PM PDT (30 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              54.14 Wh
    energy-empty:        0 Wh
    energy-full:         57.02 Wh
    energy-full-design:  57.02 Wh
    energy-rate:         0.857 W
    voltage:             12.805 V
    time to empty:       2.6 days
    percentage:          94%
    capacity:            100%
    technology:          lithium-polymer
    icon-name:          'battery-full-symbolic'
  History (charge):
    1619044487    94.000    discharging
  History (rate):
    1619044487    0.857    discharging


```

I'd also noted that whereas I used to just be able to hit the keyboard for the login prompt after suspend, now I need to tap the power button. I hope I'm not posting excessively but I want to give everyone willing to help as much information as possible.

---

### Post by Yellow Pasque on 2021-04-22
Is is your BIOS/EFI up to date?
[https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t590-type-20n4-20n5/downloads/ds539061-bios-update-utility-bootable-cd-for-windows-10-64-bit-and-linux-thinkpad-t490-t590-p53s-p43s](https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t590-type-20n4-20n5/downloads/ds539061-bios-update-utility-bootable-cd-for-windows-10-64-bit-and-linux-thinkpad-t490-t590-p53s-p43s)

---

### Post by Tupaq on 2021-04-22
Hello everyone. While my BIOS failed to update (as per my earlier post), I was able to fix the problem, simply by going into BIOS again and redoing the process over. It stuck this time and so I no longer feel I need help.

---

