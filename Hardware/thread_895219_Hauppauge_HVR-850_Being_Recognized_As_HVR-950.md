---
title: "Hauppauge HVR-850 Being Recognized As HVR-950"
date: 2008-08-20
forum: Hardware
---

### Post by Joe531 on 2008-08-20
Hi folks,

I installed a Hauppauge HVR-850 using the instructions at [http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial](http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial). The problem is that Ubuntu thinks I'm using an HVR-950, which requires different firmware than the 850 model. Is there anyway to change this so the computer knows I'm using the right tuner?

It would also seem that the HVR-850 and the HVR-950q are the same tuner, except the 950q can tune into qam signals, whereas the 850 cannot. So I think they use the same firmware.

---

### Post by Joe531 on 2008-08-20
Heh, I was a bit tired when I posted this message last night. I think the real question is...

How do I change the driver for my tv tuner to the right one?

---

### Post by Joe531 on 2008-08-20
Here is the dmesg output:

[ 2456.326634] usb 7-2: new high speed USB device using ehci_hcd and address 3
[ 2456.463969] usb 7-2: configuration #1 chosen from 1 choice
[ 2456.464148] em28xx new video device (2040:651f): interface 0, class 255
[ 2456.464156] em28xx Doesn't have usb audio class
[ 2456.464158] em28xx #0: Alternate settings: 8
[ 2456.464160] em28xx #0: Alternate setting 0, max size= 0
[ 2456.464162] em28xx #0: Alternate setting 1, max size= 0
[ 2456.464165] em28xx #0: Alternate setting 2, max size= 1448
[ 2456.464167] em28xx #0: Alternate setting 3, max size= 2048
[ 2456.464169] em28xx #0: Alternate setting 4, max size= 2304
[ 2456.464171] em28xx #0: Alternate setting 5, max size= 2580
[ 2456.464173] em28xx #0: Alternate setting 6, max size= 2892
[ 2456.464176] em28xx #0: Alternate setting 7, max size= 3072
[ 2456.465925] em28xx #0: chip ID is em2882/em2883
[ 2456.628505] tuner' 0-0061: chip found @ 0xc2 (em28xx #0)
[ 2456.660322] em28xx #0: i2c eeprom 00: 1a eb 67 95 40 20 1f 65 d0 12 5c 03 82 1e 6a 18
[ 2456.660335] em28xx #0: i2c eeprom 10: 00 00 24 57 66 07 01 00 00 00 00 00 00 00 00 00
[ 2456.660346] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b 1c 00 00
[ 2456.660357] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 01 01 00 00 00 00
[ 2456.660369] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 2456.660380] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 2456.660391] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 18 03 34 00 30 00
[ 2456.660402] em28xx #0: i2c eeprom 70: 33 00 30 00 35 00 36 00 35 00 38 00 39 00 36 00
[ 2456.660414] em28xx #0: i2c eeprom 80: 00 00 1e 03 57 00 69 00 6e 00 54 00 56 00 20 00
[ 2456.660425] em28xx #0: i2c eeprom 90: 48 00 56 00 52 00 2d 00 38 00 35 00 30 00 00 00
[ 2456.660437] em28xx #0: i2c eeprom a0: 84 12 00 00 05 50 1a 7f d4 78 23 15 ff d0 18 85
[ 2456.660448] em28xx #0: i2c eeprom b0: 1f 00 00 00 04 84 0a 00 01 01 20 77 00 40 08 8e
[ 2456.660460] em28xx #0: i2c eeprom c0: 3d f0 74 02 01 00 01 79 4e 00 00 00 00 00 00 00
[ 2456.660471] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 2456.660483] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 2456.660494] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 2456.660506] EEPROM ID= 0x9567eb1a, hash = 0x8fa450b0
[ 2456.660509] Vendor/Product ID= 2040:651f
[ 2456.660511] AC97 audio (5 sample rates)
[ 2456.660513] 500mA max power
[ 2456.660515] Table at 0x24, strings=0x1e82, 0x186a, 0x0000
[ 2456.673060] tveeprom 0-0050: Hauppauge model 65301, rev A1C0, serial# 4034056
[ 2456.673066] tveeprom 0-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[ 2456.673070] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
[ 2456.673073] tveeprom 0-0050: audio processor is None (idx 0)
[ 2456.673075] tveeprom 0-0050: has radio
[ 2456.699239] xc2028 0-0061: creating new instance
[ 2456.699246] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[ 2456.701226] xc2028 0-0061: Error: firmware xc3028-v27.fw not found.
[ 2456.790534] tvp5150 0-005c: tvp5150am1 detected.
[ 2456.934967] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[ 2456.959201] tvp5150 debug 0-005c: i2c i/o error: rc == -19 (should be 1)
[ 2456.978166] tvp5150 debug 0-005c: i2c i/o error: rc == -19 (should be 1)
[ 2456.994154] tvp5150 debug 0-005c: i2c i/o error: rc == -19 (should be 1)
[ 2456.995213] xc2028 0-0061: attaching existing instance
[ 2456.995221] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[ 2456.995225] em28xx #0/2: xc3028 attached
[ 2456.995230] DVB: registering new adapter (em28xx #0)
[ 2456.995236] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[ 2456.995688] Successfully loaded em28xx-dvb
[ 2456.995694] em28xx #0: Found Hauppauge WinTV HVR 950
[ 2456.995731] hub 7-0:1.0: over-current change on port 3
[ 2457.014114] tvp5150 debug 0-005c: i2c i/o error: rc == -19 (should be 1)
[ 2457.014125] tvp5150 0-005c: *** unknown tvp3e04 chip detected.
[ 2457.014130] tvp5150 0-005c: *** Rom ver is 12.0
[ 2457.070051] tvp5150 debug 0-005c: i2c i/o error: rc == -19 (should be 1)
[ 2457.091011] tvp5150 debug 0-005c: i2c i/o error: rc == -19 (should be 1)

As you can see, it thinks my tuner is a 950, and not 850. I just need to find a way to fix that. :)

