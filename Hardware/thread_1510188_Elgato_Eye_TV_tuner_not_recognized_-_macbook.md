---
title: "Elgato Eye TV tuner not recognized - macbook"
date: 2010-06-15
forum: Hardware
---

### Post by shreepad.panth on 2010-06-15
I have a macbook 5,5 and I'm running lucid. I can't seem to get my elgato eye tv hybrid recognized although I'm sure I have the required firmware and em28xx modules loaded:

lsusb gives me the following:

```
Bus 004 Device 003: ID 05ac:8213 Apple, Inc. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 05ac:0236 Apple, Inc. 
Bus 003 Device 003: ID 05ac:8242 Apple, Inc. 
Bus 003 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0fd9:0027  
Bus 002 Device 004: ID 05ac:8403 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:8507 Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

0fd9:0027 is the device - it has the same hardware id that shows up when I plug it into OSX, but no vendor is recognized

dmesg gives me the following lines when I plug it in

```
[ 4036.876106] usb 2-2: new high speed USB device using ehci_hcd and address 5
[ 4037.011223] usb 2-2: configuration #1 chosen from 1 choice

```

Any one with similar problems?

---

### Post by shreepad.panth on 2010-06-16
anyone?

---

### Post by danlin on 2010-12-23
elgato eye-tv dtt isn't recognized at all... in lucid,maverick,natty...
no way to use with kaffeine, me-tv, w_scan... not any info on dmesg about which firmware to load... i tried to load module dvb-usb-dib0700 .

lsusb 
Bus 002 Device 006: ID 0fd9:003f  

this dvb-t usb is given as compatible on linux on linuxtv.org , but with different usb id...

some info from [http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices)

Elgato EyeTV DTT 	compatible?? = &#10004; Yes, in
kernel since 2.6.31 0fd9:0021 USB2.0 		
firmaware: dvb-usb-dib0700-1.20.fw 
clone of Hauppauge WinTV-NOVA-T 

ANY HELP PLEASE???

---

### Post by racoon2 on 2011-01-30
I too had the same problem. Same type and same ID (0fd9:003f). 
I managed to fix by editing and compiling v4l-dvb drivers. 
Here's how: 
1) Download the driver: 
    git clone git: / / linuxtv.org / media_build.git 
2) Download the source version of Linux you have (are required to compile these drivers). 
3) edit the file media_build / linux / drivers / media / dvb / dvb-usb / dvb-usb-ids.h 
4) modifies the code of the EyeTV DTT Deluxe 0x003f as below 
    # Define USB_PID_ELGATO_EYETV_DTT_Dlx 0x003f 
5) compile the driver with the command 'make' (not with build.sh, otherwise the covers you modify it) 
6) install the drivers with 'sudo make install'. 
7) reboot linux. 
I use vcl and kaffeine without problems.

My modules:
lsmod!grep dvb:

dvb_usb_dib0700       112675  0 
dib7000p               30338  2 dvb_usb_dib0700
dib0090                24354  1 dvb_usb_dib0700
dib7000m               15179  1 dvb_usb_dib0700
dib0070                 8742  2 dvb_usb_dib0700
dvb_usb                20556  1 dvb_usb_dib0700
dib8000                33011  1 dvb_usb_dib0700
dib9000                30236  1 dvb_usb_dib0700
dvb_core              102292  4 dib7000p,dvb_usb,dib8000,dib9000
dib3000mc              13052  1 dvb_usb_dib0700
rc_core                19732  8 dvb_usb_dib0700,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,dvb_usb,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
dibx000_common          7099  6 dvb_usb_dib0700,dib7000p,dib7000m,dib8000,dib9000,dib3000mc

Bye.
):P

---

