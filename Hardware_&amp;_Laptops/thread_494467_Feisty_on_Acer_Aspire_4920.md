---
title: "Feisty on Acer Aspire 4920"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by maxalken on 2007-07-06
I am writing this post to let other people who want to buy Acer Aspire 4920 or 5920 know what will work and what will not.

First, I downloaded Feisty 64bit version. This livecd can't even boot on this machine. It showed > /bin/sh can&#8217;t access tty; job control mode off Which this guy made a summary of how to deal with it. [http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error](http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error)
My solution: Install Ubuntu Studio instead (only 32bit version though)

Second problem I had is I can't boot the system (same 'can't access tty problem' as above) if I install the root on LVM and dm-crypt, which I followed this Howto [https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto)
My solution: don't encrypt, only use LVM2. so no saucy photos on this disk

ATI X2500 Graphic card
When the system first booted, X Window didn't work. Then I simply followed this guide to make my ATI graphic card work [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
But from lspci. it tells me the card is X1600 > VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600] What the.....

Suyin webcam
It works with aMSN and ffmpeg. ```
ffmpeg -an -vd /dev/video0 -s 800x740 -sameq -vcodec mpeg4 "test.avi"
``` This camera only supports yuv mode

USB works

wired network works

DVD Multirecorder. 
Feisty didn't load **ide_generic** automatically. I added ide_generic to /etc/modules, now it is working perfectly. (I haven't tested burning function yet)

Intel 4965AGN wireless
only ndiswrapper works. the experimental native drive hung this system when boot. the native driver does not work with kernel 2.6.20
Here is how to install the ndiswrapper and where to find the windows driver [https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty)

Intel HDA ICH8 audio
It uses Realtek ALC268 chipset. I got this information from cat /proc/asound/card0/codec#0
Only the code in ALSA HG tree supports this chipset. Before I install the driver from HG tree, There is only 1 PCM channel in the mixer. So I could only hear the sound and that's all. I couldn't record. After I installed the driver, the mixer shows all channels which are supposed to be there. However, the builtin microphone still does not work. At least I can plug an external microphone to chat on Skype now. I tested the external microphone with Audacity, the sound quality is really bad.
the HG tree snapshots can be found here [ftp://ftp.suse.com/pub/projects/alsa/snapshot/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/)
and follow this to compile the HG code [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)

Bluetooth: I don't have any other Bluetooth device to test it. I don't think it works since I can't even find it from lspci and lsusb

MM/SD card reader does not work > 0f:06.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0f:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)


Euro sign and $ keys don't work
multimedia keys work as mouse buttons, and no application listen to them

firewire may not work since it's O2 Micro chip

S-video, VGA output and modem are not tested


This is the whole lspci information
> 00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
0f:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0f:06.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0f:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)


---

### Post by alvbinoy on 2007-07-07
Hi maxalken,

I have the same problem, because i bought the same laptop model Acer Aspire 4920. Installing Ubuntu Feisty was tiresome due to the fact that i think the live CD had some bug with regards to ATI video cards. So a work around was to install using the alternate CD which can also be downloaded from ubuntu site. After installation you will then need to install the ATI driver, after that you can now load the X Server.

I would like to ask you if you got the headphone jack to work on feisty. And if it worked how did you make it work?

This is my lspci

00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0f:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0f:06.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0f:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

---

### Post by lightsaber on 2007-07-09
Looks as though there are problems on the 5920 with the nVidia setup as well.  A friend of mine just bought one and he had the same issues you guys are talking about here.  In addition, x would not start at all, saying it can't find any screens.  Even when using the non-proprietary driver.

---

