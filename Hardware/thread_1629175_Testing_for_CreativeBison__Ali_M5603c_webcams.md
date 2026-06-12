---
title: "Testing for Creative/Bison  Ali M5603c webcams"
date: 2010-11-23
forum: Hardware
---

### Post by Franck78 on 2010-11-23
I would like some users to test and try my linux driver for theses Webcams


ID 041e:4055 Creative Technology, Ltd Live! Cam Video IM Pro
ID 0402:5603 ALi Corp. USB 2.0 Q-tec Webcam 300

if they have the cam of course ;)

Some notebook from Asus (A6000) have it.

Driver is here:

[http://m560x-driver.svn.sourceforge.net/viewvc/m560x-driver/m560x/branches/m5603c-gspca/](http://m560x-driver.svn.sourceforge.net/viewvc/m560x-driver/m560x/branches/m5603c-gspca/)

Franck

---

### Post by zcat on 2010-12-04
Bus 001 Device 002: ID 0402:5603 ALi Corp. USB 2.0 Q-tec Webcam 300

I'd love to test your driver but you'll need to provide slightly clearer instructions on how to compile it, it's been a while since I did this. Ubuntu 10.04.

---

### Post by zcat on 2010-12-06
> **zcat said:**
> Bus 001 Device 002: ID 0402:5603 ALi Corp. USB 2.0 Q-tec Webcam 300

I'd love to test your driver but you'll need to provide slightly clearer instructions on how to compile it, it's been a while since I did this. Ubuntu 10.04.

Finally managed to get it to compile, after a bit of hassles with the stock kernels I decided to compile a 2.6.35.4 one from backports and then managed to get the module to load. Works great (as far as I can tell, not very good light at the moment) except that cheese constantly takes pictures, I presume there's some 'take a photo' button function that needs fixing?

Anything else you want me to look at?

---

### Post by luctor on 2010-12-14
kernel 2.6.33-29-realtime
compiled ok, modprobe etc works ok

plugging camera in :
```
m5603c: ALi m5603c bridge disconnected
usb 1-8: new high speed USB device using ehci_hcd and address 10
gspca: probing 0402:5603
m5603c: ALi m5603c is USB2
m5603c: Sending binary microcode to ALi m5603c (size:3716)
m5603c: Checking Bridge ALi m5603c
m5603c: Signature 00 00 00 00
m5603c: Detected Sensor SENSOR_7648_POWDN_Q
input: m5603c as /devices/pci0000:00/0000:00:02.1/usb1/1-8/input/input8
gspca: video0 created

```
./pixfmt-test -d /dev/video0
```
./pixfmt-test: select timeout.
```
all I get is a black window
[[IMG]http://img2.imagebanana.com/img/eef81l3f/thumb/V4L2PixfmtTestPressnfornextformatcfo.png[/IMG]](http://www.imagebanana.com/view/eef81l3f/V4L2PixfmtTestPressnfornextformatcfo.png)

will try with the generic kernel

---

### Post by luctor on 2010-12-14
some more info
```
Bus 001 Device 008: ID 0402:5603 ALi Corp. M5603 Video Camera Controller
```

same result with 2.6.35-23-generic, black windows in pixfmt-test and cheese
Also tried cheese with LD_PRELOAD workaround

> **luctor said:**
> kernel 2.6.33-29-realtime
compiled ok, modprobe etc works ok

plugging camera in :
```
m5603c: ALi m5603c bridge disconnected
usb 1-8: new high speed USB device using ehci_hcd and address 10
gspca: probing 0402:5603
m5603c: ALi m5603c is USB2
m5603c: Sending binary microcode to ALi m5603c (size:3716)
m5603c: Checking Bridge ALi m5603c
m5603c: Signature 00 00 00 00
m5603c: Detected Sensor SENSOR_7648_POWDN_Q
input: m5603c as /devices/pci0000:00/0000:00:02.1/usb1/1-8/input/input8
gspca: video0 created

```
./pixfmt-test -d /dev/video0
```
./pixfmt-test: select timeout.
```
all I get is a black window
[[IMG]http://img2.imagebanana.com/img/eef81l3f/thumb/V4L2PixfmtTestPressnfornextformatcfo.png[/IMG]](http://www.imagebanana.com/view/eef81l3f/V4L2PixfmtTestPressnfornextformatcfo.png)

will try with the generic kernel

---

### Post by kuzniarpawel on 2011-01-08
Bus 004 Device 002: ID 0402:5603 ALi Corp. M5603 Video Camera Controller


[   14.160755] Linux video capture interface: v2.00
[   14.160759] WARNING: You're using an experimental version of the V4L stack. As the driver
[   14.160760]          is backported to an older kernel, it doesn't offer enough quality for
[   14.160761]          its usage in production.
[   14.160762]          Use it with care.
[   14.230922] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04791/0x300000/0x0
[   14.230924] Synaptics: Clickpad mode enabled
[   14.230928] serio: Synaptics pass-through port at isa0060/serio1/input0
[   14.288708] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.288713] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   14.288884]   alloc irq_desc for 49 on node -1
[   14.288886]   alloc kstat_irqs on node -1
[   14.288904] HDA Intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[   14.288952] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.295215] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   14.365848] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   14.365895] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   14.365910] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.365920] nvidia 0000:01:00.0: setting latency timer to 64
[   14.365925] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   14.366134] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
[   14.487895] iwlagn 0000:03:00.0: loaded firmware version 228.61.2.24
[   14.496248] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.512490] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xe0000-0xfffff
[   14.512556] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[   14.512615] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   14.559759] gspca: main v2.9.0 registered
[   14.636827] gspca: probing 0402:5603
[   14.637648] m5603c: ALi m5603c is USB2
[   14.638397] m5603c: Sending binary microcode to ALi m5603c (size:3716)
[   14.655338] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.680524] m5603c: Checking Bridge ALi m5603c
[   14.721457] m5603c: Signature 03 56 AA 55
[   14.739326] m5603c: ALi m5603c Bridge vid pid 0402.5603
[   14.749259] m5603c: Confdescripor is 1
[   14.786900] m5603c: Descriptor: For demo only
[   14.914271] m5603c: Detected Sensor SENSOR_7648_POWDN_Q
[   14.915964] input: m5603c as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/input/input7
[   14.916096] gspca: video0 created
[   14.916143] usbcore: registered new interface driver m5603c
[   14.916145] m5603c: ALi m5603c bridge v1.1.0 registered
[   16.290059] CE: hpet increased min_delta_ns to 7500 nsec
[   17.457825] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   17.829710] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   18.033191] type=1400 audit(1294481164.941:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=990 comm="apparmor_parser"
[   18.033462] type=1400 audit(1294481164.941:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=991 comm="apparmor_parser"
[   18.034142] type=1400 audit(1294481164.941:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=991 comm="apparmor_parser"
[   18.034512] type=1400 audit(1294481164.941:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=991 comm="apparmor_parser"
[   18.038910] type=1400 audit(1294481164.941:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=994 comm="apparmor_parser"
[   18.039738] type=1400 audit(1294481164.941:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=994 comm="apparmor_parser"
[   18.042973] type=1400 audit(1294481164.951:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=995 comm="apparmor_parser"
[   18.176865] ppdev: user-space parallel port driver
[   18.412952] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   18.472679] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   18.473236] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.235098] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   20.473429] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8
[   20.915223] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   20.915228] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   20.915724] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.086657] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   22.138438] EXT4-fs (sda3): re-mounted. Opts: commit=0
[   25.239054] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   25.241797] EXT4-fs (sda3): re-mounted. Opts: commit=0
[   31.750072] eth0: no IPv6 routers present
[  155.510072] CE: hpet increased min_delta_ns to 11250 nsec
[  303.675533] m5603c: entering ov7648_start_asus
[  395.297691] lo: Disabled Privacy Extensions
[  580.376638] usb 2-2: USB disconnect, address 2
[  580.385554] gspca: video0 disconnect
[  580.442765] m5603c: ALi m5603c bridge disconnected
[  591.630121] usb 2-1: new high speed USB device using ehci_hcd and address 3
[  591.700424] hub 2-0:1.0: unable to enumerate USB device on port 1
[  592.020123] usb 5-1: new full speed USB device using uhci_hcd and address 2
[  592.191200] usb 5-1: not running at top speed; connect to a high speed hub
[  592.265382] gspca: probing 0402:5603
[  592.270513] m5603c: ALi m5603c is USB1
[  592.270519] m5603c: Low usb speed (usb1) not supported.
[  603.708210] gspca: video0 released

