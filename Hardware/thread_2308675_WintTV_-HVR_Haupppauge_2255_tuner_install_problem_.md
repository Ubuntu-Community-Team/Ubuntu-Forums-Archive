---
title: "WintTV -HVR Haupppauge 2255 tuner install problem  2200"
date: 2016-01-05
forum: Hardware
---

### Post by darter on 2016-01-05
I just purchased a  Haupppauge 2255 tuner card and I am running Ubuntu 14.04. I think I am 'almost there ' but I can't seem to get it to work. In the below outputs I use  "************" to make a comment.
I really do not know how much of this works so I am trying some trial and error but I would like to understand what is really going on. 


 Thanks.


Here is info about my kernel:
whe88@whe88-desktop:~$ uname -r
3.16.0-57-generic
whe88@whe88-desktop:~$ cat /proc/version_signature
Ubuntu 3.16.0-57.77~14.04.1-generic 3.16.7-ckt20                       ***** I came to believe that the 3.16 kernel was required - does anyone know if that is true? 
whe88@whe88-desktop:~$ 



The short version of the story is that I was  initially getting this:



whe88@whe88-desktop:~$ dmesg | grep saa7164
[   13.197182] saa7164 driver loaded
[   13.197283] saa7164[0]: Your board isn't known (yet) to the driver.
[   13.197283] saa7164[0]: Try to pick one of the existing card configs via      ******************************************   so maybe I need to choose a card number? I'm not sure
[   13.197283] saa7164[0]: card=<n> insmod option.  Updating to the latest
[   13.197283] saa7164[0]: version might help as well.
[   13.197292] saa7164[0]: Here are valid choices for the card=<n> insmod option:
[   13.197294] saa7164[0]:    card=0 -> Unknown
[   13.197296] saa7164[0]:    card=1 -> Generic Rev2
[   13.197298] saa7164[0]:    card=2 -> Generic Rev3
[   13.197300] saa7164[0]:    card=3 -> Hauppauge WinTV-HVR2250
[   13.197302] saa7164[0]:    card=4 -> Hauppauge WinTV-HVR2200
[   13.197304] saa7164[0]:    card=5 -> Hauppauge WinTV-HVR2200
[   13.197307] saa7164[0]:    card=6 -> Hauppauge WinTV-HVR2200
[   13.197309] saa7164[0]:    card=7 -> Hauppauge WinTV-HVR2250
[   13.197311] saa7164[0]:    card=8 -> Hauppauge WinTV-HVR2250
[   13.197313] saa7164[0]:    card=9 -> Hauppauge WinTV-HVR2200
[   13.197315] saa7164[0]:    card=10 -> Hauppauge WinTV-HVR2200
[   13.197343] CORE saa7164[0]: subsystem: 0070:f111, board: Unknown [card=0,autodetected]
[   13.197346] saa7164[0]/0: found at 0000:05:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfe000000
[   13.197356] saa7164_initdev() Unsupported board detected, registering without firmware
whe88@whe88-desktop:~$  

My attempted solution was enter a  variant of this:  (I tried many card numbers)

echo options saa7164 card=7 | sudo tee /etc/modprobe.d/saa7164.conf
sudo modprobe -r saa7164
sudo modprobe saa7164



Now I get this: 


whe88@whe88-desktop:~$ dmesg | grep saa7164
[   10.864293] saa7164 driver loaded
[   10.864418] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2250 [card=3,insmod option]
[   10.864422] saa7164[0]/0: found at 0000:05:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfe000000
[   11.022042] saa7164_downloadfirmware() no first image
[   11.022052] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   12.341276] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   12.341278] saa7164_downloadfirmware() firmware loaded.
[   12.341286] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   12.341292] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   12.341293] saa7164_downloadfirmware() BSLSize = 0x0
[   12.341295] saa7164_downloadfirmware() Reserved = 0x0
[   12.341296] saa7164_downloadfirmware() Version = 0x1661c00
[   19.096538] saa7164_downloadimage() Image downloaded, booting...
[   19.200468] saa7164_downloadimage() Image booted successfully.
[   21.950605] saa7164_downloadimage() Image downloaded, booting...
[   23.717358] saa7164_downloadimage() Image booted successfully.
[   23.746210] saa7164_api_i2c_read() error, ret(2) = 0x13                                  ****************************** this maybe is telling me what the problem  is?
[   24.082678] saa7164_dvb_register() Frontend initialization failed
[   24.082682] saa7164_initdev() Failed to register dvb adapters on porta
[   24.084716] saa7164_dvb_register() Frontend initialization failed
[   24.084718] saa7164_initdev() Failed to register dvb adapters on portb
[   24.084798] saa7164[0]: registered device video1 [mpeg]
[   24.324641] saa7164[0]: registered device video2 [mpeg]
[   24.535674] saa7164[0]: registered device vbi0 [vbi]
[   24.535748] saa7164[0]: registered device vbi1 [vbi]

