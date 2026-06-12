---
title: "Installing Terratec Cinergy Hybrid T USB XS in Ubuntu 9.04"
date: 2009-08-08
forum: Hardware
---

### Post by stefboombastic on 2009-08-08
Hi all!

I've been getting mad trying to make my Terratec Cinergy Hybrid T USB XS ([http://www.terratec.it/prodotti/schede_tv/cinergy_hybrid_xs.shtml](http://www.terratec.it/prodotti/schede_tv/cinergy_hybrid_xs.shtml)) work in Ubuntu for days!
Previously I managed to do it very easily in Ubuntu 8.04 using Markus Rechberger's project ([http://mcentral.de/wiki/index.php5/Main_Page](http://mcentral.de/wiki/index.php5/Main_Page)) following the procedure described in [http://divilinux.netsons.org/index.php/archives/192](http://divilinux.netsons.org/index.php/archives/192) 
After formatting my Ubuntu I discovered that Markus Rechberger discontinued his work, and his repository is not more available :(
He did not reply to my email where I begged for an old source ..
I've been through hundreds of reinstallations of different kernels and thousands of posts and different ways vainly..
Finally I did it with Ubuntu 9.04 kernel 2.6.28-14-generic, and now all works great, so I report my procedure for people who may be in the same problem:

Tested succesfully in Ubuntu 9.04 Kernel 2.6.28-14-generic and also in 2.6.28-15-generic with Terratec Cinergy Hybrid T USB XS with USB ID: 0ccd:0042
There are different releases of the same card, I don't know if they differ for country.. but as far as I understoood, they need different firmwares. I could only test the following procedure on my card which USB ID is 0ccd:0042
To check  the USB id of Your card type:
```
lsusb
```
having attached the card.
It would be very useful if U posted IDs of other Cinergy XS working with my procedure!!   

NOTE: after updating from kernel 2.6.28-14-generic to 2.6.28-15-generic the card stopped working; the drivers were not loaded at startup even reloading the always with:

```
sudo modprobe em28xx 
sudo modprobe em28xx-dvb
```
The card was not working more! 
Luckily repeating the following procedure, that is, uninstalling drivers compiled for kernel 2.6.28-14-generic, and recompiling for the new kernel 2.6.28-15-generic, the card started to work again :)

*** Prerequisites ***

Install mercurial:
```
sudo apt-get install mercurial
```
Install kernel headers:
```
sudo apt-get install linux-headers-$(uname -r)
```
Install g++:
```
sudo apt-get install g++
```

UNPLUG THE DEVICE IF PLUGGED

*** Removing old drivers if any ***

If the modules em28xx and em28xx-dbv are already loaded then unload them
```
sudo rmmod -f em28xx-dvb
sudo rmmod -f em28xx
```
uninstall other versions of drivers if any, by executing:
```
sudo make unload
sudo make rminstall
```
in each of the following folders:
- v4l-dvb
- v4l-dvb-kernel  (mcentral hg copy)
- ttxs-remote

Even though You have a clean version of the kernel, having not installed other versions of the drivers, You have to remove the drivers shipped with Ubuntu 9.04 kernel.
For doing that download Devin Heitmueller's drivers:
```
cd ~
mkdir terratec-xs
cd terratec-xs 
hg clone http://linuxtv.org/hg/~dheitmueller/v4l-dvb-terratec-xs
```
Then remove drivers shipped with the kernel:  
```
cd v4l-dvb-terratec-xs
sudo make unload
sudo make rminstall
```

*** Installing the new drivers ***

Make the new drivers (You have to be inside the folder where You downloaded the drivers, see previous point):
```
sudo make
```
Install them:
```
sudo make install
```
REBOOT!!

Load drivers for analogic TV:
```
sudo modprobe em28xx 
```
Load drivers for DVB:
```
sudo modprobe em28xx-dvb
```
Check if modules are loaded fine with:
```
lsmod
```

*** Install firmware ***

