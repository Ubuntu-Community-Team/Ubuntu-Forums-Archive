---
title: "Epson Perfection 4990 Photo and Hoary"
date: 2005-09-14
forum: Hardware &amp; Laptops
---

### Post by etitor on 2005-09-14
OK, so this beast sits now on my desktop. And I **have** to use it. Is this guy going to be my return path to Windows?

I run Hoary 64 on an AMD K8.

For background information about Epson 4990 and Linux (abstract: Epson 4990 **does** work under Linux) you can see this:
[INDENT][http://lists.alioth.debian.org/pipermail/sane-devel/2005-June/013814.html](http://lists.alioth.debian.org/pipermail/sane-devel/2005-June/013814.html)[/INDENT]

and this:[INDENT][http://lists.alioth.debian.org/pipermail/sane-devel/2005-May/013674.html](http://lists.alioth.debian.org/pipermail/sane-devel/2005-May/013674.html)[/INDENT]

The 4990 may be too new to be known to Sane and it is **not** in the directly-supported scanners list: [INDENT][www.sane-project.org/sane-mfgs.html#Z-EPSON](www.sane-project.org/sane-mfgs.html#Z-EPSON)[/INDENT]

But Sane seems to support the 4990 through one of its external backends, epkowa. See:
[INDENT][www.sane-project.org/lists/sane-backends-external.html#S-EPKOWA](www.sane-project.org/lists/sane-backends-external.html#S-EPKOWA)[/INDENT] 

Once the scanner is connected,

lsusb says:
[INDENT]**Bus 003 Device 002: ID 04b8:012a Seiko Epson Corp.**
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000[/INDENT]
So I know the USB system knows the scanner is there.

scanimage -L says:

[INDENT]No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
[/INDENT]
sane-find-scanner says:

[INDENT]  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

**found USB scanner (vendor=0x04b8, product=0x012a) at libusb:003:002**
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.[/INDENT]
cat /proc/bus/usb/devices says (among other things):
[INDENT]T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=04b8 ProdID=012a Rev= 1.00
S:  Manufacturer=EPSON
S:  Product=EPSON Scanner
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
[/INDENT]
I know Vuescan supports the 4990:
[INDENT][www.hamrick.com/vuescan/vuescan.htm#epson](www.hamrick.com/vuescan/vuescan.htm#epson)[/INDENT]
So I downloaded Vuescan but it won't run. It says:
[INDENT]error while loading shared libraries: libusb-0.1.so.4: cannot open shared object file: No such file or directory[/INDENT] 
And XSane (v0.96) refuses to detect it ("No devices found").

Can you guys advise anything, or is it the dual-boot way only?

---

### Post by etitor on 2005-09-21
OK I solved it myself.

I opened /etc/sane.d/epson.conf and added this line:

[INDENT]usb 0x4b8 0x12a[/INDENT]

(I had previously omitted the "x" on that numbers), and I opened /etc/sane.d/snapscan.conf and uncommented this line:

[INDENT]/dev/usb/scanner0 bus=usb[/INDENT]

Presto! Scanimage -L now says:
[INDENT]device `epson:libusb:003:004' is a Epson GT-X800 flatbed scanner
[/INDENT]

And XSane works ok.

Hope someone cares.

---

### Post by lompolo on 2005-11-30
> Hope someone cares.
Thanks it helped

I got Epson Perfection 3490 working with Vuescan.

sane-find-scanner says: 
found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:005:002

scanimage -L doesn't find scanner

xsane doesn't find scanner :( 

What next? modules or /etc/sane.d/epkowa.conf or something else? 
> Hope someone cares.
Thanks it helped

I got Epson Perfection 3490 working with Vuescan.

sane-find-scanner says: 
found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:005:002

scanimage -L doesn't find scanner

xsane doesn't find scanner :( 

What next? modules or /etc/sane.d/epkowa.conf or something else?

---

### Post by arphe_el on 2005-12-05
any help the xsane does not recognize hp scanjet 2400

here are my questions:

1. what are the step by step procedure to make this thing work to xsane?
2. if xsane does not support this hardware what are the alternative?
3. is there other software that supports hp scanjet 2400 aside from xsane?
4. is there a command line that i can use to make scanner works?

Thank you and hope to hear from all of you. GODspeed!

---

### Post by lompolo on 2005-12-06
So because I am not only one fighting with this. I tried some new things.

(added to /etc/sane.d/dll.conf line epkowa) 
added to /etc/sane.d/epkowa.conf /proc/bus/usb/005/003 because I thought it might be device file. Any comments about this is welcome.

xsane gives error: Failed to obtain value of option monitor button: Device is busy

---

