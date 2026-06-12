---
title: "Dell Latitude 4200 cannot read serial input through Cutecom"
date: 2012-12-12
forum: Hardware
---

### Post by shipscientist on 2012-12-12
Hi all,

I am currently using an old Dell Latitude 4200 as the main computer board on an autonomous surface vessel. I have Ubuntu 12.04 installed on it as well as ROS fuerte. 

However, when I connect serial devices (through USB ports), such as the GPS or the compass, I cannot get data out either in ROS or, more worryingly, in cutecom.

The computer has only one USB 2.0 port and therefore I have attached an external USB hub. Nevertheless, whenever I connect a USB stick to this hub, Ubuntu automatically mounts it. I also tried connecting the gps and the compass, and if I list into /dev I can see both ttyUSB0 and ttyUSB1. In addition, since I also modified the local rules in 10-local.rules within /etc/rules.d , I can see both devices listed also as usbgps and usbcompass respectively.

However, when I try to open /dev/USB* where * is either 0 or 1 or /dev/usbgps or /dev/usbcompass in Cutecom, I get the error "could not open ... ". SImilarly, ROS cannot read the data from either device.

If I do the same process on an equally old Dell laptop (although a different model) or on a Beagleboard XM I can open the devices both in ROS and in Cutecom, so they are indeed working.

I think the problem may be related with some missing drivers for my USB port, but I couldn't find anything about this on the online literature.

If anyone has any ideas, they'd be really appreciated as I spent the last 2 days trying to sort out the issue unsuccessfully.

If this is the wrong place to  post this question, could you let me know it: I'm new to the forums.

Thank you in advance!

---

### Post by shipscientist on 2012-12-12
Ok, my supervisor at university found a solution.

We ran sudo cutecom in the terminal and it worked, so this means that the problem was related to a missing permit of my account to access to the USB serial data (only root could access it).

Hence, if you encounter a similar problem, all you have to do is to modify the local rules by creating a file in /etc/udev/rules.d called 10-local.rules , where you specify to the Kernel the NAME, GROUP (the one of your account) and OWNER (your account) as well as the idProduct and idVendor (I'm sure yo can find more info on other posts!). In this way also other programs not run from sudo (or the root), such as ROS, can access the serial output from the USB device.

---

