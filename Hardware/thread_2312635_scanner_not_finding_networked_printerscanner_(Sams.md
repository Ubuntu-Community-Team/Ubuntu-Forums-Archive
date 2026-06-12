---
title: "scanner not finding networked printer/scanner (Samsung M2070)"
date: 2016-02-06
forum: Hardware
---

### Post by lister171254 on 2016-02-06
Using the Samsung Unified Linux Driver repository I got my networked Samsung M2070 to print (eventually).

I cannot get the scanner to work.


Most post addressing scanner issues deal with USB connected printers, while mine is a standalone network printer/scanner.

After following various threads I found a partial solution by adding the following line to /etc/sane.d/xerox_mfp.conf

```
tcp LeosPrinter 9100
```

where LeosPrinter is an entry in the hosts file

The relevant output from **strace -o traceOut.txt -f scanimage -T** follows. So the network scanner is detected (I can also hear the printer coming out of hibernation)

```

4028  munmap(0x7f4629146000, 4096)      = 0
4028  socket(PF_INET, SOCK_STREAM, IPPROTO_TCP) = 12
4028  connect(12, {sa_family=AF_INET, sin_port=htons(9100), sin_addr=inet_addr("192.168.1.50")}, 16) = 0
4028  setsockopt(12, SOL_SOCKET, SO_RCVTIMEO, "\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 16) = 0
4028  sendto(12, "\33\250\22\0", 4, 0, NULL, 0) = 4
4028  recvfrom(12, 0x1664a5c, 1024, 0, 0, 0) = -1 EAGAIN (Resource temporarily unavailable)
4028  close(12)                         = 0
4028  read(11, "", 4096)                = 0
4028  close(11)                         = 0

```


When executing the following I get and error (see attached) regarding the device and invalid arguments

---

### Post by Abdulhadi_81 on 2016-02-06
I don't know if you have looked at this before but do you think the  information in:  [http://www.linux-hardware-guide.com/2013-04-24-samsung-scx-3405w-all-in-one-wifi-scanner-copier-laser-printer-usb-2-0](http://www.linux-hardware-guide.com/2013-04-24-samsung-scx-3405w-all-in-one-wifi-scanner-copier-laser-printer-usb-2-0)  could be of some help ?

---

### Post by echotech2 on 2016-02-06
Slightly Off Topic:  I get the same error, "invalid argument", with my HP LaserJet Pro, ethernet connected to my router, with Xsane and Gimp (which uses Xsane,). SANE works fine.

---

### Post by lister171254 on 2016-02-06
Thanks for the link, but the solution is for USB.

My problem is with the network

---

### Post by lister171254 on 2016-03-25
Solution was here  [https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)   all the time.

The section  I missed is in the attached.

All working now as expected

Thanks

---

