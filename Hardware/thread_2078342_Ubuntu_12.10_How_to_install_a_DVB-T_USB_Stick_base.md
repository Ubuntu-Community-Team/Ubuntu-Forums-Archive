---
title: "Ubuntu 12.10: How to install a DVB-T USB Stick based on a Realtek rtl2832u chip"
date: 2012-10-30
forum: Hardware
---

### Post by milro on 2012-10-30
After searching on Internet with no success for instructions ( and source) to compile a rtl2832u module on Ubuntu 12.10 (x64) with 3.5 kernel I solved the problem by doing the following

a. First, I've upgraded to 3.6 kernel series from an official ubuntu repository.
     
     Link: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/)

I've installed the following packets for my x64 enviroment:

[linux-headers-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.6.3-quantal/linux-headers-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb")       21-Oct-2012 17:57  921K
[linux-headers-3.6.3-030603_3.6.3-030603.201210211349_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.6.3-quantal/linux-headers-3.6.3-030603_3.6.3-030603.201210211349_all.deb")          21-Oct-2012 17:50   12M
[linux-image-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.6.3-quantal/linux-image-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb")        21-Oct-2012 17:57   12M
[linux-image-extra-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb        ]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.6.3-quantal/linux-image-extra-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb")21-Oct-2012 17:57   27M  

b. From this link: [http://git.linuxtv.org/media_build.git](http://git.linuxtv.org/media_build.git)
I cloned and built the repository following these instructions:

git clone git://linuxtv.org/media_build.git
cd media_build
./build

c. I did not install the modules because after I built it I wanted to recompile it again manually. First, I had to alter two files, in the source: "rtl28xxu.c" and "dvb-usb-ids.h" in order to add my dvb-t stick's vendor id (0x1b80) and product id (0xd394). I've attached a zip archive with these two altered files. You can track the changes by searching for the word:

Turbox

I found the vendor id and product id from the syslog when I connected the stick on a USB port. Below is a copy from the relevant part of my syslog:

[SIZE=2][COLOR=DarkRed]Oct 30 18:02:49 ubuntu kernel: [ 2885.211906] usb 2-1.5: new high-speed USB device number 6 using ehci_hcd
Oct 30 18:02:50 ubuntu kernel: [ 2885.313752] usb 2-1.5: New USB device found, **idVendor=1b80, idProduct=d394**
Oct 30 18:02:50 ubuntu kernel: [ 2885.313757] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Oct 30 18:02:50 ubuntu kernel: [ 2885.313760] usb 2-1.5: Product: usbtv
Oct 30 18:02:50 ubuntu kernel: [ 2885.313763] usb 2-1.5: Manufacturer: realtek[/COLOR][/SIZE]

d. I compiled manually the tree by ***cd***'ing inside the directory **media_build**($ *cd media_build*).

For compiling, first do:

*make clean*

and after

*make -C ./v4l*

e. Last I've installed the modules:

*sudo make install*

I used MeTV to scan for the channels. The scan finished succesfully but I could only tune and view the first channel on the list.
With VLC i had no problem at all. Everything worked beautifully.


I hope these instructions  to prove helpful for others too

---

### Post by LSDalKa on 2012-11-07
Hi milro
I guess you are from greece and i'm wondering if your tuner is the Turbo-X DTT-1000.
P.S. I tried your method but with the default kernel 3.5
Everything seemed to go smoothly but still the tuner is not recognized
Also, what Firmware did you use??
Thanks

---

### Post by milro on 2012-11-10
> **LSDalKa said:**
> Hi milro
I guess you are from greece and i'm wondering if your tuner is the Turbo-X DTT-1000.
P.S. I tried your method but with the default kernel 3.5
Everything seemed to go smoothly but still the tuner is not recognized
Also, what Firmware did you use??
Thanks
Hi! I am from Greece as you said and yes the commercial name of my stick is Turbo-X DTT-1000.
The most important thing before you do anything is to connect your usb stick, check the syslog and write down the idVendor (1b80 in my case) and idProduct (d394 in mycase).
If these are the same as mine then ultimately the tuner can work on Ubuntu. I did not try the 3.5 series kernel at all, but now that i've read your post i will reboot my machine to the older kernel and i will try to compile the v4l tree against it and see if it will work...
I will post again as soon as I have results...
For my tuner there is no need to do anything for the firmware

---

### Post by milro on 2012-11-10
> **milro said:**
> Hi! I am from Greece as you said and yes the commercial name of my stick is Turbo-X DTT-1000.
The most important thing before you do anything is to connect your usb stick, check the syslog and write down the idVendor (1b80 in my case) and idProduct (d394 in mycase).
If these are the same as mine then ultimately the tuner can work on Ubuntu. I did not try the 3.5 series kernel at all, but now that i've read your post i will reboot my machine to the older kernel and i will try to compile the v4l tree against it and see if it will work...
I will post again as soon as I have results...
For my tuner there is no need to do anything for the firmware

Ok, I've tried it on 3.5.0-17-generic and everything worked fine. So, probably you are doing something wrong or you have a different stick than mine which perhaps is not supported.
If you provide a relevant part from your syslog perhaps I could understand better your problem.

---

### Post by LSDalKa on 2012-11-10
WoW! You did kernel downgrade just to help me!
I really don't know what to say:D
I hope you won't curse me but I have already tried with the updated kernel from the links you provided (with the same results).
We have exactly the same tuner and the same OS.
The installation is absolutely smooth, no error at all.
One thing that I haven't tried is to wipe all the different methods  I have tried for installing the V4L&DVB and and all the firmwares etc. and all the associated files they installed before applying the modified one you provided.
Being total beginner in linux I am not sure if that interferred with anything,
BUT for sure with your method I saw two positive differences:
1)Some error-like messages at the boot screen about the device disappeared
(i don't recall the exact messages but they didn't seem fatal)
2)I found the following lines in dmesg which i think have not appeared until then: 
[ 9263.952207] usb 1-2: new high-speed USB device number 4 using ehci_hcd
[ 9264.094122] usb 1-2: New USB device found, idVendor=1b80, idProduct=d394
[ 9264.094133] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 9264.094140] usb 1-2: Product: usbtv
[ 9264.094145] usb 1-2: Manufacturer: realtek
Unfortunately none of the three DVB programs I tried seemed to 'see' the tuner.
As I am out of time today, I 'll try tommorow to clear everything fisrt and then reinstall once again watching closely the syslog and I'll report back.
Really apreciate your help...

---

### Post by milro on 2012-11-11
> **LSDalKa said:**
> WoW! You did kernel downgrade just to help me!
I really don't know what to say:D
I hope you won't curse me but I have already tried with the updated kernel from the links you provided (with the same results).
We have exactly the same tuner and the same OS.
The installation is absolutely smooth, no error at all.
One thing that I haven't tried is to wipe all the different methods  I have tried for installing the V4L&DVB and and all the firmwares etc. and all the associated files they installed before applying the modified one you provided.
Being total beginner in linux I am not sure if that interferred with anything,
BUT for sure with your method I saw two positive differences:
1)Some error-like messages at the boot screen about the device disappeared
(i don't recall the exact messages but they didn't seem fatal)
2)I found the following lines in dmesg which i think have not appeared until then: 
[ 9263.952207] usb 1-2: new high-speed USB device number 4 using ehci_hcd
[ 9264.094122] usb 1-2: New USB device found, idVendor=1b80, idProduct=d394
[ 9264.094133] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 9264.094140] usb 1-2: Product: usbtv
[ 9264.094145] usb 1-2: Manufacturer: realtek
Unfortunately none of the three DVB programs I tried seemed to 'see' the tuner.
As I am out of time today, I 'll try tommorow to clear everything fisrt and then reinstall once again watching closely the syslog and I'll report back.
Really apreciate your help...

