---
title: "USB booting options not available: cannot install os"
date: 2013-08-07
forum: Hardware
---

### Post by dovah on 2013-08-07
Hello everyone!

I'm actually running Ubuntu 12.04 on Asus X501A (w8 native), it isn't born with a CD/DVD internal reader.

My problem is that I'd like to install a new os on this machine (with an external cd/dvd or a live usb) but at booting, pressing the Esc key there is no sign of an usb option: the only three options displayed are 1.Toshiba(internal hd) 2.Realtek(internal speaker/micro) or 3.access bios. Got to say, in the past it did work perfectly: the installation of my current os was made from a live usb.

I tried to change the usb port(s) for the drives, but the problem persists.

The bios version is 2.15.1226, CSM is enabled, TDE is autodetected and secure boot is disabled.
I may have touched some booting settings... but I'm not able to find something like "add new boot device" in the bios, there's only "delete boot device"...

Can you help me with this task? 

Thanks

---

### Post by dannyboy79 on 2013-08-07
here's the steps for installing win7 from a usb stick, obviously ignore the win7 part but the other stuff should be applicable

Here's the solution:

1) Place a bootable copy of Wndows 7 on the USB drive in question (there are several utilities available for accomplishing this, including PowerISO, v4.8 or greater, and Microsoft's USB DVD Tool

2) Access the bios during bootup using F2

3) Enable CSM under the Boot tab and Save

4) Re-boot and re-access the bios again using F2

5) Select the USB option (the one without a prefix of UEFI) as Boot #1 option  and Save

6) Re-boot and Windows 7 will commence it's install from the USB drive

*Once the initial install takes place and the machine re-boots, you must re-access the bios, disable CSM, and set the internal hard drive as the Boot #1 option and save

---

### Post by dovah on 2013-08-07
I just tried your way but: 

under boot tab i got these options: 
>Boot config: >launch CSM [enabled] >launch PXE OpROM [disabled]
>Driver options priorities >nothing
>Boot options priorities: >boot#1 PO:Toshiba (THE ONLY AVAILABLE)
>Hard drive BBS >delete devices (THE ONLY AVAILABLE)

so really no usb port detected 

but... there's something in my head:
what if I tried under save&exit tab and hit the option >Restore defaults?

hope not messing up the pc :/

---

### Post by oldfred on 2013-08-07
Are you sure you have a bootable install in the flash drive. They usually are not shown as a bootable device unless it is bootable.
Confirm that download was correct with md5sum.
Reinstall with unetbootin.

       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Some other Asus, different models but may be similar?

 HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

---

### Post by dovah on 2013-08-07
Yes, I did the cd with brasero from the main ubuntu site, and I tried the usb with unetbootin installation... nothing seems to work 
I got something like that but without the "add device" option [IMG]http://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG] [URL="http://i.stack.imgur.com/kepiA.jpg"]http://i.stack.imgur.com/kepiA.jpg
[/URL]

this is the detail of my bios:

dovah@Asus-X501A:~$ sudo dmidecode --type bios
[sudo] password for dovah: 
# dmidecode 2.11
SMBIOS 2.7 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: X501A1.211
    Release Date: 08/20/2012
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 6144 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        Smart battery is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 4.6

Handle 0x0018, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Long
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

shall I flash it, then?[URL="http://i.stack.imgur.com/kepiA.jpg"]


[/URL]

---

### Post by oldfred on 2013-08-07
You also need to disable fast boot as that can make it difficult to get back into UEFI/BIOS. But that should not relate to not seeing flash drive as bootable.
Have you tried USB2 port or just any other ports. Some systems have issues with certain ports. And some flash drives just have issues also.

 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

I have had good luck with Microcenter's house brand and older Kingston. It now is to the point my wife does not let me go to the Microcenter store nearby as I always spend more on flash drive. Every time they are lower in cost and now both lower in cost & USB3. :)
USB3 is a little faster even with my USB2 ports.

---

### Post by sudodus on 2013-08-07
+1

Sandisk seems to be a good choice (fast and reliable for booting). See also these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://www.whoratesit.com/Best-Flash-Drive/Comparison/1](http://www.whoratesit.com/Best-Flash-Drive/Comparison/1)

Most but not all USB pendrives are reliable for booting, even many of the slower ones, and they are much cheaper, and should be OK particularly for regular read-only live drives (without persistence).

---

### Post by oldfred on 2013-08-07
Correction. Fast boot may interfere with USB boot.
It turns out the loading of USB drivers is somewhat slow. Fastboot with UEFI skips a lot of reinitialization, so you may not see a new device in a USB port.

[http://mjg59.dreamwidth.org/24869.html](http://mjg59.dreamwidth.org/24869.html)

> One of the requirements for Windows 8 certified hardware is that it must  complete firmware initialisation within a specific amount of time,  something that Microsoft refer to as "Fast Boot". Meeting these  requirements effectively makes it impossible to initialise USB, and it's  likely that certain other things will also be skipped.

---

### Post by dovah on 2013-08-09
[https://www.dropbox.com/s/s4ltijqdkim86dm/DSCN8450.JPG](https://www.dropbox.com/s/s4ltijqdkim86dm/DSCN8450.JPG)
[https://www.dropbox.com/s/jurrdud9ouxqnhf/DSCN8451.JPG](https://www.dropbox.com/s/jurrdud9ouxqnhf/DSCN8451.JPG)
[https://www.dropbox.com/s/hni5yk0y9h1hs0n/DSCN8452.JPG](https://www.dropbox.com/s/hni5yk0y9h1hs0n/DSCN8452.JPG)
[https://www.dropbox.com/s/bmg1vadtwn16f32/DSCN8453.JPG](https://www.dropbox.com/s/bmg1vadtwn16f32/DSCN8453.JPG)
[https://www.dropbox.com/s/w02ulr0nklh7fn6/DSCN8454.JPG](https://www.dropbox.com/s/w02ulr0nklh7fn6/DSCN8454.JPG)
[https://www.dropbox.com/s/rmkilfeusqvh1ja/DSCN8455.JPG](https://www.dropbox.com/s/rmkilfeusqvh1ja/DSCN8455.JPG)

For the moment no solution seems ok for my case.
I hope those dropbox links could help to understand my situation...

Thanks for the help and the disponibility.

---

### Post by oldfred on 2013-08-09
I do not understand all the settings but have seen others with that UEFI work. And sometimes it is settings that seem unrelated that make a difference.

 Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

Example of a new system with what would seem like an unrelated setting:

 
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.

---

