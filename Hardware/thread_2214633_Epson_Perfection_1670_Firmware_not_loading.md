---
title: "Epson Perfection 1670 Firmware not loading"
date: 2014-04-02
forum: Hardware
---

### Post by The Eight-Bit Link on 2014-04-02
I have an Epson Perfection 1670 scanner that I'd like to use in Xubuntu 13.10 or before long 14.04. I've followed many a guide saying to take the esfw30.bin and put it in the /etc/sane.d/ folder, then edit the snapscan.conf to point to the bin file. I have done this, and sane detects the scanner when I run sane-find-scanner, but it still doesn't load the firmware, nor does it work. Could someone help me figure out what the problem is?

---

### Post by The Eight-Bit Link on 2014-04-03
Still not sure what the problem is. I've even cut out all USB hubs, and it doesn't work.

---

### Post by coldraven on 2014-04-04
I've been using the advice for my Epson 1670 in this thread since Ubuntu 8.04 and it has worked every time.
[http://ubuntuforums.org/archive/index.php/t-26911.html](http://ubuntuforums.org/archive/index.php/t-26911.html)

Not sure what's gone wrong for you. Did you edit /etc/saned.d/snapscan.conf as root?
Is the filename of esfw30.bin in uppercase? It would have to be the same case as the file that you copied to /etc/sane.d
Check it for typos.

```
sudo nano /etc/saned.d/snapscan.conf
```

The only other thing I can think of is that you have plugged it into a USB3 port, maybe that is creating a problem.

Here is the important part of my snapscan.conf. Did you remove the # from the beginning of the firmware line?
```
#------------------------------ General -----------------------------------

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /etc/sane.d/ESFW30.BIN

# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb

# For SCSI scanners specify the generic device, e.g. /dev/sg0 on Linux.
# /dev/sg0

#---------------------------------------------------------------------------
# No changes should be necessary below this line
#---------------------------------------------------------------------------
```

Edit: Maybe not 8.04, it must have been since 9.10 as the dates don't match.

---

### Post by xxlray on 2014-11-30
Okay - this thread is incredibly old but I just had the same problem. In my case it was a permission problem. This fixed the issue:

```
sudo chmod 644 /etc/sane.d/esfw30.bin
```

(You may need to replace /etc/sane.d/ by the path you use)

---

