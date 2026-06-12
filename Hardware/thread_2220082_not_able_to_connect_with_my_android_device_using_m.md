---
title: "not able to connect with my android device using mtp"
date: 2014-04-26
forum: Hardware
---

### Post by nav1729 on 2014-04-26
when I connect my android phone to ubuntu 14.01, I am getting an error window displaying following message.

```
Unable to mount XT910
Unable to open MTP device '[usb:002,009]'
```

Phone icon appeared in my launcher ribbon. Right click on it shows an option to open, which is not working

little information about my laptop and other things are as follows
```

naveen@naveen-Lenovo-G570:~$ sudo uname -a
Linux naveen-Lenovo-G570 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

```

naveen@naveen-Lenovo-G570:~$ lsusb
Bus 002 Device 003: ID 04f2:b272 Chicony Electronics Co., Ltd Lenovo EasyCamera
Bus 002 Device 009: ID 22b8:437f Motorola PCS 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00d Foxconn / Hon Hai Broadcom Bluetooth 2.1 Device
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I guess motorola PCS is my phone

```

naveen@naveen-Lenovo-G570:~$ dpkg -l | grep mtp
ii  libmtp-common                                         1.1.6-20-g1b9f164-1ubuntu2                          all          Media Transfer Protocol (MTP) common files
ii  libmtp-runtime                                        1.1.6-20-g1b9f164-1ubuntu2                          amd64        Media Transfer Protocol (MTP) runtime tools
ii  libmtp9:amd64                                         1.1.6-20-g1b9f164-1ubuntu2                          amd64        Media Transfer Protocol (MTP) library
ii  libnet-smtp-ssl-perl                                  1.01-3                                              all          Perl module providing SSL support to Net::SMTP

```

Please let me know, if any other information is needed.

Note:
I checked the cable and phone setup with a windows PC.

---

### Post by nav1729 on 2014-04-27
Hi guys please let me know, if I have posted it in the wrong section.

also let me know, if anyone else has found a solution to similar problem.

---

