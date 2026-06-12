---
title: "Blank screen / sound not working / Sony Vaio VPCY21S1E"
date: 2011-01-03
forum: Hardware
---

### Post by sellibitze on 2011-01-03
Hi!

I have some troubles with Ubuntu 10.10 amd64 in combination with my 13" Sony Vaio VPCY21S1E. This notebook uses the Intel Pentium(R) 5400 with the integrated Intel GMA HD graphics chip.

The problems I'm currently facing are

[LIST=1]
[*]Blank screen after selecting Linux in grub's boot menu.
[*][COLOR=Gray]Audio doesn't work (no soundcard detected)[/COLOR]
[/LIST]
If I remove "quiet splash" from the boot options, I see Linux booting up in text mode up to the point where it tries to "mode-switch" (I think). The last lines I see contain "i915" and then the screen goes blank and the system seems to hang.

If I add "i915.modeset=0" to the boot options, Linux boots through without hanging but I get to see the text login console for about 2 minutes before X starts in a lower resolution -- 1024x768 instead of 1366x768. I also need to add i8042.nopnp in order to make the touchpad work.

I then tried to install recent Intel graphics drivers from the "xorg edgers PPA" but nothing changed so far.

Is there a way to solve these issues? Did I do something wrong? As far as I can tell other people have the same graphics chip and they got it to work. Maybe it has something to do with the amd64 version? I didn't test a 32bit Ubuntu version yet.

[COLOR=Gray]Also, it would be nice to get the sound working. The alsa-info.sh script yields:
...
!!Soundcards recognized by ALSA
--- no soundcards ---
!!PCI Soundcards installed in the system
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
...

Does this mean that the soundcard is currently not supported or just not properly configured?[/COLOR] 

I appreciate any help I get.

**Edit:** Now, after upgrading from linux 2.6.35-22 to 2.6.35-24 audio seems to work and X starts immediately with i915.modeset=0 (instead of the 2 minutes of idle time in text mode). Still only a resolution of 1024x768 and a blank screen without i915.modeset=0.

sellibitze

---

### Post by gabriel_celeste on 2011-01-14
Hi,

I was thinking about purshase this laptop and I found this tutorial:
[http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e]("http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e")

---

### Post by sellibitze on 2011-09-05
Update:

Now, I tried a fresh install of Ubuntu 11.04 on the Sony Vaio VPCY21S1E (Pentium U5400 with Intel GMA HD graphics, Atheros WLAN chip) and I have the following problems:

Graphics:
Blank screen after booting. I hear the login screen sound but the screen stays black. Using "nomodeset" it starts in "vesa mode" (?) at 1024x768 which is pretty annoying since this is not the display's native resolution (that would be 1366x768 ).

Backlight brightness control:
The system responds to the hotkeys (I get to see the OSD) but the brightness does not actually change.

WLAN:
For some reason, I can't get my WLAN activated. The network manager applet shows inconsistent entries ("wireles networks disabled" and below that a checked "wireles networks"). I tried various things (rfkill unblock, iwconfig, ifconfig wlan0 up, nmcli). It seems the card has been recognized, but I don't seem able to activate it. And no, it's certainly not "hardware-blocked".

What I did so far:
- updated everything to the latest versions (kernel 2.6.38-8 --> 2.6.38-12 IIRC)
- Added the "xorg edgers PPA" to the source list / fetched and installed all sorts of new packages including linux-image-3.0.something

But that didn't change anything. I really did not expect that having seen reports on how to make it work on Sony Vaio.

Some more infos:
The installed xserver-xorg-video-intel version is 2:2.16.0+git20110901.695e7115-0ubuntu0sarvatt~natty (natty)
```

sebi@sebivaio:~$ uname -a
Linux sebivaio 3.0.0-9-generic #14-Ubuntu SMP Thu Aug 25 17:45:32 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
sebi@sebivaio:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:24:be:5f:41:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:5856 (5.8 KB)  TX bytes:5856 (5.8 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 78:dd:08:f6:26:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sebi@sebivaio:~$ nmcli -p dev
=============================================
              Status der Geräte
=============================================
DEVICE     TYPE              STATUS       
---------------------------------------------
wlan0      802-11-wireless   not available
eth0       802-3-ethernet    not available
sebi@sebivaio:~$ nmcli -p nm
======================================================================================
                              Status von NetworkManager
======================================================================================
LAUFEND         STATUS          WLAN-HARDWARE   WLAN       WWAN-HARDWARE   WWAN      
--------------------------------------------------------------------------------------
wird ausgeführt nicht verbunden aktiviert       deaktiviert aktiviert       deaktiviert

```
If I connect my laptop (wire) with the router ETH0 works just fine, though.

---

### Post by nearo on 2011-09-23
For some reason, it does not detect the monitor. An external monitor works fine.

---

