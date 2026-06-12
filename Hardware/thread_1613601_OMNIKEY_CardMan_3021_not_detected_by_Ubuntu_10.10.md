---
title: "OMNIKEY CardMan 3021 not detected by Ubuntu 10.10"
date: 2010-11-04
forum: Hardware
---

### Post by dotchev on 2010-11-04
Hi,

I use a digital signature on a smart card. I use USB card reader OMNIKEY CardMan 3021.
Ubuntu does not detect the card reader when I plug it in the USB. I have to reboot or restart pcscd to use the smart card.

```

peter@doma:~$ opensc-tool -l
[opensc-tool] reader-pcsc.c:896:pcsc_detect_readers: SCardListReaders failed: 0x8010002e
[opensc-tool] reader-pcsc.c:1015:pcsc_detect_readers: returning with: No readers found
No smart card readers found.
peter@doma:~$ sudo pcscd -H
[sudo] password for peter: 
peter@doma:~$ opensc-tool -l
Readers known about:
Nr.    Driver     Name
0      pcsc       OMNIKEY CardMan 3x21 00 00

```There is no such issue on Windows.
I had the same issue occasionally on Ubuntu 10.04, but now with 10.10 I encounter it every time I plug the card reader.

Any ideas how to solve this?

Best regards,
Peter

---

### Post by martinpaljak on 2010-11-14
> **dotchev said:**
> Hi,

```

0      pcsc       OMNIKEY CardMan 3x21 00 00

```There is no such issue on Windows.

The reader name suggests that you have downloaded proprietary Omnikey driver.
Remove it. The Open Source CCID driver (apt-get install libccid)  (which displays names like "OmniKey CardMan 3021") works flawlessly with your reader and its use is encouraged.

Comparison to Windows does not make much sense here, pcsc-lite does not work on Windows.

---

### Post by Man Eating Duck on 2011-03-02
I know this thread is old, but I got it to work with an online java-based authentication service in Firefox by installing the following packages:
```
sudo apt-get install libpcsclite-dev pcsc-tools sun-java6-plugin libpcsclite1 pcscd libccid 
```

Just thought I'd throw it up here in case anyone arrives from Google, as I did.

---

### Post by tester100 on 2011-11-28
Hi guys

i have a simillar problem or maybe not it might even be the UDEV in ubuntu.


So here is the deal

i have 1 card reader omnikey3021 i have installed all the necessary drivers


apt-get install libpcsclite1
apt-get install libpcsclite-dev
apt-get install pcscd
apt-get install pcsc-tools


ok so first things first after installed drivers i do a pcsc_scan  to scan the correct id picked up from the device.

in my case Device 0 

i added another reader omnikey for testings and it picked up device 1 for the next reader


i runned the proggy that i needed to run on it and it runs fine in single mode with 1 card or with 2 readers ON.

Problem is sometimes it loses conection i get erros on the log

and when i make a new pscs_scan via telnet i get the information no pcsc scard connected or  scard disconnected...

so i unplug readers from USB wait couple of seconds and plug them back on and some times it detects back the PCSC card inserted again , but most times it does not detect.

So eventually i end up myself having to restart the pcscd via telnet

sudo /etc/init.d/pcscd restart , in order to detect readers again...

As anyone else had this problem, it seems to be happening only if i leave the readers plugged in for several days in the machine.

If u reboot the machine everyday etc.. it does not do that.

Any hints guys on how to solve this mystery?

Could it be related to the UDEV how does it work? 

Also how can i put this device id drivers fixed, because sometimes when it detects the readers it detects them with IDs inverted.

and it messes up my system configuration.


i am running ubuntu-server10.04

---

