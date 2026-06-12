---
title: "Wlan0 will not able on Dell Inspiron 8600"
date: 2011-09-25
forum: Hardware
---

### Post by Gordon Martin on 2011-09-25
all --

just loaded new version of Ubuntu and all is well except for the wireless network,
In the terminal mode I see the Wlan0 is disabled and I cannot get this enabled.
can anyone point me in the correct direction?
thanks is advance

Gordon

---

### Post by grahammechanical on 2011-09-25
Hi and welcome to the forums.

Have you tried clicking the network manager icon and clicking both Enable Networking and Enable wireless? Those two lines act like on off switches.

Have you used the Additional Drivers utility to activate any additional drivers? There might be an icon of a pc expansion card to the top panel. You can find this utility in System Settings or type a seach for it in the Dash. It is an Installed program.

Regards.

---

### Post by Gordon Martin on 2011-09-25
Yes I did find the enable wireless network and enable network tabs at the top of the bar, this acts like something is not correct in the set-up or some kind of compatibility
I will try what you suggested, many thanks for the welcome to this great forum

---

### Post by pjd99 on 2011-09-25
Shouldn't need additional drivers. Is it the original iw2100/2200/2915 that came with the laptop? If so, that driver has been included in the kernel for the last few years.


does a:
```

dmesg | grep Intel

```or
```

lspci | grep Wireless

```yield anything? If so, make sure the kernel module is loaded.
```

lsmod | grep ipw

```(The above code blocks assume you have an Intel PRO/Wireless card, 2100, 2200 or 2915)

---

### Post by Gordon Martin on 2011-09-25
wow this forum is amazing.
many thanks for the quick replies.
below is what I got when I tried the commands you sent.

gordonmartin@ubuntu:~$ dmesg | grep intel
[    0.493340] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[    0.548231] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[    8.486755] intel_rng: FWH not detected
[   10.730682] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   10.730703] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   11.796028] intel8x0_measure_ac97_clock: measured 55422 usecs (2670 samples)
[   11.796031] intel8x0: clocking to 48000
gordonmartin@ubuntu:~$ lspci | grep wireless
gordonmartin@ubuntu:~$ lsmod | grep ipw
gordonmartin@ubuntu:~$ 

as far as I know it should be the original wireless components inside the laptop

ideas ?

many thanks for the help

Gordon

---

### Post by pjd99 on 2011-09-25
Hmm, now i'm trying to figure out which wireless card is in your machine. My 8600 at home has a Intel ipw2200BG, but it seems this is not the case for you.

Was/is there a Centrino sticker on it? That sticker means it shipped with an Intel CPU & wireless card. Yours may have shipped with a Dell TrueMobile card. We need to find the make and model to ensure the correct driver is being loaded.

Would you be able to post the output of lspci?
```

lspci

```

---

### Post by Gordon Martin on 2011-09-25
Yes I can post the output to that command
I will try and look further for what kind of wireless card is in this unit.

again

many thanks

Gordon

gordonmartin@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5650] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02

---

### Post by Gordon Martin on 2011-09-25
under the dell support page listing the original equipment
i found the following listing
3X548	Card, Wireless, Mini PCI Card, Internal, BROADCOM CORPORATION..., 5GHz

I do not know if this would help

Gordon

---

### Post by pjd99 on 2011-09-25
See the last line in your lspci output. That is the wireless card, A Broadcom BCM4309 a/b/g. (Also called a Dell TrueMobile D400/410/600)
Now we need to see if it has a driver and if it's loaded.

can you now try:
```

lsmod | grep bcm

```Should let us know if the driver is loaded. If you get nothing, just post the output of lsmod and all currently loaded modules will show. It is possible that there is a module conflict somewhere.

If you see a bcm module loaded, post the output of:
```

iwconfig

```and you can check if the wireless radio is at the very least on.

Looking around, Broadcom never released the info for a proper open source driver to be created, so bcm43xx is a reverse-engineered one. People have also used ndiswrapper to get this card working. I have no experience with it, but there are plenty of guides on the forum if you need to go that route. It is a last resort option though, as it can be really messy.

---

### Post by Gordon Martin on 2011-09-26
i believe I understand what you are pointing out.
Below is what I gleemed off of the commands you sent.

ordonmartin@ubuntu:~$ lsmod | grep bcm
gordonmartin@ubuntu:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
gordonmartin@ubuntu:~$ 
it would appear that the wireless system I have in this dell Inspiron 8300 are not supported.
I will try what you suggested and see if I can look thru the forum for some guidance in that area.
many thanks for all the responses and help.
I had to reload Ubuntu because I tried downloading something that I thought would work and ended up knocking myself off the network wired and wireless.
I am in the sharp learning curve of Ubuntu I am afraid

again
thanks

Gordon

---

### Post by pjd99 on 2011-09-27
> **Gordon Martin said:**
> 
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
Ahh, looks like there is a driver installed, but no connection is present. I still don't know which driver it is using though...

For instance, when I'm not connected to a network I get:
```

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
And when connected:
```

wlan0     IEEE 802.11abgn  ESSID:"NOTREAL"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 14:D6:4D:A9:5F:D0   
          Bit Rate=117 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:37   Missed beacon:0

```

When you click the network manager icon on the top bar, make sure wireless is enabled, then see if there are any networks around. Then maybe try connecting to a hidden wireless network.

---

### Post by pjd99 on 2011-09-27
Also, the current state of Broadcom drivers in linux is a bit wishy-washy. Looks like bcm43xx has been removed from the kernel (2.6.26 according to wikipedia). b43 is still there, but might use experimental open-source firmware. Still idk what driver you're on.

If you come back, can you post the output of:
```

lsmod

```

I really want to find that driver...

---

