---
title: "no sound in Lenovo N100 after installing Ubuntu 7.04 , sound card being Intel 82801G"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by dew on 2007-05-01
hi Ubuntu problem-solvers,

there is no sound at all (neither external speakers nor headphone) in my N100 Lenovo notebook. When i bought notebook, it had pre-loaded Vista and i could listen to music. Then i formatted complete hard drive and installed Ubuntu 7.04.... Alas ! I have no idea what the hell has happened to sound card/speaker/headphone.... 

can anybody tell me how to get the sound back on speakers and headphone. following is the output of some commands which tells that sound card, i.e., intel 82801G, is recognized.

[COLOR="Blue"]alsamixer[/COLOR]
please see the attachment



[COLOR="Red"]aplay -l 
**** List of PLAYBACK Hardware Devices **** 
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 [/COLOR]

lspci -v 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03) 
        Subsystem: Lenovo Unknown device 2061 
        Flags: bus master, fast devsel, latency 0 
        Capabilities: <access denied> 

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA]) 
        Subsystem: Lenovo Unknown device 2062 
        Flags: bus master, fast devsel, latency 0, IRQ 17 
        Memory at d0200000 (32-bit, non-prefetchable) [size=512K] 
        I/O ports at 1800 [size=8] 
        Memory at c0000000 (32-bit, prefetchable) [size=256M] 
        Memory at d0300000 (32-bit, non-prefetchable) [size=256K] 
        Capabilities: <access denied> 

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) 
        Subsystem: Lenovo Unknown device 2062 
        Flags: bus master, fast devsel, latency 0 
        Memory at d0280000 (32-bit, non-prefetchable) [size=512K] 
        Capabilities: <access denied> 

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
        Subsystem: Lenovo Unknown device 2066 
        Flags: bus master, fast devsel, latency 0, IRQ 21 
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode]) 
        Flags: bus master, fast devsel, latency 0 
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0 
        Capabilities: <access denied> 

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode]) 
        Flags: bus master, fast devsel, latency 0 
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0 
        Memory behind bridge: d0000000-d00fffff 
        Capabilities: <access denied> 

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI]) 
        Subsystem: Lenovo Unknown device 206b 
        Flags: bus master, medium devsel, latency 0, IRQ 18 
        I/O ports at 1820 [size=32] 

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI]) 
        Subsystem: Lenovo Unknown device 206c 
        Flags: bus master, medium devsel, latency 0, IRQ 19 
        I/O ports at 1840 [size=32] 

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI]) 
        Subsystem: Lenovo Unknown device 206d 
        Flags: bus master, medium devsel, latency 0, IRQ 20 
        I/O ports at 1860 [size=32] 

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI]) 
        Subsystem: Lenovo Unknown device 206e 
        Flags: bus master, medium devsel, latency 0, IRQ 17 
        I/O ports at 1880 [size=32] 

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI]) 
        Subsystem: Lenovo Unknown device 206f 
        Flags: bus master, medium devsel, latency 0, IRQ 18 
        Memory at d0544000 (32-bit, non-prefetchable) [size=1K] 
        Capabilities: <access denied> 

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode]) 
        Flags: bus master, fast devsel, latency 0 
        Bus: primary=00, secondary=05, subordinate=09, sec-latency=32 
        I/O behind bridge: 00002000-00002fff 
        Memory behind bridge: d0100000-d01fffff 
        Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff 
        Capabilities: <access denied> 

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
        Subsystem: Lenovo Unknown device 2071 
        Flags: bus master, medium devsel, latency 0 
        Capabilities: <access denied> 

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master]) 
        Subsystem: Lenovo Unknown device 2072 
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19 
        I/O ports at 01f0 [size=8] 
        I/O ports at 03f4 [size=1] 
        I/O ports at 0170 [size=8] 
        I/O ports at 0374 [size=1] 
        I/O ports at 18b0 [size=16] 
        Capabilities: <access denied> 

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
        Subsystem: Lenovo Unknown device 2073 
        Flags: medium devsel, IRQ 10 
        I/O ports at 18c0 [size=32] 

03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01) 
        Subsystem: Broadcom Corporation Unknown device 0465 
        Flags: bus master, fast devsel, latency 0, IRQ 16 
        Memory at d0000000 (32-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 

05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
        Subsystem: Lenovo Unknown device 2074 
        Flags: bus master, medium devsel, latency 64, IRQ 22 
        I/O ports at 2000 [size=256] 
        Memory at d0100000 (32-bit, non-prefetchable) [size=256] 
        Capabilities: <access denied> 

05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01) 
        Subsystem: Lenovo Unknown device 2075 
        Flags: bus master, medium devsel, latency 168, IRQ 17 
        Memory at d0102000 (32-bit, non-prefetchable) [size=4K] 
        Bus: primary=05, secondary=06, subordinate=09, sec-latency=176 
        Memory window 0: 50000000-53fff000 (prefetchable) 
        Memory window 1: 54000000-57fff000 
        I/O window 0: 00002400-000024ff 
        I/O window 1: 00002800-000028ff 
        16-bit legacy interface ports at 0001 

