---
title: "problems installing alsa-lib"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by weaver2109 on 2008-02-05
i have no sound on my toshiba a205 notebook and i am trying to fix it.
i type in lspci in terminal and i get
```
neal@neal-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```
i searched and found a solution to the problem for those who have an Intel HDA audio device and found this site
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

i got up to "Compile and install alsa-lib" with no problems but when i type sudo ./configure, i get this response at the end:
```
checking for ANSI C header files... yes
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
neal@neal-laptop:/usr/src/alsa/alsa-utils-1.0.15$ sudo make
make: *** No targets specified and no makefile found.  Stop.

```
:confused::confused::confused:
what does this mean and how do i fix it?
please help!!

EDIT:Sorry!!! i just read the part that says "Note that you must have the curses library installed to be able to compile alsa-utils. You can install it with this command from a terminal: sudo apt-get install libncurses5-dev"
ill try that command

---

### Post by PaulFr on 2008-02-05
Did you execute this ? (This is from the URL you linked to).

```
sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`
```This has libncurses-dev in the line, so it should install curses library.

---

### Post by weaver2109 on 2008-02-05
yes i did
it installed libncurses5-dev and fixed the so-called problem
sorry for the pointless thread!

---

### Post by weaver2109 on 2008-02-05
Another question (I'm new to linux and still learning, so sorry for the noobness of my posts)
it says on the website mentioned earlier:
      First you must find which model of sound card you use, so run this command:

cat /proc/asound/card0/codec#* | grep Codec

It will return model of your sound card(s), for example: "Codec: Realtek ALC260", so your sound card is ALC260.

    *

      You should open a file in ALSA documentation. This file is here (replace KERNEL_VERSION with your kernel's version!):

/usr/src/KERNEL_VERSION/Documentation/sound/alsa/ALSA-Configuration.txt

If you didn't have this file, for version 2.6.22, you can check out [WWW] this link or you can find ALSA-Configuration.txt in the subdirectory /alsa-kernel/Documentation/ of the alsa-driver-1.x.x directory you created. 

i got my sound card model but what do i do to perform the next step??

---

### Post by PaulFr on 2008-02-06
```
cd /usr/src/alsa/alsa-driver*/alsa-kernel/Documentation
gedit ALSA-Configuration.txt
```Here you can search for lines containing your codec name.

FYI, if you look at **[http://ubuntuforums.org/showthread.php?t=616845&highlight=A205](http://ubuntuforums.org/showthread.php?t=616845&highlight=A205)**, the recommended value is **toshiba**,

i.e. the line to insert in the **sudo nano /etc/modprobe.d/alsa-base** step is
```
options snd-hda-intel model=toshiba
```Good luck with your search for sound

---

