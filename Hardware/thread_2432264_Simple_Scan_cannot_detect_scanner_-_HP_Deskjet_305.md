---
title: "Simple Scan cannot detect scanner - HP Deskjet 3050A"
date: 2019-11-29
forum: Hardware
---

### Post by kkelly77 on 2019-11-29
Hi Everyone,

I'm am using Simple Scan to connect to my 3 in 1 HP Deskjet 3050A (Printer, Scanner, Copier). However, I can't scan using Simple Scan or Xsane. I am getting a "No Scanner Detected" message. Both the printing and copy features are working fine.

Scanning did work before, with a previous printer I had of the exact same make and model. But ever since I got the replacement printer, I cannot get it to scan. 

I am using Ubuntu 18.04 LTS.

If anyone can help, I would really appreciate it. Thank you.

---

### Post by brian_p on 2019-11-29
A USB or network connection?

Post the output of ```
lpstat -t
```

---

### Post by kkelly77 on 2019-11-29
Wireless connection

```
scheduler is running
no system default destination
lpstat: No destinations added.
lpstat: No destinations added.
lpstat: No destinations added.
lpstat: No destinations added.

```

---

### Post by brian_p on 2019-11-29
> **kkelly77 said:**
> Wireless connection

```
scheduler is running
no system default destination
lpstat: No destinations added.
lpstat: No destinations added.
lpstat: No destinations added.
lpstat: No destinations added.

```

According to this there are no USB or network connected printers set up. You said

> Both the printing and copy features are working fine

I cannot see how printing could possibly be working, never mind scanning. See the manual for lpstat to understand the point I am making.

---

### Post by ajgreeny on 2019-11-29
I always used to have to add a wifi printer/scanner using the hplip-gui, first giving the printer a static IP, possibly easiest with a reserved address on the router setup, then adding the IP manually in the setup dialogues, though in most recent systems the printer/scanner has been found and can be used without me doing anything.

As the new printer/scanner is the same as the previous one I wonder if it has a new IP but the system is still looking for the old IP which is now empty, though that seems unlikely as you are able to print.

---

### Post by brian_p on 2019-11-29
I said

> I cannot see how printing could possibly be working,...

You never said whether you were on USB or on the network. Give us ```
lpinfo -v
```

---

### Post by kkelly77 on 2019-11-29
I wasn't connected to my internal network which the printer is on.

```
scheduler is running
system default destination: HP-Deskjet-3050A-J611-series
device for HP-Deskjet-3050A-J611-series: hp:/net/Deskjet_3050A_J611_series?hostname=Huawei-HG658c-i.local
HP-Deskjet-3050A-J611-series accepting requests since Fri 29 Nov 2019 20:39:51 GMT
printer HP-Deskjet-3050A-J611-series is idle.  enabled since Fri 29 Nov 2019 20:39:51 GMT

```

However, I have now got the scanner working :confused::confused::rolleyes::rolleyes:. After so long of NOT having the scanner working. I'm not even 100% sure how I did it.

I could see the printer listed under Settings>Devices>Printers
I was trying to print to it so I could get relevant details using lpstat in Temrinal
Printer wouldn't print and was displaying an exclamation symbol on the printer icon (!)
I right clicked on it to get into Properties
The printer icon disappeared :confused::confused::confused:
I clicked on Add and could see the printer name listed Network Printer
When this completed, there were now 2 printers listed under Settings>Devices>Printers. The "new" printer was set as default
I opened Simple Scan AND IT WORKED!!!!
I deleted the "old" printer listed.

Bear in mind, when this problem first occurred, I tried to remove and add the printer again, which did not fix it. I have no idea why this worked.

---

### Post by brian_p on 2019-11-29
> **kkelly77 said:**
> I wasn't connected to my internal network which the printer is on.

```
scheduler is running
system default destination: HP-Deskjet-3050A-J611-series
device for HP-Deskjet-3050A-J611-series: hp:/net/Deskjet_3050A_J611_series?hostname=Huawei-HG658c-i.local
HP-Deskjet-3050A-J611-series accepting requests since Fri 29 Nov 2019 20:39:51 GMT
printer HP-Deskjet-3050A-J611-series is idle.  enabled since Fri 29 Nov 2019 20:39:51 GMT

```

That looks exactly as one would expect.

> 
However, I have now got the scanner working :confused::confused::rolleyes::rolleyes:. After so long of NOT having the scanner working. I'm not even 100% sure how I did it.

Your perseverance is commendable. Thanks for listening.

---

### Post by krist-poffyn on 2020-09-03
Similar problem here:

krist@krist-MS-16Y1:~$ lpstat -t
scheduler is running
no system default destination
device for CUPS-BRF-Printer: cups-brf:/
device for HPDeskjet3635: ipp://HP99D3C4/ipp/
CUPS-BRF-Printer accepting requests since zo 30 aug 2020 19:14:52
HPDeskjet3635 accepting requests since vr 04 sep 2020 00:03:52
printer CUPS-BRF-Printer is idle.  enabled since zo 30 aug 2020 19:14:52
printer HPDeskjet3635 now printing HPDeskjet3635-44.  enabled since vr 04 sep 2020 00:03:52
    Unable to locate printer "HP99D3C4".
HPDeskjet3635-44        krist            47104   vr 04 sep 2020 00:03:52
HPDeskjet3635-45        krist             1024   vr 04 sep 2020 00:05:11
krist@krist-MS-16Y1:~$

---

