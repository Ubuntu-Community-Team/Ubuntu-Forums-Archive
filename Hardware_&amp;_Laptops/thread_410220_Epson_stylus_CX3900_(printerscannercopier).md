---
title: "Epson stylus CX3900 (printer/scanner/copier)"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by Neuralgia on 2007-04-15
Hi,

I own an Epson Stylus CX3900. Prints, scans, copies.

My Edgy detects it as cx3900, and with the cx3810 driver I can print, but CAN'T SCAN.

when i use "sane-find-scanner" I get this:

[B]
found USB scanner (vendor=0x04b8 [EPSON], product=0x082f [USB MFP]) at libusb:003:002
# Your USB scanner was (probably) detected. It may or may not be supported by
# SANE. Try scanimage -L and read the backend's manpage.[/B]

I modified the epson.conf, and finally get it like thislike this:

[B]# epson.conf
#
# here are some examples for how to configure the EPSON backend
#
# SCSI scanner:
scsi EPSON
# for the GT-6500:
scsi "EPSON SC"
#
# Parallel port scanner:
#pio 0x278
#pio 0x378
#pio 0x3BC
#
# USB scanner:
# There are two different methods of configuring a USB scanner: libusb and the kernel module
# For any system with libusb support (which is pretty much any recent Linux distribution) the
# following line is sufficient. This however assumes that the connected scanner (or to be more
# accurate, it's device ID) is known to the backend.
usb
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
usb 0x04b8 0x082f
# And for the scanner module, use the following configuration:
#usb /dev/usbscanner0
#usb /dev/usb/scanner0
[/B]

and my  45-libsane.rules is finally like this:

[B]# Epson # Epson CX-3900
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082f", MODE="664", GROUP="scanner"CX-3900
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082f", MODE="664", GROUP="scanner"
[/B]


with all this changes, My Xsane starts my scanner, the optical thing moves, but doesn't throw any image. Just some blurry very B&W kind of thing.

The main problem is that I use a lot my scanner, so I have to boot XP about once or twice a day, and trust me, I hate to do that... i might get a flu or some thing :winK:

any ideas?

---

### Post by ramjet_1953 on 2007-04-16
This link might help to solve your problem:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX3900](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX3900)

Regards,
Roger :cool:

---

### Post by Neuralgia on 2007-04-18
thanks for the help, but now I'm stuck. when I try to install whit through shell, I get this messg:

>  sudo rpm -i iscan-2.6.0-0.c2.i386.rpm
error: Failed dependencies:
        /bin/sh is needed by iscan-2.6.0-0.c2.i386
        libatk-1.0.so.0 is needed by iscan-2.6.0-0.c2.i386
        libc.so.6 is needed by iscan-2.6.0-0.c2.i386
        libc.so.6(GLIBC_2.0) is needed by iscan-2.6.0-0.c2.i386
        libc.so.6(GLIBC_2.1) is needed by iscan-2.6.0-0.c2.i386
        libc.so.6(GLIBC_2.1.3) is needed by iscan-2.6.0-0.c2.i386
        libc.so.6(GLIBC_2.2) is needed by iscan-2.6.0-0.c2.i386
        libc.so.6(GLIBC_2.3) is needed by iscan-2.6.0-0.c2.i386
        libc.so.6(GLIBC_2.3.4) is needed by iscan-2.6.0-0.c2.i386
        libdl.so.2 is needed by iscan-2.6.0-0.c2.i386
        libdl.so.2(GLIBC_2.0) is needed by iscan-2.6.0-0.c2.i386
        libdl.so.2(GLIBC_2.1) is needed by iscan-2.6.0-0.c2.i386
        libgcc_s.so.1 is needed by iscan-2.6.0-0.c2.i386
        libgcc_s.so.1(GCC_3.0) is needed by iscan-2.6.0-0.c2.i386
        libgdk-x11-2.0.so.0 is needed by iscan-2.6.0-0.c2.i386
        libgdk_pixbuf-2.0.so.0 is needed by iscan-2.6.0-0.c2.i386
        libglib-2.0.so.0 is needed by iscan-2.6.0-0.c2.i386
        libgmodule-2.0.so.0 is needed by iscan-2.6.0-0.c2.i386
        libgobject-2.0.so.0 is needed by iscan-2.6.0-0.c2.i386
        libgtk-x11-2.0.so.0 is needed by iscan-2.6.0-0.c2.i386
        libieee1284.so.3 is needed by iscan-2.6.0-0.c2.i386
        libjpeg.so.62 is needed by iscan-2.6.0-0.c2.i386
        libm.so.6 is needed by iscan-2.6.0-0.c2.i386
        libm.so.6(GLIBC_2.0) is needed by iscan-2.6.0-0.c2.i386
        libnsl.so.1 is needed by iscan-2.6.0-0.c2.i386
        libpango-1.0.so.0 is needed by iscan-2.6.0-0.c2.i386
        libpangox-1.0.so.0 is needed by iscan-2.6.0-0.c2.i386
        libpangoxft-1.0.so.0 is needed by iscan-2.6.0-0.c2.i386
        libstdc++.so.6 is needed by iscan-2.6.0-0.c2.i386
        libstdc++.so.6(CXXABI_1.3) is needed by iscan-2.6.0-0.c2.i386
        libstdc++.so.6(GLIBCXX_3.4) is needed by iscan-2.6.0-0.c2.i386
        libusb-0.1.so.4 is needed by iscan-2.6.0-0.c2.i386
        sane-backends is needed by iscan-2.6.0-0.c2.i386