It loads on reboot - but gives black screen in Cheese. After disconnecting and reconnecting camera to USB gives m5603c: Low usb speed (usb1) not supported.

on SWEEX webcam

---

### Post by kuzniarpawel on 2011-01-08
Bus 001 Device 003: ID 041e:4055 Creative Technology, Ltd Live! Cam Video IM Pro


works perfectly 


[  801.652746] gspca: probing 041e:4055
[  801.653539] m5603c: ALi m5603c is USB2
[  801.654286] m5603c: Sending binary microcode to ALi m5603c (size:3716)
[  801.696666] m5603c: Checking Bridge ALi m5603c
[  801.737548] m5603c: Signature 03 56 AA 55
[  801.755293] m5603c: ALi m5603c Bridge vid pid 041e.4055
[  801.765168] m5603c: Confdescripor is 1
[  801.825429] m5603c: Descriptor: Live! Cam Video IM Pro
[  801.956423] m5603c: setup gpio addr:4 state:1
[  801.957895] m5603c: setup gpio addr:5 state:0
[  801.959417] m5603c: setup gpio addr:2 state:0
[  801.962300] input: m5603c as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/input/input9
[  801.964247] gspca: video0 created

---

### Post by kuzniarpawel on 2011-01-09
tested once again with Sweex webcam

