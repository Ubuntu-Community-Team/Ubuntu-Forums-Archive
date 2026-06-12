---
title: "DCP-195C scanner not detected"
date: 2011-12-18
forum: Hardware
---

### Post by timtammittee on 2011-12-18
Hey guys,

I'm having some problems with the printer/scanner DCP-195C. I installed the brother linux drivers from here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

after doing so the printer worked just fine but I'm having problems with the scanner. When running *sane-find-scanner* I get following output:
```

# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04f9, product=0x0222) at libusb:002:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```So it did find the scanner connected to the USB port. But when running
*scanimage -L* I get the output:
```

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```so something is going wrong, can anyone help?

---

### Post by Jose Catre-Vandis on 2011-12-18
So you installed brscan3 driver?

What is the output (in terminal) from the following command:

```
dpkg  -l  |  grep  Brother
```

Have you done this bit:

```
Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 
```

---

### Post by timtammittee on 2011-12-18
The output from the Brother grep is 
 ```

ii  brscan-skey                                                 0.2.1-3                                 Brother Linux scanner S-KEY tool
ii  brscan3                                                     0.2.11-4                                Brother Scanner Driver
ii  dcp195ccupswrapper:i386                                     1.1.2-2                                 Brother CUPS Inkjet Printer Definitions
ii  dcp195clpr:i386                                             1.1.2-1                                 Brother lpr Inkjet Printer Definitions
ii  ptouch-driver                                               1.3-0ubuntu11                           CUPS/Foomatic driver for Brother P-touch label printers

```so the driver should be installed

I added the line to libsane rules, I also tried it when specifying the exact model in the file

any other idea?

---

### Post by Jose Catre-Vandis on 2011-12-19
Try running xsane as root, it might be a permissions problem:
```
sudo xsane
``` (It will complain about the dangers but carry on...)

---

### Post by demonipuch on 2011-12-20
Hello

Are you using a 64-bits version of Ubuntu?

If yes, you need to run these commands :

```
sudo cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane
sudo cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/sane
sudo cp /usr/lib64/sane/libsane-brother3.so /usr/lib/sane
sudo cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
sudo cp /usr/lib64/libbrscandec3.so /usr/lib
sudo cp /usr/lib64/libbrscandec3.so.1 /usr/lib
```

---