GET & INSTALL FIRMWARE xc3028-v27.fw as described here:
[http://forum.ubuntu-it.org/index.php/topic,298450.msg2235209.html#msg2235209](http://forum.ubuntu-it.org/index.php/topic,298450.msg2235209.html#msg2235209)
For all those who don't want to go through all the steps described in the previous post for getting the firmware file, I have attached the firmware compiled on my Ubuntu 9.04 Kernel 2.6.28-14-generic. You can simply download it, unzip and then type:
```
sudo cp xc3028-v27.fw /lib/firmware
```


*** Checking results ***

Check device informations from /var/log/messages:
```
sudo tail -f /var/log/messages
``` 
leaving the consolle open PLUG the device!
You should see something alike:
[HTML]Aug  8 08:51:29 Stefano-PC kernel: [   17.938901] skge eth1: enabling interface
Aug  8 08:51:29 Stefano-PC kernel: [   17.942188] ADDRCONF(NETDEV_UP): eth1: link is not ready
Aug  8 08:51:29 Stefano-PC kernel: [   17.943296] eth0: link down
Aug  8 08:51:29 Stefano-PC kernel: [   17.943440] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  8 08:51:30 Stefano-PC kernel: [   19.625707] skge eth1: Link is up at 100 Mbps, full duplex, flow control both
Aug  8 08:51:30 Stefano-PC kernel: [   19.625853] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug  8 08:57:31 Stefano-PC kernel: [  380.539673] Linux video capture interface: v2.00
Aug  8 08:57:31 Stefano-PC kernel: [  380.604364] usbcore: registered new interface driver em28xx
Aug  8 08:57:31 Stefano-PC kernel: [  380.604368] em28xx driver loaded
Aug  8 08:57:43 Stefano-PC kernel: [  392.858640] Em28xx: Initialized (Em28xx dvb Extension) extension
Aug  8 08:59:07 Stefano-PC kernel: [  476.780015] usb 1-3: new high speed USB device using ehci_hcd and address 2
Aug  8 08:59:07 Stefano-PC kernel: [  476.921029] usb 1-3: configuration #1 chosen from 1 choice
Aug  8 08:59:07 Stefano-PC kernel: [  476.921216] em28xx: New device TerraTec Electronic GmbH Cinergy Hybrid T USB XS @ 480 Mbps (0ccd:0042, interface 0, class 0)
Aug  8 08:59:07 Stefano-PC kernel: [  476.921222] em28xx #0: Identified as Terratec Hybrid XS (card=11)
Aug  8 08:59:07 Stefano-PC kernel: [  476.921299] em28xx #0: chip ID is em2882/em2883
Aug  8 08:59:07 Stefano-PC kernel: [  477.078681] em28xx #0: i2c eeprom 00: 1a eb 67 95 cd 0c 42 00 50 12 5c 03 9e 32 6a 34
Aug  8 08:59:07 Stefano-PC kernel: [  477.078695] em28xx #0: i2c eeprom 10: 00 00 06 57 46 07 00 00 00 00 00 00 00 00 00 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078708] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 31 00 b8 00 14 00 5b 00 00 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078721] em28xx #0: i2c eeprom 30: 00 00 20 40 20 6e 02 20 10 01 00 00 00 00 00 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078733] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078745] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078757] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 34 03 54 00 65 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078769] em28xx #0: i2c eeprom 70: 72 00 72 00 61 00 54 00 65 00 63 00 20 00 45 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078782] em28xx #0: i2c eeprom 80: 6c 00 65 00 63 00 74 00 72 00 6f 00 6e 00 69 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078794] em28xx #0: i2c eeprom 90: 63 00 20 00 47 00 6d 00 62 00 48 00 00 00 32 03
Aug  8 08:59:07 Stefano-PC kernel: [  477.078806] em28xx #0: i2c eeprom a0: 43 00 69 00 6e 00 65 00 72 00 67 00 79 00 20 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078819] em28xx #0: i2c eeprom b0: 48 00 79 00 62 00 72 00 69 00 64 00 20 00 54 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078831] em28xx #0: i2c eeprom c0: 20 00 55 00 53 00 42 00 20 00 58 00 53 00 00 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078843] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078855] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078867] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Aug  8 08:59:07 Stefano-PC kernel: [  477.078881] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x303d5d95
Aug  8 08:59:07 Stefano-PC kernel: [  477.078883] em28xx #0: EEPROM info:
Aug  8 08:59:07 Stefano-PC kernel: [  477.078885] em28xx #0:^IAC97 audio (5 sample rates)
Aug  8 08:59:07 Stefano-PC kernel: [  477.078886] em28xx #0:^I500mA max power
Aug  8 08:59:07 Stefano-PC kernel: [  477.078889] em28xx #0:^ITable at 0x06, strings=0x329e, 0x346a, 0x0000
Aug  8 08:59:07 Stefano-PC kernel: [  477.088462] tvp5150 0-005c: chip found @ 0xb8 (em28xx #0)
Aug  8 08:59:07 Stefano-PC kernel: [  477.095964] tuner 0-0061: chip found @ 0xc2 (em28xx #0)
Aug  8 08:59:07 Stefano-PC kernel: [  477.122746] xc2028 0-0061: creating new instance
Aug  8 08:59:07 Stefano-PC kernel: [  477.122750] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
Aug  8 08:59:07 Stefano-PC kernel: [  477.122757] i2c-adapter i2c-0: firmware: requesting xc3028-v27.fw
Aug  8 08:59:07 Stefano-PC kernel: [  477.148297] xc2028 0-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
Aug  8 08:59:07 Stefano-PC kernel: [  477.196011] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
Aug  8 08:59:08 Stefano-PC kernel: [  478.093577] xc2028 0-0061: Loading firmware for type=(0), id 000000000000b700.
Aug  8 08:59:08 Stefano-PC kernel: [  478.107449] SCODE (20000000), id 000000000000b700:
Aug  8 08:59:08 Stefano-PC kernel: [  478.107454] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
Aug  8 08:59:08 Stefano-PC kernel: [  478.288095] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/input/input6
Aug  8 08:59:08 Stefano-PC kernel: [  478.292453] em28xx #0: Config register raw data: 0x50
Aug  8 08:59:08 Stefano-PC kernel: [  478.293200] em28xx #0: AC97 vendor ID = 0xffffffff
Aug  8 08:59:08 Stefano-PC kernel: [  478.294448] em28xx #0: AC97 features = 0x6a90
Aug  8 08:59:08 Stefano-PC kernel: [  478.294451] em28xx #0: Empia 202 AC97 audio processor detected
Aug  8 08:59:08 Stefano-PC kernel: [  478.412456] tvp5150 0-005c: tvp5150am1 detected.
Aug  8 08:59:08 Stefano-PC kernel: [  478.508831] em28xx #0: v4l2 driver version 0.1.2
Aug  8 08:59:09 Stefano-PC kernel: [  478.574928] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
Aug  8 08:59:09 Stefano-PC kernel: [  478.644156] xc2028 0-0061: attaching existing instance
Aug  8 08:59:09 Stefano-PC kernel: [  478.644161] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
Aug  8 08:59:09 Stefano-PC kernel: [  478.644163] em28xx #0/2: xc3028 attached
Aug  8 08:59:09 Stefano-PC kernel: [  478.644166] DVB: registering new adapter (em28xx #0)
Aug  8 08:59:09 Stefano-PC kernel: [  478.644169] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...
Aug  8 08:59:09 Stefano-PC kernel: [  478.644447] Successfully loaded em28xx-dvb
Aug  8 08:59:09 Stefano-PC kernel: [  478.750702] usbcore: registered new interface driver snd-usb-audio
Aug  8 08:59:09 Stefano-PC kernel: [  478.761210] tvp5150 0-005c: tvp5150am1 detected.
Aug  8 08:59:09 Stefano-PC pulseaudio[3015]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume[/HTML]
Other informations can be got checking dmesg: 
```
dmesg | grep em28xx
```
If You get something alike the following:
[HTML][  380.604364] usbcore: registered new interface driver em28xx
[  380.604368] em28xx driver loaded
[  476.921216] em28xx: New device TerraTec Electronic GmbH Cinergy Hybrid T USB XS @ 480 Mbps (0ccd:0042, interface 0, class 0)
[  476.921222] em28xx #0: Identified as Terratec Hybrid XS (card=11)
[  476.921299] em28xx #0: chip ID is em2882/em2883
[  477.078681] em28xx #0: i2c eeprom 00: 1a eb 67 95 cd 0c 42 00 50 12 5c 03 9e 32 6a 34
[  477.078695] em28xx #0: i2c eeprom 10: 00 00 06 57 46 07 00 00 00 00 00 00 00 00 00 00
[  477.078708] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 31 00 b8 00 14 00 5b 00 00 00
[  477.078721] em28xx #0: i2c eeprom 30: 00 00 20 40 20 6e 02 20 10 01 00 00 00 00 00 00
[  477.078733] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  477.078745] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  477.078757] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 34 03 54 00 65 00
[  477.078769] em28xx #0: i2c eeprom 70: 72 00 72 00 61 00 54 00 65 00 63 00 20 00 45 00
[  477.078782] em28xx #0: i2c eeprom 80: 6c 00 65 00 63 00 74 00 72 00 6f 00 6e 00 69 00
[  477.078794] em28xx #0: i2c eeprom 90: 63 00 20 00 47 00 6d 00 62 00 48 00 00 00 32 03
[  477.078806] em28xx #0: i2c eeprom a0: 43 00 69 00 6e 00 65 00 72 00 67 00 79 00 20 00
[  477.078819] em28xx #0: i2c eeprom b0: 48 00 79 00 62 00 72 00 69 00 64 00 20 00 54 00
[  477.078831] em28xx #0: i2c eeprom c0: 20 00 55 00 53 00 42 00 20 00 58 00 53 00 00 00
[  477.078843] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  477.078855] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  477.078867] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  477.078881] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x303d5d95
[  477.078883] em28xx #0: EEPROM info:
[  477.078885] em28xx #0:	AC97 audio (5 sample rates)
[  477.078886] em28xx #0:	500mA max power
[  477.078889] em28xx #0:	Table at 0x06, strings=0x329e, 0x346a, 0x0000
[  477.088462] tvp5150 0-005c: chip found @ 0xb8 (em28xx #0)
[  477.095964] tuner 0-0061: chip found @ 0xc2 (em28xx #0)
[  478.288095] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/input/input6
[  478.292453] em28xx #0: Config register raw data: 0x50
[  478.293200] em28xx #0: AC97 vendor ID = 0xffffffff
[  478.294448] em28xx #0: AC97 features = 0x6a90
[  478.294451] em28xx #0: Empia 202 AC97 audio processor detected
[  478.508831] em28xx #0: v4l2 driver version 0.1.2
[  478.574928] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[  478.644163] em28xx #0/2: xc3028 attached
[  478.644166] DVB: registering new adapter (em28xx #0)
[  478.644447] Successfully loaded em28xx-dvb
[  478.663130] em28xx audio device (0ccd:0042): interface 1, class 1
[  478.663170] em28xx audio device (0ccd:0042): interface 2, class 1[/HTML]
then all is ok :) 

*** Install software for watching TV and scan for channels ***

- kaffeine:
```
sudo apt-get install kaffeine
```
If everything was fine kaffeine should detect the device (though with another name,for me Zarlink MT352 DVB-T)
Open the new menu called DVB.
Push channels -> Start Scan
If everything was fine it creates a list of channels and You can watch them :)

- GXINE o VLC

We have to create a channel list for our player.
At first we have to scan frequencies. There is an automatic way to go, and a manual.
I'll go with automatic by using the tool w_scan:
Therefore let's install w_scan:
```
sudo apt-get install w_scan
```

Let it make a scan, writing the results in a file (AutoFrequencies) that we are going to use for creating the channels list:
```
w_scan -x > AutoFrequencies
```

For parsing the frequencies into a channels list we need another tool from DVB-utils, so let's install:
```
sudo apt-get install dvb-utils
```
Finally let's create the channels file
```
scan AutoFrequencies > channels.conf
```

- if we want to use gxine
Install gxine:
```
sudo apt-get install gxine
```
Copy the channels file into xine folder so that it will be imported automatically: 
```
sudo cp channels.conf ~/.xine
```

Open gxine, and start DVB with File -> DVB
The channels list is in File -> Playlist

- If we want to use VLC
Install VLC:
```
sudo apt-get install vlc
```

Open VLC.
Open the channels file:
Media -> open File
select filter "all files" and load channels.conf created previously.
You can find the channles list in:
Playlist -> Mostra playlist

** REMOTE CONTROL **
For me, the remote control was already working after that.. 
If not for You:
```
cd ~
cd terratec-xs
hg clone http://kernellabs.com/hg/~dheitmueller/ttxs-remote
cd ttxs-remote
sudo make
sudo make install
```
REBOOT

Enjoy! :popcorn:


THANKS TO: Devin Heitmueller for working drivers and to Mauro Carvalho Chehab for all work with LinuxTV!

Feel free to contact me for any question!

---

### Post by alexmeister on 2009-08-23
Hi! I own the same USB stick and I've been struggling to watch TV on Kubuntu, still with no success. I followed precisely your instructions, but I tried also to produce the firmware as described in the link you provided, before copying the one you attached to your message. I get no error, but still I don't get any DVB menu in Kaffeine. Honestly I think that, in the end, the stick is just not recognized as a DVB device. 

Here is what happens when I plug the stick. 

[HTML]Aug 23 08:41:00 discovery kernel: [ 2386.208875] em28xx driver loaded                                                                          
Aug 23 08:41:05 discovery kernel: [ 2390.790645] Em28xx: Initialized (Em28xx dvb Extension) extension                                          
Aug 23 08:41:41 discovery kernel: [ 2427.100028] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.      
Aug 23 08:41:41 discovery kernel: [ 2427.329061] usb 2-3: new high speed USB device using ehci_hcd and address 2                               
Aug 23 08:41:41 discovery kernel: [ 2427.673858] usb 2-3: configuration #1 chosen from 1 choice                                                
Aug 23 08:41:41 discovery kernel: [ 2427.674012] em28xx: New device TerraTec Electronic GmbH Cinergy Hybrid T USB XS (2882) @ 480 Mbps (0ccd:005e, interface 0, class 0)                                                                                                                      
Aug 23 08:41:41 discovery kernel: [ 2427.674024] em28xx #0: Identified as Terratec Hybrid XS (em2882) (card=55)                                
Aug 23 08:41:41 discovery kernel: [ 2427.674322] em28xx #0: chip ID is em2882/em2883                                                           
Aug 23 08:41:44 discovery kernel: [ 2429.733060] em28xx #0: i2c eeprom 00: 1a eb 67 95 cd 0c 5e 00 d0 12 5c 03 9e 40 de 1c                     
Aug 23 08:41:44 discovery kernel: [ 2429.733086] em28xx #0: i2c eeprom 10: 6a 34 27 57 46 07 01 00 00 00 00 00 00 00 00 00                     
Aug 23 08:41:44 discovery kernel: [ 2429.733110] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 31 00 b8 00 14 00 5b 1e 00 00                     
Aug 23 08:41:44 discovery kernel: [ 2429.733133] em28xx #0: i2c eeprom 30: 00 00 20 40 20 6e 02 20 10 01 00 00 00 00 00 00                     
Aug 23 08:41:44 discovery kernel: [ 2429.733155] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00                     
Aug 23 08:41:44 discovery kernel: [ 2429.733177] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00                     
Aug 23 08:41:44 discovery kernel: [ 2429.733199] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 34 03 54 00 65 00                     
Aug 23 08:41:44 discovery kernel: [ 2429.733221] em28xx #0: i2c eeprom 70: 72 00 72 00 61 00 54 00 65 00 63 00 20 00 45 00                     
Aug 23 08:41:44 discovery kernel: [ 2429.733243] em28xx #0: i2c eeprom 80: 6c 00 65 00 63 00 74 00 72 00 6f 00 6e 00 69 00                     
Aug 23 08:41:44 discovery kernel: [ 2429.733265] em28xx #0: i2c eeprom 90: 63 00 20 00 47 00 6d 00 62 00 48 00 00 00 40 03                     
Aug 23 08:41:44 discovery kernel: [ 2429.733287] em28xx #0: i2c eeprom a0: 43 00 69 00 6e 00 65 00 72 00 67 00 79 00 20 00                     
Aug 23 08:41:44 discovery kernel: [ 2429.733309] em28xx #0: i2c eeprom b0: 48 00 79 00 62 00 72 00 69 00 64 00 20 00 54 00                     
Aug 23 08:41:44 discovery kernel: [ 2429.733331] em28xx #0: i2c eeprom c0: 20 00 55 00 53 00 42 00 20 00 58 00 53 00 20 00                     
Aug 23 08:41:44 discovery kernel: [ 2429.733353] em28xx #0: i2c eeprom d0: 28 00 32 00 38 00 38 00 32 00 29 00 00 00 1c 03                     
Aug 23 08:41:44 discovery kernel: [ 2429.733375] em28xx #0: i2c eeprom e0: 30 00 37 00 30 00 32 00 30 00 31 00 30 00 30 00                     
Aug 23 08:41:44 discovery kernel: [ 2429.733398] em28xx #0: i2c eeprom f0: 35 00 33 00 38 00 33 00 00 00 00 00 00 00 00 00                     
Aug 23 08:41:44 discovery kernel: [ 2429.733422] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x1813bcbe                                    
Aug 23 08:41:44 discovery kernel: [ 2429.733428] em28xx #0: EEPROM info:
Aug 23 08:41:44 discovery kernel: [ 2429.733431] em28xx #0:^IAC97 audio (5 sample rates)
Aug 23 08:41:44 discovery kernel: [ 2429.733436] em28xx #0:^I500mA max power
Aug 23 08:41:44 discovery kernel: [ 2429.733440] em28xx #0:^ITable at 0x27, strings=0x409e, 0x1cde, 0x346a
Aug 23 08:41:44 discovery kernel: [ 2429.817336] tvp5150 6-005c: chip found @ 0xb8 (em28xx #0)
Aug 23 08:41:44 discovery kernel: [ 2430.420141] tuner 6-0061: chip found @ 0xc2 (em28xx #0)
Aug 23 08:41:44 discovery kernel: [ 2430.459488] xc2028 6-0061: creating new instance
Aug 23 08:41:44 discovery kernel: [ 2430.459495] xc2028 6-0061: type set to XCeive xc2028/xc3028 tuner
Aug 23 08:41:44 discovery kernel: [ 2430.459510] i2c-adapter i2c-6: firmware: requesting xc3028-v27.fw
Aug 23 08:41:44 discovery kernel: [ 2430.469606] xc2028 6-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
Aug 23 08:41:44 discovery kernel: [ 2430.516052] xc2028 6-0061: Loading firmware for type=BASE (1), id 0000000000000000.
Aug 23 08:41:45 discovery kernel: [ 2431.582461] xc2028 6-0061: Loading firmware for type=(0), id 000000000000b700.
Aug 23 08:41:45 discovery kernel: [ 2431.599562] SCODE (20000000), id 000000000000b700:
Aug 23 08:41:45 discovery kernel: [ 2431.599578] xc2028 6-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
Aug 23 08:41:46 discovery kernel: [ 2431.884191] em28xx #0: Config register raw data: 0xd0
Aug 23 08:41:46 discovery kernel: [ 2432.184188] em28xx #0: AC97 vendor ID = 0xffffffff
Aug 23 08:41:46 discovery kernel: [ 2432.384221] em28xx #0: AC97 features = 0x6a90
Aug 23 08:41:46 discovery kernel: [ 2432.384229] em28xx #0: Empia 202 AC97 audio processor detected
Aug 23 08:41:49 discovery kernel: [ 2435.208059] tvp5150 6-005c: tvp5150am1 detected.
Aug 23 08:41:49 discovery kernel: [ 2435.505443] em28xx #0: v4l2 driver version 0.1.2
Aug 23 08:41:53 discovery kernel: [ 2439.288312] em28xx #0: V4L2 device registered as /dev/video1 and /dev/vbi0
Aug 23 08:41:53 discovery kernel: [ 2439.357652] em28xx-audio.c: probing for em28x1 non standard usbaudio
Aug 23 08:41:53 discovery kernel: [ 2439.357659] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
Aug 23 08:41:53 discovery kernel: [ 2439.358252] Em28xx: Initialized (Em28xx Audio Extension) extension
Aug 23 08:41:55 discovery kernel: [ 2440.720066] tvp5150 6-005c: tvp5150am1 detected.
Aug 23 08:41:58 discovery pulseaudio[3392]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 23 08:41:58 discovery pulseaudio[3392]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.[/HTML]

As you can see the main difference from your result is the missing "DVB etc. etc." lines. That is:

[HTML]
Aug  8 08:59:09 Stefano-PC kernel: [  478.644166] DVB: registering new adapter (em28xx #0)
Aug  8 08:59:09 Stefano-PC kernel: [  478.644169] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...
Aug  8 08:59:09 Stefano-PC kernel: [  478.644447] Successfully loaded em28xx-dvb

[/HTML]

Furthermore, the current kernel version is 2.6.28-15.

 Do you have any idea which the cause could be?

---

### Post by stefboombastic on 2009-08-23
Hi! 
Unluckily I am not a big expert of Linux drivers, I've just posted the procedure I followed for making it work for me, after many many tries.
I tried it more than once to be sure it worked, formatting and reinstalling my Ubuntu from scratch.
 As far as I remember there were different versions of the same device maybe due to different countries. I bought mine in Italy.
If You compare better my /var/log/messages with Yours, You will notice some different codes in our devices:

Mine:

Aug  8 08:59:07 Stefano-PC kernel: [  476.921216] em28xx: New device TerraTec Electronic GmbH Cinergy Hybrid T USB XS @ 480 Mbps ([COLOR="Red"]0ccd:0042[/COLOR], interface 0, class 0)
Aug  8 08:59:07 Stefano-PC kernel: [  476.921222] em28xx #0: Identified as Terratec Hybrid XS ([COLOR="Red"]card=11[/COLOR])

Yours:

Aug 23 08:41:41 discovery kernel: [ 2427.674012] em28xx: New device TerraTec Electronic GmbH Cinergy Hybrid T USB XS (2882) @ 480 Mbps ([COLOR="Red"]0ccd:005e[/COLOR], interface 0, class 0)                                                                                                                      
Aug 23 08:41:41 discovery kernel: [ 2427.674024] em28xx #0: Identified as Terratec Hybrid XS (em2882) ([COLOR="Red"]card=55[/COLOR])                                


I remember that when in past I used Mark Rechberger's drivers I had to download the following firmwares:

```
#install firmwares:
cd /lib/firmware/$(uname -r)
sudo wget http://konstantin.filtschew.de/v4l-firmware/firmware_v3.tgz
sudo tar xvzf firmware_v3.tgz
```

But version 3 of those firmwares was good only for my card identified by USB ID 0ccd:0042, while the same Cinergy XS with different USB ID had to use different firmware versions! Read this:
[https://wiki.ubuntu.com/em28xx#head-4c3197d9f2](https://wiki.ubuntu.com/em28xx#head-4c3197d9f2)
You see that Your card needed the version 2 of konstantin filtschew's firmwares, while mine needed version 3.
Then I think that this new firmware doesn't work with Your card.
In Your place I would format ubuntu, repeating my procedure, but replacing the part of installing the firmwares with the following:

```
$ cd /lib/firmware/$(uname -r) 
$ sudo wget http://konstantin.filtschew.de/v4l-firmware/firmware_v2.tgz
$ sudo tar xvzf firmware_v2.tgz 

```
Honestly I am not sure if this firmwares work at all with the new drivers :(  
The alternative is to get a windows driver for YOUR card and try to extract the firmware as done in that post: [http://forum.ubuntu-it.org/index.php...tml#msg2235209](http://forum.ubuntu-it.org/index.php...tml#msg2235209)
I have no idea how to do it in general ( I simply did copy and paste ;) ), but I guess that spending some time understanding how to do it, would make the life in Linux much better! ;)
Last thing:
I remember that until I got:
```
[  478.644163] em28xx #0/2: xc3028 attached
[  478.644166] DVB: registering new adapter (em28xx #0)
[  478.644447] Successfully loaded em28xx-dvb

```
Kaffeine never detected anything.. so do not go crazy trying other players, or trying to set Kaffeine..until U get the driver loaded succesfully, Your device won't work!
And of course DO IT ALWAYS with fresh ubuntu installations!
Hope that can help You!
Regards,
Stefano B.

---

### Post by stefboombastic on 2009-09-07
Thanks to Mr LobosD ([http://ubuntuforums.org/member.php?u=339890](http://ubuntuforums.org/member.php?u=339890))
 I've got a second working set of drivers for Cinergy XS:
[http://www.dolezel.info/download/em28xx-new.tar.bz2](http://www.dolezel.info/download/em28xx-new.tar.bz2)

I've tested these drivers succesfully both in Ubuntu 8.04 kernel 2.6.24-24-generic and Ubuntu 9.04 kernel 2.6.28-15-generic with Terratec Cinergy Hybrid T USB XS which USB ID is 0ccd:0042

The procedure is very alike the previous one, but I'll report it here for Your convenience.

** Prerequisites **

Install kernel headers:
```
sudo apt-get install linux-headers-$(uname -r)
```

Install g++:
```
sudo apt-get install g++
```

Install patch (needed for unapplying the patch for kernel 2.6.30)
```
sudo apt-get install patch
```

UNPLUG THE DEVICE IF PLUGGED

*** Removing old drivers if any ***

If the modules em28xx and em28xx-dbv are already loaded then unload them
```
sudo rmmod -f em28xx-dvb
sudo rmmod -f em28xx
```
Extract the content of the compressed file [http://www.dolezel.info/download/em28xx-new.tar.bz2](http://www.dolezel.info/download/em28xx-new.tar.bz2) into Your home folder.
Then call also unload from within it for completely unloading previously installed versions of the drivers:
```
cd ~
cd em28xx-new
sudo make unload
```

** unapply the patch if using a kernel lower than 2.6.30 ** 
```
patch -p1 -R < fix-2.6.30.patch
```

** make & install the drivers **
```
sudo make
sudo make install
```

REBOOT!!!

*** Load drivers for DVB ***
```
sudo modprobe em28xx-dvb
```
Check if modules are loaded fine with:
```
lsmod
```

*** Install firmware ***

GET & INSTALL FIRMWARE xc3028-v27.fw as described here:
[http://forum.ubuntu-it.org/index.php...tml#msg2235209](http://forum.ubuntu-it.org/index.php...tml#msg2235209)
For all those who don't want to go through all the steps described in the previous post for getting the firmware file, I have attached the firmware compiled on my Ubuntu 9.04 Kernel 2.6.28-14-generic in the first post. You can simply download it, unzip and then type:

```
sudo cp xc3028-v27.fw /lib/firmware
```

*** Checking results ***

Check device informations from /var/log/messages:
```
sudo tail -f /var/log/messages

```
Other informations can be got checking dmesg:
```
dmesg | grep em28xx
```

Then You can install the software You prefer for watching the DVB-TV by following the steps described in my first post!
ENJOY!:popcorn:

THANKS TO: LubosD for providing the drivers([http://ubuntuforums.org/showthread.php?p=7911557&posted=1#post7911557](http://ubuntuforums.org/showthread.php?p=7911557&posted=1#post7911557)) and of course to their developers!

---

### Post by superdexter on 2009-10-17
I've upgraded to the 9.10 beta.  I know to expect problems.  I'm just wondering if you have an indication of what the following error during the make process might mean:

make[1]: Entering directory `/home/user/em28xx-new'
rm -rf Module.symvers; 
make -C /lib/modules/`if [ -d /lib/modules/2.6.21.4-eeepc ]; then echo 2.6.21.4-eeepc; else uname -r; fi`/build SUBDIRS=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/user/em28xx-new/em28xx-i2c.o
/home/user/em28xx-new/em28xx-i2c.c:876: error: unknown field ‘client_register’ specified in initializer
make[3]: *** [/home/user/em28xx-new/em28xx-i2c.o] Error 1
make[2]: *** [_module_/home/user/em28xx-new] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/user/em28xx-new'

I received similar messages after applying the 2.6.30 patch.  Both actions were a fail.  Does this maybe indicate something that I missed in the process or a missing package somewhere?

---

### Post by scally on 2010-04-17
thanks for being so helpful with this issue.
i am having the same issues in 9.10

ive tried installing  the firmware supplied in the tutorial mentioned above but keep getting:

```
sean@sean-desktop:~/em28xx-new$ sudo make

running ./build.sh build

make[1]: Entering directory `/home/sean/em28xx-new'
rm -rf Module.symvers; 
make -C /lib/modules/`if [ -d /lib/modules/2.6.21.4-eeepc ]; then echo 2.6.21.4-eeepc; else uname -r; fi`/build SUBDIRS=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/sean/em28xx-new/em28xx-video.o
/home/sean/em28xx-new/em28xx-video.c: In function ‘em28xx_config_i2c’:
/home/sean/em28xx-new/em28xx-video.c:411: error: ‘VIDIOC_INT_S_VIDEO_ROUTING’ undeclared (first use in this function)
/home/sean/em28xx-new/em28xx-video.c:411: error: (Each undeclared identifier is reported only once
/home/sean/em28xx-new/em28xx-video.c:411: error: for each function it appears in.)
/home/sean/em28xx-new/em28xx-video.c: In function ‘video_mux’:
/home/sean/em28xx-new/em28xx-video.c:456: error: ‘VIDIOC_INT_S_VIDEO_ROUTING’ undeclared (first use in this function)
/home/sean/em28xx-new/em28xx-video.c:463: error: ‘VIDIOC_INT_I2S_CLOCK_FREQ’ undeclared (first use in this function)
/home/sean/em28xx-new/em28xx-video.c: In function ‘em28xx_v4l2_open’:
/home/sean/em28xx-new/em28xx-video.c:734: error: ‘VIDIOC_INT_S_AUDIO_ROUTING’ undeclared (first use in this function)
/home/sean/em28xx-new/em28xx-video.c: In function ‘em28xx_video_do_ioctl’:
/home/sean/em28xx-new/em28xx-video.c:2462: error: ‘struct device’ has no member named ‘bus_id’
/home/sean/em28xx-new/em28xx-video.c:2879: warning: passing argument 6 of ‘em28xx_do_ioctl’ from incompatible pointer type
/home/sean/em28xx-new/em28xx-video.c:1922: note: expected ‘v4l2_kioctl’ but argument is of type ‘int (*)(struct file *, unsigned int,  void *)’
/home/sean/em28xx-new/em28xx-video.c: In function ‘em28xx_v4l2_ioctl’:
/home/sean/em28xx-new/em28xx-video.c:2918: warning: passing argument 4 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘int (*)(struct inode *, struct file *, unsigned int,  void *)’
/home/sean/em28xx-new/em28xx-video.c: In function ‘em28xx_init_dev’:
/home/sean/em28xx-new/em28xx-video.c:3214: warning: assignment from incompatible pointer type
/home/sean/em28xx-new/em28xx-video.c:3301: warning: assignment from incompatible pointer type
/home/sean/em28xx-new/em28xx-video.c:3340: warning: assignment from incompatible pointer type
make[3]: *** [/home/sean/em28xx-new/em28xx-video.o] Error 1
make[2]: *** [_module_/home/sean/em28xx-new] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/sean/em28xx-new'
sean@sean-desktop:~/em28xx-new$ 
```

any help would be greatly appreciated!

Thanks in advance.

---

### Post by manvalcas on 2012-11-09
Hello I'm a new user of Linux so I beg you help to install this hardware. My distribution is Linux Maya Cinnamon 64bit ruling Kernel Linux 3.2.0-23-generic in AMD NVDIa SLI with 8 GB RAM DDR2

First of All, I don't understand the process you describe in your post, because my overall ignorance of the Linux O/S basics so I have tried to introduce in the terminal the suggested commands. I explain the subsequent result step by step.

>      Code:
     sudo modprobe em28xx  sudo modprobe em28xx-dvb 
RESULT: Nothing remarkable, any message returned

> 

Install mercurial:
     Code:
     sudo apt-get install mercurial 
RESULT: Success

> 

Install kernel headers:
     Code:
     sudo apt-get install linux-headers-$(uname -r) 
RESULT: A long paragraph the last one make me feel nervous

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.2.0-23-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  kde-l10n-es language-pack-kde-zh-hans-base firefox-locale-zh-hans
  language-pack-kde-en kde-l10n-engb language-pack-zh-hans-base kde-l10n-zhcn
  language-pack-zh-hans language-pack-kde-zh-hans language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 86 not upgraded.


> 

Install g++:
     Code:
     sudo apt-get install g++ 
RESULT: Success

...........................................................

The rest of the process turns imposible to understand... now i realized that i had to download some kind of "v4l". Now i feel "in the middle of nothing" and I don´t have the  knowledge to "undo" (typical windows false mentality) the changes "i've made" or complete the "installation process(??)"

Could you help me??

> [   61.246966] usbcore: registered new interface driver em28xx
[   61.246969] em28xx driver loaded
[  465.363790] em28xx: New device TerraTec Electronic Gm\xffffffef\xffffffbf\xffffffbf\xffffffc3\xffffffbf @ 480 Mbps (0ccd:0042, interface 0, class 0)
[  465.363833] em28xx #0: chip ID is em2882/em2883
[  465.539497] em28xx #0: i2c eeprom 00: 1a eb 67 95 cd 0c 42 00 50 12 5c 03 9e 32 6a 34
[  465.539506] em28xx #0: i2c eeprom 10: 00 00 06 57 46 07 00 00 00 00 00 00 00 00 00 00
[  465.539513] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 31 00 b8 00 14 00 5b 00 00 00
[  465.539520] em28xx #0: i2c eeprom 30: 00 00 20 40 20 6e 02 20 10 01 00 00 00 00 00 00
[  465.539527] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  465.539534] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  465.539541] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 34 03 54 00 65 00
[  465.539548] em28xx #0: i2c eeprom 70: 72 00 72 00 61 00 54 00 65 00 63 00 20 00 45 00
[  465.539555] em28xx #0: i2c eeprom 80: 6c 00 65 00 63 00 74 00 72 00 6f 00 6e 00 69 00
[  465.539562] em28xx #0: i2c eeprom 90: 63 00 20 00 47 00 6d 00 ff ff ff 00 00 00 a1 ff
[  465.539568] em28xx #0: i2c eeprom a0: 43 00 69 00 6e 00 65 00 72 00 67 00 79 00 20 00
[  465.539575] em28xx #0: i2c eeprom b0: 48 00 79 00 62 00 72 00 69 00 64 00 20 00 54 00
[  465.539582] em28xx #0: i2c eeprom c0: 20 00 55 00 53 00 42 00 20 00 58 00 53 00 00 00
[  465.539589] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  465.539596] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  465.539602] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  465.539610] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x060a7969
[  465.539612] em28xx #0: EEPROM info:
[  465.539613] em28xx #0:    AC97 audio (5 sample rates)
[  465.539615] em28xx #0:    500mA max power
[  465.539616] em28xx #0:    Table at 0x06, strings=0x329e, 0x346a, 0x0000
[  465.540753] em28xx #0: Identified as Terratec Cinnergy Hybrid T USB XS (em2882) (card=55)
[  465.543797] tvp5150 9-005c: chip found @ 0xb8 (em28xx #0)
[  465.644108] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:0a.1/usb1/1-2/rc/rc0/input4
[  465.644171] rc0: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:0a.1/usb1/1-2/rc/rc0
[  465.644940] em28xx #0: Config register raw data: 0x50
[  465.645689] em28xx #0: AC97 vendor ID = 0xffffffff
[  465.646064] em28xx #0: AC97 features = 0x6a90
[  465.646065] em28xx #0: Empia 202 AC97 audio processor detected
[  465.833225] em28xx #0: v4l2 driver version 0.1.3
[  465.919572] em28xx #0: V4L2 video device registered as video0
[  465.919575] em28xx #0: V4L2 VBI device registered as vbi0
[COLOR=SandyBrown][  465.983027] em28xx #0: /2: dvb frontend not attached. Can't attach xc3028[/COLOR]
[  465.983093] em28xx audio device (0ccd:0042): interface 1, class 1


---