Also, I see on the forums that maybe a 2250 card is the same as a 2255. I am therefore unclear if I want 2250 drivers or special new drivers for a 2255. 

---- lshw command yields  ----

*-usb:4
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fe806000-fe806fff
        *-pci:4
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:fdc00000-fe3fffff
           *-multimedia
                description: Multimedia controller
                product: SAA7164                                   ************************  does this prove that SAA7164 is the correct driver that I must have? So , am I okay so far ?
                vendor: Philips Semiconductors                
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 81
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=saa7164 latency=0
                resources: irq:16 memory:fe000000-fe3fffff memory:fdc00000-fdffffff



So - does anyone spot an obvious blunder I am making? 


These are the files I copied to  the lib/firmware directory.                           (I hope those are correct for my card).

NXP7164-2010-03-10.1.fw
v4l-saa7164-1.0.2-3.fw
v4l-saa7164-1.0.3-3.fw




Also I take this as proof that something is not working

whe88@whe88-desktop:~$  w_scan -fa -A1 -c US -X                                    ****** I used instructions from  [http://www.hauppauge.com/site/support/install_ubuntu14_04_2-kernel-3.16.txt](http://www.hauppauge.com/site/support/install_ubuntu14_04_2-kernel-3.16.txt)
w_scan version 20130331 (compiled for DVB API 5.10)                                  
using settings for UNITED STATES
ATSC
VSB US/CA, DVB-T TW
scan type TERRCABLE_ATSC, channellist 1
output format czap/tzap/szap/xine
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
main:3228: FATAL: ***** NO USEABLE TERRCABLE_ATSC CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.
whe88@whe88-desktop:~$ 





Lastly, my understanding  of this stuff is not deep so maybe I am just missing something obvious. 
Thanks for your help.

---

### Post by Bucky Ball on 2016-01-05
*Thread moved to **Hardware***.

Welcome. Doesn't look Mythbuntu specific, if that is what you're using, and please add code tags to your terminal output for clarity. See the last link in my signature for how. Thanks.

---

### Post by aelfric55 on 2016-01-05
1. The necessary saa7164 driver upgrade for the Hauppauge 2255 was only incorporated in the 4.2 series and above kernels. With kernel 4.2.x and 4.3.x, the digital side of the Hauppauge 2255 fires up and works perfectly.

2. Unlike in the discontinued Hauppauge 2250, analog does not function yet in the Hauppauge 2255 (for cable box outputs and such). The saa7164 driver developers over at linuxtv.org cite a development problem upstream preventing analog implementation. The current state of affairs is that the kernel will register /dev/videoX device nodes for the analog half of the 2255 card, but if you attempt to tune analog on the 2255 you'll just end up with a blue screen.

So the short of it is that with a kernel upgrade (or patching and recompiling the saa7164 driver), your Hauppauge 2255 will become a very good digital-only card.

---

### Post by darter on 2016-01-05
So, in my situation it sounds like a might upgrade my kernel to 4.3.x (maybe). Can you tell me if that would have some downsides - perhaps less stability or update problems?

For now I am trying this (instead) since I got a proper patch (I believe). Here are my notes so far:

1.
from email from  haup I got  a link to a patch file

The file you need is on the following page.

[http://www.hauppauge.com/site/support/linux.html](http://www.hauppauge.com/site/support/linux.html)     **** this leads to  the patch I never before could locate
 
last link at the bottom contains what you need. 

2.

after decompression I used 

 sudo tar xJf /home/whe88/Downloads/patchy/Linux-Ubuntu-14-04-2/patch/hvr-9x5-19x5-22x5-kernel-3.16-2015-05-21.patch.tar.xz
to place the patch into /usr/src/linux-3.16

----- ls yields: 
> 0001-base-packaging.patch                       include          REPORTING-BUGS
0002-debian-changelog.patch                     init             samples
0003-configs-based-on-Ubuntu-3.16.0-7.12.patch  ipc              scripts
arch                                            Kbuild           security
block                                           Kconfig          signing_key.priv
COPYING                                         kernel           signing_key.x509
CREDITS                                         lib              sound
crypto                                          MAINTAINERS      System.map
debian                                          Makefile         tools
debian.master                                   mm               usr
Documentation                                   modules.builtin  virt
drivers                                         modules.order    vmlinux
firmware                                        Module.symvers   vmlinux.o
fs                                              net              x509.genkey
hvr-9x5-19x5-22x5-kernel-3.16-2015-05-21.patch  README     *********** so now the patch is there for the first time
whe88@whe88-desktop:/usr/src/linux-3.16$ 



-----
3. Now I followed these instructions: (this is what I had earlier omitted because I had no patch at the earlier time)
Apply the tuner patch.

$ sudo patch -p1 < hvr-9x5-19x5-22x5-kernel-3.16-2015-05-21.patch

then I followed the rest of the instructions to build my own kernel

sudo make -j2 INSTALL_MOD_STRIP=1 LOCALVERSION=-hvr-test deb-pkg  *** now I am just waiting !

---

### Post by aelfric55 on 2016-01-06
The only issue I've noticed with the 4.x.x kernels in general is that they all (when used in conjunction with Mythtv 0.27.x) break analog support on the old Hauppauge HVR 1600 card, using the cx18 driver. Since you don't appear to have this card (or any cx18-based card) you should have no problems with a stock 4.3 series kernel package if the patched 3.16.x fails to deliver. If the patch works for you, keep the source handy --you may have to re-patch and recompile every time there's a kernel auto-update.

---

### Post by darter on 2016-01-07
Okay. The tuner now works after  applying the patches in the link sent to me (in step 1 above). So that's great news. Here is some info that somebody find useful if they are starting out. The output below is from my system with a working 2255 tuner (according to the retail box) and kernel  3.16 patched as per instructions (above). I can tune shows on either of the two tuners and record a TV show using  Me-TV.  Now I am wondering about the remote control device that came in the box. Would anybody  know if this is going to work with Ubuntu? I'm not really sure how that works. Once connected can it serve as a general input device and control lots of different software? Sort of like a wireless keyboard? I guess that it too will need its own drivers?
That is my next project.   

---

```
]whe88@whe88-desktop:~$ uname -r
3.16.0-hvr-test                     **** this is the name that the instruction said to use 
whe88@whe88-desktop:~$ ^C
whe88@whe88-desktop:~$ 
```

----

```
whe88@whe88-desktop:~$ dmesg | grep saa7164
[   10.871086] saa7164 driver loaded
[   10.871204] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2255 [card=11,autodetected]
[   10.871208] saa7164[0]/0: found at 0000:05:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfe000000
[   11.031420] saa7164_downloadfirmware() no first image
[   11.031438] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-04-01.1.fw)
[   11.698908] saa7164_downloadfirmware() firmware read 3283792 bytes.
[   11.698911] saa7164_downloadfirmware() firmware loaded.
[   11.698916] saa7164_downloadfirmware() SecBootLoader.FileSize = 3283792
[   11.698922] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   11.698923] saa7164_downloadfirmware() BSLSize = 0x0
[   11.698924] saa7164_downloadfirmware() Reserved = 0x0
[   11.698925] saa7164_downloadfirmware() Version = 0x1d21
[   18.550178] saa7164_downloadimage() Image downloaded, booting...
[   18.654090] saa7164_downloadimage() Image booted successfully.
[   21.164374] saa7164_downloadimage() Image downloaded, booting...
[   22.723293] saa7164_downloadimage() Image booted successfully.
[   22.767288] saa7164[0]: Hauppauge eeprom: model=151061
[   28.621849] DVB: registering new adapter (saa7164)
[   28.621853] saa7164 0000:05:00.0: DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   33.366029] DVB: registering new adapter (saa7164)
[   33.366033] saa7164 0000:05:00.0: DVB: registering adapter 1 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   33.366502] saa7164[0]: registered device video1 [mpeg]
[   33.595966] saa7164[0]: registered device video2 [mpeg]
[   33.805894] saa7164[0]: registered device vbi0 [vbi]
[   33.805941] saa7164[0]: registered device vbi1 [vbi]
[   33.807737] saa7164_api_set_debug() error, ret = 0x13

---- scan


871086] saa7164 driver loaded
[   10.871204] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2255 [card=11,autodetected]
[   10.871208] saa7164[0]/0: found at 0000:05:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfe000000
[   11.031420] saa7164_downloadfirmware() no first image
[   11.031438] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-04-01.1.fw)
[   11.698908] saa7164_downloadfirmware() firmware read 3283792 bytes.
[   11.698911] saa7164_downloadfirmware() firmware loaded.
[   11.698916] saa7164_downloadfirmware() SecBootLoader.FileSize = 3283792
[   11.698922] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   11.698923] saa7164_downloadfirmware() BSLSize = 0x0
[   11.698924] saa7164_downloadfirmware() Reserved = 0x0
[   11.698925] saa7164_downloadfirmware() Version = 0x1d21
[   18.550178] saa7164_downloadimage() Image downloaded, booting...
[   18.654090] saa7164_downloadimage() Image booted successfully.
[   21.164374] saa7164_downloadimage() Image downloaded, booting...
[   22.723293] saa7164_downloadimage() Image booted successfully.
[   22.767288] saa7164[0]: Hauppauge eeprom: model=151061
[   28.621849] DVB: registering new adapter (saa7164)
[   28.621853] saa7164 0000:05:00.0: DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   33.366029] DVB: registering new adapter (saa7164)
[   33.366033] saa7164 0000:05:00.0: DVB: registering adapter 1 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   33.366502] saa7164[0]: registered device video1 [mpeg]
[   33.595966] saa7164[0]: registered device video2 [mpeg]
[   33.805894] saa7164[0]: registered device vbi0 [vbi]
[   33.805941] saa7164[0]: registered device vbi1 [vbi]
[   33.807737] saa7164_api_set_debug() error, ret = 0x13
whe88@whe88-desktop:~$ ^C
```
```
whe88@whe88-desktop:~$ w_scan -fa -A1 -c US -X
w_scan version 20130331 (compiled for DVB API 5.10)
using settings for UNITED STATES
ATSC
VSB US/CA, DVB-T TW
scan type TERRCABLE_ATSC, channellist 1
output format czap/tzap/szap/xine
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
    /dev/dvb/adapter0/frontend0 -> TERRCABLE_ATSC "LG Electronics LGDT3306A VSB/QAM Frontend": good :-)
    /dev/dvb/adapter1/frontend0 -> TERRCABLE_ATSC "LG Electronics LGDT3306A VSB/QAM Frontend": good :-)
Using TERRCABLE_ATSC frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.a
frontend 'LG Electronics LGDT3306A VSB/QAM Frontend' supports
INVERSION_AUTO
8VSB
QAM_64
QAM_256
FREQ (54.00MHz ... 858.00MHz)
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
57000: 8VSB(time: 00:01) 
63000: 8VSB(time: 00:10) 
69000: 8VSB(time: 00:15) 
79000: 8VSB(time: 00:20) 
85000: 8VSB(time: 00:24) ^C
ERROR: interrupted by SIGINT, dumping partial result...
dumping lists (0 services)
Done.
```
```
whe88@whe88-desktop:~$ w_scan -fa -A1 -c US -X
w_scan version 20130331 (compiled for DVB API 5.10)
using settings for UNITED STATES
ATSC
VSB US/CA, DVB-T TW
scan type TERRCABLE_ATSC, channellist 1
output format czap/tzap/szap/xine
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
    /dev/dvb/adapter0/frontend0 -> TERRCABLE_ATSC "LG Electronics LGDT3306A VSB/QAM Frontend": good :-)
    /dev/dvb/adapter1/frontend0 -> TERRCABLE_ATSC "LG Electronics LGDT3306A VSB/QAM Frontend": good :-)
Using TERRCABLE_ATSC frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.a
frontend 'LG Electronics LGDT3306A VSB/QAM Frontend' supports
INVERSION_AUTO
8VSB
QAM_64
QAM_256
FREQ (54.00MHz ... 858.00MHz)
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
57000: 8VSB(time: 00:01) 
63000: 8VSB(time: 00:06) 
69000: 8VSB(time: 00:11) 
79000: 8VSB(time: 00:16) 
85000: 8VSB(time: 00:21) 
177000: 8VSB(time: 00:26) 
183000: 8VSB(time: 00:30) 
189000: 8VSB(time: 00:34) 
195000: 8VSB(time: 00:38) 
201000: 8VSB(time: 00:43) 
207000: 8VSB(time: 00:48) 
213000: 8VSB(time: 00:53) 
473000: 8VSB(time: 00:58) 
479000: 8VSB(time: 01:01) (time: 01:03) signal ok:    ******************** this indicates to me that the tuner found a channel so now I know it is working
    8VSB     f=479000 kHz
485000: 8VSB(time: 01:03) 
491000: 8VSB(time: 01:08) 
497000: 8VSB(time: 01:13) 
503000: 8VSB(time: 01:18) 
509000: 8VSB(time: 01:22) 
515000: 8VSB(time: 01:27) 
521000: 8VSB(time: 01:32) 
527000: 8VSB(time: 01:36) 
533000: 8VSB(time: 01:41) 
539000: 8VSB(time: 01:45) 
545000: 8VSB(time: 01:48) 
551000: 8VSB(time: 01:53) (time: 01:55) signal ok:           ********** another channel
    8VSB     f=551000 kHz
557000: 8VSB(time: 01:55) 
563000: 8VSB(time: 02:00) 
569000: 8VSB(time: 02:05) 
575000: 8VSB(time: 02:09) 
581000: 8VSB(time: 02:14) 
587000: 8VSB(time: 02:19) (time: 02:20) signal ok:
    8VSB     f=587000 kHz
593000: 8VSB(time: 02:21) (time: 02:22) signal ok:
    8VSB     f=593000 kHz
599000: 8VSB(time: 02:22) (time: 02:23) signal ok:
    8VSB     f=599000 kHz
605000: 8VSB(time: 02:24) (time: 02:25) signal ok:
    8VSB     f=605000 kHz
611000: 8VSB(time: 02:25) 
617000: 8VSB(time: 02:30) 
623000: 8VSB(time: 02:34) 
629000: 8VSB(time: 02:39) 
635000: 8VSB(time: 02:44) 
641000: 8VSB(time: 02:49) 
647000: 8VSB(time: 02:54) 
653000: 8VSB(time: 02:59) 
659000: 8VSB(time: 03:02) 
665000: 8VSB(time: 03:07) 
671000: 8VSB(time: 03:12) 
677000: 8VSB(time: 03:17) (time: 03:18) signal ok:
    8VSB     f=677000 kHz
683000: 8VSB(time: 03:19) 
689000: 8VSB(time: 03:24) (time: 03:25) signal ok:
    8VSB     f=689000 kHz
695000: 8VSB(time: 03:25) 
701000: 8VSB(time: 03:30) 
707000: 8VSB(time: 03:35) 
713000: 8VSB(time: 03:40) 
719000: 8VSB(time: 03:45) 
725000: 8VSB(time: 03:49) 
731000: 8VSB(time: 03:54) 
737000: 8VSB(time: 03:59) 
743000: 8VSB(time: 04:04) 
749000: 8VSB(time: 04:09) 
755000: 8VSB(time: 04:14) 
761000: 8VSB(time: 04:18) 
767000: 8VSB(time: 04:23) 
773000: 8VSB(time: 04:28) 
779000: 8VSB(time: 04:33) 
785000: 8VSB(time: 04:38) 
791000: 8VSB(time: 04:43) 
797000: 8VSB(time: 04:48) 
803000: 8VSB(time: 04:52) 
tune to: 8VSB     f=479000 kHz 
(time: 04:57) service is running. Channel number: 14:1. Name: 'WFDC-DT'
service is running. Channel number: 14:2. Name: 'GET-TV'
service is running. Channel number: 14:3. Name: 'GRITtv'
service is running. Channel number: 14:4. Name: 'Escape-TV'
tune to: 8VSB     f=551000 kHz 
(time: 04:59) service is running. Channel number: 26:1. Name: 'WETA-HD'
service is running. Channel number: 26:2. Name: 'WETA UK'
service is running. Channel number: 26:3. Name: 'KIDS'
service is running. Channel number: 26:4. Name: 'TV26'
tune to: 8VSB     f=587000 kHz 
(time: 05:00) service is running. Channel number: 32:1. Name: 'WHUT-HD'
service is running. Channel number: 32:2. Name: 'WHUT-SD'
tune to: 8VSB     f=593000 kHz 
(time: 05:01) service is running. Channel number: 66:1. Name: 'ION'
service is running. Channel number: 66:2. Name: 'qubo'
service is running. Channel number: 66:3. Name: 'IONLife'
service is running. Channel number: 66:4. Name: 'Shop'
service is running. Channel number: 66:5. Name: 'HSN'
service is running. Channel number: 66:6. Name: 'QVC'
tune to: 8VSB     f=599000 kHz 
(time: 05:03) service is running. Channel number: 20:1. Name: 'WDCA DT'
service is running. Channel number: 20:2. Name: 'MOVIES!'
service is running. Channel number: 20:3. Name: 'HEROES & ICONS'
tune to: 8VSB     f=605000 kHz 
(time: 05:04) service is running. Channel number: 5:1. Name: 'WTTG-DT'
service is running. Channel number: 5:2. Name: 'BUZZR  '
tune to: 8VSB     f=677000 kHz 
(time: 05:06) service is running. Channel number: 4:1. Name: 'WRC-HD '
service is running. Channel number: 4:2. Name: 'WRC-SD '
tune to: 8VSB     f=689000 kHz 
(time: 05:07) service is running. Channel number: 50:1. Name: 'WDCW-DT'
service is running. Channel number: 50:2. Name: 'AntTV  '
service is running. Channel number: 50:3. Name: 'ThisTV '
dumping lists (26 services)
WFDC-DT:479000000:8VSB:49:52:1
GET-TV:479000000:8VSB:65:68:2
GRITtv:479000000:8VSB:81:84:3
Escape-TV:479000000:8VSB:97:100:4
WETA-HD:551000000:8VSB:49:52:1
WETA UK:551000000:8VSB:65:68:2
KIDS:551000000:8VSB:81:84:3
TV26:551000000:8VSB:97:100:4
WHUT-HD:587000000:8VSB:49:52:1
WHUT-SD:587000000:8VSB:65:68:2
ION:593000000:8VSB:49:52:3
qubo:593000000:8VSB:65:68:4
IONLife:593000000:8VSB:81:84:5
Shop:593000000:8VSB:97:100:6
HSN:593000000:8VSB:113:116:7
QVC:593000000:8VSB:129:132:8
WDCA DT:599000000:8VSB:49:52:3
MOVIES!:599000000:8VSB:65:68:4
HEROES & ICONS:599000000:8VSB:81:84:5
WTTG-DT:605000000:8VSB:49:52:3
BUZZR  :605000000:8VSB:65:68:4
WRC-HD :677000000:8VSB:49:52:3
WRC-SD :677000000:8VSB:65:68:4
WDCW-DT:689000000:8VSB:49:52:3
AntTV  :689000000:8VSB:65:68:4
ThisTV :689000000:8VSB:81:84:5
Done.
whe88@whe88-desktop:~$ ^C
```

---

### Post by deadflowr on 2016-01-07
Please use code tags when posting terminal output.
And try to breakdown the output per command.

---

### Post by aelfric55 on 2016-01-08
The HVR-2255 is supposed to contain the same IR receiver/blaster as the 2250. IR on the 2250 tuner remains unsupported on Linux according to [https://www.mythtv.org/wiki/Digital_Tuner_Cards](https://www.mythtv.org/wiki/Digital_Tuner_Cards) so I doubt it is any better on the 2255.

That said, the remote itself is presumably a common Windows Media Center remote. So any WMC-capable USB IR-receiver ought to be usable, either with LIRC and the appropriate kernel modules, or, with somewhat less functionality, as an IR keyboard by mapping keycodes for most of the special keys you'll use in X with xmodmap.

---

### Post by Terry_Kramer on 2016-02-29
I am a new to Linux.  Also am building a Ubuntu box to support a Hauppauge 2255 and Kodi.  I as a bit confused about [COLOR=#DD4814][COLOR=#000000][aelfric55]("http://ubuntuforums.org/member.php?u=1877832") [/COLOR][/COLOR]post that the 2255 will only be a digital card.  I thought the FCC forced the phaseout of remaining  analog overair by Sept 2015.  In my geographical area, I only see overair digital currently.  Is there another way to receive analog that I am overlooking?

---

