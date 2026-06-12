---
title: "Getting Brother DCP-7040 scanner functions working"
date: 2017-09-19
forum: Hardware
---

### Post by gleedadswell on 2017-09-19
I've previously successfully got scanning working with this printer and several different computers, including the one I'm using at the moment.  I have followed instructions (some written by me) here:

[HTML]https://ubuntuforums.org/showthread.php?t=1124867&page=2[/HTML]

but this time it is failing.  Presumably changes in 16.04 combined possibly  with changes to the scanner drivers since the last time I did this are causing this.  Here's the status:

My distro. is:

```

uname -a
Linux geoff-office-OptiPlex-7440-AIO 4.4.0-96-generic #119-Ubuntu SMP Tue Sep 12 14:59:54 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

My computer is a Dell Optiplex with
Processor: Intel® Core&#8482; i5-6500 CPU @ 3.20GHz × 4
Graphics: Intel® HD Graphics 530 (Skylake GT2) 

and I'm running 64-bit linux.

I have followed the Brother site instructions to install the brscan2 and brscan-skey packages using dpkg.  I've also installed the package that is supposed to make the printer accessible to regular users without fuss (brother-udev-rule-type1) I can see that these are successfully installed by running

```

dpkg -l | grep Brother
ii  brother-udev-rule-type1                       1.0.0-1                                        all          Brother udev rule type 1
ii  brscan                                        0.2.4                                          amd64        Brother CUPS Printer Definitions
ii  brscan-skey                                   0.2.4-1                                        amd64        Brother Linux scanner S-KEY tool
ii  printer-driver-brlaser                        3-5~ubuntu1                                    amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                         1.4-1                                          amd64        printer driver Brother P-touch label printers

```

Printing all seems to work, and has for months (it took me a while to get around to installing the scanner software).

If I run the sane utility for finding the scanner as root I get

```

root@geoff-office-OptiPlex-7440-AIO:~# sane-find-scanner 


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


found USB scanner (vendor=0x04f9, product=0x01e9) at libusb:001:004
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.



```

I find that a bit cryptic but the line "found USB scanner..." looks encouraging.  Running simple scan as root, it fails to find the scanner (asking it to scan results in it generating a blank page without the scanner hardware ever doing anything).  Running it as a regular user has the same effect.

Ideas for what to try next?

Edit: Just found that I had installed brscan2 by mistake (this printer requires brscan3).  Uninstalled all of the brother software and reinstalled it with the correct brscan.  However, this doesn't seem to have changed anything.

---

### Post by pdc on 2017-09-19
and you did that "**Copy the following files under /usr/lib64/ to /usr/lib/**."

from here [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101) 

so brscan3 Brother say is ..... with a sudo ........

cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane
cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/sane
cp /usr/lib64/sane/libsane-brother3.so /usr/lib/sane
cp /usr/lib64/libbrscandec3.so /usr/lib
cp /usr/lib64/libbrscandec3.so.1 /usr/lib

---

### Post by gleedadswell on 2017-09-20
Ah, thanks I had missed that.  That hasn't got scanning working but it has changed the behaviour.

I made those changes then rebooted.  Now when I try to scan in simple-scan it comes up with the red banner at the top of the window saying 

"Failed to scan
Unable to connect to scanner"

With a button available to "change scanner".  If I hit that button the dialogue window that comes up provides me with two options in a dropdown list for the scanner.

Brother DCP-7040
Epson PID 08CD

So at least the Brother scanner is showing up in simple-scan (it wasn't before).  I don't know what's up with the Epson.  I've never had an Epson scanner.

The output from sane-find-scanner seems to be unchanged.  I also tried

```

scanimage -L
device `brother3:bus2;dev2' is a Brother DCP-7040 USB scanner
device `epson2:net:142.12.7.72' is a Epson PID 08CD flatbed scanner

```

which is just showing what the dialogue in simple-scan was showing.  So, now at least sane (and by extension simple-scan) seems to recognize that the Brother scanner exists.  But for some reason it isn't able to connect to it.

When I open xsane instead of simple-scan it now provides the option to select a scanner (it didn't before).  It provides the Brother DCP-7040 and the (seemingly nonexistent) Epson as options.  I select the Brother.  Then a dialogue box comes up saying

"Failed to open device 'brother3:bus2;dev2': Invalid argument"

---

### Post by pdc on 2017-09-20
I think Brother need a big sit-down and sort this stuff out; there seems a lot of "heritage" baggage about; Epson and Brother are the two trickiest to get scanners going; Canon seem fine; and do the HP ones;

---