05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (prog-if 10 [OHCI]) 
        Subsystem: Lenovo Unknown device 2076 
        Flags: bus master, medium devsel, latency 64, IRQ 21 
        Memory at d0100800 (32-bit, non-prefetchable) [size=2K] 
        Capabilities: <access denied> 

05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) 
        Subsystem: Lenovo Unknown device 2077 
        Flags: bus master, medium devsel, latency 64, IRQ 18 
        Memory at d0100400 (32-bit, non-prefetchable) [size=256] 
        Capabilities: <access denied> 

05:06.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01) 
        Subsystem: Lenovo Unknown device 2078 
        Flags: medium devsel, IRQ 5 
        Memory at d0101000 (32-bit, non-prefetchable) [disabled] [size=256] 
        Capabilities: <access denied> 

05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a) 
        Subsystem: Lenovo Unknown device 2079 
        Flags: medium devsel, IRQ 5 
        Memory at d0101400 (32-bit, non-prefetchable) [disabled] [size=256] 
        Capabilities: <access denied> 

05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05) 
        Subsystem: Lenovo Unknown device 207a 
        Flags: medium devsel, IRQ 5 
        Memory at d0101800 (32-bit, non-prefetchable) [disabled] [size=256] 
        Capabilities: <access denied> 

[COLOR="Red"]cat /proc/asound/modules 
 0 snd_hda_intel [/COLOR]

[COLOR="Blue"]grep 'audio' /etc/group 
audio:x:29:username,username [/COLOR]

please give your fruitful suggestions to fix this no-sound problem.  sometimes i feel as if i have lost sound and got muted ! it will be beyond words to thank someone who can tell me how to get sound back.

S.O.S.

---

### Post by cptcrunch on 2007-05-01
This is a common problem. Your laptop is fairly new and we'll have to wait for ALSA to update the drivers. Check [http://www.alsa-project.org/](http://www.alsa-project.org/) for updated drivers

---

### Post by zanjabeel5 on 2007-05-02
I have lenovo c200 for almost half a year, so no it's not a new problem.

latest driver version of alsa seems to solve this
take a look here:
( use guest login )

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=0003002](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=0003002)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2725](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2725)

it looks like a fix was introduced in the latest alsa drivers
take a look here on how to install these
[http://www.w1ldt4ng3nt.net/blog/item/77](http://www.w1ldt4ng3nt.net/blog/item/77)

I moved to ubuntu 4 weeks ago and I have yet to hear sound comming out from my laptop.
Good luck

---

### Post by toolish on 2007-05-14
Hi all,

I don't think the patch which fixes this has made it into the Alsa source yet.

It is necessary to apply the patch manually at the moment.

Theres a howto available at [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)

It's for a different model laptop but it is the same card. 

It does require some terminal usage. If anyones not comfortable with this, i have made a package with a script to install it, available here [http://rapidshare.com/files/31068197/alsa-patched.tar.bz2.html](http://rapidshare.com/files/31068197/alsa-patched.tar.bz2.html) [^]

It contains all the necessary Alsa files patched.

Double click the .bz2 and uncompress the folder.

Browse to the newly created folder 'alsa-patched'

Double click the file named 'install_alsapatch.sh' and you should be presented with a box with 4 options:
'run in terminal', 'display', 'cancel', and 'run' 

Choose 'run in terminal'

The script will run in a terminal and after a few minutes you should have working sound. You may need to turn the volume up after it has been installed.

If you run into problems with the script not executing and opening in a text editor instead, right click the script and go to the permissions tab and ensure that 'Allow executing as a program' is ticked.

Hope it helps

---

### Post by sherlockholmes on 2007-11-02
Hi Toolish,

                    I have a Lenovo N100 too, and I have exactly the same problem as quoted in the first message in this thread. 
I tried running your script but to no avail.
And then, I tried reinstalling alsa as advised (carefully following your commands) in another thread. But I still have no sound whatsoever either through my laptop speakers or through my USB headphones.

I am rather a novice on ubuntu. Can you help me fix this?
I guess I have not really defined the problem well enough for you suggest possible solutions; I will be happy to provide you with more data if you tell me exactly what you want to know.

Thanks a ton!

---