Do not be afraid, I will not curse you because I did not do any downgrades :-) I 've just booted to a previous kernel using the advanced option in ubuntu boot menu.
Seeing your log, this is the exact message I saw when I first connected my usb stick after the 12.10 ubuntu installation without any drivers for it. So if you see just that then it will not work.
Let's try modify my original instructions for the default kernel and be more specific...

1. You have to install git. You can do that from the ubuntu software center

2. You have to install the linux headers for your kernel (I do not remember if originally are there already...):
Close the ubuntu software center if it is still open
On Dash menu (the first icon, top left on your monitor)  write **synaptic**. You will see an application with that name, open it.
It will ask for your password to authenticate.
When it's open you will see on top a search lens icon and besides it a search box. Write on the search box **linux-headers-3.5.0-17** (you do not have to press enter). You will see immediately below the result of your search. Every line has a check box. One of the lines, beside the check box it will has the exact name **linux-headers-3.5.0-17**. If it is checked then the headers are installed. If you are not sure, you can do a right click on this line and on the menu you will see the options to install, reinstall, upgrade, remove, etc. If the install option is greyed out then the headers are installed. If not, click on the install option and then on the synaptic window at the top, on the same line with the search box, press the apply icon. It will present you an information dialog window (or more than one): press apply (or ok) and wait to finish. After it finishes press close on the dialog (if it is not automatically closed) and close synaptics.

