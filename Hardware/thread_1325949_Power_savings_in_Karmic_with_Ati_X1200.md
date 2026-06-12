---
title: "Power savings in Karmic with Ati X1200"
date: 2009-11-13
forum: Hardware
---

### Post by smsmith050 on 2009-11-13
I am running Hardy and Karmic on an HP6715 laptop CPU=Turion TL-60 with ATi X1200 UMA graphics. 
I noticed the battery life is shorter with Karmic than Hardy.

Comparison Karmic and Hardy battery power - display on, wifi on, idle.

Hardy battery power 13.9W  bluetooth off, X1200 power saving enabled 
Karmic battery power 20.5W default
Enable power savings feature set hci0 (bluetooth) down
Karmic battery power 18.3W hci0 down
Enable power saving feature radeon X1200 power savings on
Karmic battery power 17W radeon power saving + hci0 down

So Karmic power goes down 3.5W by turning off bluetooth and enabling X1200 power saving features. 

Karmic with power saving features is still 3W higher than Hardy. 

To enable radeon X1200 power savings create an xorg.conf file with the following options, place it in the /etc/X11 directory

       Section "Device"
         Identifier "Builtin Default ati Device 0"
         Driver "radeon"
	 Option "ClockGating" "true"
         Option "ForceLowPowerMode" "true"
	 Option "DynamicPM" "true"
       EndSection

To disable bluetooth sudo hciconfig hci0 down

The reason Karmic takes more power is the CPU C1E percentage is 25% while Hardy gets a CPU C1E percentage of 64%. When the CPU is in C1E state the memory is self-refresh, the processor clocks are ramped down and the hyper-transport link is tri-stated.

Karmic may have a low C1E percentage because of the radeon driver. I can't prove it because the Karmic fglrx driver won't load. I think the radeon X1200 is too old for the Karmic fglrx driver.

---

### Post by Noahod on 2009-12-05
I am in the same boat as I have an X1600 that uses much more power. 

I think you will find it's not about the CPU power states, but more that the ati (open-source) driver does not support the power management features of the propriety driver, in particular, while it supports clocking down the gpu, it never reduces the voltage.

---

