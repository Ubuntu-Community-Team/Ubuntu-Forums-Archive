---
title: "Wireless Device Cannot be Enabled"
date: 2011-07-12
forum: Hardware
---

### Post by MercuryThreads on 2011-07-12
Hi, I'm new here at the forum, I've been using Ubuntu 10.04 LTS for about 8-9 months now, but I'm still pretty much a noob.

Anyway, last night I used my laptop (Latitude D505) for watching video, and as usual I fell asleep (~10PM) and did not turn it off. First thing in the morning (~5AM), I checked my laptop, moved the mouse and the cursor worked fine. Tried to play the video but it crashed VLC. After that, it was pretty much unresponsive; I could move the cursor, use the touchpad, but nothing happened on click, keyboard shortcut, nor even the power button to bring the shutdown menu. I was forced to hard reboot the laptop.

I should note when I restarted the laptop, it made a weird spinning hard drive noise, which I never heard before. It got to the splash screen, but didn't go further after I waited for a while (usually it only took 1-2 min max to boot and get google chrome ready for browsing). I used hard shutdown again (not good idea, like always) to turn it off, figured it was too hot.

About 3 hours later, I tried again, now it loaded all the way. I can use everything, and that weird noise has gone. However, I couldn't help but notice that I couldn't go to the web. I right click on the internet button (I use dockbarx btw) and networking is enabled. However, the 'enable wireless' option is greyed out and unchecked, so pretty much I couldn't go wireless (like the radio is turned off). I know that my wirelss network works fine, as I tested it using my droid phone.

I should also mention that this is the first time it happens. I have left my laptop on overnight in the past, sometimes it was on for 10-12 hours straight.

Here is the output from iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and from lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

So I know for sure that it detected my wireless adapter, but I just didn't know what to do from that point. If anyone might have a slight bit of hint, that'd be one step closer and I'd greatly appreciate it.

Thanks

---

