---
title: "how to install Brother HL-2240 driver on Ubuntu 10"
date: 2012-04-23
forum: Hardware
---

### Post by nazaroo2 on 2012-04-23
I can see the cupswrapper driver is installed from the Synaptic Package Manager.

But the 2240 doesn't come up in the Printing menu,
and when I try to add it I can't find the driver.
I don't thing there is a ppd driver available for it.

I downloaded both files from Brother (both DEB and RPM versions) to desktop, 
but I don't know what to do next.

---

### Post by LinuxFan999 on 2012-04-23
Are you using Ubuntu 10.04 or 10.10?

---

### Post by nazaroo2 on 2012-04-23
> **LinuxFan999 said:**
> Are you using Ubuntu 10.04 or 10.10?

**Ubuntu 10.04** according to System Monitor.

---

### Post by nazaroo2 on 2012-04-23
Also, the printer previously did work, so a driver was installed once.

But that was several episodes ago.

---

### Post by nazaroo2 on 2012-04-24
Okay I tried the final advice in this thread here, while I was waiting:

[http://ubuntuforums.org/showthread.php?t=1627516](http://ubuntuforums.org/showthread.php?t=1627516)

This finally made the printer show up (and deleted other unconnected printers).

I think part of the success came from purging and reinstalling CUPS

It still wouldn't print, but showed up with a red-flag like it was offline or disconnected.
I unplugged, replugged, still no go.
Then I clicked on it and re-connected it to the USB port by clicking on that under the printer properties, I think.
Then it printed a test page successfully (and 4 other pages in the que).

YAY!

I think it is working now.

---

### Post by SushiAddiction on 2012-05-02
This worked for me. I think plugging in the printer after ubuntu starts is what made it work.
[http://linux.eaton.net.nz/?p=129](http://linux.eaton.net.nz/?p=129)

First I tried to install the printer after booting with it connected and it did not work. Could be a coincidence :/ Logging in/out may not do the job either.
I had to uninstall previous attempt not working driver install > reboot without printer usb connected > after ubuntu starts, plug in printer > ignore dialogue asking what printer driver to install....> then install printer (see above link)

---

