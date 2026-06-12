---
title: "udev ignoring rules? any help appreciated! ubuntu 9.10"
date: 2009-11-03
forum: Hardware
---

### Post by M1GEO on 2009-11-03
I recently done a fresh install of Ubuntu 9.10.  Very pleased with it so far. I have been keeping up with the news on problems, etc.  Fortunately I have had none of the problems.  I do however have this issue: 

I have a piece of hardware for programming FPGA chips within Xilinx.  This causes many people major issues in Ubuntu.  I wrote a howto explaining how this works, and how to overcome the problems of getting the USB drivers to work, and offered a solution for fixing udev to load the firmware into the programmer.  This worked perfectly (and still does) on Ubuntu 9.04, MintLinux, Debian Lenny, etc.

However, when I try the same approach on Ubuntu 9.10, it does not work.  This is more than likely my own failing, rather than that of udev, but either way I would appreciate some help so I can update my howto...

From lsusb, I am given that the device I wish to upload firmware to is at:
> 
Bus 002 Device 011: ID 03fd:000d Xilinx, Inc. 

However, firmware is never loaded to the device.  The appropriate udev rules are given below.  This is the content of /etc/udev/rules.d/xusbdfwu.rules
> 
# version 0003
SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0008", MODE="666"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0007", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusbdfwu.hex -D $TEMPNODE"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0009", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xup.hex -D $TEMPNODE"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="000d", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_emb.hex -D $TEMPNODE"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="000f", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xlp.hex -D $TEMPNODE"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0013", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xp2.hex -D $TEMPNODE"
BUS=="usb", ACTION=="add", SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="0015", RUN+="/sbin/fxload -v -t fx2 -I /usr/share/xusb_xse.hex -D $TEMPNODE"


From previous experience, fxload sends various versions of firmware to the device, i.e. it is plugged in, firmware is sent, it restarts (with a different id), and different firmware is sent, etc etc.

However, none of this happens.  This is slightly out of my league.  I managed to stumble through with my knowledge when writing my howto originally, but, this problem is baffling me.  I've checked that all the files in /usr/share are readable, etc.

I monitor udev to see what happens when i plug in the programmer, and the output is shown below:
> 
george@transistor:~$ sudo udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[1257301401.579175] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-1 (usb)
KERNEL[1257301401.579330] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0 (usb)
UDEV  [1257301401.582417] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-1 (usb)
UDEV  [1257301401.587721] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0 (usb)

To be honest, I am not sure what is supposed to be shown here. I expected something telling me it was invoking fxload.

I also had a little dabble with fxload itself, and tried calling it like udev should do (according to the rules file).  However, this was not a fair test, as I had no real idea what I was doing.

Any help/explanation/etc, would be greatly received.  If you would like to know more about using Xilinx JTAG Programmers under Linux, visit my site, [Xilinx_JTAG_Linux]("http://www.george-smart.co.uk/wiki/Xilinx_JTAG_Linux").

Thanks in advance, 
Regards

George Smart
Department of Electronic & Electrical Engineering
University College London

---

### Post by rndhro on 2009-11-05
change "$TEMPNODE" to "$tempnode" in your xusbdfw.rules  worked for me,    hth     edit: just had a look at your page, you dont need to prelink the libusb-drivers for xilinx versions newer than 10.1, google for XIL_IMPACT_USE_LIBUSB enviroment variable. further there is no need to add the xilinx paths to $PATH, the settings(64).sh files do all this $XILINX, $PATH and $LD_LIBRARY_PATH stuff for you...

---

### Post by nesimi on 2009-11-07
Hi George and rndhro,
I have been suffering from installation of usb cable driver on Ubuntu. And now I am done with the driver. :p I think it is really related with the case of the word "tempnode". I  just changed the "TEMPNODE" to "tempnode" in xusbdfw.rules. That is what I have done apart from your howto, George. Now the led near the usb cable (showing the installation of firmware) and one of the discrete led (according to my test HDL code) is lighting. I think, we should write here a detailed howto for other Ubuntu users suffering from the same problem. Thank you again, guys.

PS: I am using ISE 11.1 Webpack on Ubuntu 9.10.

---

### Post by M1GEO on 2009-11-08
Thanks for the information guys.  Since posting this thread I have had several emails (over this weekend) about this issue.  I will update my website.  I will also adapt the site as suggested.

Regards.
George Smart

---

