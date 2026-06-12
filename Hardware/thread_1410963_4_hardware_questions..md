---
title: "4 hardware questions."
date: 2010-02-19
forum: Hardware
---

### Post by fleppmar on 2010-02-19
Hi!

I have 3 questions for you guys. :-)

1. When I reboot my computer, I cannot access the BIOS, that is becase GRUB shadows my original BIOS, and doesnt load the keyboard and touchpad driver until afterwards. Sometimes, I need a second reboot to  get my keyboard and touchpad going.
Anyone know what commands I need to run to fix this? :-)

2. My sound does not work, if I dont have it connected to my stereo. I have tried reinstalling the driver, and went from Windows to Linux (Ubuntu 9.10) to fix it, but still. It does not work.
Anyone have a sollution to this problem?
Im not sure wich soundcard I have, since there are 4 different types that may be installed in my laptop.

3. I am having problems with wine, and installing spotify. I can right click on the spotify.ink and run it throug wine. And it works. But cant install it through the terminal.
When I try: sudo wine install "spotify exe"
And other varisons of that command I always get:
wine: could not load L"C:\\windows\\system32\\install.exe": Couldnt locate the module

I have even made a folder in wine, to match this. But still get the same error.

4. When I reinstalled Ubuntu 9.10 it seems that I cant connect to wi-fi. I can "make" them, but cant connect to them. It looks like the wifi is on, but inactive. Cant think of a better way to descrie it. heh. :-)

Can anyone help me with this? :-)

My laptop is a Fujitsu-Siemens Amilo PA 3553


Thanks!.

Regards.
fleppmar
*noobie*

---

### Post by fleppmar on 2010-02-23
No one has any solutions? :-(

---

### Post by pirateghost on 2010-02-23
to touch on the BIOS portion of it.  BIOS loads before the harddrive, so its impossible for GRUB to be taking over your BIOS.  BIOS is not on the harddrive, it is a chip on the motherboard and GRUB wouldnt even load if BIOS wasnt working.  perhaps you just arent seeing the BIOS post screen because it is booting too fast?  what key is it you are supposed to press to get into BIOS?  try tapping that as you fire up your computer

---

### Post by Demask on 2010-02-23
I have no idea if this helps, but upgrading my Pa3553 to the latest BIOS fixed my WLAN-problems. It added some new options in BIOS where you could disable/enable wireless more or less permanently. Maybe number 4 is related to any of those options?

I'm pretty much guessing here, but if it helps, why not?

---

### Post by pirateghost on 2010-02-23
my guess is the wireless is probably a broadcom, which requires the restricted drivers in order to get it working properly.  just hardwire the thing, open up Hardware Drivers app and let it find the appropriate drivers.

---

### Post by cchhrriiss121212 on 2010-02-23
Regarding sound problems, type this to see what sound device you are using:
```
aplay -l
```

In order to install something through wine you need an .exe file, do you have one for spotify? If so just right click and open with wine to install. I'm not sure how you can run spotify without having it installed.

Pirateghost is right about BIOS, just hit f2 when you turn on. I would not mess around with BIOS unless you have a specific reason for it anyway.

---

### Post by fleppmar on 2010-02-23
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI_1 [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

This is my soundcard. :)

Thanks for the tips. I will try it right now. :)

---

### Post by fleppmar on 2010-02-23
Ok. Jeez! Now I found a new problem!

If I touch any key before the login window, neither keyboard or tocuhpad will work untill I reboot. I rebooted 3times now, just to check. Thats weird!
Good thing I have USB-mouse that works eitherway!

And, the tapping F2 didnt work. :-\

I dont think my computer likes me. :P

And, installing spotify through wine wont work. Just have to right-click and run the .exe file directly from the desktop.

---

### Post by pirateghost on 2010-02-23
different manufacturers have different hotkeys to get into BIOS
F2, F8, F10, delete  just to name a few

---

### Post by fleppmar on 2010-02-23
I have tried, ESC, TAB, F1->F12, backspace, DEL, ENTER, even SPACE, and [FN] + different -F buttons.

Nothing works.

---

### Post by cchhrriiss121212 on 2010-02-24
I googled your laptop model and it seems to have 2 graphics devices installed which I think is why you are getting those device 3 HDMI results from aplay -l.
The device you should use is the first analog one. What options do you have in pulse audio control?
And how are you connecting it to your stereo? It may be that your internal laptop speakers are faulty.

---

### Post by fleppmar on 2010-03-04
Hi.

Sorry for my late reply! Have been crazy at school and work the last week!

But, I have tried all theese things. Have the same problem with audio still. So think my internal speakers is busted. :-\

As for the Wi-Fi issue. Googled around a bit, and all seems to be okey with my Wi-Fi.

I tried different commands in terminal and got theese responses regarding my wi-fi card.

laptop:~$ sudo lshw -businfo
Bus info          Device      Class       Description
=====================================================
                              system      AMILO Notebook Pa 3553
                              bus         P15
                              memory      110KiB BIOS
cpu@0                         processor   AMD Turion(tm) X2 Dual-Core Mobile RM-
                              memory      128KiB L1 cache
                              memory      512KiB L2 cache
                              memory      4GiB System Memory
                              memory      2GiB DIMM DDR2 Synchronous
                              memory      2GiB DIMM DDR2 Synchronous
cpu@1                         processor   
                              memory      128KiB L1 cache
                              memory      512KiB L2 cache
