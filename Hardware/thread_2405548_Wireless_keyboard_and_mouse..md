---
title: "Wireless keyboard and mouse."
date: 2018-11-07
forum: Hardware
---

### Post by Doodaad on 2018-11-07
I am using a Logitech K270 keyboard keyboard and mouse. The problem is my receiver is on a usb port on the rear of my machine and I need to move it up front due to signal loss.
When I move it Linux will not detect it even after restarting. Unfortunately I do not have a wired keyboards that I can use. Is there a way that I can edit a config file somewhere and change the port it is on?

lsusb
Bus 003 Device 002: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I appreciate any help.

---

### Post by Autodave on 2018-11-07
I would try shutting the PC down, then move the receiver to your preferred port, then power back up and see if that works.

---

### Post by Doodaad on 2018-11-08
Did that and keyboard and mouse will not work until I move it back to the original usb port.

---

### Post by him610 on 2018-11-08
Maybe you have a defective front USB port. Do other USB devices work on the front USB port?

---

### Post by Autodave on 2018-11-08
Sounds like a bad port to me, also.  You could always get a USB extension cable to move the receiver closer to the keyboard.

---

### Post by him610 on 2018-11-08
A few years ago I bought a Logitech K400r wireless keyboard that came with a USB standoff, or extension about 1-1/2 inches long that was used with the Logitech Unifying Receiver. I can only assume the standoff/extension was added to circumvent excessive electro-magnetic interference from within the inside of a desktop, or laptop. I never found it necessary to use mine though.

+AutoDave
> get a USB extension cable Like this: [https://www.showmecables.com/usb-2-a-male-a-female-passive-extension-cable-6-inches?gclid=Cj0KCQiA2o_fBRC8ARIsAIOyQ-moqs53c61C_5IKtt4EkWvxjh0Hxp2bkkQ5UgELvJd3yH9ucKC8gAUaAm1bEALw_wcB]("https://www.showmecables.com/usb-2-a-male-a-female-passive-extension-cable-6-inches?gclid=Cj0KCQiA2o_fBRC8ARIsAIOyQ-moqs53c61C_5IKtt4EkWvxjh0Hxp2bkkQ5UgELvJd3yH9ucKC8gAUaAm1bEALw_wcB")

---

### Post by QIII on 2018-11-08
If you have a monitor with USB to PC connectivity, you could get an extension between the monitor and the computer, plug that into the PC USB port that works and then plug your wireless transceiver into the monitor.

I do that and the transceiver is a foot away from the keyboard and mouse.

I just have to make sure the stack of empty soda cans and snack wrappers doesn't get so high as to mess up the RF signal.

---

### Post by him610 on 2018-11-08
When was the last time you replaced the batteries in the wireless keyboard and mouse? They last a long time, but not forever. How far away is your keyboard/mouse combo from the Unifying Receiver? Are there any other sources of RFI nearby? Maybe, you have low amperage in your USB ports.

You could try swapping the ports of the Netgear AC600 wireless access adapter and the Logitech Unifying Receiver to see if that has any effect.

---

