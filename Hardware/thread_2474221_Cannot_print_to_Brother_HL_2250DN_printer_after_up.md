---
title: "Cannot print to Brother HL 2250DN printer after upgrade to 22.04"
date: 2022-04-24
forum: Hardware
---

### Post by cookieninja22 on 2022-04-24
Anyone else get this issue?

Printer can be seen using all the troubleshooting commands I tried like:

  sudo /usr/lib/cups/backend/dnssd
  /usr/lib/cups/backend/snmp  192.168.0.5
  lpinfo -v
  avahi-browse -a -v -t -r
  avahi-browse -a -v -c -r

Just that in the CUPs brother admin interface I see one of these errors depending how driver set up
Processing - "The printer may not exist or is unavailable at this time."
Processing - "Unable to locate printer "BRN001BA9C651EA"."

Worked fine in previous LTS version and still does using Windows 10
Official drivers from Brother installed, in case anyone asks about that. I'd expect they're provided now as part of OS install given age of printer but have to try everything and make sure!

Any ideas what to do?

---

### Post by him610 on 2022-04-24
Well, I had not downloaded and installed the Brother software for my MFC-7360N; however, after reading your post, I decided I would. I just successfully installed the Brother software on Xubuntu 22.04 machine. 
Scans too. I will install the send-receive fax capability later.

From the information you have provided, it seems (IMOH) that the Brother software was improperly installed. 
The Brother Driver Install Tool works very well, provided, the installation procedures are followed exactly. 
The tool can be found here, [https://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=hl2250dn_eu_as&os=128]("https://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=hl2250dn_eu_as&os=128")
Be sure to follow the sequential procedural steps to install.

---

### Post by cookieninja22 on 2022-04-24
> **him610 said:**
> Well, I had not downloaded and installed the Brother software for my MFC-7360N; however, after reading your post, I decided I would. I just successfully installed the Brother software on Xubuntu 22.04 machine. 
Scans too. I will install the send-receive fax capability later.

From the information you have provided, it seems (IMOH) that the Brother software was improperly installed. 
The Brother Driver Install Tool works very well, provided, the installation procedures are followed exactly. 
The tool can be found here, [https://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=hl2250dn_eu_as&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=hl2250dn_eu_as&os=128)
Be sure to follow the sequential procedural steps to install.

That's not the problem, it was installed fine and in any case was probably not needed. I've had this printer for over a decade now and set it up many times without a problem.

So, this issue is specific to Ubuntu. Comparing with a different flavour of Ubuntu and a different printer which uses different drivers isn't really an apples for apples comparison

---

### Post by brian_p on 2022-04-24
> **cookieninja22 said:**
> Anyone else get this issue?

Printer can be seen using all the troubleshooting commands I tried like:

  sudo /usr/lib/cups/backend/dnssd
  /usr/lib/cups/backend/snmp  192.168.0.5
  lpinfo -v
  avahi-browse -a -v -t -r
  avahi-browse -a -v -c -r


We would like to see what you see. Could that possibly be arranged?

---

### Post by him610 on 2022-04-25
CUPS versions did change from 20.04 to 22.04
LTS 20.04 cups version
```
$ dpkg -l cups
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version          Architecture Description
+++-==============-================-============-===================================================================
ii  cups           2.3.1-9ubuntu1.1 amd64        Common UNIX Printing System(tm) - PPD/driver support, web interface

```
LTS 22.04 cups version
```
 $ dpkg -l cups
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version           Architecture Description
+++-==============-=================-============-===================================================================
ii  cups           2.4.1op1-1ubuntu4 amd64        Common UNIX Printing System(tm) - PPD/driver support, web interface

```
This information from Brother webpage, [https://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=hl2250dn_eu_as&os=128]("https://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=hl2250dn_eu_as&os=128")
> Brother HL-2250DN Driver Install Tool 19/08/2021 (2.2.3-1)
So, it was updated about 8 months ago.

Maybe you have a legitimate bug; you should submit a discrepancy report.

---

### Post by brian_p on 2022-04-26
> **cookieninja22 said:**
> That's not the problem, it was installed fine and in any case was probably not needed. I've had this printer for over a decade now and set it up many times without a problem.

Into every life a little rain must fall :).

> So, this issue is specific to Ubuntu. Comparing with a different flavour of Ubuntu and a different printer which uses different drivers isn't really an apples for apples comparison

Not at all; it is specific to you. I downloaded and installed two Brother packages and haven't any problem printing with them.

---

### Post by cookieninja22 on 2022-04-29
> **brian_p said:**
> Into every life a little rain must fall :).



Not at all; it is specific to you. I downloaded and installed two Brother packages and haven't any problem printing with them.


So you use different drivers for a different printer and you think what we are doing and the end result should be exactly the same? 

It's like saying an issue I am experiencing with Chrome is down to my installation because you're doing just fine with Firefox. That would be comical if it wasn't an actual real problem for me.

---

### Post by brian_p on 2022-04-29
> **cookieninja22 said:**
> So you use different drivers for a different printer and you think what we are doing and the end result should be exactly the same? 

It's like saying an issue I am experiencing with Chrome is down to my installation because you're doing just fine with Firefox. That would be comical if it wasn't an actual real problem for me.

The two Brother driver packages I used were for the Brother HL 2250DN printe. In other words, I used what you did. I probably did not write as clearly as I should have.

---

