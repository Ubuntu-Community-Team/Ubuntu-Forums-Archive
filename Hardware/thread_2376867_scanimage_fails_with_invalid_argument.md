---
title: "scanimage fails with invalid argument"
date: 2017-11-07
forum: Hardware
---

### Post by weswitt on 2017-11-07
I have SANE installed on Ubuntu 16.04. XSANE works perfectly and scanimage was working until I started a scan and CTRL-C to end the scan. Now scanimage fails with "scanimage: open of device epkowa:interpreter:001:006 failed: Invalid argument". sane-find-scanner, "scanimage -L" and "scanimage --test" all work perfectly as does XSANE. What is now broken is command line scanning with scanimage. I'm a bit baffled why terminating scanimage would break this. One interesting this is that I cannot telnet to the network port of saned.

Any help would be appreciated.

Below is the output from diagnostics:

root@WESWUBUNTU:/# scanimage -d epkowa:interpreter:001:006 --resolution 100 -x 100 -y 100 >scan.ppm
scanimage: open of device epkowa:interpreter:001:006 failed: Invalid argument



root@WESWUBUNTU:/etc/default# scanimage --test
scanimage: scanning image of size 2544x3509 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 7632 bytes...  PASS
scanimage: reading one byte...          PASS
scanimage: stepped read, 2 bytes...     PASS
scanimage: stepped read, 4 bytes...     PASS
scanimage: stepped read, 8 bytes...     PASS
scanimage: stepped read, 16 bytes...    PASS
scanimage: stepped read, 32 bytes...    PASS
scanimage: stepped read, 64 bytes...    PASS
scanimage: stepped read, 128 bytes...   PASS
scanimage: stepped read, 256 bytes...   PASS
scanimage: stepped read, 512 bytes...   PASS
scanimage: stepped read, 1024 bytes...  PASS
scanimage: stepped read, 2048 bytes...  PASS
scanimage: stepped read, 4096 bytes...  PASS
scanimage: stepped read, 8192 bytes...  PASS
scanimage: stepped read, 8191 bytes...  PASS
scanimage: stepped read, 4095 bytes...  PASS
scanimage: stepped read, 2047 bytes...  PASS
scanimage: stepped read, 1023 bytes...  PASS
scanimage: stepped read, 511 bytes...   PASS
scanimage: stepped read, 255 bytes...   PASS
scanimage: stepped read, 127 bytes...   PASS
scanimage: stepped read, 63 bytes...    PASS
scanimage: stepped read, 31 bytes...    PASS
scanimage: stepped read, 15 bytes...    PASS
scanimage: stepped read, 7 bytes...     PASS
scanimage: stepped read, 3 bytes...     PASS


root@WESWUBUNTU:/# sane-find-scanner | grep 0x04
found USB scanner (vendor=0x04b8 [EPSON], product=0x0131 [EPSON Scanner]) at libusb:001:007


root@WESWUBUNTU:/# scanimage -L
device `epkowa:interpreter:001:007' is a Epson Perfection V300 flatbed scanner


root@WESWUBUNTU:/# lsusb
Bus 001 Device 007: ID 04b8:0131 Seiko Epson Corp. GT-F720 [GT-S620/Perfection V30/V300 Photo]


root@WESWUBUNTU:~# systemctl status saned.socket
? saned.socket - saned incoming socket
   Loaded: loaded (/lib/systemd/system/saned.socket; disabled; vendor preset: enabled)
   Active: inactive (dead) since Mon 2017-11-06 21:36:25 PST; 3min 44s ago
   Listen: [::]:6566 (Stream)
 Accepted: 0; Connected: 0


Nov 06 21:32:47 WESWUBUNTU systemd[1]: Listening on saned incoming socket.
Nov 06 21:36:25 WESWUBUNTU systemd[1]: Closed saned incoming socket.
Nov 06 21:38:22 WESWUBUNTU systemd[1]: Closed saned incoming socket.


root@WESWUBUNTU:~# telnet localhost 6566
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

---

