---
title: "Unable to connect to a modem"
date: 2009-07-26
forum: Hardware
---

### Post by urisc on 2009-07-26
Hi all,
I am a new ubuntu (Jaunty) user trying to create a working platform with my Acer Aspire 2920 laptop. I have tried to connect with my 56K ITU V.92 modem and here's what I get:
efax-0.9a: 16:44:05 &#1514;&#1511;&#1500;&#1492;: local ID (09-7962087) has non-standard characters 
efax-0.9a: 16:44:05 &#1492;&#1514;&#1511;&#1503; /dev/ttyS1 &#1504;&#1508;&#1514;&#1495; 
efax-0.9a: 16:44:05 &#1513;&#1490;&#1497;&#1488;&#1492;: tcgetattr on fd=3 failed: Input/output error 
efax-0.9a: 16:44:05 failed page /home/uri/faxout/output90509.ps.001 
efax-0.9a: 16:44:05 &#1513;&#1490;&#1497;&#1488;&#1492;: fax device write: Input/output error 
efax-0.9a: 16:44:07 &#1513;&#1490;&#1497;&#1488;&#1492;: tcgetattr on fd=3 failed: Input/output error 
efax-0.9a: 16:44:09 &#1513;&#1490;&#1497;&#1488;&#1492;: fax device write: Input/output error 
efax-0.9a: 16:44:11 &#1513;&#1490;&#1497;&#1488;&#1492;: tcgetattr on fd=3 failed: Input/output error 
efax-0.9a: 16:44:11 &#1505;&#1504;&#1499;&#1512;&#1493;&#1503;: &#1502;&#1493;&#1512;&#1497;&#1491; DTR 
efax-0.9a: 16:44:12 &#1513;&#1490;&#1497;&#1488;&#1492;: tcgetattr on fd=3 failed: Input/output error 
efax-0.9a: 16:44:12 &#1513;&#1490;&#1497;&#1488;&#1492;: tcgetattr on fd=3 failed: Input/output error 
efax-0.9a: 16:44:14 &#1513;&#1490;&#1497;&#1488;&#1492;: fax device write: Input/output error 
efax-0.9a: 16:44:16 &#1513;&#1490;&#1497;&#1488;&#1492;: tcgetattr on fd=3 failed: Input/output error 
efax-0.9a: 16:44:16 &#1513;&#1490;&#1497;&#1488;&#1492;: fax device write: Input/output error 
efax-0.9a: 16:44:16 &#1513;&#1490;&#1497;&#1488;&#1492;: fax device write: Input/output error 
efax-0.9a: 16:44:16 &#1505;&#1504;&#1499;&#1512;&#1493;&#1503;: &#1513;&#1493;&#1500;&#1495; escapes 
efax-0.9a: 16:44:16 &#1513;&#1490;&#1497;&#1488;&#1492;: tcgetattr on fd=3 failed: Input/output error 
efax-0.9a: 16:44:16 &#1513;&#1490;&#1497;&#1488;&#1492;: fax device write: Input/output error 
efax-0.9a: 16:44:16 &#1513;&#1490;&#1497;&#1488;&#1492;: fax device write: Input/output error 
efax-0.9a: 16:44:18 &#1513;&#1490;&#1497;&#1488;&#1492;: fax device write: Input/output error 
efax-0.9a: 16:44:20 &#1513;&#1490;&#1497;&#1488;&#1492;: fax device write: Input/output error 
efax-0.9a: 16:44:22 &#1513;&#1490;&#1497;&#1488;&#1492;: &#1505;&#1504;&#1499;&#1512;&#1493;&#1503;: &#1492;&#1502;&#1493;&#1491;&#1501; &#1500;&#1488; &#1502;&#1490;&#1497;&#1489; 
efax-0.9a: 16:44:22 &#1513;&#1490;&#1497;&#1488;&#1492;: tcgetattr on fd=3 failed: Input/output error 
efax-0.9a: 16:44:22 &#1492;&#1505;&#1514;&#1497;&#1497;&#1502;&#1492; - &#1513;&#1490;&#1497;&#1488;&#1492; &#1500;&#1500;&#1488; &#1488;&#1508;&#1513;&#1512;&#1493;&#1514; &#1492;&#1514;&#1488;&#1493;&#1513;&#1513;&#1493;&#1514; 

I also tried to connect via Genome ppp and I got a massage "can't connect to modem". I have searched the forums quiet a bit but I could not fined the solution to my problem. Are there any ideas that I might try?
Thanks much in advance.
Uri.:)

---

### Post by gamerchick02 on 2009-07-26
Have you tried to connect using wvdial?

It's a terminal application that you have to add in all your modem information to the config file.

Amy

---

