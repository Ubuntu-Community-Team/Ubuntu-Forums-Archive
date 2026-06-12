---
title: "USB Keyboard and Mouse not working with Beagleboard-xM"
date: 2011-09-17
forum: Hardware
---

### Post by TurboFreak on 2011-09-17
Hello,

I tried installing Ubuntu Natty and Oneiric Beta 1 on a SD Card for using it with a BeagleBoard-xM Rev. C, following these instructions: [https://wiki.ubuntu.com/ARM/OmapNetbook](https://wiki.ubuntu.com/ARM/OmapNetbook)

(For Oneiric i did not update the kernel like the instructions tells for Natty)
These are the images i used:
[http://cdimage.ubuntu.com/releases/11.04/release/ubuntu-11.04-preinstalled-netbook-armel+omap.img.gz](http://cdimage.ubuntu.com/releases/11.04/release/ubuntu-11.04-preinstalled-netbook-armel+omap.img.gz)
[http://cdimage.ubuntu.com/releases/11.10/beta-1/ubuntu-11.10-beta1-preinstalled-desktop-armel+omap.img.gz](http://cdimage.ubuntu.com/releases/11.10/beta-1/ubuntu-11.10-beta1-preinstalled-desktop-armel+omap.img.gz)

For both images i had the same problem of the USB keyboard and mouse not working.
With the original Ångström Linux, which was shipped preinstalled on a SD Card, mouse and keyboard was working nicely, though.

I have not found anything usefull when searchig for this on the internet. Other people seem not to have this problem.

I would like to give you a nice bootlog but unfortunately the output on the serial port stops after the booting of the kernel starts (see below) while the screen shows the booting continuing.
(The original Ångström Linux gives a proper bootlog.)

Does anyone have any idea what i can do to tackle this problem?
Or how to get at least a full bootlog first?


The following is the output i get from the serial port when booting the SD Card i installed Oneiric on:
```
Texas Instruments X-Loader 1.5.1 (Jul 15 2011 - 21:29:14)                             
Beagle xM                                                                             
Reading boot sector
Loading u-boot.bin from mmc


U-Boot 2011.06 (Aug 29 2011 - 16:51:02)

OMAP3630/3730-GP ES2.1, CPU-OPP2, L3-165MHz, Max CPU Clock 1 Ghz
OMAP3 Beagle board + LPDDR/NAND
I2C:   ready
DRAM:  512 MiB
WARNING: Caches not enabled
NAND:  0 MiB
MMC:   OMAP SD/MMC: 0
*** Warning - readenv() failed, using default environment

In:    serial
Out:   serial
Err:   serial
Beagle unknown 0x02
No EEPROM on expansion board
Die ID #340a00029ff800000163810c1502f01e
Hit any key to stop autoboot:  0 
SD/MMC found on device 0
reading boot.scr

356 bytes read
Running bootscript from mmc ...
## Executing script at 82000000
reading uImage

3710572 bytes read
reading uInitrd

6616482 bytes read
## Booting kernel from Legacy Image at 80000000 ...
   Image Name:   Ubuntu Kernel
   Image Type:   ARM Linux Kernel Image (uncompressed)
   Data Size:    3710508 Bytes = 3.5 MiB
   Load Address: 80008000
   Entry Point:  80008000
   Verifying Checksum ... OK
## Loading init Ramdisk from Legacy Image at 81600000 ...
   Image Name:   Ubuntu Initrd
   Image Type:   ARM Linux RAMDisk Image (gzip compressed)
   Data Size:    6616418 Bytes = 6.3 MiB
   Load Address: 00000000
   Entry Point:  00000000
   Verifying Checksum ... OK
   Loading Kernel Image ... OK
OK

Starting kernel ...

Uncompressing Linux... done, booting the kernel.
```

---

### Post by TurboFreak on 2011-09-18
OK, i found this page: [https://wiki.ubuntu.com/ARM/BeagleEditBootscr](https://wiki.ubuntu.com/ARM/BeagleEditBootscr)
and followed it's instructions to modify my boot.scr file to enable the serial console and get a boot log.

I added "console=ttyS2,115200n8" to the "setenv bootargs" line so the script now looks like this:

```
        fatload mmc 0:1 0x80000000 uImage
        fatload mmc 0:1 0x81600000 uInitrd
        setenv bootargs console=ttyS2,115200n8 ro elevator=noop vram=12M omapfb.mode=dvi:1280x720MR-16@60 mpurate=auto root=UUID=065b0a56-079e-4957-b875-b949552f6a75 fixrtc quiet splash
        bootm 0x80000000 0x81600000
```

Unfortunately it did not work.

The serial output now looks like shown below.
It has not changed much but you can see that the new boot.scr has been read ("379 bytes read" instead of 356).
Also with this modification now the screen is just staying black.
Though the screen is getting some signal as it's LEDs indicate and it reports to be driven with a resolution of 1280x720@60Hz.

```
Texas Instruments X-Loader 1.5.1 (Jul 15 2011 - 21:29:14)                          
Beagle xM                                                                          
Reading boot sector
Loading u-boot.bin from mmc


U-Boot 2011.06 (Aug 29 2011 - 16:51:02)

OMAP3630/3730-GP ES2.1, CPU-OPP2, L3-165MHz, Max CPU Clock 1 Ghz
OMAP3 Beagle board + LPDDR/NAND
I2C:   ready
DRAM:  512 MiB
WARNING: Caches not enabled
NAND:  0 MiB
MMC:   OMAP SD/MMC: 0
*** Warning - readenv() failed, using default environment

In:    serial
Out:   serial
Err:   serial
Beagle unknown 0x02
No EEPROM on expansion board
Die ID #340a00029ff800000163810c1502f01e
Hit any key to stop autoboot:  0 
SD/MMC found on device 0
reading boot.scr

379 bytes read
Running bootscript from mmc ...
## Executing script at 82000000
reading uImage

3710572 bytes read
reading uInitrd

6616482 bytes read
## Booting kernel from Legacy Image at 80000000 ...
   Image Name:   Ubuntu Kernel
   Image Type:   ARM Linux Kernel Image (uncompressed)
   Data Size:    3710508 Bytes = 3.5 MiB
   Load Address: 80008000
   Entry Point:  80008000
   Verifying Checksum ... OK
## Loading init Ramdisk from Legacy Image at 81600000 ...
   Image Name:   Ubuntu Initrd
   Image Type:   ARM Linux RAMDisk Image (gzip compressed)
   Data Size:    6616418 Bytes = 6.3 MiB
   Load Address: 00000000
   Entry Point:  00000000
   Verifying Checksum ... OK
   Loading Kernel Image ... OK
OK

Starting kernel ...

Uncompressing Linux... done, booting the kernel.
```

---

### Post by TurboFreak on 2011-10-04
To make this more graspable i've recorded a video of the problem:
[http://www.youtube.com/watch?v=mVsrByp283g](http://www.youtube.com/watch?v=mVsrByp283g)

It shows the boot processes and how the mouse and keyboard works with the shipped Angström Linux but don't work with Ubuntu Oneiric Beta 2.

---

### Post by msewing on 2011-10-09
I am having the same problem with Natty on my Beagleboard XM.  I downloaded 'ubuntu-11.04-preinstalled-netbook-armel+omap.img.gz', unpacked it to the SD and then applied 'beagleXM-natty.tgz' changes according to instructions at [https://wiki.ubuntu.com/ARM/OmapNetbook](https://wiki.ubuntu.com/ARM/OmapNetbook).

Ubuntu started and reconfigured its disk correctly (it seems).  It rebooted itself, making a very nice red screen(!) and finally hung at the Natty configure window, asking for my language.  My mouse LED was dark, and no mouse or keyboard commands were accepted.  Changed USB ports, no better.

I made the console=ttyS2 change in the boot script, as recommended.  I see a login prompt on my console device.  Can't log in though, since I have not configured a password or user account yet.

Angstrom works fine, FWIW.

What to do?  TIA!

Martin

---

### Post by yanamandra on 2011-10-24
Hi,
 
I have the same problem. I have been trying to find out a solution to this. 
Please let me know if you could resolve the problem.
 
-Venu

---

### Post by msewing on 2011-10-24
I've changed to a different kernel, so I cannot easily try the following, which I stumbled across somewhere else.

Try attaching the keyboard and mouse to an external USB2 hub and attaching the hub to the BB USB port.  The suggestion is that the Ubuntu USB driver is not able to work with slower devices.  Worth a shot.  Post if you try this.

Martin

---

### Post by yanamandra on 2011-10-26
Went through responses over the internet where an externally powered USB devices were also not recognized.
So, tried another method that completely worked. :)
 
1. Followed the installation instructions for Ubuntu 11.04 from:
[https://wiki.ubuntu.com/ARM/OmapNetbook](https://wiki.ubuntu.com/ARM/OmapNetbook)
Including those under the section:  "Update for BeagleXM Rev B & Rev C" 
 
2. After everything was done from step#1, I, went ahead and mounted the microSD card on my linux box. Mounted sdb1 and replaced u-boot.bin
mkdir /tmp/2; mount /dev/sdb1 /tmp/2; rm -f u-boot.bin; wget [http://www.angstrom-distribution.org/demo/beagleboard/u-boot.bin](http://www.angstrom-distribution.org/demo/beagleboard/u-boot.bin) .
 
  Note: the u-boot.bin that I downloaded is with this timestamp and size: "23-Oct-2011 15:03  318K"
 
 
3. Then, I created a uEnv.txt file from the default boot.scr script of ubuntu and placed it in the /dev/sdb1 file system.
 
  Contents of uEnv.txt is as below:
 
bootargs=ro elevator=noop vram=12M omapfb.mode=dvi:1280x720MR-16@60 mpurate=500 root=UUID=195f94b2-d64e-4702-b85d-91a269683828 fixrtc quiet splash
uenvcmd=mmc rescan;fatload mmc 0:1 0x80000000 uImage;fatload mmc 0:1 0x81600000 uInitrd;bootm 0x80000000 0x81600000
 
 
4. Rebooted the beagleboard and yes, the mouse and keyboard were not only powered up but are also detected. :)
 
5. Enjoy!!!
 
 
Regards,
Venu Yanamandra

---

### Post by fx08 on 2012-01-06
Thanks for the solution Venu. It works!!

I want to make a tiny addition for newbies to use the new version of mentioned uBoot ([http://www.angstrom-distribution.org/demo/beagleboard/]("http://www.angstrom-distribution.org/demo/beagleboard/")). 
(I used "02-Nov-2011 08:15  318K" version of uBoot.)

Just copy original uImage from the first partition of sd card to Boot directory in the second partition. Otherwise uBoot will show kernel not found error.

With this change kernel starts printing to console (serial port) also.

---

### Post by eggsmartha on 2012-02-28
Hi.  I'm having the same problem, but when I check the angstrom archive there's not a u-boot.bin file there.  I'm looking at [http://www.angstrom-distribution.org/demo/beagleboard/](http://www.angstrom-distribution.org/demo/beagleboard/), the only file that's close to the size you mentioned is u-boot.img which is 321k.  Thanks for any help you can provide.

---

### Post by onizukal on 2012-02-29
try that ' wget [http://www.beagleboard.org/angstrom-mirror/www.angstrom-distribution.org/demo/beagleboard/u-boot.bin](http://www.beagleboard.org/angstrom-mirror/www.angstrom-distribution.org/demo/beagleboard/u-boot.bin) ' instead of the previous one because the previous one is in img format. and after you created uEnv.txt don't forget to change " root=UUID=195f94b2-d64e-4702-b85d-91a269683828 " line as the same with your boot.scr file . You can open boot.scr with gedit. 

When i used that way , my keyboard and mause come to the alive :D but problem is the new installation is going on so slow then before. For example maybe it took 15 min just for the language selection screen coming . The previous which my usb ports are not avaiable is like 4 min for the same screen .  Have any idea ?

---

### Post by eggsmartha on 2012-02-29
thanks for the quick reply, it's working now.  awesome!

---

### Post by vinay3065 on 2012-03-27
Hi,

I am facing same problem and will be trying the solution 

getting new u-boot.bin and creating uEnv.txt

However, I am not clear about  what the following line means

"root=UUID=195f94b2-d64e-4702-b85d-91a269683828"

Please explain

Thanks

Vinay Chaddha

---

### Post by marin123 on 2012-04-21
Please can someone clarify this.

So, I have installed Ubuntu on my Beagleboard xM. It doesn't power up the mouse or recognize it.

I went to download u-boot.bin. That file does not exist. What do I do? Do I have to download u-boot.img and extract it or what?

What is with uImage file? Do I have to download that?

Where do I have to put these files? Just on first partition or on both?

@Vinay, you copy the contents of /boot/boot.script on your second partition. Thats where UUID came from.

---

### Post by skykooler on 2012-04-22
I followed the instructions, but it still isn't powering up my USB mouse (which works fine under Angstrom.)

> **marin123 said:**
> I went to download u-boot.bin. That file does not exist. What do I do? Do I have to download u-boot.img and extract it or what?

See the previous page:

> **onizukal] try that ' wget [http://www.beagleboard.org/angstrom-mirror/www.angstrom-distribution.org/demo/beagleboard/u-boot.bin](http://www.beagleboard.org/angstrom-mirror/www.angstrom-distribution.org/demo/beagleboard/u-boot.bin) ' instead of the previous one because the previous one is in img format.[/QUOTE]

The u-boot.img file is in the wrong format, but the link onizukal gave works fine.

[QUOTE=marin123 said:**
> What is with uImage file? Do I have to download that?
No. That is the Angstrom kernel.

> **marin123 said:**
> Where do I have to put these files? Just on first partition or on both?

Just the first partition.

---

### Post by marin123 on 2012-04-23
Thank you skykooler!

But now I have another problem. I installed Ubuntu Precise to an SD card and booted. Boots fine, but no mouse or keyboard.

Then I replaced u-boot.bin and added uEnv.txt and now it can't boot. When I plug in the power, it doesn't even read the sd card.
When I put back original u-boot.bin, Beagleboard boots.

I even tried renaming uEnv.txt to uEnv, without effect.

Does anyone else have this problem? Should I try Oneiric?

---

### Post by loscorners on 2012-05-09
> **marin123 said:**
> Thank you skykooler!

But now I have another problem. I installed Ubuntu Precise to an SD card and booted. Boots fine, but no mouse or keyboard.

Then I replaced u-boot.bin and added uEnv.txt and now it can't boot. When I plug in the power, it doesn't even read the sd card.
When I put back original u-boot.bin, Beagleboard boots.

I even tried renaming uEnv.txt to uEnv, without effect.

Does anyone else have this problem? Should I try Oneiric?
Could you solve the problem, marin123?

---

### Post by Akampan Dey on 2012-06-11
HI all,
 
  Even I am trying to make my USB(Mass storage) to get detected in the OMAP 3XXX board, but it is not getting detected, couldn't find out the solution. But the driver for that board is up.
 
Can anyone tell me the quick solution for this, if you want more details I can post it here.
 
Regards
Akampan

---

