---
title: "How to clean printer heads on Epson Stylus S21?"
date: 2010-12-28
forum: Hardware
---

### Post by Mariane on 2010-12-28
I followed the instructions here: 
[http://ubuntuforums.org/showthread.php?t=1415955&highlight=Epson+Stylus+ink](http://ubuntuforums.org/showthread.php?t=1415955&highlight=Epson+Stylus+ink)

But I got repeatedly the error:
Cannot open /dev/lp0 read/write: Permission denied

So I did:
sudo chmod 777 /dev/lp0
and now the error is:
Cannot write to /dev/lp0: Resource temporarily unavailable

This error appears whatever I try to do: refresh the ink levels - they are all at zero even though I've just changed two cartridges -, print a test page, clean the heads... 

My .stylus-toolbox.conf says:
[device]
model = escp2-s21
is newer usb printer = True
raw device = /dev/lp0
[external programs]
escputil binary = /usr/bin/escputil

I don't really know if it is on lp0, I just copied that from the link above. 

lsusb says:
Bus 002 Device 007: ID 04b8:0005 Seiko Epson Corp. Stylus D88+
Bus 002 Device 003: ID 046d:c062 Logitech, Inc. 
Bus 002 Device 002: ID 05a4:9999 Ortek Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

So the printer is seen but this command does not tell me on which port it is and I don't know the command word to ask that information. 

Please help. 

Mariane

---

### Post by dabl on 2010-12-28
Open your browser, and in the URL address window enter

> localhost:631

This will open the CUPS interface.  I think the printer utilities are under "Maintenance" (I'm away from my Linux/KDE desktop).

---

### Post by oldfred on 2010-12-28
If printer heads really need cleaning the old fashioned q-tip and some alcohol work. I have had old printer cartridges with dried up ink on the surface start working just with a cleaning.

Some printers do not like cartridges to be removed & reinstalled, others are designed to allow for it as you may want different kinds for different purposes.

---

