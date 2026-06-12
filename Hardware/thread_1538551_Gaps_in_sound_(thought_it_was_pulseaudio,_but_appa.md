---
title: "Gaps in sound (thought it was pulseaudio, but apparently not!) ALC268"
date: 2010-07-25
forum: Hardware
---

### Post by ian_hawdon on 2010-07-25
Hi folks, been having an intermittent issue with sound for a while now. I was using Ubuntu 9.10 (or maybe even 9.04) when this issue started. During play back, every now and again, there would be a small gap, every 2 seconds or so. Many people said it was Pulseaudio and I should attempt to remove it.

Instead, I opted to go for Kubuntu 10.04 when it was released as, from what I've heard, it doesn't use Pulse. But strangely, I'm having the same issue! I have no idea where to even begin finding out where this issue is coming from! When it's happening, I have plenty of memory available, and my processor reports to be virtually idle!

I'm using an HP Touchsmart TX2, and Alsa report the sound chip to be: Realtek ALC268

Cheers

---

### Post by lidex on 2010-07-25
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by ian_hawdon on 2010-07-25
[http://www.alsa-project.org/db/?f=4f496ca01a88720ec93760d5b4c8607fe599c065](http://www.alsa-project.org/db/?f=4f496ca01a88720ec93760d5b4c8607fe599c065)

cheers

---

### Post by lidex on 2010-07-25
Are you getting any error messages? I don't use kde, so not sure if it's the same as gnome, but try looking here:
```
cat /var/log/messages
cat /var/log/syslog
```
These outputs also please:
```
dpkg -l | grep "alsa"
dpkg -l | grep "pulse"
```

```
sudo dmidecode -t bios
sudo dmidecode -t baseboard
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*

```

---

### Post by ian_hawdon on 2010-07-25
> **lidex said:**
> 
These outputs also please:
```
dpkg -l | grep "alsa"
```

```
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                            ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                   ALSA utilities
ii  bluez-alsa                           4.65-0ubuntu1                                     Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                         GStreamer plugin for ALSA
ii  libsdl1.2debian-alsa                 1.2.14-4ubuntu1.1                                 Simple DirectMedia Layer (with X11 and ALSA 
ii  libsox-fmt-alsa                      14.3.0-1.1build1                                  SoX alsa format I/O library
```


[QUOTE=lidex]```
dpkg -l | grep "pulse"
```[/QUOTE]
```
ii  libpulse-mainloop-glib0              1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14   PulseAudio client libraries (glib support)
ii  libpulse0                            1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14   PulseAudio client libraries
ii  libsox-fmt-pulse                     14.3.0-1.1build1                                  SoX PulseAudio format I/O library
ii  vlc-plugin-pulse                     1.1.0+svn20100502~pre3~webupd8~lucid9             PulseAudio plugin for VLC

```

[QUOTE=lidex]```
sudo dmidecode -t bios
```[/QUOTE]
```
# dmidecode 2.9                                                                                                                                                                     
SMBIOS 2.4 present.                                                                                                                                                                 
                                                                                                                                                                                    
Handle 0x0000, DMI type 0, 24 bytes                                                                                                                                                 
BIOS Information                                                                                                                                                                    
        Vendor: Hewlett-Packard
        Version: F.23
        Release Date: 09/22/2009
        ROM Size: 1024 kB
        Characteristics:
                ISA is supported
                PCI is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                Smart battery is supported
                BIOS boot specification is supported
                Targeted content distribution is supported
        BIOS Revision: 15.35
        Firmware Revision: 22.21

```
[QUOTE=lidex]```
sudo dmidecode -t baseboard
```[/QUOTE]
```
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 16 bytes
Base Board Information
        Manufacturer: Quanta
        Product Name: 3045
        Version: 16.15
        Serial Number: None
        Asset Tag: Base Board Asset Tag
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: Base Board Chassis Location
        Chassis Handle: 0x0003
        Type: Motherboard
        Contained Object Handles: 0

Handle 0x0007, DMI type 10, 6 bytes
On Board Device Information
        Type: Video
        Status: Enabled
        Description: 256

```
[QUOTE=lidex]```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```[/QUOTE]

```
                     USER PID ACCESS COMMAND
/dev/snd/controlC0:  Slmodemd    972 F.... slmodemd
                     ian        1583 F.... kmix
                     ian        6642 F.... chromium-browse
/dev/snd/pcmC0D0p:   ian        1532 F...m knotify4
                     ian        1613 F...m amarok
                     ian        6642 F...m chromium-browse
/dev/snd/pcmC0D6c:   Slmodemd    972 F.... slmodemd
/dev/snd/pcmC0D6p:   Slmodemd    972 F.... slmodemd
/dev/snd/timer:      ian        1532 f.... knotify4
                     ian        1613 f.... amarok
                     ian        6642 f.... chromium-browse

```

---

### Post by lidex on 2010-07-25
If you are not using your modem, uninstall this:
```
sudo apt-get remove sl-modem-daemon
```
**Reboot**

---

### Post by ian_hawdon on 2010-08-01
Thought that might have fixed it, but nope, still happening from time to time! :-(

---

### Post by lidex on 2010-08-01
Try upgrading your alsa install. Use the alsa-upgrade link in my sig.

---

