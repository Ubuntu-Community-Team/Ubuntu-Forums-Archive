---
title: "Realtek SD memory card : not detected"
date: 2011-11-21
forum: Hardware
---

### Post by mamboknave on 2011-11-21
How can I make the SD card reader visible/usable in Ubuntu?

As of now it goes totally undetected, even if I reboot the laptop with an SD card plugged in.

Looking fwd to read some hint/feedback. Thanks!


Laptop: HP Pavilion G6
OS: Ubuntu 10.04 64b, kernel 2.6.32-35 (this is LTS and I *cannot* upgrade due to legacy)

SD card device, from lspci:
03:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)

Most probable driver (does not compile, exits with errors)  :
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=25&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=25&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false#2)

lsusb does not show anything related to the card reader.

---

### Post by hugh.st on 2011-11-21
I've got a similar problem in that my card reader won't detect an SD card unless I insert it before turning on the computer. I've tried creating a partition and reformatting it but it still goes undetected.

My computer is an Acer Aspire AX1301 and is running 10.10 and I can't find the card reader's model at the moment.

Thanks for any help.

---