[  207.024090] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  207.231147] gspca: probing 0402:5603
[  207.231855] m5603c: ALi m5603c is USB2
[  207.232729] m5603c: Sending binary microcode to ALi m5603c (size:3716)
[  207.274971] m5603c: Checking Bridge ALi m5603c
[  207.315706] m5603c: Signature 03 56 AA 55
[  207.333446] m5603c: ALi m5603c Bridge vid pid 0402.5603
[  207.343318] m5603c: Confdescripor is 1
[  207.376550] m5603c: Descriptor: For demo only
[  207.496113] m5603c: Detected Sensor SENSOR_7648_POWDN_Q
[  207.498654] input: m5603c as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/input/input8
[  207.499548] gspca: video0 created
[  234.770585] m5603c: entering ov7648_start_asus
[  283.514386] lo: Disabled Privacy Extensions
[  307.742289] lo: Disabled Privacy Extensions
[  640.789012] usb 1-1: USB disconnect, address 3
[  640.789097] gspca: video0 disconnect
[  640.789389] gspca: video0 released
[  640.789395] m5603c: ALi m5603c bridge disconnected
[  644.240101] usb 1-2: new high speed USB device using ehci_hcd and address 4
[  644.447104] gspca: probing 0402:5603
[  644.448043] m5603c: ALi m5603c is USB2
[  644.448768] m5603c: Sending binary microcode to ALi m5603c (size:3716)
[  644.491152] m5603c: Checking Bridge ALi m5603c
[  644.531912] m5603c: Signature 03 56 AA 55
[  644.549664] m5603c: ALi m5603c Bridge vid pid 0402.5603
[  644.559540] m5603c: Confdescripor is 1
[  644.592664] m5603c: Descriptor: For demo only
[  644.716409] m5603c: Detected Sensor SENSOR_7648_POWDN_Q
[  644.719053] input: m5603c as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/input/input9
[  644.719979] gspca: video0 created

