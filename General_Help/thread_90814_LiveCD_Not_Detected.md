---
title: "LiveCD Not Detected"
date: 2005-11-15
forum: General Help
---

### Post by Cath0de on 2005-11-15
Hi, I'm new here, and I'm not sure whether this is in the right forum (there are an awful lot).

So I downloaded the .iso image for the LiveCD, and I have ubuntu-5.10-live-i386.iso

I burned that image onto a disc, went into my bios and set my disc drive as the primary booting device, saved and exited. Now I expect that ubuntu is supposed to boot from the disc, but I'm just going back to my old WindowsXP boot. It happens on multiple computers, and I've burned the image on several discs with different programs, always the same problem. It's just not being detected.

Help.

--------[ AIDA32 (c) 1995-2004 Tamas Miklos ]---------------------------------------------------------------------------

    Version                                           AIDA32 v3.94.2
    Author                                            [email]tamas.miklos@aida32.hu[/email]
    Homepage                                          [http://www.aida32.hu](http://www.aida32.hu)
    Report Type                                       Quick Report
    Computer                                          CATH0DE
    Generator                                         Michael
    Operating System                                  Microsoft Windows XP Home Edition 5.1.2600 (WinXP Retail)
    Date                                              2005-11-15
    Time                                              20:20


--------[ Summary ]-----------------------------------------------------------------------------------------------------

    Computer:
      Operating System                                  Microsoft Windows XP Home Edition
      OS Service Pack                                   Service Pack 2
      Internet Explorer                                 6.0.2900.2180
      Computer Name                                     CATH0DE
      User Name                                         Michael
      Logon Domain                                      CATH0DE

    Motherboard:
      CPU Type                                          Intel Pentium 4HT, 3000 MHz (3.75 x 800)
      Motherboard Name                                  Intel Rock Lake D865PERL  (5 PCI, 1 AGP, 4 DIMM)
      Motherboard Chipset                               Intel Springdale i865PE
      System Memory                                     1536 MB  (DDR SDRAM)
      BIOS Type                                         AMI (04/02/04)
      Communication Port                                Communications Port (COM1)
      Communication Port                                Printer Port (LPT1)

    Display:
      Video Adapter                                     RADEON 9600 SERIES - Secondary  (128 MB)
      Video Adapter                                     RADEON 9600 SERIES  (128 MB)
      3D Accelerator                                    ATI Radeon 9600 XT (RV360)
      Monitor                                           ViewSonic A90f+  (351030551138)

    Multimedia:
      Audio Adapter                                     Creative SB Live! Sound Card
      Audio Adapter                                     Intel 82801EB ICH5 - AC'97 Audio Controller

    Storage:
      Floppy Drive                                      Floppy disk drive
      Disk Drive                                        ST360021A  (60 GB, 7200 RPM, Ultra-ATA/100)
      Optical Drive                                     Generic DVD-ROM SCSI CdRom Device
      Optical Drive                                     PLEXTOR CD-R   PX-W1610A  (16x/10x/40x CD-RW)
      Optical Drive                                     SAMSUNG DVD-ROM SD-616F  (16x/48x DVD-ROM)

    Partitions:
      C: (NTFS)                                         57231 MB (3453 MB free)

    Input:
      Keyboard                                          Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
      Mouse                                             Microsoft USB IntelliMouse Explorer
      Game Controller                                   Microsoft PC-joystick driver

    Network:
      Primary IP Address                                192.168.1.100
      Primary MAC Address                               00-00-C5-53-15-51
      Network Adapter                                   Intel 21143-Based PCI Fast Ethernet Adapter (Generic)  (192.168.1.100)

    Peripherals:
      Printer                                           Auto hp deskjet 995c series on IBM-0EA81F6150F
      Printer                                           hp deskjet 995c series
      Printer                                           Microsoft Office Document Image Writer
      USB Device                                        Logitech Driving Force USB
      USB Device                                        Microsoft USB IntelliMouse Explorer
      USB Device                                        USB Printing Support

    Problems & Suggestions:
      Problem                                           Disk free space is only 6% on drive C:.

---

### Post by dbott67 on 2005-11-15
Make sure that the .iso file is being burned as an image, as opposed to just copying the file to CD.

Read the [link in my signature]("http://www.ubuntuforums.org/showthread.php?p=465704#post465704") about how to burn an ISO image using Nero below.

-Dave

---

### Post by Cath0de on 2005-11-15
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Major props to this guy. I'm just not familiar with burning this kind of thing, I usually just use daemon to mount an .iso on a virtual drive.

---

### Post by kruz on 2005-11-15
yes and also make sure ur drive is set to boot usb if u have a usb device
in the bios

use nero trial to burn ur iso buddy
download.com
then nero
holla!

---

### Post by Cath0de on 2005-11-15
well, I'm posting this through Ubuntu, so I got it to work. I'm still working with some other stuff though.

---

### Post by teaker1s on 2005-11-15
alter boot sequence in bios so it checks dvd and cd rom first -if you have an old computer it may have to boot with a floppy to get cd rom support

---

### Post by fin on 2005-11-15
[QUOTE=dbott67]Make sure that the .iso file is being burned as an image, as opposed to just copying the file to CD.[/QUOTE]

Also, burn it at a slower speed. I burned it at 8x and it didn't work. Burned it again at 6x and it was flawless.

---

