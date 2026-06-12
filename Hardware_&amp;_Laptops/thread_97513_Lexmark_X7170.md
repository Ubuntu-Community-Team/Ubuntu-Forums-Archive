---
title: "Lexmark X7170"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by inittab on 2005-12-01
Just wondering if anybody has got this printer to actually print. I have tried using the z600 series driver with no luck and also tried to make a deb file out of lexmarks redhat and suse driver for this printer but it does not show up in the gnome print drivers.

The printer states that it is ready in z600 but does not actually print anything, the jobs just sit there,

if i turn the x7170 drivers from lexmark into a tarball and extract this is what i get.

> ./
./usr/
./usr/include/
./usr/include/lexmark-H/
./usr/include/lexmark-H/alignmentdata.h
./usr/include/lexmark-H/cartridgemanager.h
./usr/include/lexmark-H/cartridgeuserinterface.h
./usr/include/lexmark-H/cleaningdata.h
./usr/include/lexmark-H/clock.h
./usr/include/lexmark-H/errorcommunicator.h
./usr/include/lexmark-H/linuxinkjetprinter.h
./usr/include/lexmark-H/mediamanager.h
./usr/include/lexmark-H/portmonitor.h
./usr/include/lexmark-H/printerdevice.h
./usr/include/lexmark-H/printjobmanager.h
./usr/include/lexmark-H/scanerrorinterface.h
./usr/include/lexmark-H/scannerdevice.h
./usr/lib/
./usr/lib/liblexx7170printer.a
./usr/lib/liblexx7170printer.la
./usr/lib/liblexx7170printer.so
./usr/lib/liblexx7170printer.so.0
./usr/lib/liblexx7170printer.so.0.0.0
./usr/lib/liblexx7170printjob.a
./usr/lib/liblexx7170printjob.la
./usr/lib/liblexx7170printjob.so
./usr/lib/liblexx7170printjob.so.0
./usr/lib/liblexx7170printjob.so.0.0.0
./usr/lib/liblexx7170scanner.a
./usr/lib/liblexx7170scanner.la
./usr/lib/liblexx7170scanner.so
./usr/lib/liblexx7170scanner.so.0
./usr/lib/liblexx7170scanner.so.0.0.0
./usr/lib/liblxbxflib.so
./usr/lib/liblxbxhpec.so
./usr/lib/liblxbxhpeh.so
./usr/lib/liblxbxhpep.so
./usr/local/
./usr/local/x7170llpddk/
./usr/local/x7170llpddk/utility/
./usr/local/x7170llpddk/utility/lxbxaual.out
./usr/local/x7170llpddk/utility/lxbxcln.out
./usr/local/x7170llpddk/utility/lxbxclr1.lut
./usr/local/x7170llpddk/utility/lxbxphau.out
./usr/local/x7170llpddk/utility/lxbxphcl.out
./usr/local/x7170llpddk/utility/scanGray.lut
./usr/local/x7170llpddk/utility/scanRGB.lut


but are these files actually going to help me or no? Any help is appreciated.

---

### Post by jazzer on 2005-12-04
As far as I know, having tried to get the x7170 to work in linux, you are likely not to have too much luck.  There is no printer driver for the x7170 in linux, the lexmark download site has a sample SANE driver (which is a driver for the scanner portion) and a driver development kit for the printer portion, but no actual driver for the printer.

---

### Post by displague on 2005-12-15
I received this printer free with an Emachine purchase.  I would also be interested in any solutions for this printer, as it has yet to spill first ink.

I also installed the sample drivers from Lexmark (a bunch of .a, .so, .la, and .h's), and they seems pretty useless with a filter or something built against them.  I also tried to print to it using the pbm2l7k driver, but that didn't help.

---

