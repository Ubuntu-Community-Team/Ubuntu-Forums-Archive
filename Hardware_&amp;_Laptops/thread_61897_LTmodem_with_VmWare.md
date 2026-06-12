---
title: "LTmodem with VmWare"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by sscotti on 2005-09-02
Hi,

I'm trying to get an Ltmodem that is voice capable on windows to work with VMWare on Ubuntu.  I have VMware installed just fine and everything seems to work OK and I have the Ltmodem mapped to /dev/modem.  I can communicate with the modem doing a query, but the modem won't dial and the voice features aren't recognized.  I am using the same driver for the guest windows os as I am using for the real windows  os on my dual boot system.  The modem seems to operate OK on the Ubuntu host.  The modem is a PCI modem.  I also have a D-Link voice modem that is a serial modem but I can't get that to work either.

Any suggestions or help welcome.

/sds
[email]sscotti@sscotti.net[/email]

---

### Post by mlomker on 2005-09-02
I doubt you'll get that to work through VMWare.  VMWare emulates a serial port but does not allow the driver to access the other features of the software/firmware running on the host.  

I'm not aware of a linux softmodem driver that supports additional functions beyond dialing a modem.  Indeed, many of us can't even find drivers for the modem part.

---

