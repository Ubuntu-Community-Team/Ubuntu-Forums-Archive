---
title: "Installing Printer Driver for Brother HL 2220 Printer, not working"
date: 2015-01-01
forum: Hardware
---

### Post by jwalway on 2015-01-01
Hello,

I have Ubuntu version 12.04.5, running in VirtualBox.      I've got a Brother HL 2220 printer hooked to the USB port.   The printer is recognized by Ubuntu, but I can't seem to get the right driver.

I downloaded a gz file from brother for the printer driver and installed it, and even ran through the print test, which worked.   The file was titled:
linux-brprinter-installer-2.0.0-1.gz

However, when I went to System Settings --> Printing and tried to search for the driver for the printer, it could not find the HL 2220 driver in the database, despite the fact that I had just installed it.   I also tried a reboot.

I also tried to browse to Cups, but it wants a password and username, and I don't have one.  All I have is the superuser password.   However, I'm not sure that Cups is the answer.

I have printed from a network printer with this ubuntu, but it is now defunct.  I'm not able to get this to properly print to the Brother HL2220.

Does anyone have any ideas? 

Thanks!

...John

---

### Post by plucky on 2015-01-02
Open a terminal and post output for ```
dpkg -l | grep -i brother
```

> I also tried to browse to Cups

In the address bar of your Browser ```
http://127.0.0.1:631/
``` will open the CUPS interface.

> I downloaded a gz file from brother for the printer driver and installed it, and even ran through the print test, which worked. The file was titled:
linux-brprinter-installer-2.0.0-1.gz

What procedure did you use to run the installer script?

---

