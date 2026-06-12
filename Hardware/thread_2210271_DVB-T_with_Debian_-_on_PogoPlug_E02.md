---
title: "DVB-T with Debian - on PogoPlug E02"
date: 2014-03-10
forum: Hardware
---

### Post by mohamed3 on 2014-03-10
Dears

I have got PogoPlug E02 and finally after many problem i have installed Debian.

Now  i can FTP and download-upload the HDD normally and after some tried i  have successfully connect my MF190S ZTE USB Modem to it and can connect  to internet.

Now i need to integrate WebCam and DVB-T to it.

Yesterday  i have installed some DVB-APP to it and tried with some help and  instruction from here  ([http://ubuntuforums.org/showthread.php?t=1898046&p=11862272#post11862272](http://ubuntuforums.org/showthread.php?t=1898046&p=11862272#post11862272))  but have the following problem

this is my DVB-T

Bus 002 Device 005: ID 048d:9135 Integrated Technology Express, Inc. Zolid Mini DVB-T Stick

During Build I got the following Errors

```

root@debian:~/v4l/media_build# ./build
Checking if the needed tools for Debian GNU/Linux 7 \n \l are available
Needed package dependencies are met.

************************************************************
* This script will download the latest tarball and build it*
* Assuming that your kernel is compatible with the latest  *
* drivers. If not, you'll need to add some extra backports,*
* ./backports/<kernel> directory.                          *
* It will also update this tree to be sure that all compat *
* bits are there, to avoid compilation failures            *
************************************************************
************************************************************
* All drivers and build system are under GPLv2 License     *
* Firmware files are under the license terms found at:     *
* [http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/)               *
* Please abort in the next 5 secs if you don't agree with  *
* the license                                              *
************************************************************

Not aborted. It means that the licence was agreed. Proceeding...

****************************
Updating the building system
****************************
From git://linuxtv.org/media_build
 * branch            master     -> FETCH_HEAD
Already up-to-date.
make: Entering directory `/root/v4l/media_build/linux'
wget [http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5](http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5) -O linux-media.tar.bz2.md5.tmp
--2014-03-10 05:55:42--  [http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5](http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5)
Resolving linuxtv.org (linuxtv.org)... 130.149.80.248
Connecting to linuxtv.org (linuxtv.org)|130.149.80.248|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 93 [application/x-bzip2]
Saving to: `linux-media.tar.bz2.md5.tmp'

100%[==============================================================================================================================>] 93          --.-K/s   in 0s      

2014-03-10 05:55:43 (2.76 MB/s) - `linux-media.tar.bz2.md5.tmp' saved [93/93]

make: Leaving directory `/root/v4l/media_build/linux'
make: Entering directory `/root/v4l/media_build/linux'
tar xfj linux-media.tar.bz2
rm -f .patches_applied .linked_dir .git_log.md5
make: Leaving directory `/root/v4l/media_build/linux'
**********************************************************
* Downloading firmwares from linuxtv.org.                *
**********************************************************
dvb-fe-bcm3510-01.fw
dvb-fe-or51132-qam.fw
dvb-fe-or51132-vsb.fw
dvb-fe-or51211.fw
dvb-fe-xc5000-1.6.114.fw
dvb-ttpci-01.fw-261a
dvb-ttpci-01.fw-261b
dvb-ttpci-01.fw-261c
dvb-ttpci-01.fw-261d
dvb-ttpci-01.fw-261f
dvb-ttpci-01.fw-2622
dvb-usb-avertv-a800-02.fw
dvb-usb-bluebird-01.fw
dvb-usb-dib0700-1.20.fw
dvb-usb-dibusb-5.0.0.11.fw
dvb-usb-dibusb-6.0.0.8.fw
dvb-usb-dtt200u-01.fw
dvb-usb-terratec-h5-drxk.fw
dvb-usb-terratec-h7-az6007.fw
dvb-usb-terratec-h7-drxk.fw
dvb-usb-umt-010-02.fw
dvb-usb-vp702x-01.fw
dvb-usb-vp7045-01.fw
dvb-usb-wt220u-01.fw
dvb-usb-wt220u-02.fw
v4l-cx231xx-avcore-01.fw
v4l-cx23418-apu.fw
v4l-cx23418-cpu.fw
v4l-cx23418-dig.fw
v4l-cx23885-avcore-01.fw
v4l-cx23885-enc.fw
v4l-cx25840.fw
******************
* Start building *
******************
make -C /root/v4l/media_build/v4l allyesconfig
make[1]: Entering directory `/root/v4l/media_build/v4l'
make[2]: Entering directory `/root/v4l/media_build/linux'
Applying patches for kernel 3.13.1-kirkwood-tld-2
patch -s -f -N -p1 -i ../backports/api_version.patch
patch -s -f -N -p1 -i ../backports/pr_fmt.patch
patch -s -f -N -p1 -i ../backports/of_graph.patch
The text leading up to this was:
--------------------------
|diff --git a/include/linux/of_graph.h b/include/linux/of_graph.h
|index 2b233db..befef42 100644
|--- a/include/linux/of_graph.h
|+++ b/include/linux/of_graph.h
--------------------------
No file to patch.  Skipping patch.
1 out of 1 hunk ignored
make[2]: *** [apply_patches] Error 1
make[2]: Leaving directory `/root/v4l/media_build/linux'
make[1]: *** [allyesconfig] Error 2
make[1]: Leaving directory `/root/v4l/media_build/v4l'
make: *** [allyesconfig] Error 2
can't select all drivers at ./build line 490.

```


for my device 

```
root@debian:~# dmesg |grep it913x
[   27.461509] it913x: Chip Version=02 Chip Type=9135
[   27.493348] it913x: Firmware Version 52887808it913x: Dual mode=0 Tuner Type=38
[   27.542099] it913x: Unknown tuner ID applying default 0x60<6>[   27.576743] usb 1-1.3: dvb_usb_v2: found a 'ITE 9135 Generic' in warm state
[   27.688404] dvb_usb_it913x: probe of 1-1.3:1.0 failed with error -12
[   27.696666] usbcore: registered new interface driver dvb_usb_it913x
```

and still cant know why cant detect Frontend0

```
root@debian:~# scan /usr/share/dvb/dvb-c/at-Vienna
scanning /usr/share/dvb/dvb-c/at-Vienna
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2745: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
```

```
root@debian:~# dvbscan 
Failed to open frontend
```

---

