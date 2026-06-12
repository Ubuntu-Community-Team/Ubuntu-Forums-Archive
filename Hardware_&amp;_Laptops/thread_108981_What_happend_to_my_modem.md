---
title: "What happend to my modem?"
date: 2005-12-27
forum: Hardware &amp; Laptops
---

### Post by vempire on 2005-12-27
[FONT="Arial"][B]Hi, i have installed a driver modem for kernel 2.6.12-10-k7 in a compaq presario 2100 series with amd athlon xp 2800+, 768 mb ram, 30 gb hdd.

The driver is for a conexant i downloaded from [www.linuxant.com](www.linuxant.com).
I use gnome-ppp in the terminal as root user this is the problem:[/B][/FONT]

GNOME PPP: STDOUT: Scanning your serial ports for a modem.
GNOME PPP: STDOUT:
GNOME PPP: STDERR: Port Scan: Scanning ttySHSF0 first, /dev/modem is a link to it.
GNOME PPP: STDERR: ttySHSF0: ATQ0 V1 E1 -- OK
GNOME PPP: STDERR: ttySHSF0: ATQ0 V1 E1 Z -- OK
GNOME PPP: STDERR: ttySHSF0: ATQ0 V1 E1 S0=0 -- OK
GNOME PPP: STDERR: ttySHSF0: ATQ0 V1 E1 S0=0 &C1 -- OK
GNOME PPP: STDERR: ttySHSF0: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
GNOME PPP: STDERR: ttySHSF0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
GNOME PPP: STDERR: ttySHSF0: Modem Identifier: ATI -- 56000
GNOME PPP: STDERR: ttySHSF0: Speed 4800: AT -- OK
GNOME PPP: STDERR: ttySHSF0: Speed 9600: AT -- OK
GNOME PPP: STDERR: ttySHSF0: Speed 19200: AT -- OK
GNOME PPP: STDERR: ttySHSF0: Speed 38400: AT -- OK
GNOME PPP: STDERR: ttySHSF0: Speed 57600: AT -- OK
GNOME PPP: STDERR: ttySHSF0: Speed 115200: AT -- OK
GNOME PPP: STDERR: ttySHSF0: Speed 230400: AT -- OK
GNOME PPP: STDERR: ttySHSF0: Speed 460800: AT -- OK
GNOME PPP: STDERR: ttySHSF0: Max speed is 460800; that should be safe.
GNOME PPP: STDERR: ttySHSF0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
GNOME PPP: STDERR: ttyS0: ATQ0 V1 E1 -- failed with 2400 baud, next try: 960 0 baud
GNOME PPP: STDERR: ttyS0: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115 200 baud
GNOME PPP: STDERR: ttyS0: ATQ0 V1 E1 -- and failed too at 115200, giving up.
GNOME PPP: STDERR: Port Scan: S1 S2 S3 S4 S5 S6 S7 S8
GNOME PPP: STDERR: Port Scan: S9 S10 S11 S12 S13 S14 S15 S16
GNOME PPP: STDERR: Port Scan: S17 S18 S19 S20 S21 S22 S23 S24
GNOME PPP: STDOUT:
GNOME PPP: STDERR: Port Scan: S25 S26 S27 S28 S29 S30 S31 S32
GNOME PPP: STDOUT: Found a modem on /dev/ttySHSF0, using link /dev/modem in conf ig.
GNOME PPP: STDERR: Port Scan: S33 S34 S35 S36 S37 S38 S39 S40
GNOME PPP: STDOUT: Modem configuration written to /dev/null.
GNOME PPP: STDERR: Port Scan: S41 S42 S43 S44 S45 S46 S47 SHSF1
GNOME PPP: STDERR: Port Scan: SHSF2 SHSF3 SHSF4 SHSF5 SHSF6 SHSF7
GNOME PPP: STDERR: ttySHSF0: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 + FCLASS=0"
GNOME PPP: Conectando...
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.54.0
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Please enter password (or empty password to stop):
GNOME PPP: Conectando...
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.54.0
GNOME PPP: STDERR: --> Cannot open /dev/ttySHSF0: Device or resource busy
GNOME PPP: STDERR: --> Cannot open /dev/ttySHSF0: Device or resource busy
GNOME PPP: STDERR: --> Cannot open /dev/ttySHSF0: Device or resource busy

so what happend? any suggestions?:confused: :confused:

Hey Come on! any ideas???

---

