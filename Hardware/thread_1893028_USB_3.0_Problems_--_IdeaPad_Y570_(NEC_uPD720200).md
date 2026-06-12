---
title: "USB 3.0 Problems -- IdeaPad Y570 (NEC uPD720200)"
date: 2011-12-09
forum: Hardware
---

### Post by jshayden on 2011-12-09
Upon installing 11.10, only the USB 2 port worked; neither of the USB 3.0 ports work at all (not even for a USB 2 device).  After running updates and rebooting, they both started working.

Then, they simply stopped working---not after more updates; not after a reboot.  They simply stopped working in the middle of using them.

Has anyone seen this?  Any ideas?  Thanks!

```
# lspci | grep -i usb\ 3.0
09:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```

```
# uname -a
Linux jsh-y570 3.0.0-13-generic-pae #22-Ubuntu SMP Wed Nov 2 15:17:35 UTC 2011 i686 i686 i386 GNU/Linux
```

```
# lsmod | grep xhci
xhci_hcd               77080  0
```

---

### Post by BC59 on 2011-12-09
Looks like Ubuntu doesn't support perfectly USB3

[http://ubuntuforums.org/showthread.php?t=1776361](http://ubuntuforums.org/showthread.php?t=1776361)

---

### Post by jshayden on 2011-12-09
I understand that the support and drivers are limited, but it seems rather odd that it would stop working in the middle of a running session.

Anyone have any ideas?

Thanks!

---

### Post by Objekt on 2011-12-12
I've had USB 3.0 difficulties too.

My hardware is different, however.  My USB 3.0 ports are on a non-branded PCI Express expansion card I bought from Dealextreme.com.  It does not use a NEC/Renesas USB 3.0 controller chip, but rather what appears to be a Chinese knockoff of the genuine article.

The knockoff controller is apparently reverse-engineered just enough to work under Windows.  It works fine in Windows 7 using the NEC/Renesas drivers, but only works about half the time when I run either Ubuntu 10.04 or Linux Mint 12.

That is, when I reboot the machine, sometimes my USB 3.0 external hard drive shows up, sometimes it doesn't, regardless of whether I have it plugged in & powered up.

Hotplugging is also a gamble.  Sometimes it shows up, sometimes not.  Haven't had it disappear spontaneously, however.

---

### Post by Mark Phelps on 2011-12-14
> **jshayden said:**
> I understand that the support and drivers are limited, but it seems rather odd that it would stop working in the middle of a running session.

Anyone have any ideas?

Thanks!

Actually, I had the same problem with USB 3.0 -- and the fix turned out to require new firmware and new drivers.  Renesas (who bought Nec) put out new firware for the USB 3.0 devices to address problems.  Unfortunately, I was only able to find firmware updates and drivers through Google at the Renesas site that worked in Windows.  But, once the firmware is flashed, the device then works in Ubuntu as well.

---

### Post by Objekt on 2011-12-14
I'm hoping the firmware update may work on my USB 3.0 card as well, even though the controller is (as far as I can tell) a fake.

Even if it gets bricked, I won't be too upset.  Silly counterfeit chip didn't work anyway (in Linux).

The driver I'm using with the card at present (in Windows 7) is from 2009.

update:
Installed the new USB 3.0 drivers.  They're dated 9/13/2011.  However, I'm not sure this will do anything to how the card behaves with Ubuntu (or other Linuxes).

update2:
Turns out there's another, even newer driver update, dated 15 November 2011.

---

### Post by Mark Phelps on 2011-12-15
> **Objekt said:**
> Turns out there's another, even newer driver update, dated 15 November 2011.

In my case, while the drivers helped, it was really the firmware update that "fixed" the USB 3.0 problems.  You have to know the controller model number to do the firware update ... and since you say yours is "fake", if you don't mind "bricking" it, you can try all of the firmware updates to see if any work.

---

### Post by Objekt on 2011-12-16
I tried to run the Renesas USB 3.0 controller firmware update, but it stalled indefinitely.  As in, I gave it a couple of hours to complete, but it didn't.  So I rebooted, tried again. same result.

However, my off-brand USB 3.0 card still works.  The failed firmware update didn't brick it.

The Renesas utility reports the driver version (now 2.1.28.0, newer than the one I mentioned above), and says my controller has the 4015 firmware version.  So I guess it already had that firmware when I bought the card, a few months ago.  Or, it's part of the fake-ness - the chip is simply lying to the software.

---

