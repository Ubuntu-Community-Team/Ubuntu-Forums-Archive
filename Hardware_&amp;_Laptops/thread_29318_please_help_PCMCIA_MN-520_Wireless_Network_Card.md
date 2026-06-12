---
title: "please help PCMCIA MN-520 Wireless Network Card"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by coreyb on 2005-04-23
Hi,

First off I just installed ubuntu today, after previous failures with other distros on my rather archaic IBM Thinkpad 600E.

I have a Microsoft MN-520 Wireless 802.11b network card for this laptop. Today I ran out and bought myself a nice Belkin wireless router. I have two other comps in my home that are hard wired to this router (my means of posing this).

Being a complete newbie to Linux itself I am pretty much at a loss on how to make it work! I have read through the forum and found somethings interesting, but I always ran into some sort of problem while trying to follow the directions. 

I am in need of complete, step-by-step, help to install and get on the internet with my network card. 

I am comfortable with the terminal, but I lack the command knowledge to give you information in order to help you help me. 

I can tell you that I am sure that the card is functioning because it was working perfect while the laptop was running Windows XP. 

Any and all help is appreciated.   :neutral:  ](*,) 

Thanks in Advance,
Corey

---

### Post by kelvinq on 2005-04-24
I myself am a newbie but let me just try to help you through.

First of all, have you tried "iwconfig" and "ifconfig"?

"iwconfig" is meant for wireless interfaces while "ifconfig" is meant for network interface, including wireless. Type "man iwconfig" and "man ifconfig" to find out more.

Here's my output from both:

```

kelvinq@ubuntu:/$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"default"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:50:18:28:F2:0D
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Power Management:off
          Link Quality=0/0  Signal level=25/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

kelvinq@ubuntu:/$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5300 (5.1 KiB)  TX bytes:5300 (5.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:05:5D:84:78:69
          inet addr:192.168.123.111  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe84:7869/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:14354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9941386 (9.4 MiB)  TX bytes:1849909 (1.7 MiB)

```

If your device is supported, it should show up here. If so, then you can configure your device using System>Administration>Networking.

To see if you pci device is detected by hotplug, try "lspci" and find your device. Your device being listed does not mean your system has the drivers for them. It merely means that hotplug detected your device. You should then go on to check if iwconfig has your device listed. If not you have to find the drivers for it.

Try finding the drivers for your particular wireless card on google. You should be able to find at least a clue or two, then come back and ask in the forums.

HTH.

---

### Post by kelvinq on 2005-04-24
And, oh, to make your life a little breezy on your 400Mhz laptop, do try to install xfce as your alternative to bloated Gnome.

Go on Synaptic, search for Xfce and install. :)

---

### Post by rtdespres on 2005-11-29
I'm having the same problem.
Here are the results of the aforementiond commands.
What to do next?

$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.

$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (r ev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #3) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Co ntroller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go ] (rev a3)
0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev  78)
0000:02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controlle r
0000:02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controlle r
0000:02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controlle r

---

### Post by rtdespres on 2005-11-29
oh, I have a Dell Inspiron 8200 (not a thinkpad)

---

