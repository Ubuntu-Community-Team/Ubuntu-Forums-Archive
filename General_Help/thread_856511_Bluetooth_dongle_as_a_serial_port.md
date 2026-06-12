---
title: "Bluetooth dongle as a serial port"
date: 2008-07-11
forum: General Help
---

### Post by jonlemur on 2008-07-11
I'm working with a robot that runs embedded Linux, and I'm trying to get Bluetooth to work with it.  The robot has serial port connections on it that I've soldered onto with an RS232 port and I've gotten that to work with an RS232 to USB adapter connected to my computer.  Now I'm wanting to upgrade to Bluetooth, and to do so, I've connected a Bluetooth chip to the serial port on the robot, and I have a Bluetooth dongle for my computer.  My problem is I have no idea how to connect to the chip in a way that I can send commands.

With the RS232, I ran minicom and I could access the Linux filesystem on the robot and issue it commands.  So what would be ideal for me is use the dongle in a similar way to the RS232, where I could use minicom to communicate (i.e. call shell scripts) with the robot.

Any ideas on what I need to do to do that?

Also, my long term goal is to automate the robot from my computer.  I would like to set up a C++ (or python) interface with the Bluetooth.  Does anyone know a good way to go about this?

---

### Post by jonlemur on 2008-07-12
bump

---

### Post by metcalfe on 2008-07-20
re-bump. 

this is interesting stuff, i'd like to know cool things to do with my bluetooth dongle other than transferring files from and to the pc.

---

### Post by cmdowns on 2008-07-22
This sounds very similar to a project that I've been working on and is described in [this post](http://www.internettablettalk.com/forums/showpost.php?p=189331&postcount=44)

Basically what I did was to take an old RC car and replace the internal electronics with an Arduino uC coupled with a [Blue SMiRF Bluetooth modem from Sparkfun](http://www.sparkfun.com/commerce/product_info.php?products_id=8332).

I sent serial data to the BT modem from my Nokia n800 Internet Tablet, basically a handheld computer with Wifi and BT capability running a version of Linux as the OS.

I used a simple Python script to read commands from my tablet (just up, down, left and right on the directional pad). The script used pyGame and pySerial. Initially I worked the project over a hardwired USB connection. Recently I replaced the cable with the BT signal.

I used hcitool to scan for BT signals, and once that gave me the BT address, I used rfcomm to bind the address to a port. I functions just like the original USB connection did.

Hope that helps. Let me know if you have any other questions.

---

