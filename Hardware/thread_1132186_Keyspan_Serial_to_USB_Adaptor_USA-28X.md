---
title: "Keyspan Serial to USB Adaptor USA-28X"
date: 2009-04-21
forum: Hardware
---

### Post by tidris on 2009-04-21
When I recently tried to use my Keyspan usa-28x serial to usb adaptor under intrepid 8.10 kernel 2.6.27-11 I couldn't get it to work. I eventually learned that although intrepid 8.10 comes with the keyspan device driver built in, the firmware necessary to support any of the keyspan usa-XXX models is not included. This is apparently because the firmware for those models is only available in binary form and the ubuntu/debian developers don't like that.

So where can one get the firmware for the usa-XXX adaptors? It turns out all the necessary firmware is actually in the kernel source, but it is in a HEX format the keyspan driver can't use directly. To get get the *.fw files the driver likes, the kernel has to be compiled with the right options. I am not going to explain how to compile the kernel because there already are many threads on that topic (very short summary: you use "make menuconfig" followed by "make"). The key detail here is that the .config file has to have 

CONFIG_FIRMWARE_IN_KERNEL=y

After the kernel is compiled, the *.fw files (for example, usa28x.fw for my adapter) can be found in the firmware/keyspan/ subdirectory of the freshly compiled kernel. On the kernel I use these files show up:

firmware/keyspan/mpr.fw
firmware/keyspan/usa19qw.fw  
firmware/keyspan/usa28xb.fw
firmware/keyspan/usa18x.fw
firmware/keyspan/usa19w.fw
firmware/keyspan/usa28x.fw
firmware/keyspan/usa19.fw
firmware/keyspan/usa28.fw
firmware/keyspan/usa49w.fw
firmware/keyspan/usa19qi.fw
firmware/keyspan/usa28xa.fw
firmware/keyspan/usa49wlc.fw

To use them they have to be copied to the /lib/firmware/keyspan/ directory. There is no need to reboot, but for best results the keyspan adaptor should be unplugged before copying the *.fw files. 

If you did things right, when the keyspan adaptor is plugged in you will see /dev/ttyUSB* files show up, where * is a number depending on how many ports your adaptor has. In my case I get /dev/ttyUSB0 and /dev/ttyUSB1 because my adaptor has two serial ports in it. When the adaptor is unplugged the /dev/ttyUSB* files will go away. 

I hope that info keeps someone from wasting hours of valuable time researching this.

---

### Post by Chaim Leib on 2009-10-20
This is an update for Jaunty 9.04 users.

To get my keyspan device working for my system, I combined the info from tidris and gary ([http://scie.nti.st/2008/3/13/keyspan-usb-to-serial-adapter-support-in-ubuntu](http://scie.nti.st/2008/3/13/keyspan-usb-to-serial-adapter-support-in-ubuntu)) to come up with this walkthrough.  For this to work, make sure that you have third-party sources enabled in the Software Sources prefs.

A warning: this set of steps compiles and installs a custom kernel. Meaning, this is the linux equivalent of voiding a warranty.  You assume responsibility for what happens to your computer. I do not guarantee that this works -- it just worked for me (Fujitsu Lifebook N6420, Intel Core 2 T5500@1.67Ghz).

Step 1: Execute the following in the terminal.
```

$ mkdir ~/kernel
$ cd ~/kernel
$ sudo apt-get source linux-image-2.6.28-16-generic 
$ cd linux-2.6.28/debian.master/config/

```Step 2: Now, execute
```
$ sudo gedit i386/config
``` or ```
 $ sudo gedit amd64/config
``` depending on your processor architecture.  If you don't know which processor architecture is yours, it doesn't hurt to change both the config files.  

Step 3: You need to make changes in two places:
Search for a line containing "CONFIG_FIRMWARE_IN_KERNEL", and change it to read
```
CONFIG_FIRMWARE_IN_KERNEL=y
```Then, search for a line containing "CONFIG_USB_SERIAL_KEYSPAN".  Change this area of the text file to be like this:
```

...
# CONFIG_USB_SERIAL_IUU is not set
CONFIG_USB_SERIAL_KEYSPAN=m
# added by Chaim Leib:
CONFIG_USB_SERIAL_KEYSPAN_MPR=y
CONFIG_USB_SERIAL_KEYSPAN_USA28=y
CONFIG_USB_SERIAL_KEYSPAN_USA28X=y
CONFIG_USB_SERIAL_KEYSPAN_USA28XA=y
CONFIG_USB_SERIAL_KEYSPAN_USA28XB=y
CONFIG_USB_SERIAL_KEYSPAN_USA19=y
CONFIG_USB_SERIAL_KEYSPAN_USA18X=y
CONFIG_USB_SERIAL_KEYSPAN_USA19W=y
CONFIG_USB_SERIAL_KEYSPAN_USA19QW=y
CONFIG_USB_SERIAL_KEYSPAN_USA19QI=y
CONFIG_USB_SERIAL_KEYSPAN_USA49W=y
CONFIG_USB_SERIAL_KEYSPAN_USA49WLC=y
# end of added section
CONFIG_USB_SERIAL_KEYSPAN_PDA=m
CONFIG_USB_SERIAL_KLSI=m
...
```
Step 4: Once the "config" file is saved to the hard drive, jump back to the terminal and run the following as root:
```

# cd ../..
# debian/rules binary-generic
# cd ..
# dpkg -i linux-image*.deb linux-headers*.deb

```
Step 5: The device drivers should now be installed. After a reboot, plug in your adapter, and you should see some output when running these:
```
$ dmesg | tail -n 15
$ ls /dev/ttyUSB*
```

Cheers!

---

