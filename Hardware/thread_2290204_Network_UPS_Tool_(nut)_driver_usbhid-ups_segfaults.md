---
title: "Network UPS Tool (nut) driver usbhid-ups segfaults with libusb / libc on 14.04.3 LTS"
date: 2015-08-10
forum: Hardware
---

### Post by davis5 on 2015-08-10
I'm installing and hoping to configure NUT on a remote machine attached to an APC UPS CS-210 via USB.
I've aptitude updated (everything) and installed NUT:

```
root@barnbox:~# dpkg -l nut-\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                             Version               Architecture          Description
+++-================================-=====================-=====================-=====================================================================
ii  nut-cgi                          2.7.1-1ubuntu1        amd64                 network UPS tools - web interface
ii  nut-client                       2.7.1-1ubuntu1        amd64                 network UPS tools - clients
un  nut-hal-drivers                  <none>                <none>                (no description available)
un  nut-ipmi                         <none>                <none>                (no description available)
un  nut-monitor                      <none>                <none>                (no description available)
ii  nut-server                       2.7.1-1ubuntu1        amd64                 network UPS tools - core system
un  nut-snmp                         <none>                <none>                (no description available)
un  nut-xml                          <none>                <none>                (no description available)
```


I've done the very basic-level config of the UPS driver as hinted at here: [http://www.networkupstools.org/docs/man/usbhid-ups.html](http://www.networkupstools.org/docs/man/usbhid-ups.html)

```
root@barnbox:~# tail -n 7 /etc/nut/ups.conf


[apc]
        driver = usbhid-ups
        port = auto
        desc = "APC Back-UPS"
    bus="001" # these lines make no difference to the outcome
    vendor="051d"
```

Now, although I can start nut, it can't connect to the usbhid-ups driver, and I get this error in dmesg:

```
[ 2128.229552] usbhid-ups[3003]: segfault at 0 ip 00007fd96720e48c sp 00007ffcaa1e0b78 error 4 in libc-2.19.so[7fd9670cd000+1bb000]

```

In case it's useful, I have these versions of libusb installed:


```
root@barnbox:~# dpkg -l libusb\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                             Version               Architecture          Description
+++-================================-=====================-=====================-=====================================================================
ii  libusb-0.1-4:amd64               2:0.1.12-23.3ubuntu1  amd64                 userspace USB programming library
ii  libusb-1.0-0:amd64               2:1.0.17-1ubuntu2     amd64                 userspace USB programming library
un  libusb0                          <none>                <none>                (no description available)
ii  libusbmuxd2                      1.0.8-2ubuntu1        amd64                 USB multiplexor daemon for iPhone and iPod Touch devices - library


```
and my system version is:

```
 root@barnbox:~# lsb_release -a ; uname -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
Linux barnbox 3.13.0-61-generic #100-Ubuntu SMP Wed Jul 29 11:21:34 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

My aim is to get this machine communicating successfully with the UPS, and shutting down on power failure. However, I can't even communicate with the UPS:

```
root@barnbox:~# upsc apc
Init SSL without certificate database
Error: Driver not connected

```
Does anyone know why or how to start fixing this?

Thanks

USB listing and the results of running the driver manually:

```
root@barnbox:~# lsusb && /lib/nut/usbhid-ups -u nut -a apc -x bus=001 -x vendorid=051d -x productid=0002 -DDDD
Bus 002 Device 004: ID 0424:4030 Standard Microsystems Corp. 
Bus 002 Device 003: ID 0424:2660 Standard Microsystems Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Network UPS Tools - Generic HID driver 0.38 (2.7.1)
USB communication driver 0.32
   0.000000    debug level is '4'
   0.000438    upsdrv_initups...
   0.030198    Checking device (1D6B/0003) (005/001)
   0.030470    - VendorID: 1d6b
   0.030485    - ProductID: 0003
   0.030497    - Manufacturer: unknown
   0.030508    - Product: unknown
   0.030518    - Serial Number: unknown
   0.030529    - Bus: 005
   0.030539    Trying to match device
   0.030558    Device does not match - skipping
   0.030688    Checking device (1D6B/0002) (004/001)
   0.030817    - VendorID: 1d6b
   0.030834    - ProductID: 0002
   0.030845    - Manufacturer: unknown
   0.030857    - Product: unknown
   0.030868    - Serial Number: unknown
   0.030879    - Bus: 004
   0.030889    Trying to match device
   0.030902    Device does not match - skipping
   0.030935    Checking device (1D6B/0001) (003/001)
   0.054114    - VendorID: 1d6b
   0.054183    - ProductID: 0001
   0.054195    - Manufacturer: unknown
   0.054206    - Product: unknown
   0.054217    - Serial Number: unknown
   0.054228    - Bus: 003
   0.054239    Trying to match device
   0.054256    Device does not match - skipping
   0.062061    Checking device (0424/4030) (002/004)
   0.062107    - VendorID: 0424
   0.062120    - ProductID: 4030
   0.062132    - Manufacturer: unknown
   0.062143    - Product: unknown
   0.062154    - Serial Number: unknown
   0.062164    - Bus: 002
   0.062175    Trying to match device
   0.062187    Device does not match - skipping
   0.062201    Checking device (0424/2660) (002/003)
   0.062218    - VendorID: 0424
   0.062230    - ProductID: 2660
   0.062240    - Manufacturer: unknown
   0.062251    - Product: unknown
   0.062261    - Serial Number: unknown
   0.062272    - Bus: 002
   0.062282    Trying to match device
   0.062293    Device does not match - skipping
   0.062307    Checking device (8087/0024) (002/002)
   0.062323    - VendorID: 8087
   0.062336    - ProductID: 0024
   0.062346    - Manufacturer: unknown
   0.062357    - Product: unknown
   0.062367    - Serial Number: unknown
   0.062378    - Bus: 002
   0.062388    Trying to match device
   0.062399    Device does not match - skipping
   0.062418    Checking device (1D6B/0002) (002/001)
   0.062437    - VendorID: 1d6b
   0.062450    - ProductID: 0002
   0.062461    - Manufacturer: unknown
   0.062472    - Product: unknown
   0.062483    - Serial Number: unknown
   0.062493    - Bus: 002
   0.062503    Trying to match device
   0.062515    Device does not match - skipping
   0.062528    Checking device (051D/0002) (001/003)
   0.062547    - VendorID: 051d
   0.062559    - ProductID: 0002
   0.062570    - Manufacturer: unknown
   0.062580    - Product: unknown
   0.062591    - Serial Number: unknown
   0.062601    - Bus: 001
   0.062612    Trying to match device
Segmentation fault (core dumped)
root@barnbox:~# 
```

---