3. Open a terminal (you can do it from dash writing: **terminal** and pressing **Enter** on keyboard). On the terminal write:

a. **git clone git://linuxtv.org/media_build.git**

press **Enter** and wait to finish downloading and setting up the tree

b. **cd media_build**

press **Enter**

c. **./build**

press **Enter**. It will take a few (or more than a few) minutes to finish because it will automatically download and compile the drivers for you.

d. Assuming that the previous step finished with no errors then write (on the same terminal window, always)

**sudo make install**this

Probably it will ask for your password. Write it and press enter. Imediatelly will install the drivers for you.

e. execute on terminal **sudo nautilus /home**. It will open a fime manager window where you will see a folder with your username. This is your home directory. Find the attached file you downloaded from this post, extract it and copy it to this path:
**/lib/modules/3.5.0-17-generic/kernel/drivers/media/usb/dvb-usb-v2/** replacing the original file

f. Close the nautilus window. On terminal execute:

**sudo depmod -a**

It will take less than a few seconds to finish. After it finishes close everything and restart your computer. After you login again disconnect and then reconnect your stick. If you see a similar message on syslog to this:

[I][B]Nov 11 13:01:23 ubuntu kernel: [65969.062117] usb 2-1.5: new high-speed USB device number 6 using ehci_hcd
Nov 11 13:01:23 ubuntu kernel: [65969.164218] usb 2-1.5: New USB device found, idVendor=1b80, idProduct=d394
Nov 11 13:01:23 ubuntu kernel: [65969.164223] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov 11 13:01:23 ubuntu kernel: [65969.164227] usb 2-1.5: Product: usbtv
Nov 11 13:01:23 ubuntu kernel: [65969.164229] usb 2-1.5: Manufacturer: realtek
Nov 11 13:01:23 ubuntu kernel: [65969.171574] usb 2-1.5: dvb_usb_v2: found a 'Turbo-X DTT-1000 Digital TV tuner' in warm state
Nov 11 13:01:23 ubuntu mtp-probe: checking bus 2, device 6: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5"
Nov 11 13:01:23 ubuntu mtp-probe: bus: 2, device: 6 was not an MTP device
Nov 11 13:01:23 ubuntu kernel: [65969.217205] usb 2-1.5: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
Nov 11 13:01:23 ubuntu kernel: [65969.217220] DVB: registering new adapter (Turbo-X DTT-1000 Digital TV tuner)
Nov 11 13:01:23 ubuntu kernel: [65969.220434] usb 2-1.5: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
Nov 11 13:01:23 ubuntu kernel: [65969.220760] fc0012: Fitipower FC0012 successfully attached.
Nov 11 13:01:23 ubuntu kernel: [65969.229619] Registered IR keymap rc-empty
Nov 11 13:01:23 ubuntu kernel: [65969.229719] input: Turbo-X DTT-1000 Digital TV tuner as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/rc/rc1/input18
Nov 11 13:01:23 ubuntu kernel: [65969.229788] rc1: Turbo-X DTT-1000 Digital TV tuner as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/rc/rc1[/B][/I]

then you are ok.

Now you only have to setup your tv application and this may prove difficult. As I said I am using **Vlc** because **Me-TV** did not work as expected. On Vlc everything is manual. You have to know the frequencies the dvb-tv channels for your location are broadcasted... Then you can setup a playlist with these frequencies stored and you can access the channels for each frequency from the VLC Menu: **Playback **(or **Play**?) -> Program...

***Caution: these instructions are only for the 3.5.0-17 kernel. Most probably will not work for any other kernel because the attached file is compiled for the 3.5.0-17 kernel. That means if you upgrade your kernel your dvb-t stick will stop working***.

---

### Post by LSDalKa on 2012-11-12
Thanks for your help but i can't get it to work.
I cleaned up the system from previous v4l installations and i tried with both 3.6.xx and 3.5.17 kernels and the result is the same(I thought that in the first post you said that you got it working with the 3.6 kernel :-s).
Nothing interesting in syslog.
Only some warnings during the build process like:

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

WARNING: "sms_ir_exit" [/home/lsdalka/media_build/v4l/smsmdtv.ko] undefined!
WARNING: "sms_ir_event" [/home/lsdalka/media_build/v4l/smsmdtv.ko] undefined!
WARNING: "sms_ir_init" [/home/lsdalka/media_build/v4l/smsmdtv.ko] undefined!
WARNING: "snd_tea575x_set_freq" [/home/lsdalka/media_build/v4l/radio-shark.ko] undefined!

and during make install:
Hmm... distro kernel with a non-standard place for module backports detected.
Please always prefer to use vanilla upstream kernel with V4L/DVB

Furthermore the **sudo depmod -a** command lasts less than a second and doesn't give any output (probably normal)

Everything else is normal so maybe something else is missing(some service not running maybe)

Anyway I don't even watch much tv but it sucks not to be able to fix any pc issue.
I'll definitely setup the SDR though (already done that in windows) which is pretty awesome with the exception that i couldn't tune in the police bandwith.Hahahaa

Thanks again

---

### Post by milro on 2012-11-13
> **LSDalKa said:**
> Thanks for your help but i can't get it to work.
I cleaned up the system from previous v4l installations and i tried with both 3.6.xx and 3.5.17 kernels and the result is the same(I thought that in the first post you said that you got it working with the 3.6 kernel :-s).
Nothing interesting in syslog.
Only some warnings during the build process like:

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

WARNING: "sms_ir_exit" [/home/lsdalka/media_build/v4l/smsmdtv.ko] undefined!
WARNING: "sms_ir_event" [/home/lsdalka/media_build/v4l/smsmdtv.ko] undefined!
WARNING: "sms_ir_init" [/home/lsdalka/media_build/v4l/smsmdtv.ko] undefined!
WARNING: "snd_tea575x_set_freq" [/home/lsdalka/media_build/v4l/radio-shark.ko] undefined!

and during make install:
Hmm... distro kernel with a non-standard place for module backports detected.
Please always prefer to use vanilla upstream kernel with V4L/DVB

Furthermore the **sudo depmod -a** command lasts less than a second and doesn't give any output (probably normal)

Everything else is normal so maybe something else is missing(some service not running maybe)

Anyway I don't even watch much tv but it sucks not to be able to fix any pc issue.
I'll definitely setup the SDR though (already done that in windows) which is pretty awesome with the exception that i couldn't tune in the police bandwith.Hahahaa

Thanks again

Well, sorry that it did not work out for you till now.
The warnings from the build process are normal. To install the whole thing you have to do: **sudo make install** or else nothing will be installed...
Why don't you try to replace the two files in the source folder (somewhere inside the **media_build** subfolders with the ones I've attached in my first post. Then from inside the **media_build** directory - folder execute (in a terminal window always) first:

**make clean**

then

**make -C ./v4l**

and after this command finishes

**sudo make install**

Reboot the machine and check the syslog.
Caution: this will work only if you have at least once, previously, ececuted the **./build** command inside the **media_build** folder.

About SDR... thanks for reminding me about this. I have, definitely, to check this out...

---

### Post by fmcgorenc on 2012-11-22
hi i'm doing this in mint 14 and get this error when running ./build

```
In file included from include/linux/stat.h:61:0,
                 from include/linux/fs.h:400,
                 from include/linux/input.h:1167,
                 from /home/gmc/dvb-2382u/media_build/v4l/compat.h:9,
                 from <command-line>:0:
include/linux/uidgid.h: In function 'gid_valid':
include/linux/uidgid.h:128:1: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.7/README.Bugs> for instructions.
The bug is not reproducible, so it is likely a hardware or OS problem.
make[3]: *** [/home/gmc/dvb-2382u/media_build/v4l/sn9c102_mt9v111.o] Error 1
make[2]: *** [_module_/home/gmc/dvb-2382u/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.6.7-030607-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/gmc/dvb-2382u/media_build/v4l'
make: *** [all] Error 2
build failed at ./build line 452.
```

i'm running kernel 3.6.7

```
$ uname -a
Linux gmc-desktop 3.6.7-030607-generic #201211171710 SMP Sat Nov 17 22:18:03 UTC 2012 i686 i686 i686 GNU/Linux
```

i did this before on ubuntu 12.10 with kernel 3.6.3 without a problem.

can someone give me some hint to resolve this please.

My usb device is "Not Only TV LV5T Deluxe" LV5TDLX  usbid 1f4d:c803

---

### Post by kdim2637 on 2012-12-25
&#916;&#949;&#957; &#956;&#960;&#959;&#961;&#974; &#957;&#945; &#954;&#945;&#957;&#969; &#964;&#951;&#957; ubuntu &#957;&#945; &#948;&#949;&#953; &#964;&#959; crypto redi pc 50 a &#949;&#960;&#949;&#953;&#963;&#951;&#962; &#951; &#947;&#957;&#969;&#963;&#949;&#953;&#962; &#956;&#959;&#965; &#960;&#945;&#957;&#969; &#963;&#964;&#951;&#957; linux &#949;&#953;&#957;&#945;&#953; &#955;&#953;&#947;&#949;&#962; &#960;&#945;&#961;&#945;&#952;&#949;&#964;&#969; &#960;&#945;&#961;&#945;&#954;&#945;&#964;&#969; &#964;&#951; &#948;&#953;&#945;&#946;&#945;&#950;&#949;&#953; &#964;&#959; lsusb &#954;&#945;&#953; &#964;&#959; dmesg


Bus 002 Device 006: ID 1f4d:a803 G-Tek Electronics Group 
Bus 002 Device 003: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[ 4386.059600] usb 2-1: >USB disconnect, device number 5
[ 4396.136059] usb 2-1: >new high-speed USB device number 6 using ehci_hcd
[ 4396.279949] usb 2-1: >New USB device found, idVendor=1f4d, idProduct=a803
[ 4396.279954] usb 2-1: >New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 4396.279957] usb 2-1: >Product: RTL2838UHIDIR
[ 4396.279959] usb 2-1: >Manufacturer: Realtek
[ 4396.279961] usb 2-1: >SerialNumber: 000000041

&#960;&#945;&#961;&#945;&#954;&#945;&#955;&#969; &#946;&#959;&#942;&#952;&#949;&#953;&#945;

---

### Post by kdim2637 on 2012-12-27
> **milro said:**
> After searching on Internet with no success for instructions ( and source) to compile a rtl2832u module on Ubuntu 12.10 (x64) with 3.5 kernel I solved the problem by doing the following

a. First, I've upgraded to 3.6 kernel series from an official ubuntu repository.
     
     Link: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/)

I've installed the following packets for my x64 enviroment:

[linux-headers-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.6.3-quantal/linux-headers-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb")       21-Oct-2012 17:57  921K
[linux-headers-3.6.3-030603_3.6.3-030603.201210211349_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.6.3-quantal/linux-headers-3.6.3-030603_3.6.3-030603.201210211349_all.deb")          21-Oct-2012 17:50   12M
[linux-image-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.6.3-quantal/linux-image-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb")        21-Oct-2012 17:57   12M
[linux-image-extra-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb        ]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.6.3-quantal/linux-image-extra-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb")21-Oct-2012 17:57   27M  

b. From this link: [http://git.linuxtv.org/media_build.git](http://git.linuxtv.org/media_build.git)
I cloned and built the repository following these instructions:

git clone git://linuxtv.org/media_build.git
cd media_build
./build

c. I did not install the modules because after I built it I wanted to recompile it again manually. First, I had to alter two files, in the source: "rtl28xxu.c" and "dvb-usb-ids.h" in order to add my dvb-t stick's vendor id (0x1b80) and product id (0xd394). I've attached a zip archive with these two altered files. You can track the changes by searching for the word:

Turbox

I found the vendor id and product id from the syslog when I connected the stick on a USB port. Below is a copy from the relevant part of my syslog:

[SIZE=2][COLOR=DarkRed]Oct 30 18:02:49 ubuntu kernel: [ 2885.211906] usb 2-1.5: new high-speed USB device number 6 using ehci_hcd
Oct 30 18:02:50 ubuntu kernel: [ 2885.313752] usb 2-1.5: New USB device found, **idVendor=1b80, idProduct=d394**
Oct 30 18:02:50 ubuntu kernel: [ 2885.313757] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Oct 30 18:02:50 ubuntu kernel: [ 2885.313760] usb 2-1.5: Product: usbtv
Oct 30 18:02:50 ubuntu kernel: [ 2885.313763] usb 2-1.5: Manufacturer: realtek[/COLOR][/SIZE]

d. I compiled manually the tree by ***cd***'ing inside the directory **media_build**($ *cd media_build*).

For compiling, first do:

*make clean*

and after

*make -C ./v4l*

e. Last I've installed the modules:

*sudo make install*

I used MeTV to scan for the channels. The scan finished succesfully but I could only tune and view the first channel on the list.
With VLC i had no problem at all. Everything worked beautifully.


I hope these instructions  to prove helpful for others too


in my case stop at build with that error 
/home/kostaslaptop/media_build/v4l/ppi.c:23:26: fatal error: asm/bfin_ppi.h: No such file or directory
compilation terminated.
make[3]: *** [/home/kostaslaptop/media_build/v4l/ppi.o] Error 1
make[2]: *** [_module_/home/kostaslaptop/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/kostaslaptop/media_build/v4l'
make: *** [all] Error 2
build failed at ./build line 452.
what i must do please lilte help here

---

### Post by batticiof on 2012-12-27
I guess someone has updated the file, but he forgot to insert a file. In fact, I was able to install perfectly the driver until this afternoon. I have followed the same procedure, but I get this error. I am trying to find a solution. A solution could be to follow the second or third approach suggested here
[http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

I am not a Linux geek, therefore I am waiting for other suggestion.

---

### Post by Baltazard on 2013-01-20
Hello,

Can anyone put a guide on how to setup this RTL2832u chip in Ubuntu 12.10?
I have an August  DVB-T 205 V3.0 with:
idVendor = 1f4d
idProduct = a803

Thank you.

note: I've manage to change dvb-usb-ids.h and rtl28xxu.c but I have no clue where and how I can put them :confused:

---

### Post by beardedwondr on 2013-01-20
I'm struggling with this stick as well, or at least a variant. I've posted the info in another part of the forum: [http://ubuntuforums.org/showthread.php?p=12448339#post12448339](http://ubuntuforums.org/showthread.php?p=12448339#post12448339)

---

### Post by Baltazard on 2013-01-20
> **beardedwondr said:**
> I'm struggling with this stick as well, or at least a variant. I've posted the info in another part of the forum: [http://ubuntuforums.org/showthread.php?p=12448339#post12448339](http://ubuntuforums.org/showthread.php?p=12448339#post12448339)

well that's why I hate linux; other distros are worst, at least ubuntu is used by a lot of people, I hope that they will fix these kind of issues.:o

---

### Post by beardedwondr on 2013-01-25
I've managed to get a fair bit further, it looks like i've compiled the drivers and installed them. However, now i have run into this problem:
dmesg:
```
[15676.672862] usb 1-4: dvb_usb_v2: found a 'Realtek RTL2831U reference design' in warm state
[15676.704116] usb 1-4: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[15676.704198] DVB: registering new adapter (Realtek RTL2831U reference design)
[15676.705328] [COLOR=Red]rtl2830_attach: driver disabled by Kconfig[/COLOR]
[15676.709628] usb 1-4: dvb_usb_v2: 'Realtek RTL2831U reference design' error while loading driver (-19)
[15676.710279] usb 1-4: dvb_usb_v2: 'Realtek RTL2831U reference design' successfully deinitialized and disconnected
```I don't know what file Kconfig is referring to, the .config in V4L seems to be setup correctly:
```
CONFIG_DVB_USB_RTL28XXU=m
```Can anyone help?

---

### Post by Baltazard on 2013-01-26
> **beardedwondr said:**
> I've managed to get a fair bit further, it looks like i've compiled the drivers and installed them. However, now i have run into this problem:
dmesg:
```
[15676.672862] usb 1-4: dvb_usb_v2: found a 'Realtek RTL2831U reference design' in warm state
[15676.704116] usb 1-4: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[15676.704198] DVB: registering new adapter (Realtek RTL2831U reference design)
[15676.705328] [COLOR=Red]rtl2830_attach: driver disabled by Kconfig[/COLOR]
[15676.709628] usb 1-4: dvb_usb_v2: 'Realtek RTL2831U reference design' error while loading driver (-19)
[15676.710279] usb 1-4: dvb_usb_v2: 'Realtek RTL2831U reference design' successfully deinitialized and disconnected
```I don't know what file Kconfig is referring to, the .config in V4L seems to be setup correctly:
```
CONFIG_DVB_USB_RTL28XXU=m
```Can anyone help?
I gave up on using the TeVii s660 remote control, I've just screwed my Ubuntu 12.10 and have had to reinstall gnome-remix 12.10 instead :-)

---