no problem with low speed usb
but still gives black screen only

---

### Post by chiefofthejojos on 2011-04-02
I'm having trouble compiling, can anyone provide a binary?

---

### Post by nikio on 2011-04-28
Hello,
I have a Creative Im Pro cam (ID 043e:4055) and I'm trying to install the driver, I'm following the instructions step by step except from the installation of libncurses5-dev.
I got to the "make menuconfig" step:
> 3) Compile minimal source from v4l-dvb; 300 modules, 5 required!
    Deselect everything except gspca/m5603c
    cd ./v4l-dvb/v4l
    make menuconfig
-I'm not sure whether "Deselect everything except gspca/m5603c" is the title for the following or if it is an something I should do (deselect from where?) I've decided for the first and moved on

- I need to type "**sudo** make menuconfig" in order to avoid errors, and after that a text interface opens but I don't know what to do with it,
can anyone help?

---

### Post by nikio on 2011-04-28
I managed to install the driver, the **image** works but it is very dark, **nearly black**.

I have a couple of suggestions to make the installation a little more straight forward for newbies like me:
-I think I've installed loads of useless things, maybe you could include in the package an essential .config file that contains only the useful lines? One that can be copied directly in the directory?
-in ubuntu many of the commands must be preceded by sudo
- about step 3)
>     Deselect everything except gspca/m5603c
    cd ./v4l-dvb/v4l
    make menuconfig
the "deselect" line should come after "make menu config" line, I think.
maybe you could add a couple of lines to explain the deselecting thing?


**EDIT**: for the **brightness issue** no2498 suggested to install v4l2ucp, a control panel for video regulations.
in my experience the "brightness" control makes it crash but with the gamma control I got a fair image.

---

### Post by Ubuntaqua on 2012-01-09
Hello all,

Digging this from the grave as I tried to have my Creative Live! work. I don't know if the author is still listening :)

I failed to compile the module independantly for some reason and ended up compiling a whole kernel instead, just adding the m5603c bits. (for some reason I cannot change the "My Ubuntu distro" in my profile info, but it's on an old laptop running Lubuntu Oneiric, kernel 3.0.0.

Module loads (somewhat dark immage) and my first attempt at changing brightness/contrast/whatever through the v4l control app resulted in a X crash. I'll try to get logs if needed.

To be added in the Intallation Readme:
- To compile v4l-utils and/or pixfmt-test, you will need libjpeg and xlibs developpment packages.

Cheers !

---

### Post by Franck78 on 2012-06-08
Hello,
I do sometime come to see what is happening.

I have the page fault on brigthness. Will look at it. So much things to simplify this driver before sendind it to Jean François (gspcav2) ;-)

Note: I have a perfect image with my creative cam as well as the integrated qtec in my Asus notebook.

Franck

---

### Post by mörgæs on 2012-08-06
Hi, I have an Asus A6U with the ALi Corp. M5603 integrated webcam.

Using Lubuntu 12.04 everything but the cam works well.

Are the any drivers for 12.04 available?

---

### Post by tovmeod on 2012-12-12
Sorry for reviving the old post, but I got the 041e:4055 Creative Technology, Ltd Live! Cam Video IM Pro

I downloaded the m5603c driver and the v4l project following instruction here: [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)
 I'm having trouble compiling the m5603c driver, when I hist make this is what I get:

