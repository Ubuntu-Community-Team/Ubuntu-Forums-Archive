---
title: "Ubuntu Netbook 10.04 for Sony Vaio W-series (VPCW211AX)"
date: 2010-08-18
forum: Hardware
---

### Post by IperBug on 2010-08-18
Hi all, first post here and first Linux experience for me. I apologize in advance if any question sounds silly and should be better posted in the Absolute Beginner Talk.

I decided to try Ubuntu Netbook 10.04 on my Vaio W-series. I still have the original Windows starter and installed Ubuntu next to it. As a first novice experience, I got to say it went pretty smooth. 

I would like you to share your issues here. At the moment, the most annoying one is related to the built-in microphone not working properly (it seems like the volume is super low). I tried to play with the alsamixer, muting, not muting, increasing the volume, but it does not seem to work.

As a consequence, I cannot make good use of Skype and alike. Any suggestion?

External hardware (USB keys, printer, external CD reader/writer) seem to work just fine. Also, I do not have the issue related to the immediate suspension of the laptop when it is running on battery (it is reported here:  [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks))


Any help will be appreciated. Also, if you need more info on my side, just let me know.

---

### Post by IperBug on 2010-08-19
Here are some specs:

#uname -a
Linux IperBug-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux


#cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0- 0]: hardware dependent
  7: [ 0]   : control


#head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC262


#cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.



Info on my motherboard

#udo dmidecode -t bios
[sudo] password for IperBug: 
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: INSYDE
    Version: R0240E2
    Release Date: 12/07/2009
    ROM Size: 1024 kB
    Characteristics:
        PCI is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        8042 keyboard services are supported (int 9h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        Smart battery is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
    BIOS Revision: 2.40
    Firmware Revision: 2.40


#sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 10 bytes
Base Board Information
    Manufacturer: Sony Corporation
    Product Name: VAIO
    Version: N/A
    Serial Number: C103WNET




As I said, I tried alsamixer, pulseaudio, sound preferences, muted one by one all the inputs, checked with sound recorder. But nothing happens. All the tricks provided in similar threads do not seem to work, including adding some options line at the end of alsa-base.conf


I attach a screenshot of my alsamixer. After playing around with it, I notice that I can have a very very low sound recorded with the Capture Device (NOT with Capture 1 and Capture 2, this is why they are muted, but changing them does not affect the matter). Also, the Atapi mic does not seem to to the trick. I also treid toggling from Mic to Front Mic to Line, but nothing again. In the Configuration Tab of Volume Control of pulseaudio I have Analog Stereo Duplex as a profile. 

Any help would be appreciated. Thanks.

---

### Post by IperBug on 2010-08-19
I upgraded to the last Alsa version 

#cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Aug 18 2010 for kernel 2.6.32-24-generic (SMP).


And the microphone now works perfectly.

---