---

### Post by Joe531 on 2008-08-20
Does this have anything to do with my situation?

[http://www.nabble.com/HVR950Q-driver-for-LUM-td17994360.html](http://www.nabble.com/HVR950Q-driver-for-LUM-td17994360.html) The part with:

Impact: Certain DVB boards are not supported in Hardy.

Fix: Driver will be added to LUM as additional driver modules. The IDs
are unique. No degredation should be expected.

Testcase: Without the new modules the following cards will not work:
        { USB_DEVICE(0x2040, 0x7200),
                .driver_info = AU0828_BOARD_HAUPPAUGE_HVR950Q },
        { USB_DEVICE(0x2040, 0x7240),
                .driver_info = AU0828_BOARD_HAUPPAUGE_HVR850 },
        { USB_DEVICE(0x2040, 0x7210),
                .driver_info = AU0828_BOARD_HAUPPAUGE_HVR950Q },
        { USB_DEVICE(0x2040, 0x7217),
                .driver_info = AU0828_BOARD_HAUPPAUGE_HVR950Q },
        { USB_DEVICE(0x2040, 0x721b),
                .driver_info = AU0828_BOARD_HAUPPAUGE_HVR950Q },
        { USB_DEVICE(0x0fd9, 0x0008),
                .driver_info = AU0828_BOARD_HAUPPAUGE_HVR950Q },
        { USB_DEVICE(0x2040, 0x721f),
                .driver_info = AU0828_BOARD_DELL_HVR950Q },
        { USB_DEVICE(0x2040, 0x7280),
                .driver_info = AU0828_BOARD_DELL_HVR950Q },

---

### Post by tpost001 on 2009-01-28
Hi Joe531.  I saw at [http://www.avsforum.com/avs-vb/archive/index.php/t-1057089.html](http://www.avsforum.com/avs-vb/archive/index.php/t-1057089.html) that you finally got your HRV-850 to work.  Someone by the name of CityK had an idea and EUREKA you figured out how to get it to work.  For me the steps you must have taken to get it to work is confusing and I don't know what steps you took to undo what you did.  Is there any way you could write a How-to so the rest of us can get our HVR-850s working without out recreating all the problems you had to go through?

---

### Post by MountainX on 2009-02-24
I'm in the same situation. I'm trying to use the HVR-850 with Mythbuntu 8.10. The best instructions I have found so far are from here:
[http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html#comment-93273](http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html#comment-93273)

But they are for Feisty. Anyone know if this still applied? 
You would think that by now, things would not require building from source....


---------------------------------------------

For Ubuntu’s Feisty Fawn :

sudo su

apt-get install mercurial linux-headers-$(uname -r) linux-source build-essential

cd /lib/firmware

wget [http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz](http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz)

tar xvzf firmware_v4.tgz

hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental)

cd v4l-dvb-experimental

make

make install

reboot

sudo modprobe em2880-dvb

If on the next reboot, the card stops working the em2880-dvb module is not being loaded properly in Feisty. To fix this :

cd /etc/modprobe.d
sudo gedit dvbstick

then add this line to the new dvbstick file :
install em28xx /sbin/modprobe --ignore-install em28xx; /bin/sleep 2; /sbin/modprobe em2880-dvb

reboot and it should be back up and running.

---

