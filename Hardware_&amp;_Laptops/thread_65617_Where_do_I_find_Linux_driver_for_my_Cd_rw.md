---
title: "Where do I find Linux driver for my Cd rw?????"
date: 2005-09-14
forum: Hardware &amp; Laptops
---

### Post by sunshine82 on 2005-09-14
have a sony cd -rw crx140e  and I need a driver for it. I have checked the samsung website there is only dos and windows format. Does anyne know where I can get the driver Please help.....

---

### Post by Juergen on 2005-09-14
'Drivers' are Kernel modules, and especially IDE-drives are supported out of the box.
So you don't need a 'driver' I think

You should rather explain what goes wrong and post some error messages here.

Open an xterm and type 
```
dmesg | grep -i sony
cdrecord -scanbus -dev=ATAPI'
```and show the output here.

---

### Post by sunshine82 on 2005-09-25
I have attach the dmesg result and this is the cdrecord scanbus:

drecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-9-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

---

### Post by Juergen on 2005-09-27
The /dev/pg* cdrecord tries to open are for ATAPI over parallel port.
I don't know why it chose this, did you append the '-dev=ATAPI'?
If not, try again.

In dmesg the interesting lines are somehow scrolled out.
I just wanted to know if you have something like (for me)
> hdc: SAMSUNG CDRW/DVD SM-352B, ATAPI CD/DVD-ROM drive
hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache

But all those lines with
> hdc: command error: status=0x51 { DriveReady SeekComplete Error }are a bit irritating. 
Do you know where they might come from?

---

### Post by sunshine82 on 2005-09-27
I'n new to it all I dont know where anything come from sorry

---

### Post by Juergen on 2005-09-28
Beeing new is something we all have experienced, no need to be sorry ;-)
But it is very unusual that a simple IDE CD burner doesn't work (it is an internal drive, isn't it?)
Did you really do
```
sudo cdrecord -scanbus -dev=ATAPI
```
with '-dev=ATAPI'? (did I forget the 'sudo'? Shame on me - it might be needed)
Your burner is the first device on the 2nd IDE-cable, right?
If so, what's the output of
```
grep -i hdc /var/log/messages
```?
If that's empty, try
```
grep -i hdc /var/log/messages.0
```
And if it's repeating just cut out one part of it.
And if it is the 2nd drive on the 2nd cable replace hdc with hdd - see a system? ;-)

---

