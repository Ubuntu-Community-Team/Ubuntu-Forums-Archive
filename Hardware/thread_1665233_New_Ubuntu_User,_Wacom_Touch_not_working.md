---
title: "New Ubuntu User, Wacom Touch not working"
date: 2011-01-12
forum: Hardware
---

### Post by Hunter Tech on 2011-01-12
I have just began using linux and i like most things about it.  I have had some issues with configuration with my equipment but all is well now EXCEPT my tablet is not working.  I have found a thread for this topic but the most current post is somewhat old and the solution that was presented was beyond my scope of knowledge.  I was hoping that someone has by now created a simple "fix".  Has this been done yet?  I have ubuntu 10.10, bamboo touch.  

i have installed the installation software from cd, in order to ge around the executable bit problem i had to copy the files from the cd to the machine and the make the exe file executable.  once i did that the software installed properly but still no functionality of the pad.  Also when i click the bamboo utility within wine it pops up a error window stating the "there is no windows program configured to run this program".

Not sure if the additional information will help but maybe

thanks in advance

---

### Post by Favux on 2011-01-12
Hi Hunter Tech,

You do not need the Windows drivers.  There are already Wacom linux drivers pre-installed in Maverick.  The problem you are running into is that the default usb kernel driver called wacom.ko in Maverick does not have your tablet model in it.  See the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Following part I. will get you a working wacom.ko.

You can check your model by entering in a terminal:
```
lsusb
```
Compare it to the product ID's in the model box near the top of the HOW TO.

Unfortunately right now touch is broken in the X driver xf86-input-wacom (part II) due to all of the new code added the last couple of weeks.  Fixes have been submitted and hopefully will be committed to the git repository shortly.  In the meantime you could place your Touch on the Synaptic driver, see part VIII.

---

### Post by Hunter Tech on 2011-01-12
i had found that thread previously but me being a newb it might as well have been in greek to me.  I am going through the steps in section 1 now to get the "usb kernel" repaired, or however one would word that.  Hopefully that works.

---

