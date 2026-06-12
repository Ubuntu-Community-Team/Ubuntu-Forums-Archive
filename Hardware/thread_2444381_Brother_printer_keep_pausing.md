---
title: "Brother printer keep pausing"
date: 2020-05-29
forum: Hardware
---

### Post by e10310 on 2020-05-29
Hello folks.
I cannot find the right solution for me after a few hours of search.
Ubuntu 20.04 recently upgraded.
My printer is a Brother HL-L2350DW brand new.

I installed the drivers as showed on [the Brother Support page]("https://support.brother.com/g/b/downloadhowto.aspx?c=au&lang=en&prod=hll2365dw_eu_as&os=128&dlid=dlf101917_000&flang=4&type3=561").

When I launch a print job or test job from the printer's settings, it seems to start but get stucked. Printer's Settings shows that "Active" is uncheck.
If I check it, it turns on but next print job, gets inactive again.

What I get from [HTML]dpkg  -l  |  grep  Brother[/HTML]
[HTML]ii  brgenml1cupswrapper:i386                   3.1.0-1                               i386         Brother BrGenML1 CUPS wrapper driver
ii  brgenml1lpr:i386                           3.1.0-1                               i386         Brother BrGenML1 LPR driver
ii  hll2350dwpdrv:i386                         4.0.0-1                               i386         Brother HL-L2350DW printer driver (lpd/cups)
ii  hll2360dcupswrapper:i386                   3.2.0-1                               i386         Brother HL-L2360D CUPS wrapper driver
ii  hll2360dlpr:i386                           3.2.0-1                               i386         Brother HL-L2360D LPR driver
ii  mfcj680dwlpr:i386                          1.0.0-0                               i386         Brother inkjet lpr printer Driver 
ii  printer-driver-brlaser                     6-1build1                             amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                      1.4.2-3                               amd64        printer driver Brother P-touch label printers[/HTML]


Please help![FONT=Verdana]
[/FONT]

---

### Post by oldfred on 2020-05-29
I just installed a 2390 and have no issues.
fred@Z170N-focal:~$ lpstat -l -e
Brother_HL_L2390DW network none ipp://Brother%20HL-L2390DW._ipp._tcp.local/
HL_L2390DW network none ipp://HL-L2390DW._ipp._tcp.local/

You should not have to install drivers and would not want 32 bit drivers. (i386). Or is this an old 32 bit install?

Ubuntu now uses Airprint, so everything is supposed to be automatic and for me it was. As soon as I plugged it in, it worked.
I did not test scanning until after I set up Wi-Fi, so not sure if scan is using USB or Wi-Fi.

WiFi Brother Print
[https://help.brother-usa.com/app/answers/detail/a_id/166020/~/connect-to-a-wireless-network---linux](https://help.brother-usa.com/app/answers/detail/a_id/166020/~/connect-to-a-wireless-network---linux)
scan issues 2395
[https://ubuntuforums.org/showthread.php?t=2443188](https://ubuntuforums.org/showthread.php?t=2443188)

```
fred@Z170N-focal:~$ ls /etc/cups/*
/etc/cups/classes.conf       /etc/cups/cups-files.conf  /etc/cups/snmp.conf
/etc/cups/classes.conf.O     /etc/cups/printers.conf    /etc/cups/subscriptions.conf
/etc/cups/cups-browsed.conf  /etc/cups/printers.conf.O  /etc/cups/subscriptions.conf.O
/etc/cups/cupsd.conf         /etc/cups/raw.convs
/etc/cups/cupsd.conf.O       /etc/cups/raw.types

/etc/cups/interfaces:

/etc/cups/ppd:
Brother_HL_L2390DW.ppd  HL_L2390DW.ppd
```

I think as soon as I turned on printer it added the ppd files.

---

### Post by e10310 on 2020-06-09
.

---

### Post by slickymaster on 2020-06-09
*Thread moved to **Hardware**.*

---

### Post by e10310 on 2020-06-09
Okay I found this way:

[FONT=Arial]Commands:[/FONT]
```
[FONT=Consolas]sudo mv /var/lib/dpkg/info/brgenml1lpr.* /tmp/
sudo mv /var/lib/dpkg/info/hll2360dlpr.* /tmp/
sudo mv /var/lib/dpkg/info/mfcj680dwlpr.* /tmp/[/FONT]
```
[FONT=Arial]Then[/FONT]
```
[FONT=Consolas]sudo dpkg --remove --force-remove-reinstreq brgenml1lpr
sudo dpkg --remove --force-remove-reinstreq hll2360dlpr
sudo dpkg --remove --force-remove-reinstreq mfcj680dwlpr[/FONT]
```
And all drivers are gone. Now time to reinstall the printer.

---

### Post by e10310 on 2020-06-09
Okay... tried to install and I get at the same place: I have 2 printers listed, not one works. A page test or document get stucked and the printer dont't come out of sleep.

[ATTACH=CONFIG]286169[/ATTACH]
Both pictograms indicates they are on a network, which isn't. USB port connected.
In Printer properties, I got this:
**Description:  **Brother HL-L2350DW series (driverless)
**Place:**
**URI device:** ipp://HL-L2350DW%20series._ipp._tcp.local/
**Brand model:** Brother HL-L2350DW series, driverless, cups-filters 1.27.4
**Printer state:** Arrêté (Paused) - Rendering completed

The job's attributes shows: cannot get printer's state:

When I activate it, it send the job showing "Printing" but get stucked again.
I know many have similr problem but I cannot find the answer working for me.

---

### Post by mIk3_08 on 2020-06-09
> **e10310 said:**
> 
When I launch a print job or test job from the printer's settings, it seems to start but get stucked. Printer's Settings shows that "Active" is uncheck.
If I check it, it turns on but next print job, gets inactive again.

Please help![FONT=Verdana]
[/FONT]

Try to check maybe the paper just get stuck or having some jam paper but not totally detected by printer. Just may be.

---

### Post by SeijiSensei on 2020-06-09
Pull out the power cord, wait a few seconds, then reconnect it.  Sometimes helps with my Brother.

---

### Post by e10310 on 2020-06-09
OKAY it works. Seen on this thread (post # 2718): [https://forum.ubuntu-fr.org/viewtopic.p…](https://forum.ubuntu-fr.org/viewtopic.p…) 2931 & p = 109 Delete ippusbxd with:
```
[COLOR=#000000]sudo apt purge ippusbxd[/COLOR]
```
- Then, I removed the installed printers (network and local), 
- disconnected, reconnected the USB cable and installed BUT ... 
- Not from the green **Add ...** button in the printer settings window, but from the long white button below named: **Parameters of additional printers ...**, 
- there it opens the small window **"Printers - localhost"**, add button and there it finds what it needs. 
- In the list, I did not choose "Generic (Recommended)" but in the **Brother** list, I found "**HL-L2350DW (CUPS)"**, and direct the test page prints. 
Now its location is indicated which was not the case before. 
Thanks for the help!

---

### Post by ActionParsnip on 2020-06-09
Could remove the printer, leave the drives installed then access
[http://localhost:631](http://localhost:631)
in your favourite web browser, add the printer there
HTH

---