None of them seem to be in synaptic... how do I install them ?

---

### Post by rickggreen on 2007-04-18
The line in yor epson.d file is wrong, in the sane folder.

should be

usb 0x4b8 0x818

---

### Post by Neuralgia on 2007-04-19
Actually it was already OK.

I had on the "Type" category, the option "by ext"... not on "jpg" o "png".

Sorry, just changed that and everything was OK.

No need for installing special drivers.

Conclusion: If anyone has the same problem, please, make the changes made on my first post and that's about it. If you need any help, send me a PM, and I'll be glad to help.

Neuralgia

---

### Post by Fenix-TX on 2007-04-20
I have this problem on Festy with my Epson DX5000, was working well on Edgy adding id and vendor on /etc/udev/libsane-extras.rules and /etc/saned.d/epson.conf

I think is a bug on Feisty i can't scan :-(

Solved, commenting all the contents on files hplip and libsane-extras from /etc/saned.d/dll.d/

---

### Post by jjalocha on 2007-05-08
Hi, I'm running Xubuntu Feisty, and this is my very first attempt at installing a printer under Linux. I can't find a printer configuration tool, so i think i will have to do it manually.

When I plug in the CX3900 USB, the following changes are detected:

```

$ lpinfo -v
direct hal:///org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_printer_noserial
direct usb://EPSON/Stylus%20CX3900

```

According to the [CUPS Software Administrators Manual]("http://www.cups.org/doc-1.1/sam.html"), I should add the printer with something which looks like this:

```

$ lpadmin -p DeskJet -E -v parallel:/dev/lp1 -m deskjet.ppd

```

But really I don't know what parameters I should use for this printer...

---

### Post by Neuralgia on 2007-05-08
have you tried the instruction on the first post... worked for me

---

### Post by jjalocha on 2007-05-08
Sorry... I am not yet trying to scan, I am trying to print first.

Since this is my first printer in Linux, I really don't have a clue. The [Xubuntu Desktop Guide]("https://help.ubuntu.com/xubuntu/desktopguide/C/printer-configuration.html") says that I need to add the printer with 'lpadmin', but I don't know what parameters I should use.

---