avraham@avraham-ubuntu:~/media_build/v4l$ make
creating symbolic links...
make -C firmware prep
make[1]: Entering directory `/home/avraham/media_build/v4l/firmware'
make[1]: Leaving directory `/home/avraham/media_build/v4l/firmware'
make -C firmware
make[1]: Entering directory `/home/avraham/media_build/v4l/firmware'
make[1]: Nothing to be done for `default'.
make[1]: Leaving directory `/home/avraham/media_build/v4l/firmware'
Kernel build directory is /lib/modules/3.5.0-19-generic/build
make -C ../linux apply_patches
make[1]: Entering directory `/home/avraham/media_build/linux'
Patches for 3.5.0-19-generic already applied.
make[1]: Leaving directory `/home/avraham/media_build/linux'
make -C /lib/modules/3.5.0-19-generic/build SUBDIRS=/home/avraham/media_build/v4l  modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-19-generic'
  CC [M]  /home/avraham/media_build/v4l/m5603c_core.o
/home/avraham/media_build/v4l/m5603c_core.c: In function 'sd_start':
/home/avraham/media_build/v4l/m5603c_core.c:402:3: error: implicit declaration of function 'err' [-Werror=implicit-function-declaration]
/home/avraham/media_build/v4l/m5603c_core.c: In function 'sd_disconnect':
/home/avraham/media_build/v4l/m5603c_core.c:638:2: error: implicit declaration of function 'info' [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/avraham/media_build/v4l/m5603c_core.o] Error 1
make[1]: *** [_module_/home/avraham/media_build/v4l] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-19-generic'
make: *** [default] Error 2


any thoughts?

thanks

---

### Post by Franck78 on 2012-12-13
Hello,
This driver source is very old and gspca changed since.

Espacially macros in gspca.h

So find replace every
err -> pr_err
infor -> pr_info

My Asus have been stolen, so I don't have anymore integrated Cam
But my livecam impro is still ready to test ;-)

Just need time to cleanup the driver !


in m5603c_core.c find this :

[COLOR=SlateGray]        /*  Turn RED the led */
        if (cam->cam_creative) {
                set_gpio_port(cam, 4, 0); /* GREEN off */
                set_gpio_port(cam, 2, 1); /* what on? button ??*/
                set_gpio_port(cam, 5, 1); /* RED on */
        } else /* for now creative don't use Qtec tables */
                cam->cb_set_default_exposure(cam);
[/COLOR]
and try with that
[COLOR=SlateGray]        /*  Turn RED the led */
        if (cam->cam_creative) {
                set_gpio_port(cam, 4, 0); /* GREEN off */
                set_gpio_port(cam, 2, 1); /* what on? button ??*/
                set_gpio_port(cam, 5, 1); /* RED on */
[COLOR=DarkRed]        };
[/COLOR][/COLOR][COLOR=DarkRed]         cam->cb_set_default_exposure(cam);
[/COLOR]
but this driver is really ugly. I sometime work on another one.

Franck

---

### Post by tovmeod on 2012-12-15
the important thing is that it works, I should eventually buy a new webcam, but for now this is what I got.

In any case I still get errors on make:

/home/avraham/media_build/v4l/m5603c_core.c: In function 'sd_start':
/home/avraham/media_build/v4l/m5603c_core.c:402:3: error: implicit declaration of function 'err' [-Werror=implicit-function-declaration]
/home/avraham/media_build/v4l/m5603c_core.c: In function 'sd_disconnect':
/home/avraham/media_build/v4l/m5603c_core.c:638:2: error: implicit declaration of function 'info' [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/avraham/media_build/v4l/m5603c_core.o] Error 1
make[1]: *** [_module_/home/avraham/media_build/v4l] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-19-generic'
make: *** [default] Error 2

---

### Post by Franck78 on 2012-12-16
[B]So find replace every
err -> pr_err
infor -> pr_info

[/B]*m5603c_core.c:402:3:error: implicit declaration of function 'err' *

If you don't do what I told you, what do you want ?

Anyway, I think it won't be enougth, so many changes on the linuxtv.org side !

---

### Post by mörgæs on 2012-12-16
> **Franck78 said:**
> 
but this driver is really ugly. I sometime work on another one.


If a new version is coming up, please let us know!

Is there anything we can do in order to help the process?

---