pci@0000:00:00.0              bridge      RS780 Host Bridge
pci@0000:00:01.0              bridge      RS780 PCI to PCI bridge (int gfx)
pci@0000:01:05.0              display     RS780M/RS780MN [Radeon HD 3200 Graphic
pci@0000:01:05.1              multimedia  RS780 Azalia controller
pci@0000:00:02.0              bridge      RS780 PCI to PCI bridge (ext gfx port 
pci@0000:02:00.0              display     Mobility Radeon HD 3400 Series
pci@0000:02:00.1              multimedia  RV620 Audio device [Radeon HD 34xx Ser
pci@0000:00:04.0              bridge      RS780 PCI to PCI bridge (PCIE port 0)
pci@0000:00:05.0              bridge      RS780 PCI to PCI bridge (PCIE port 1)
pci@0000:08:00.0  ra0         network     RT2860
pci@0000:00:06.0              bridge      RS780 PCI to PCI bridge (PCIE port 2)
pci@0000:09:00.0  eth0        network     RTL8111/8168B PCI Express Gigabit Ethe
pci@0000:00:07.0              bridge      RS780 PCI to PCI bridge (PCIE port 3)
pci@0000:0a:00.0              bus         IEEE 1394 Host Controller
pci@0000:0a:00.1              generic     SD/MMC Host Controller
pci@0000:0a:00.2              generic     Standard SD Host Controller
pci@0000:0a:00.3              generic     MS Host Controller
pci@0000:0a:00.4              generic     xD Host Controller
pci@0000:00:11.0  scsi0       storage     SB700/SB800 SATA Controller [AHCI mode
scsi@0:0.0.0      /dev/sda    disk        320GB WDC WD3200BEVT-2
scsi@0:0.0.0,1    /dev/sda1   volume      146GiB Windows NTFS volume
scsi@0:0.0.0,2    /dev/sda2   volume      151GiB Extended partition
                  /dev/sda5   volume      6542MiB HPFS/NTFS partition
                  /dev/sda6   volume      139GiB Linux filesystem partition
                  /dev/sda7   volume      6094MiB Linux swap / Solaris partition
scsi@1:0.0.0      /dev/cdrom  disk        DVD RW AD-7590S
pci@0000:00:12.0              bus         SB700/SB800 USB OHCI0 Controller
pci@0000:00:12.1              bus         SB700 USB OHCI1 Controller
pci@0000:00:12.2              bus         SB700/SB800 USB EHCI Controller
pci@0000:00:13.0              bus         SB700/SB800 USB OHCI0 Controller
pci@0000:00:13.1              bus         SB700 USB OHCI1 Controller
pci@0000:00:13.2              bus         SB700/SB800 USB EHCI Controller
pci@0000:00:14.0              bus         SBx00 SMBus Controller
pci@0000:00:14.2              multimedia  SBx00 Azalia (Intel HDA)
pci@0000:00:14.3              bridge      SB700/SB800 LPC host controller
pci@0000:00:14.4              bridge      SBx00 PCI to PCI Bridge
pci@0000:00:18.0              bridge      Mobile K10 [Turion X2, Athlon X2, Semp
pci@0000:00:18.1              bridge      Family 11h [Turion X2, Athlon X2, Semp
pci@0000:00:18.2              bridge      Mobile K10 [Turion X2, Athlon X2, Semp
pci@0000:00:18.3              bridge      Mobile K10 [Turion X2, Athlon X2, Semp
pci@0000:00:18.4              bridge      Mobile K10 [Turion X2, Athlon X2, Semp
usb@1:3.2         scsi4       storage     
scsi@4:0.0.0      /dev/sdb    disk        1TB 10EAVS External
scsi@4:0.0.0,1    /dev/sdb1   volume      931GiB Windows NTFS volume
                              power       Lithium Ion Battery
 sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: ra0
       version: 00
       serial: 00:16:44:e1:fa:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:f0200000-f020ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:00:d7:73
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.101 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:b000(size=256) memory:f0300000-f0300fff memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)
assbear@assbear-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I have tried using Wi-FI radar. And it is the same problem there.  Can "create" wifi networks. But cant connect to them.

But, when I disconnect my ethernet cable, it says that wi-fi connection has been terminated.

---

### Post by fleppmar on 2010-03-05
Okey. Now the audio stopped completely. And every video on youtube, or on my computer goes inn FFx2 or worse!

Only player that worsk normaly is VLC. This happende after the latest update.

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: HDMI_1 [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
This is my aplay -l list.

I use: Internal Audio - Analog stereo input 
And use it as a analog stero output.

The exit unit for sound is: RS780 Azalia controller Digital Stereo (HDMI) stereo

---

### Post by fleppmar on 2010-03-16
So.. noone can help me with this?

I have been trying to fix it for a week now. Nothing works. :-(

Seems that I have to go back to Windows, so that stuff works.

Who would think that?!

---

### Post by Megafag on 2010-03-16
> **fleppmar said:**
> 3. I am having problems with wine, and installing spotify. I can right click on the spotify.ink and run it throug wine. And it works. But cant install it through the terminal.
When I try: sudo wine install "spotify exe"
And other varisons of that command I always get:
wine: could not load L"C:\\windows\\system32\\install.exe": Couldnt locate the module

No silly you have to point wine straight at the installer.

say if i had "winrarsetup.exe" in my home downloads folder, i would have to type this  

```
sudo wine /home/megafag/downloads/winrarsetup.exe 
```

EDIT:

> **fleppmar said:**
> So.. noone can help me with this?

I have been trying to fix it for a week now. Nothing works. :-(

Seems that I have to go back to Windows, so that stuff works.

Who would think that?!

If Ubuntu dosent work for you, because you don't have time to stuff around with it then use windows.
its not a sin, its just unpreferable.

---