### Post by maxalken on 2007-07-12
Hi alvbinoy. I've got the headphone jack working by installing a ALSA HG tree snapshot
it can be found here [ftp://ftp.suse.com/pub/projects/alsa/snapshot/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/)
and follow this to compile the HG code [https://help.ubuntu.com/community/Hd...ight=%28hda%29](https://help.ubuntu.com/community/Hd...ight=%28hda%29)

---

### Post by maxalken on 2007-07-12
Here is a summary of what I can't get them work so far. If anyone can get any of these work, please share your solution here. :)

these do **NOT** work:
[LIST]
[*]built-in microphone
[*]line out jack
[*]MMC/SD card reader
[*]Bluetooth
[*]Euro sign and $ keys
[*]multimedia keys
[*] the blue "e" key and the key has a "human shape" on it (is there any way to assign them as application launcher keys in Gnome?)
[/LIST]

you need to do something to make these work: (all you need to do is read my first post and follow the HOWTOs)
[LIST]
[*]ATI X2500 Graphic card
[*]DVD Multirecorder
[*]Intel 4965AGN wireless
[*]Intel HDA ICH8 audio (headphone and microphone jacks)
[/LIST]

these **works** automatically after installing Feisty:
[LIST]
[*]Suyin webcam
[*]USB
[*]wired network
[/LIST]

---

### Post by alvbinoy on 2007-07-13
Hi maxalken,

I have got the headphone jack working by following the link you gave me. I only compiled the driver and not compiled the lib and utils. Is that okay? Because when I was issuing the command 

sudo ./configure 

in the lib directory the configure command there was an output 

"./configure: line 20827: python-config: command not found
Unable to determine python libraries! Probably python-config is not
available on this system. Please, use --with-pythonlibs options."

so when I configured the lib for the second time i issued the command

sudo ./configure --with-pythonlibs

after that i issued 

sudo make

and it returned this

[INDENT]python.c: In function 'alsa_mixer_simple_event':
python.c:869: error: 'PyThreadState' undeclared (first use in this function)
python.c:869: error: 'tstate' undeclared (first use in this function)
python.c:869: error: 'origstate' undeclared (first use in this function)
python.c:869: warning: left-hand operand of comma expression has no effect
python.c:870: error: 'PyObject' undeclared (first use in this function)
python.c:870: error: 't' undeclared (first use in this function)
python.c:870: error: 'o' undeclared (first use in this function)
python.c:870: warning: left-hand operand of comma expression has no effect
python.c:870: error: 'r' undeclared (first use in this function)
python.c:870: warning: left-hand operand of comma expression has no effect
python.c:873: warning: implicit declaration of function 'PyThreadState_New'
python.c:873: error: 'main_interpreter' undeclared (first use in this function)
python.c:874: warning: implicit declaration of function 'PyThreadState_Swap'
python.c:878: error: expected expression before ')' token
python.c:879: warning: implicit declaration of function 'find_helem'
python.c:882: warning: implicit declaration of function 'new_helem'
python.c:887: warning: implicit declaration of function 'Py_INCREF'
python.c:888: warning: implicit declaration of function 'find_melem'
python.c:888: error: 'Py_None' undeclared (first use in this function)
python.c:891: error: 'struct python_priv' has no member named 'py_event_func'
python.c: In function 'alsa_mixer_simple_free':
python.c:914: error: 'struct python_priv' has no member named 'py_mixer'
python.c:915: error: 'struct python_priv' has no member named 'py_mixer'
python.c:916: error: 'struct python_priv' has no member named 'py_mixer'
python.c:919: error: 'struct python_priv' has no member named 'py_event_func'
python.c:920: warning: implicit declaration of function 'Py_Finalize'
python.c: In function 'alsa_mixer_simple_finit':
python.c:932: error: 'PyObject' undeclared (first use in this function)
python.c:932: error: 'obj' undeclared (first use in this function)
python.c:932: error: 'obj1' undeclared (first use in this function)
python.c:932: warning: left-hand operand of comma expression has no effect
python.c:932: error: 'obj2' undeclared (first use in this function)
python.c:932: warning: left-hand operand of comma expression has no effect
python.c:932: error: 'py_mod' undeclared (first use in this function)
python.c:932: warning: left-hand operand of comma expression has no effect
python.c:932: error: 'mdict' undeclared (first use in this function)
python.c:932: warning: left-hand operand of comma expression has no effect
python.c:951: warning: implicit declaration of function 'Py_Initialize'
python.c:952: warning: implicit declaration of function 'PyType_Ready'
python.c:952: error: 'pymelem_type' undeclared (first use in this function)
python.c:954: error: 'pymixer_type' undeclared (first use in this function)
python.c:956: warning: implicit declaration of function 'Py_InitModule'
python.c:956: error: 'python_methods' undeclared (first use in this function)
python.c:958: error: 'main_interpreter' undeclared (first use in this function)
python.c:958: warning: implicit declaration of function 'PyThreadState_Get'
python.c:958: error: invalid type argument of '->'
python.c:959: warning: implicit declaration of function 'PyImport_GetModuleDict'
python.c:960: warning: implicit declaration of function 'PyDict_GetItemString'
python.c:962: error: 'struct python_priv' has no member named 'py_mdict'
python.c:962: warning: implicit declaration of function 'PyModule_GetDict'
python.c:963: warning: implicit declaration of function 'PyString_FromString'
python.c:965: warning: implicit declaration of function 'PyDict_SetItemString'
python.c:972: warning: implicit declaration of function 'PyModule_AddObject'
python.c:972: error: expected expression before ')' token
python.c:973: error: expected expression before ')' token
python.c:984: error: 'struct python_priv' has no member named 'py_mixer'
python.c:991: warning: implicit declaration of function 'PyRun_FileEx'
python.c:991: error: 'Py_file_input' undeclared (first use in this function)
python.c:995: error: 'struct python_priv' has no member named 'py_event_func'
python.c:996: error: 'struct python_priv' has no member named 'py_event_func'
make[3]: *** [python.lo] Error 1
make[3]: Leaving directory `/usr/src/alsa/alsa-lib-hg20070712/modules/mixer/simple'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-lib-hg20070712/modules/mixer'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-lib-hg20070712/modules'
make: *** [all-recursive] Error 1
[/INDENT]

So that's why I am asking if it is alright just to install the just the driver. Or do I need to also install the lib and utils? If so how can I fix the problem when I am issuing the make command in the lib? Also I want to ask if after you made the headphone jack to work, after you insert the headphone in the jack does your system automatically mute the laptop speakers? Because after I install the driver from the link you gave me, my system detected the headphones, but after I plug my headphones in they both have sounds. The speaker and the headphones. I need  to mute the laptop speakers in the Volume Control. 

Thanks in advance

---

### Post by errenay on 2007-07-21
> **maxalken said:**
> I am writing this post to let other people who want to buy Acer Aspire 4920 or 5920 know what will work and what will not.

First, I downloaded Feisty 64bit version. This livecd can't even boot on this machine. It showed  Which this guy made a summary of how to deal with it. [http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error](http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error)
My solution: Install Ubuntu Studio instead (only 32bit version though)


I have problems with Acer 5920. I have tried to install Kubuntu 7.04 LiveCD 64bit, but the mentioned error has appeared. Maybe does someone know solution (instead of trying Ubuntu Studio)?

---

### Post by Fifty-Nine on 2007-07-25
> **alvbinoy said:**
> compiler errors

I had a similar problem. First, you need to do:

sudo apt-get install python-dev

to get python-config. It still failed to compile for me at this point. The reason is the compiler is looking for a python header in the wrong directory. You can either edit python.c under ./modules/mixer/simple/python.c so that the line that says

#include <python/Python.h>

now says 

#include <python2.5/Python.h>

or you can just make a symlink for it:

sudo ln -s /usr/include/python2.5 /usr/include/python

Either way should work. After that, just do sudo ./cvscompile and cross your fingers

---

### Post by alvbinoy on 2007-07-28
> **Fifty-Nine said:**
> I had a similar problem. First, you need to do:

sudo apt-get install python-dev

to get python-config. It still failed to compile for me at this point. The reason is the compiler is looking for a python header in the wrong directory. You can either edit python.c under ./modules/mixer/simple/python.c so that the line that says

#include <python/Python.h>

now says 

#include <python2.5/Python.h>

or you can just make a symlink for it:

sudo ln -s /usr/include/python2.5 /usr/include/python

Either way should work. After that, just do sudo ./cvscompile and cross your fingers

Thanks a lot, the above work around worked.

---

### Post by thestranger on 2007-07-30
hi,

i've the same problem with acer aspire 5920, using textual installation the system will proceed succesfully but when i reboot into my new system i receive an error from xorg.
can anyone help me?

---

### Post by errenay on 2007-08-01
I have finally installed Kubuntu 7.04 32 bit using alternate CD (Acer Aspire 5920).
Apropos DVD recorder - instead of module "ide_generic" (it looks that there is no DMA with this fix) I have used "piix" (added to /etc/modules). It looks to work better (with DMA).

---

### Post by errenay on 2007-08-04
One more thing - has someone managed to make this laptop (Acer Aspire 5920) hibernate / suspend? I tried uswsusp (as mentioned here:
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5920](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5920)
), but so far it doesn't work. It looks like laptop is trying very hard to hibernate (screen with "saving pages") but could not finish process and turn itself off.

---