### Post by Hunter Tech on 2011-01-12
OK i have went through part 1 and got to this piece of code 
sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko 
once i get to that point i get no such file or directory error.  below is the entire "dialogue" (not sure what the proper term is) if you anyone could possibly tell me what i did wrong that would be awesome.




Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-headers-2.6.35-24 all 2.6.35-24.42 [10.3MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-headers-2.6.35-24-generic i386 2.6.35-24.42 [780kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-headers-generic i386 2.6.35.24.28 [5,026B]
Fetched 11.1MB in 2min 39s (69.6kB/s)                                          
tar: ./md5sums: time stamp 2010-12-02 02:05:55 is 139665956.281408495 s in the future
tar: ./control: time stamp 2010-12-02 02:05:53 is 139665954.280868974 s in the future
tar: .: time stamp 2010-12-02 02:05:54 is 139665955.280793895 s in the future
Selecting previously deselected package linux-headers-2.6.35-24.
(Reading database ... 122593 files and directories currently installed.)
Unpacking linux-headers-2.6.35-24 (from .../linux-headers-2.6.35-24_2.6.35-24.42_all.deb) ...
tar: ./postinst: time stamp 2010-12-02 02:14:45 is 139666476.213304781 s in the future
tar: ./md5sums: time stamp 2010-12-02 02:16:04 is 139666555.209107271 s in the future
tar: ./control: time stamp 2010-12-02 02:16:03 is 139666554.208959418 s in the future
tar: .: time stamp 2010-12-02 02:16:03 is 139666554.208888599 s in the future
Selecting previously deselected package linux-headers-2.6.35-24-generic.
Unpacking linux-headers-2.6.35-24-generic (from .../linux-headers-2.6.35-24-generic_2.6.35-24.42_i386.deb) ...
tar: ./control: time stamp 2010-12-01 23:23:21 is 139656182.406313284 s in the future
tar: ./md5sums: time stamp 2010-12-01 23:23:25 is 139656186.405861344 s in the future
tar: .: time stamp 2010-12-01 23:23:25 is 139656186.405785496 s in the future
Preparing to replace linux-headers-generic 2.6.35.22.23 (using .../linux-headers-generic_2.6.35.24.28_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Setting up linux-headers-2.6.35-24 (2.6.35-24.42) ...
Setting up linux-headers-2.6.35-24-generic (2.6.35-24.42) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
Setting up linux-headers-generic (2.6.35.24.28) ...
trevor@trevor-915P-A2:~/Desktop$ tar xjvf linuxwacom-0.8.8-10.tar.bz2
linuxwacom-0.8.8-10/
linuxwacom-0.8.8-10/README
tar: linuxwacom-0.8.8-10/README: time stamp 2010-10-12 13:04:27 is 135295363.691867175 s in the future
linuxwacom-0.8.8-10/acinclude.m4
tar: linuxwacom-0.8.8-10/acinclude.m4: time stamp 2010-10-12 13:04:27 is 135295363.690316916 s in the future
linuxwacom-0.8.8-10/prebuilt/
linuxwacom-0.8.8-10/prebuilt/64/
linuxwacom-0.8.8-10/prebuilt/64/wacom_drv.so
tar: linuxwacom-0.8.8-10/prebuilt/64/wacom_drv.so: time stamp 2010-10-12 15:23:12 is 135303688.673522545 s in the future
linuxwacom-0.8.8-10/prebuilt/64/.libs/
linuxwacom-0.8.8-10/prebuilt/64/.libs/libwacomxi.so.0.0.0
tar: linuxwacom-0.8.8-10/prebuilt/64/.libs/libwacomxi.so.0.0.0: time stamp 2010-10-12 15:22:56 is 135303672.669812664 s in the future
linuxwacom-0.8.8-10/prebuilt/64/.libs/libwacomcfg.lai
tar: linuxwacom-0.8.8-10/prebuilt/64/.libs/libwacomcfg.lai: time stamp 2010-10-12 15:22:56 is 135303672.669631916 s in the future
linuxwacom-0.8.8-10/prebuilt/64/.libs/libwacomcfg.a
tar: linuxwacom-0.8.8-10/prebuilt/64/.libs/libwacomcfg.a: time stamp 2010-10-12 15:22:56 is 135303672.668919189 s in the future
linuxwacom-0.8.8-10/prebuilt/64/.libs/libwacomxi.a
tar: linuxwacom-0.8.8-10/prebuilt/64/.libs/libwacomxi.a: time stamp 2010-10-12 15:22:56 is 135303672.663631741 s in the future
linuxwacom-0.8.8-10/prebuilt/64/.libs/libwacomxi.lai
tar: linuxwacom-0.8.8-10/prebuilt/64/.libs/libwacomxi.lai: time stamp 2010-10-12 15:22:56 is 135303672.663417469 s in the future
linuxwacom-0.8.8-10/prebuilt/64/.libs/xsetwacom
tar: linuxwacom-0.8.8-10/prebuilt/64/.libs/xsetwacom: time stamp 2010-10-12 15:22:56 is 135303672.659184759 s in the future
linuxwacom-0.8.8-10/prebuilt/64/.libs/libwacomcfg.so.0.0.1
tar: linuxwacom-0.8.8-10/prebuilt/64/.libs/libwacomcfg.so.0.0.1: time stamp 2010-10-12 15:22:56 is 135303672.657694284 s in the future
linuxwacom-0.8.8-10/prebuilt/64/wacomcfg.h
tar: linuxwacom-0.8.8-10/prebuilt/64/.libs: time stamp 2010-10-12 15:22:56 is 135303672.657592456 s in the future
tar: linuxwacom-0.8.8-10/prebuilt/64/wacomcfg.h: time stamp 2010-10-12 15:22:56 is 135303672.656727546 s in the future
linuxwacom-0.8.8-10/prebuilt/64/wacomcpl
tar: linuxwacom-0.8.8-10/prebuilt/64/wacomcpl: time stamp 2010-10-12 15:22:56 is 135303672.656542048 s in the future
linuxwacom-0.8.8-10/prebuilt/64/wacdump
tar: linuxwacom-0.8.8-10/prebuilt/64/wacdump: time stamp 2010-10-12 15:22:56 is 135303672.633936073 s in the future
linuxwacom-0.8.8-10/prebuilt/64/xidump
tar: linuxwacom-0.8.8-10/prebuilt/64/xidump: time stamp 2010-10-12 15:22:56 is 135303672.631951683 s in the future
linuxwacom-0.8.8-10/prebuilt/64/wacom_drv.o
tar: linuxwacom-0.8.8-10/prebuilt/64/wacom_drv.o: time stamp 2010-10-12 15:22:56 is 135303672.620789425 s in the future
linuxwacom-0.8.8-10/prebuilt/64/wacomcpl-exec
tar: linuxwacom-0.8.8-10/prebuilt/64/wacomcpl-exec: time stamp 2010-10-12 15:22:56 is 135303672.615698579 s in the future
linuxwacom-0.8.8-10/prebuilt/64/xsetwacom
tar: linuxwacom-0.8.8-10/prebuilt/64/xsetwacom: time stamp 2010-10-12 15:22:56 is 135303672.615225966 s in the future
linuxwacom-0.8.8-10/prebuilt/64/libwacomcfg.la
tar: linuxwacom-0.8.8-10/prebuilt/64/libwacomcfg.la: time stamp 2010-10-12 15:22:56 is 135303672.6150485 s in the future
linuxwacom-0.8.8-10/prebuilt/64/libwacomxi.la
tar: linuxwacom-0.8.8-10/prebuilt/64/libwacomxi.la: time stamp 2010-10-12 15:22:56 is 135303672.614886399 s in the future
linuxwacom-0.8.8-10/prebuilt/64/pkgIndex.tcl
tar: linuxwacom-0.8.8-10/prebuilt/64/pkgIndex.tcl: time stamp 2010-10-12 15:22:56 is 135303672.614751745 s in the future
linuxwacom-0.8.8-10/prebuilt/install
tar: linuxwacom-0.8.8-10/prebuilt/64: time stamp 2010-10-12 15:23:12 is 135303688.614680438 s in the future
tar: linuxwacom-0.8.8-10/prebuilt/install: time stamp 2010-10-12 13:04:27 is 135295363.613534348 s in the future
linuxwacom-0.8.8-10/prebuilt/wacom.4x.gz
tar: linuxwacom-0.8.8-10/prebuilt/wacom.4x.gz: time stamp 2010-10-12 15:22:56 is 135303672.613336349 s in the future
linuxwacom-0.8.8-10/prebuilt/uninstall
tar: linuxwacom-0.8.8-10/prebuilt/uninstall: time stamp 2010-10-12 13:04:27 is 135295363.613204769 s in the future
linuxwacom-0.8.8-10/prebuilt/32/
linuxwacom-0.8.8-10/prebuilt/32/wacom_drv.so
tar: linuxwacom-0.8.8-10/prebuilt/32/wacom_drv.so: time stamp 2010-10-12 13:06:35 is 135295491.60346545 s in the future
linuxwacom-0.8.8-10/prebuilt/32/.libs/
linuxwacom-0.8.8-10/prebuilt/32/.libs/libwacomxi.so.0.0.0
tar: linuxwacom-0.8.8-10/prebuilt/32/.libs/libwacomxi.so.0.0.0: time stamp 2010-10-12 13:05:31 is 135295427.60211312 s in the future
linuxwacom-0.8.8-10/prebuilt/32/.libs/libwacomcfg.lai
tar: linuxwacom-0.8.8-10/prebuilt/32/.libs/libwacomcfg.lai: time stamp 2010-10-12 13:05:31 is 135295427.601942918 s in the future
linuxwacom-0.8.8-10/prebuilt/32/.libs/libwacomcfg.a
tar: linuxwacom-0.8.8-10/prebuilt/32/.libs/libwacomcfg.a: time stamp 2010-10-12 13:05:31 is 135295427.601043366 s in the future
linuxwacom-0.8.8-10/prebuilt/32/.libs/libwacomxi.a
tar: linuxwacom-0.8.8-10/prebuilt/32/.libs/libwacomxi.a: time stamp 2010-10-12 13:05:31 is 135295427.599473971 s in the future
linuxwacom-0.8.8-10/prebuilt/32/.libs/libwacomxi.lai
tar: linuxwacom-0.8.8-10/prebuilt/32/.libs/libwacomxi.lai: time stamp 2010-10-12 13:05:31 is 135295427.599296784 s in the future
linuxwacom-0.8.8-10/prebuilt/32/.libs/xsetwacom
tar: linuxwacom-0.8.8-10/prebuilt/32/.libs/xsetwacom: time stamp 2010-10-12 13:05:31 is 135295427.597527574 s in the future
linuxwacom-0.8.8-10/prebuilt/32/.libs/libwacomcfg.so.0.0.1
tar: linuxwacom-0.8.8-10/prebuilt/32/.libs/libwacomcfg.so.0.0.1: time stamp 2010-10-12 13:05:31 is 135295427.596472766 s in the future
linuxwacom-0.8.8-10/prebuilt/32/wacomcfg.h
tar: linuxwacom-0.8.8-10/prebuilt/32/.libs: time stamp 2010-10-12 13:05:31 is 135295427.596360043 s in the future
tar: linuxwacom-0.8.8-10/prebuilt/32/wacomcfg.h: time stamp 2010-10-12 13:05:31 is 135295427.596205624 s in the future
linuxwacom-0.8.8-10/prebuilt/32/wacomcpl
tar: linuxwacom-0.8.8-10/prebuilt/32/wacomcpl: time stamp 2010-10-12 13:05:31 is 135295427.596105542 s in the future
linuxwacom-0.8.8-10/prebuilt/32/wacdump
tar: linuxwacom-0.8.8-10/prebuilt/32/wacdump: time stamp 2010-10-12 13:05:31 is 135295427.591776522 s in the future
linuxwacom-0.8.8-10/prebuilt/32/xidump
tar: linuxwacom-0.8.8-10/prebuilt/32/xidump: time stamp 2010-10-12 13:05:31 is 135295427.588365421 s in the future
linuxwacom-0.8.8-10/prebuilt/32/wacom_drv.o
tar: linuxwacom-0.8.8-10/prebuilt/32/wacom_drv.o: time stamp 2010-10-12 13:05:29 is 135295425.512306405 s in the future
linuxwacom-0.8.8-10/prebuilt/32/wacomcpl-exec
tar: linuxwacom-0.8.8-10/prebuilt/32/wacomcpl-exec: time stamp 2010-10-12 13:05:31 is 135295427.507589907 s in the future
linuxwacom-0.8.8-10/prebuilt/32/xsetwacom
tar: linuxwacom-0.8.8-10/prebuilt/32/xsetwacom: time stamp 2010-10-12 13:05:31 is 135295427.507400708 s in the future
linuxwacom-0.8.8-10/prebuilt/32/libwacomcfg.la
tar: linuxwacom-0.8.8-10/prebuilt/32/libwacomcfg.la: time stamp 2010-10-12 13:05:31 is 135295427.507283934 s in the future
linuxwacom-0.8.8-10/prebuilt/32/libwacomxi.la
tar: linuxwacom-0.8.8-10/prebuilt/32/libwacomxi.la: time stamp 2010-10-12 13:05:31 is 135295427.506225843 s in the future
linuxwacom-0.8.8-10/prebuilt/32/pkgIndex.tcl
tar: linuxwacom-0.8.8-10/prebuilt/32/pkgIndex.tcl: time stamp 2010-10-12 13:05:31 is 135295427.506088257 s in the future
linuxwacom-0.8.8-10/depcomp
tar: linuxwacom-0.8.8-10/prebuilt/32: time stamp 2010-10-12 13:06:35 is 135295491.506021558 s in the future
tar: linuxwacom-0.8.8-10/prebuilt: time stamp 2010-10-12 15:22:56 is 135303672.505975673 s in the future
tar: linuxwacom-0.8.8-10/depcomp: time stamp 2010-10-12 13:04:27 is 135295363.504519001 s in the future
linuxwacom-0.8.8-10/src/
linuxwacom-0.8.8-10/src/2.6.30/
linuxwacom-0.8.8-10/src/2.6.30/wacom.h
tar: linuxwacom-0.8.8-10/src/2.6.30/wacom.h: time stamp 2010-10-12 13:04:27 is 135295363.504168748 s in the future
linuxwacom-0.8.8-10/src/2.6.30/wacom_wac.h
tar: linuxwacom-0.8.8-10/src/2.6.30/wacom_wac.h: time stamp 2010-10-12 13:04:27 is 135295363.503040049 s in the future
linuxwacom-0.8.8-10/src/2.6.30/wacom_sys.c
tar: linuxwacom-0.8.8-10/src/2.6.30/wacom_sys.c: time stamp 2010-10-12 13:04:27 is 135295363.502235272 s in the future
linuxwacom-0.8.8-10/src/2.6.30/Makefile.in
tar: linuxwacom-0.8.8-10/src/2.6.30/Makefile.in: time stamp 2010-10-12 13:04:27 is 135295363.502061927 s in the future
linuxwacom-0.8.8-10/src/2.6.30/wacom_wac.c
tar: linuxwacom-0.8.8-10/src/2.6.30/wacom_wac.c: time stamp 2010-10-12 13:04:27 is 135295363.478068911 s in the future
linuxwacom-0.8.8-10/src/xsetwacom.4x
tar: linuxwacom-0.8.8-10/src/2.6.30: time stamp 2010-10-12 13:04:27 is 135295363.47794648 s in the future
tar: linuxwacom-0.8.8-10/src/xsetwacom.4x: time stamp 2010-10-12 13:04:27 is 135295363.477818391 s in the future
linuxwacom-0.8.8-10/src/Makefile.am
tar: linuxwacom-0.8.8-10/src/Makefile.am: time stamp 2010-10-12 13:04:27 is 135295363.475907404 s in the future
linuxwacom-0.8.8-10/src/xdrv/
linuxwacom-0.8.8-10/src/xdrv/wcmCustomDebug.c
tar: linuxwacom-0.8.8-10/src/xdrv/wcmCustomDebug.c: time stamp 2010-10-12 13:04:27 is 135295363.47565451 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmMapping.c
tar: linuxwacom-0.8.8-10/src/xdrv/wcmMapping.c: time stamp 2010-10-12 13:04:27 is 135295363.471770795 s in the future
linuxwacom-0.8.8-10/src/xdrv/xf86Wacom.h
tar: linuxwacom-0.8.8-10/src/xdrv/xf86Wacom.h: time stamp 2010-10-12 13:04:27 is 135295363.471142087 s in the future
linuxwacom-0.8.8-10/src/xdrv/Makefile.am
tar: linuxwacom-0.8.8-10/src/xdrv/Makefile.am: time stamp 2010-10-12 13:04:27 is 135295363.471002824 s in the future
linuxwacom-0.8.8-10/src/xdrv/xf86Wacom.c
tar: linuxwacom-0.8.8-10/src/xdrv/xf86Wacom.c: time stamp 2010-10-12 13:04:27 is 135295363.468386512 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmConfig.c
tar: linuxwacom-0.8.8-10/src/xdrv/wcmConfig.c: time stamp 2010-10-12 13:04:27 is 135295363.46623143 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmTouchFilter.c
tar: linuxwacom-0.8.8-10/src/xdrv/wcmTouchFilter.c: time stamp 2010-10-12 13:04:27 is 135295363.465132274 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmCommon.c
tar: linuxwacom-0.8.8-10/src/xdrv/wcmCommon.c: time stamp 2010-10-12 13:04:27 is 135295363.462265303 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmTilt2Rotation.c
tar: linuxwacom-0.8.8-10/src/xdrv/wcmTilt2Rotation.c: time stamp 2010-10-12 13:04:27 is 135295363.460579902 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmFilter.c
tar: linuxwacom-0.8.8-10/src/xdrv/wcmFilter.c: time stamp 2010-10-12 13:04:27 is 135295363.460370798 s in the future
linuxwacom-0.8.8-10/src/xdrv/Makefile.in
tar: linuxwacom-0.8.8-10/src/xdrv/Makefile.in: time stamp 2010-10-12 13:04:27 is 135295363.459192861 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmUSB.c
tar: linuxwacom-0.8.8-10/src/xdrv/wcmUSB.c: time stamp 2010-10-12 13:04:27 is 135295363.456602391 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmSerial.h
tar: linuxwacom-0.8.8-10/src/xdrv/wcmSerial.h: time stamp 2010-10-12 13:04:27 is 135295363.456428487 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmValidateDevice.c
tar: linuxwacom-0.8.8-10/src/xdrv/wcmValidateDevice.c: time stamp 2010-10-12 13:04:27 is 135295363.456048203 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmSerial.c
tar: linuxwacom-0.8.8-10/src/xdrv/wcmSerial.c: time stamp 2010-10-12 13:04:27 is 135295363.453225162 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmISDV4.c
tar: linuxwacom-0.8.8-10/src/xdrv/wcmISDV4.c: time stamp 2010-10-12 13:04:27 is 135295363.431148442 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmXCommand.c
tar: linuxwacom-0.8.8-10/src/xdrv/wcmXCommand.c: time stamp 2010-10-12 13:04:27 is 135295363.42921322 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmFilter.h
tar: linuxwacom-0.8.8-10/src/xdrv/wcmFilter.h: time stamp 2010-10-12 13:04:27 is 135295363.427956851 s in the future
linuxwacom-0.8.8-10/src/xdrv/wcmCompat.c
tar: linuxwacom-0.8.8-10/src/xdrv/wcmCompat.c: time stamp 2010-10-12 13:04:27 is 135295363.427777569 s in the future
linuxwacom-0.8.8-10/src/xdrv/xf86WacomDefs.h
tar: linuxwacom-0.8.8-10/src/xdrv/xf86WacomDefs.h: time stamp 2010-10-12 13:04:27 is 135295363.425724665 s in the future
linuxwacom-0.8.8-10/src/wacom.4x
tar: linuxwacom-0.8.8-10/src/xdrv: time stamp 2010-10-12 13:04:27 is 135295363.425618786 s in the future
tar: linuxwacom-0.8.8-10/src/wacom.4x: time stamp 2010-10-12 13:04:27 is 135295363.424964237 s in the future
linuxwacom-0.8.8-10/src/include/
linuxwacom-0.8.8-10/src/include/kernel-config.h.in
tar: linuxwacom-0.8.8-10/src/include/kernel-config.h.in: time stamp 2010-10-12 13:04:27 is 135295363.424709876 s in the future
linuxwacom-0.8.8-10/src/include/util-config.h.in
tar: linuxwacom-0.8.8-10/src/include/util-config.h.in: time stamp 2010-10-12 13:04:27 is 135295363.424590518 s in the future
linuxwacom-0.8.8-10/src/include/Xwacom.h
tar: linuxwacom-0.8.8-10/src/include/Xwacom.h: time stamp 2010-10-12 13:04:27 is 135295363.423534453 s in the future
linuxwacom-0.8.8-10/src/include/xdrv-config.h.in
tar: linuxwacom-0.8.8-10/src/include/xdrv-config.h.in: time stamp 2010-10-12 13:04:27 is 135295363.423366835 s in the future
linuxwacom-0.8.8-10/src/Makefile.in
tar: linuxwacom-0.8.8-10/src/include: time stamp 2010-10-12 13:04:27 is 135295363.42329001 s in the future
tar: linuxwacom-0.8.8-10/src/Makefile.in: time stamp 2010-10-12 13:04:27 is 135295363.413495237 s in the future
linuxwacom-0.8.8-10/src/2.6.18/
linuxwacom-0.8.8-10/src/2.6.18/wacom.h
tar: linuxwacom-0.8.8-10/src/2.6.18/wacom.h: time stamp 2010-10-12 13:04:27 is 135295363.412030184 s in the future
linuxwacom-0.8.8-10/src/2.6.18/Makefile.in
tar: linuxwacom-0.8.8-10/src/2.6.18/Makefile.in: time stamp 2010-10-12 13:04:27 is 135295363.411831906 s in the future
linuxwacom-0.8.8-10/src/wacomxi/
tar: linuxwacom-0.8.8-10/src/2.6.18: time stamp 2010-10-12 13:04:27 is 135295363.411758712 s in the future
linuxwacom-0.8.8-10/src/wacomxi/wacomcpl
tar: linuxwacom-0.8.8-10/src/wacomxi/wacomcpl: time stamp 2010-10-12 13:04:27 is 135295363.411552821 s in the future
linuxwacom-0.8.8-10/src/wacomxi/wacomcpl.in
tar: linuxwacom-0.8.8-10/src/wacomxi/wacomcpl.in: time stamp 2010-10-12 13:04:27 is 135295363.409926295 s in the future
linuxwacom-0.8.8-10/src/wacomxi/wacomxi.h
tar: linuxwacom-0.8.8-10/src/wacomxi/wacomxi.h: time stamp 2010-10-12 13:04:27 is 135295363.409715236 s in the future
linuxwacom-0.8.8-10/src/wacomxi/Makefile.am
tar: linuxwacom-0.8.8-10/src/wacomxi/Makefile.am: time stamp 2010-10-12 13:04:27 is 135295363.409582538 s in the future
linuxwacom-0.8.8-10/src/wacomxi/wacomxi.c
tar: linuxwacom-0.8.8-10/src/wacomxi/wacomxi.c: time stamp 2010-10-12 13:04:27 is 135295363.405320705 s in the future
linuxwacom-0.8.8-10/src/wacomxi/Makefile.in
tar: linuxwacom-0.8.8-10/src/wacomxi/Makefile.in: time stamp 2010-10-12 13:04:27 is 135295363.404043943 s in the future
linuxwacom-0.8.8-10/src/wacomxi/wacomcpl-exec
tar: linuxwacom-0.8.8-10/src/wacomxi/wacomcpl-exec: time stamp 2010-10-12 13:04:27 is 135295363.400162393 s in the future
linuxwacom-0.8.8-10/src/wacomxi/pkgIndex.tcl
tar: linuxwacom-0.8.8-10/src/wacomxi/pkgIndex.tcl: time stamp 2010-10-12 13:04:27 is 135295363.399984299 s in the future
linuxwacom-0.8.8-10/src/2.6.24/
tar: linuxwacom-0.8.8-10/src/wacomxi: time stamp 2010-10-12 13:04:27 is 135295363.399899093 s in the future
linuxwacom-0.8.8-10/src/2.6.24/wacom.h
tar: linuxwacom-0.8.8-10/src/2.6.24/wacom.h: time stamp 2010-10-12 13:04:27 is 135295363.3996851 s in the future
linuxwacom-0.8.8-10/src/2.6.24/Makefile.in
tar: linuxwacom-0.8.8-10/src/2.6.24/Makefile.in: time stamp 2010-10-12 13:04:27 is 135295363.39957552 s in the future
linuxwacom-0.8.8-10/src/util/
tar: linuxwacom-0.8.8-10/src/2.6.24: time stamp 2010-10-12 13:04:27 is 135295363.399516085 s in the future
linuxwacom-0.8.8-10/src/util/60-wacom.rules
tar: linuxwacom-0.8.8-10/src/util/60-wacom.rules: time stamp 2010-10-12 13:04:27 is 135295363.399279324 s in the future
linuxwacom-0.8.8-10/src/util/wacserial.c
tar: linuxwacom-0.8.8-10/src/util/wacserial.c: time stamp 2010-10-12 13:04:27 is 135295363.333397949 s in the future
linuxwacom-0.8.8-10/src/util/hal-setup-wacom.c
tar: linuxwacom-0.8.8-10/src/util/hal-setup-wacom.c: time stamp 2010-10-12 13:04:27 is 135295363.332579623 s in the future
linuxwacom-0.8.8-10/src/util/wacdump.c
tar: linuxwacom-0.8.8-10/src/util/wacdump.c: time stamp 2010-10-12 13:04:27 is 135295363.331418168 s in the future
linuxwacom-0.8.8-10/src/util/xsetwacom.c
tar: linuxwacom-0.8.8-10/src/util/xsetwacom.c: time stamp 2010-10-12 13:04:27 is 135295363.329487485 s in the future
linuxwacom-0.8.8-10/src/util/wacomcfg.c
tar: linuxwacom-0.8.8-10/src/util/wacomcfg.c: time stamp 2010-10-12 13:04:27 is 135295363.328340138 s in the future
linuxwacom-0.8.8-10/src/util/wacomcfg.h
tar: linuxwacom-0.8.8-10/src/util/wacomcfg.h: time stamp 2010-10-12 13:04:27 is 135295363.328167491 s in the future
linuxwacom-0.8.8-10/src/util/Makefile.am
tar: linuxwacom-0.8.8-10/src/util/Makefile.am: time stamp 2010-10-12 13:04:27 is 135295363.327711989 s in the future
linuxwacom-0.8.8-10/src/util/10-linuxwacom.fdi
tar: linuxwacom-0.8.8-10/src/util/10-linuxwacom.fdi: time stamp 2010-10-12 13:04:27 is 135295363.327612465 s in the future
linuxwacom-0.8.8-10/src/util/wacomxrrd.c
tar: linuxwacom-0.8.8-10/src/util/wacomxrrd.c: time stamp 2010-10-12 13:04:27 is 135295363.326622889 s in the future
linuxwacom-0.8.8-10/src/util/xidump.c
tar: linuxwacom-0.8.8-10/src/util/xidump.c: time stamp 2010-10-12 13:04:27 is 135295363.325081569 s in the future
linuxwacom-0.8.8-10/src/util/wacscrn.c
tar: linuxwacom-0.8.8-10/src/util/wacscrn.c: time stamp 2010-10-12 13:04:27 is 135295363.324909551 s in the future
linuxwacom-0.8.8-10/src/util/wcmAction.h
tar: linuxwacom-0.8.8-10/src/util/wcmAction.h: time stamp 2010-10-12 13:04:27 is 135295363.324798225 s in the future
linuxwacom-0.8.8-10/src/util/Makefile.in
tar: linuxwacom-0.8.8-10/src/util/Makefile.in: time stamp 2010-10-12 13:04:27 is 135295363.323464892 s in the future
linuxwacom-0.8.8-10/src/util/wacusb.c
tar: linuxwacom-0.8.8-10/src/util/wacusb.c: time stamp 2010-10-12 13:04:27 is 135295363.321814829 s in the future
linuxwacom-0.8.8-10/src/util/wactablet.h
tar: linuxwacom-0.8.8-10/src/util/wactablet.h: time stamp 2010-10-12 13:04:27 is 135295363.321192267 s in the future
linuxwacom-0.8.8-10/src/util/wacusb.h
tar: linuxwacom-0.8.8-10/src/util/wacusb.h: time stamp 2010-10-12 13:04:27 is 135295363.321004884 s in the future
linuxwacom-0.8.8-10/src/util/wcmAction.c
tar: linuxwacom-0.8.8-10/src/util/wcmAction.c: time stamp 2010-10-12 13:04:27 is 135295363.320276723 s in the future
linuxwacom-0.8.8-10/src/util/wacscrn.h
tar: linuxwacom-0.8.8-10/src/util/wacscrn.h: time stamp 2010-10-12 13:04:27 is 135295363.320138437 s in the future
linuxwacom-0.8.8-10/src/util/wacserial.h
tar: linuxwacom-0.8.8-10/src/util/wacserial.h: time stamp 2010-10-12 13:04:27 is 135295363.319403711 s in the future
linuxwacom-0.8.8-10/src/util/wactablet.c
tar: linuxwacom-0.8.8-10/src/util/wactablet.c: time stamp 2010-10-12 13:04:27 is 135295363.317911978 s in the future
linuxwacom-0.8.8-10/src/2.6.16/
tar: linuxwacom-0.8.8-10/src/util: time stamp 2010-10-12 13:04:27 is 135295363.317809452 s in the future
linuxwacom-0.8.8-10/src/2.6.16/wacom.h
tar: linuxwacom-0.8.8-10/src/2.6.16/wacom.h: time stamp 2010-10-12 13:04:27 is 135295363.317591059 s in the future
linuxwacom-0.8.8-10/src/2.6.16/wacom_wac.h
tar: linuxwacom-0.8.8-10/src/2.6.16/wacom_wac.h: time stamp 2010-10-12 13:04:27 is 135295363.316754993 s in the future
linuxwacom-0.8.8-10/src/2.6.16/wacom_sys.c
tar: linuxwacom-0.8.8-10/src/2.6.16/wacom_sys.c: time stamp 2010-10-12 13:04:27 is 135295363.315878839 s in the future
linuxwacom-0.8.8-10/src/2.6.16/Makefile.in
tar: linuxwacom-0.8.8-10/src/2.6.16/Makefile.in: time stamp 2010-10-12 13:04:27 is 135295363.315106468 s in the future
linuxwacom-0.8.8-10/src/2.6.16/wacom_wac.c
tar: linuxwacom-0.8.8-10/src/2.6.16/wacom_wac.c: time stamp 2010-10-12 13:04:27 is 135295363.312377922 s in the future
linuxwacom-0.8.8-10/src/2.6.16/hid-core.c
tar: linuxwacom-0.8.8-10/src/2.6.16/hid-core.c: time stamp 2010-10-12 13:04:27 is 135295363.30264426 s in the future
linuxwacom-0.8.8-10/mkxincludes.in
tar: linuxwacom-0.8.8-10/src/2.6.16: time stamp 2010-10-12 13:04:27 is 135295363.302533004 s in the future
tar: linuxwacom-0.8.8-10/src: time stamp 2010-10-12 13:04:27 is 135295363.302485163 s in the future
tar: linuxwacom-0.8.8-10/mkxincludes.in: time stamp 2010-10-12 13:04:27 is 135295363.302368179 s in the future
linuxwacom-0.8.8-10/install-sh
tar: linuxwacom-0.8.8-10/install-sh: time stamp 2010-10-12 13:04:27 is 135295363.300550778 s in the future
linuxwacom-0.8.8-10/config.guess
tar: linuxwacom-0.8.8-10/config.guess: time stamp 2010-10-12 13:04:27 is 135295363.297442088 s in the future
linuxwacom-0.8.8-10/Makefile.am
tar: linuxwacom-0.8.8-10/Makefile.am: time stamp 2010-10-12 13:04:27 is 135295363.297268394 s in the future
linuxwacom-0.8.8-10/autom4te.cache/
linuxwacom-0.8.8-10/autom4te.cache/output.1
tar: linuxwacom-0.8.8-10/autom4te.cache/output.1: time stamp 2010-10-12 13:04:27 is 135295363.187410555 s in the future
linuxwacom-0.8.8-10/autom4te.cache/output.0
tar: linuxwacom-0.8.8-10/autom4te.cache/output.0: time stamp 2010-10-12 13:04:27 is 135295363.074272776 s in the future
linuxwacom-0.8.8-10/autom4te.cache/traces.1
tar: linuxwacom-0.8.8-10/autom4te.cache/traces.1: time stamp 2010-10-12 13:04:27 is 135295363.071374517 s in the future
linuxwacom-0.8.8-10/autom4te.cache/traces.0
tar: linuxwacom-0.8.8-10/autom4te.cache/traces.0: time stamp 2010-10-12 13:04:27 is 135295363.041464088 s in the future
linuxwacom-0.8.8-10/autom4te.cache/requests
tar: linuxwacom-0.8.8-10/autom4te.cache/requests: time stamp 2010-10-12 13:04:27 is 135295363.040214145 s in the future
linuxwacom-0.8.8-10/ltmain.sh
tar: linuxwacom-0.8.8-10/autom4te.cache: time stamp 2010-10-12 13:04:27 is 135295363.040099327 s in the future
tar: linuxwacom-0.8.8-10/ltmain.sh: time stamp 2010-10-12 13:04:27 is 135295362.961531275 s in the future
linuxwacom-0.8.8-10/aclocal.m4
tar: linuxwacom-0.8.8-10/aclocal.m4: time stamp 2010-10-12 13:04:27 is 135295362.932969265 s in the future
linuxwacom-0.8.8-10/GPL
tar: linuxwacom-0.8.8-10/GPL: time stamp 2010-10-12 13:04:27 is 135295362.931160455 s in the future
linuxwacom-0.8.8-10/ChangeLog
tar: linuxwacom-0.8.8-10/ChangeLog: time stamp 2010-10-12 13:04:27 is 135295362.930259995 s in the future
linuxwacom-0.8.8-10/configure.in
tar: linuxwacom-0.8.8-10/configure.in: time stamp 2010-10-12 13:04:27 is 135295362.927899791 s in the future
linuxwacom-0.8.8-10/Makefile.in
tar: linuxwacom-0.8.8-10/Makefile.in: time stamp 2010-10-12 13:04:27 is 135295362.926576864 s in the future
linuxwacom-0.8.8-10/missing
tar: linuxwacom-0.8.8-10/missing: time stamp 2010-10-12 13:04:27 is 135295362.925936702 s in the future
linuxwacom-0.8.8-10/config.sub
tar: linuxwacom-0.8.8-10/config.sub: time stamp 2010-10-12 13:04:27 is 135295362.924073485 s in the future
linuxwacom-0.8.8-10/AUTHORS
tar: linuxwacom-0.8.8-10/AUTHORS: time stamp 2010-10-12 13:04:27 is 135295362.923885194 s in the future
linuxwacom-0.8.8-10/bootstrap
tar: linuxwacom-0.8.8-10/bootstrap: time stamp 2010-10-12 13:04:27 is 135295362.923776801 s in the future
linuxwacom-0.8.8-10/configure
tar: linuxwacom-0.8.8-10/configure: time stamp 2010-10-12 13:04:27 is 135295362.841921407 s in the future
tar: linuxwacom-0.8.8-10: time stamp 2010-10-12 13:04:27 is 135295362.841609497 s in the future
trevor@trevor-915P-A2:~/Desktop$ cd linuxwacom-0.8.8-10
trevor@trevor-915P-A2:~/Desktop/linuxwacom-0.8.8-10$ ./configure --enable-wacom --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... configure: error: newly created file is older than distributed files!
Check your system clock
trevor@trevor-915P-A2:~/Desktop/linuxwacom-0.8.8-10$ sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
cp: cannot stat `./src/2.6.30/wacom.ko': No such file or directory
trevor@trevor-915P-A2:~/Desktop/linuxwacom-0.8.8-10$ ./configure --enable-wacom --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... configure: error: newly created file is older than distributed files!
Check your system clock
trevor@trevor-915P-A2:~/Desktop/linuxwacom-0.8.8-10$ sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
cp: cannot stat `./src/2.6.30/wacom.ko': No such file or directory
trevor@trevor-915P-A2:~/Desktop/linuxwacom-0.8.8-10$ ^C
trevor@trevor-915P-A2:~/Desktop/linuxwacom-0.8.8-10$

---

### Post by Favux on 2011-01-12
According to the output your computer's date and clock are not set correctly.  Check the date and time, it should be in the upper right corner of the top panel.  If it is wrong go to System > Administration > Time and Date and set the correct settings.

---

### Post by Hunter Tech on 2011-01-12
i have went through the section 8 but in the folder for X11 and i do not have the xorg.conf.d file at all.

---

### Post by Hunter Tech on 2011-01-12
> **Favux said:**
> According to the output your computer's date and clock are not set correctly.  Check the date and time, it should be in the upper right corner of the top panel.  If it is wrong go to System > Administration > Time and Date and set the correct settings.

I have now setup the time properly, should i redo that step?

---

### Post by Favux on 2011-01-12
Yes, you need a working wacom.ko.

So you compiled the working wacom.ko and copied it into place now?  Because Synaptic won't work without it.

It should be at /usr/share/X11/xorg.conf.d/.  If you are talking about /etc/X11/ you may have to create it.  Change to path below to /etc/X11/60-bamboo.conf  And you would edit it with:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-synaptics.conf
```
You use gksudo instead of sudo to make you root/super user because it is the graphical version of sudo.  And the text editor gedit (Gnome edit) is a graphical program.  You need to be root to have permission to modify a system file.  The rest is the directory path to the file.

---

### Post by Hunter Tech on 2011-01-12
i am going to redo step 1 now that i have the date and time correct.  Also could the date and time thing have anything to do with my nvidia graphics card problem?  each time i install that driver (173) my computer freezes up at boot during the checking battery status phase

---

### Post by Favux on 2011-01-12
Good.  Hope it works for you now.

Could be.  Also make sure in Hardware Drivers you're selecting the Nvidia driver that says Recommended.

---

