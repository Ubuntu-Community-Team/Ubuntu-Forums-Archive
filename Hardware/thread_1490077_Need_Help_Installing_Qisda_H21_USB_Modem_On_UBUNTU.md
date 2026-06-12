---
title: "Need Help Installing Qisda H21 USB Modem On UBUNTU LUCID 10.04"
date: 2010-05-21
forum: Hardware
---

### Post by emcube009 on 2010-05-21
Guys
I bought a H21 USB Modem. When i inserted it. a cd drive  appeared. i opened it a found installation folders of different os( MAC  WINDOWS LINUX)
I open the linux folder n found the source code(which i  compiled to create the usb switch for the modem) and instruction  manual.
I was able to complete upto step five but still d device is  not communicating as a modem

{1. Open Terminal (Ctrl + Alt + T),  enter the following instruction:
sudo apt-get install libusb-dev wget  build-essential
2. EP0_Switch_Utility.cpp crawl source as a file  compiled into execution switch
3. Compile:
g + +  EP0_Switch_Utility.cpp-lusb-o switch
4. Will execute the copy switch  files to / sbin
 CONTENTS: sudo cp switch / sbin /
5.1 Add the  following documents to ensure that the H21 can each execute when linked  switching.

sudo gedit / etc/udev/rules.d/50-h21.rules
In this  file, add the following two of instructions and storage:

SUBSYSTEM  == "usb", SYSFS (idProduct) == "F000",
SYSFS (idVendor) == "1DA5",  RUN + = "/ sbin / switch"

6. Insert H21, executive confirmed:
ls  / dev / ttyUSB *
If there are three USB devices generate, H21 is  connected to the normal line of order.
/ Dev/ttyUSB0 / dev/ttyUSB1 /  dev/ttyUSB2

7. Open the Terminal (Ctrl + Alt + T) and enter the  following instructions to H21 mounted on the future Linux:
modprobe  usbserial product = 0x4512 vendor = 0x1DA5 maxSize = 2048
8. Will  yield to establish the future of the modem port in the / dev / modem in:
ln-s-f  / dev / usb / ttyUSB / dev / modem
9 new (modified) / etc /  modprobe.conf, add the following:
options usbserial vendor = 0x1da5  product = 0x4512
(The part of the changes is to use the order H21  modem driver usbserial module.)
10. Sure / etc / modules of content  that contain usbserial, if not advised to exercise together. As
Automatic  Automatic loading usbserial module in future.}


Find  attachement the source code

Thank you very much

---

