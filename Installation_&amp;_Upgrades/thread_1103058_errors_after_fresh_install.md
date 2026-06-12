---
title: "errors after fresh install"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by Guus1982 on 2009-03-22
I'm getting errors after i reinstalled ubuntu (64bit now but had em also when i was running 32bit)

I dont mind getting errors but getting to easy solutions seems very hard. 
Google doenst get me anything, still looking for a needle in a haystack.

I dont know if there are related:

From the Xorg.0.log:
(II) intel(0): EDID vendor "SEC", prod id 12865
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 12865
(EE) intel(0): Mode 1280x1024 does not fit virtual size 1024x1024 - internal error

The user.log
Mar 22 17:39:40 guus-laptop pulseaudio[7559]: ltdl-bind-now.c: Failed to find original dlopen loader.
Mar 22 17:39:40 guus-laptop pulseaudio[7561]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar 22 17:39:40 guus-laptop pulseaudio[7561]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

From the sys.log:
Mar 22 15:33:33 guus-laptop kernel: [  151.256388] ppdev0: registered pardevice
Mar 22 15:33:33 guus-laptop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Mar 22 15:33:33 guus-laptop kernel: [  151.304363] ppdev0: unregistered pardevice
Mar 22 15:33:33 guus-laptop kernel: [  151.772388] ppdev0: registered pardevice
Mar 22 15:33:33 guus-laptop python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Mar 22 15:33:33 guus-laptop kernel: [  151.820204] ppdev0: unregistered pardevice
Mar 22 15:33:35 guus-laptop kernel: [  153.005695] ppdev0: registered pardevice
Mar 22 15:33:35 guus-laptop kernel: [  153.053076] ppdev0: unregistered pardevice

And last but not least from the auth.log:
Mar 22 15:32:02 guus-laptop gdm[6636]: pam_unix(gdm:session): session opened for user guus by (uid=0)
Mar 22 15:32:02 guus-laptop gdm[6636]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Mar 22 15:32:02 guus-laptop gdm[6636]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar 22 15:32:02 guus-laptop gdm[6636]: Autolaunch error: X11 initialization failed.
Mar 22 15:32:02 guus-laptop gdm[6636]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar 22 15:32:02 guus-laptop gdm[6636]: Autolaunch error: X11 initialization failed.
Mar 22 15:32:02 guus-laptop gdm[6636]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar 22 15:32:02 guus-laptop gdm[6636]: Autolaunch error: X11 initialization failed.
Mar 22 15:32:02 guus-laptop gdm[6636]: )

---

### Post by Guus1982 on 2009-03-22
can some1 point me into the right direction

---

### Post by Guus1982 on 2009-03-22
any1?

---

### Post by Guus1982 on 2009-03-24
please do help me. i need support

---

### Post by Guus1982 on 2009-03-24
bump

---

### Post by oldos2er on 2009-03-24
Can you post your hardware specs?

---

### Post by Guus1982 on 2009-03-24
Laptop NC4400 ([http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-306995-1847961.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-306995-1847961.html))

HP Compaq 4400 series


Processor5                Intel Core Duo Processor T2600† (2.16-GHz, 667-MHz FSB, 2MB-L2 cache)


Chipset                   Mobile Intel 945GM Express Chipset with 667-MHz FSB


Memory                     2gb DDR2 SDRAM, 667-MHz, two SODIMM

Hard drive(s)8             80 5400 rpm


Display                    12.1-inch XGA (1024 × 768 resolution and 16M colors), Ambient Light Sensor

Graphics                    Intel Graphics Media Accelerator 950, up to 128-MB shared system memory


Audio                       High Definition Audio support w/24-bit audio DAC, headphone jack, stereo/mono microphone jack, integrated mono
  microphone


Wireless2 support           Intel PRO/Wireless 3945ABG Network Connection, Intel PRO/Wireless 3945BG Network Connection, Broadcom 4311AG

802.11a/b/g WiFi Adapter, Broadcom 4311BG 802.11b/g WiFi Adapter, HP BluetoothTM 2.0


Communications               Broadcom NetXtreme Gigabit Ethernet PCI Express Controller3 (10/100/1000 NIC), 56K v.92 modem, HP Smart Power NIC

technology


Expansion slots              1 Type I/II PC Card slot supports 32-bit CardBus and 16-bit cards, Secure Digital slot


Ports                        3 USB 2.0, VGA, RJ-11, RJ-45, S-video TV out, headphone, microphone, Fast IR, secure digital slot, AC adapter, docking


connectors                        connector, accessory battery connector


Input devices                     nc4400 models - Full-sized keyboard; Enhanced dual pointing devices (touchpad and pointstick) with scroll zone

---

### Post by Guus1982 on 2009-03-31
lets bump again

---

### Post by Guus1982 on 2009-04-02
bump again

---

### Post by Guus1982 on 2009-04-10
bump

---

### Post by Guus1982 on 2009-04-17
will i ever get support from this outstanding community...
feel a litlle lost here

---

