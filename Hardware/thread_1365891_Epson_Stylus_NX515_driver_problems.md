---
title: "Epson Stylus NX515 driver problems"
date: 2009-12-27
forum: Hardware
---

### Post by tlroche on 2009-12-27
summary: I'd appreciate help installing a driver for my Epson Stylus NX515 inkjet all-in-one onto jaunty boxes.

details:

newbie alert: I have some but not lots experience with linux desktops. (I have lots more experience with cygwin and with CLI access to linux servers.)

I have an Epson Stylus NX515 printer/scanner/copier that works fine under winxp sp3. I have a System76 jaunty laptop

```
$ uname -srvmo
Linux 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009 x86_64 GNU/Linux
```

and my GF has a System76 jaunty UNR netbook

```
$ uname -srvmo
Linux 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686 GNU/Linux
```

on which I'm trying to install a driver for the NX515, but I'm having problems with the architectures and dependencies. There is an i386 (only) driver and PPD for the NX515 @

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do")

and instructions @

[http://linux.avasys.jp/drivers/pipslite/doc/ppd-001/Instructions%20on%20use%20of%20PPD%20files.txt]("http://linux.avasys.jp/drivers/pipslite/doc/ppd-001/Instructions%20on%20use%20of%20PPD%20files.txt")

which advises one to

[LIST=1]
[*]download the driver package (pipslite_1.4.0-5_i386.deb) and the PPD (Epson-Stylus_NX515-pipslite-en.ppd). The PPD must be saved to /usr/share/cups/model, so I mkdir-ed that dir and downloaded both the PPD and the deb there.
[*]install the driver. I pushd-ed to/usr/share/cups/model and tried

```
$ dpkg -i pipslite_1.4.0-3_i386.deb
```

which failed due to architecture mismatch, so I tried 

```
$ dpkg -i --force-architecture pipslite_1.4.0-3_i386.deb
```

which told me

```
dpkg: dependency problems prevent configuration of pipslite:
 pipslite depends on libltdl3 (>= 1.5.2-2); however:
 Package libltdl3 is not installed.
```

Naively I tried

```
$ sudo apt-get install libltdl3
```

which said

```
Package libltdl3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libltdl3 has no installation candidate
```

but also broke the software index per Software Update. Per its advice, I ran

```
$ sudo apt-get install -f
```

which removed package=pipslite. I then searched for "libltdl" in
synaptic. I found I already had libltdl7 but not libltdl7-dev, so I
installed the latter, which installed autotools-dev and libtool.
I then reran

```
$ sudo dpkg -i --force-architecture pipslite_1.4.0-5_i386.deb
```

but got the same error regarding libltdl3. 
[/LIST]

So I'm wondering:

[LIST=1]
[*]How to satisfy the Avasys .deb's desire for libltdl3?
[*]Should I try another driver? Epson only provides windows and mac [here]("http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&oid=128289&prodoid=63083693&infoType=Downloads&platform=All"). Avasys also provides .rpm (which I'm not sure how to use under ubuntu) and source (which I could try to configure, make, make install).
[*]Is there another alternative I should attempt?
[/LIST]

---

### Post by utrescu on 2009-12-28
[http://avasys.jp/eng/linux_driver/faq/id000613.php](http://avasys.jp/eng/linux_driver/faq/id000613.php)

---

### Post by SGC622 on 2010-01-14
ha i just bought the same exact printer as you, this is what i did(at least for karmic)

system settings>printer configuration>new printer>new network printer>EPSONxxxxxx(second option)

then select epson from database 
then on the next screen click on stylus nx400
after that you should be good to go, i was 

my apologies if your printer configuration isnt set up the same way i am running kubuntu 9.10
best of luck to you

---

### Post by tlroche on 2010-01-24
Thanks, SGC622, this approach is working on my GF's [starling]("http://system76.com/product_info.php?products_id=92"), after I upgraded to karmic. Pretty nearly the same procedure in UNR karmic as kubuntu karmic:

[LIST=1]
[*]turn on printer, check that it's on local wireless network
[*]System>Administration>Printing>New>Printer>Network Printer>Epson Stylus NX510 (your IP# here), take defaults, Forward
[*]dialog=Choose Driver: Select printer from database>Epson>Stylus NX400
[*]dialog=Describe Printer: take defaults or give shortname, description, location
[*]it offers to print test page: takes quite awhile, but it prints
[/LIST]

I'll still try to
[LIST=1]
[*]assign a stable IP# for the printer, and redo the above for that
[*]install the NX515 PPD from Avasys
[/LIST]
when I get a chance, but this seems to be working for now.

---

### Post by toogooda on 2010-03-16
I have solved this one, it is a two step process.

First get correct Driver for your scanner/printer,
Second get dependancies

To get your scanner and printer working use this site it had mine and many others I was after Epson RX610

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do")

When you try to install you will get a dependency error on a lib called "libltdl3" you will not find this on the repositories anymore but I found the FAQ on the site from the drivers

[http://avasys.jp/eng/linux_driver/faq/id000613.php]("http://avasys.jp/eng/linux_driver/faq/id000613.php")

The instructions tell you to download the dependancy from here


32-Bit =
[http://packages.ubuntu.com/en/hardy/i386/libltdl3/download]("http://packages.ubuntu.com/en/hardy/i386/libltdl3/download")

64-Bit = [http://packages.ubuntu.com/en/hardy/amd64/libltdl3/download]("http://packages.ubuntu.com/en/hardy/amd64/libltdl3/download")

All working in xsane for me now, hope it helps

AT

---

### Post by Apache0c on 2010-05-08
> **toogooda said:**
> I have solved this one, it is a two step process.

First get correct Driver for your scanner/printer,
Second get dependancies

To get your scanner and printer working use this site it had mine and many others I was after Epson RX610

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

When you try to install you will get a dependency error on a lib called "libltdl3" you will not find this on the repositories anymore but I found the FAQ on the site from the drivers

[http://avasys.jp/eng/linux_driver/faq/id000613.php](http://avasys.jp/eng/linux_driver/faq/id000613.php)

The instructions tell you to download the dependancy from here


32-Bit =
[http://packages.ubuntu.com/en/hardy/i386/libltdl3/download](http://packages.ubuntu.com/en/hardy/i386/libltdl3/download)

64-Bit = [http://packages.ubuntu.com/en/hardy/amd64/libltdl3/download](http://packages.ubuntu.com/en/hardy/amd64/libltdl3/download)

All working in xsane for me now, hope it helps

AT
Can you elaborate further on this? I'm running 10.04 now. The printer works across the wireless network and I want the scanner to work also. I looked through those driver pages are there are tons of choices, I'm having a tough time knowing what to pick.

---

### Post by akxiii on 2010-07-05
> **toogooda said:**
> I have solved this one, it is a two step process.

First get correct Driver for your scanner/printer,
Second get dependancies

To get your scanner and printer working use this site it had mine and many others I was after Epson RX610

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do")

When you try to install you will get a dependency error on a lib called "libltdl3" you will not find this on the repositories anymore but I found the FAQ on the site from the drivers

[http://avasys.jp/eng/linux_driver/faq/id000613.php]("http://avasys.jp/eng/linux_driver/faq/id000613.php")

The instructions tell you to download the dependancy from here


32-Bit =
[http://packages.ubuntu.com/en/hardy/i386/libltdl3/download]("http://packages.ubuntu.com/en/hardy/i386/libltdl3/download")

64-Bit = [http://packages.ubuntu.com/en/hardy/amd64/libltdl3/download]("http://packages.ubuntu.com/en/hardy/amd64/libltdl3/download")

All working in xsane for me now, hope it helps

AT


Does this work over wireless or just wired?
Thanks for your help

---

### Post by toogooda on 2010-07-13
Sorry just usb not wireless, can't really see why you would scan wireless?after all you have to be at the scanner to put something on it to scan?

Sorry can't help you

---