### Post by jjalocha on 2007-05-09
I am asking for help for the printer setup in the following thread:
[http://ubuntuforums.org/showthread.php?t=438114](http://ubuntuforums.org/showthread.php?t=438114)

---

### Post by Neuralgia on 2007-05-11
in regular Ubuntu, you shoul go to System>Administration>Printing

Add New Printer... choose the Epson Stylus CX3810 driver.

That's about it.

I haven't tried XFCE yet, so no clue about that... yet :P

---

### Post by stevebakerj on 2007-05-11
In terminal find where the scanner is connected:
"sane-find-scanner | grep 0x082f"

* Your result should return something like: 
"found USB scanner (vendor=0x04b8 [EPSON], product=0x082f [USB2.0 MFP(Hi-Speed)]) at libusb:003:002" this last thing is important

enter new command to change mode of the USB port, using the address returned: 
"sudo chmod 0666 /proc/bus/usb/003/002" 
(obviously the 003/002 will depend on what is returned by sane-find-scanner)

You should now be able to run sane and detect the new scanner as a normal user and not have to run as root.

---

### Post by jjalocha on 2007-05-11
stevebakerj, thank you very much for the instructions. I am at home now, but I will try as soon as I get to my office.

Neuralgia, sadly enough, Xubuntu doesn't have such a printer administration tool (yet), but I am using the CUPS web interface now.

---

### Post by Neuralgia on 2007-05-11
sorry about that :(

at least the sane-find-scanner was related :jeje:

---

### Post by jjalocha on 2007-05-14
I just managed to install the **scanner** of Epson Stylus CX3900 under Xubuntu Gutsy with help of all the above postings. This should also work well with previous versions.

Install SANE:

```

$ sudo aptitude update
$ sudo aptitude install xsane sane-utils

```

Identify your scanner:

```

$ sane-find-scanner | grep USB
found USB scanner (vendor=0x04b8, product=0x082f) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by

```

Edit the '/etc/sane.d/epson.conf' file, and add libusb support adding the following line. ('product ID' and 'device ID' taken from 'vendor' and 'product' above):

```

...
# usb <product ID> <device ID>
usb 0x04b8 0x082f
...

```

It is now possible to use the scanner as root. You can test this with 'sudo scanimage -L'.

In order to make the scanner available for all users, you have to add the following rule to the '/etc/udev/rules.d/45-libsane.rules' file:
```

# Epson CX4000 | DX4000 | DX4050
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082f", MODE="664", GROUP="scanner"

```
Add these lines anywhere between the SUBSYSTEM and LABEL tags.

Apply the new rules:
```

$ sudo /etc/init.d/udev restart

```

Make sure that the user is authorized to use the scanner. Check under System > Users and Groups > Properties > User Privileges. The user should belong to the 'scanner' group.

Running 'scanimage -L' as a normal (authorized) user now detects my scanner as DX4000. This seems to be correct, since the [official driver]("http://www.avasys.jp/english/linux_e/dl_spc.html") is both for CX3900 and DX4000.

Run 'xsane' directly, or from the Gimp: File->Acquire->Xsane.

OBSOLETE:
Before I knew how to fix the 'sudo scanimage -L' file, I had to change the write permission of the USB port shown above, in order to use the scanner as a normal user. This could be done manually with:
```

$ sudo chmod 666 /proc/bus/usb/001/003

```


2007-05-15 EDIT: gimp and xsane annded.
2007-12-18 EDIT: /etc/udev/rules.d/45-libsane.rules fix added. Gutsy update.

---

### Post by jjalocha on 2007-05-19
After each restart, the permissions for '[FONT="Fixedsys"]/proc/bus/usb/001/*[/FONT]' are reset to read-only, and my printer shows up under different locations. So I have always to 'chmod' again.

Anyone who understands the basics can provide a permanent fix for this?

---

### Post by jjalocha on 2007-09-06
:confused: bump...

---

### Post by jjalocha on 2007-12-18
Following the instructions in [thread 303593]("http://ubuntuforums.org/showpost.php?p=3594872&postcount=16"), i was finally able to solve the ugly permissions problem, modifying '/etc/udev/rules.d/45-libsane.rules'. See my edited post above for the details.

---

### Post by twistadias on 2008-04-02
hi i have an epson cx3900 too and cant get the scanner to work
currently using ubuntu 7.10
sane xsane iscan are installed
I have edited the '/etc/sane.d/epson.conf' file,

when i type 'sudo scanimge -L' in the terminal, this is what I get
```

device `v4l:/dev/video0' is a Noname USB 2.0 Camera virtual device
device `epson:libusb:001:005' is a Epson CX4000 flatbed scanner

``` 

then when I type  ```
 sudo chmod 0666 /proc/bus/usb/001/005
sudo scanimage -L
```

I get 
```

device `v4l:/dev/video0' is a Noname USB 2.0 Camera virtual device

```

I also have a finger print reader which is sometimes detected as a scanner

please help. I a newbie at linux so please explain in detail

---

### Post by twistadias on 2008-04-03
bump...

---

### Post by twistadias on 2008-04-04
It still thinks that my camera is a scanner. Can anyone help me please!

EIDT: Finally worked
 You have to restart something by typing this in the terminal
```
sudo /etc/init.d/udev restart
```

---

### Post by scanCX3900 on 2008-04-14
# Epson # Epson CX-3900
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082f", MODE="664", GROUP="scanner"CX-3900
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082f", MODE="664", GROUP="scanner"

Where do I have to put these lines? In the same epson.conf or in some other place?

---

