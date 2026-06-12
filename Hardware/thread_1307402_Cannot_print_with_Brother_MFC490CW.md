---
title: "Cannot print with Brother MFC490CW"
date: 2009-10-31
forum: Hardware
---

### Post by gman2 on 2009-10-31
Just installed Ubuntu 9.10 to see how it compares to PCLinuxOS.

I cannot print with my Brother MFC490CW. I get the com.apple.print.recoverable error, whatever that means. I know my network printing works, I can successfully print in PCLinuxOS.

While I really like Ubuntu 9.10, as of now I give it a failing grade simply because printer setup should be working without hassle as it does in other distros such as PCLinuxOS and Mandriva.

---

### Post by grandtoubab on 2009-10-31
try to manage your printer using CUPS

[http://localhost:631/](http://localhost:631/)

The select Administration tab

Give your standard login/password if requested by CUPS

---

### Post by gman2 on 2009-10-31
Tried the cups interface at localhost:631, same issues.

I shoudl have provided more information. I'm connecting to the printer via the wireless network. Like I said works in PCLinuxOS (and Mandriva) without issue. When I try to add the printer in Ubuntu, the network is browsed and I get three choices with the following connection information:

dnssd://Brother%20MFC-490CW._pdl-datastream._tcp.local/
lpd://BRW00234D47B313/BINARY_P1
dnssd://Brother%20MFC-490CW._printer._tcp.local/

At no time do I get a printer listed as socket://192.168.2.2:9100 or does the IP address get found like I do in Mandriva and PCLinuxOS. SO I add the printer manually using socket://192.168.2.2:9100, but no go. I'm wondering if it is a firewall issue, but I can;t finds any security settings to work with. This is a shame because otherwise I really like Ubuntu 9.10. but without printing the OS is useless.

---

### Post by grandtoubab on 2009-10-31
[http://www.cups.org/doc-1.1/sam.html](http://www.cups.org/doc-1.1/sam.html)

Look[ **B -  Common Network Settings**]("http://www.cups.org/doc-1.1/sam.html#COMMON_NETWORK")

---

### Post by gman2 on 2009-11-01
Wasn't an issue with Ubuntu. My printer had become disconnected from the wireless network. This happened about three months ago. I had to power down and unplug the printer, than plug back in and power up. Once I did that it reconnected to the network. 

But I did discover that Ubuntu did not automatically find the printer on the network. For the device URI I had to manually add the printer via socket://ip:9100. Once I did that things worked fine from there.

I can say that as someone who was never a real big fan of Ubuntu, I really like 9.10 and can recommend to friends and family.

---

