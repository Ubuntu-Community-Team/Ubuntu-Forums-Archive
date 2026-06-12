---
title: "Scanner not found in 8.0.4.1"
date: 2008-08-31
forum: General Help
---

### Post by Alabamian on 2008-08-31
Folks,

I can't get my HP ScanJet 4100c to work with XSANE.  It says No devices found.  It used to work fine in XP, but HP has no drivers for Vista and won't make any, so it doesn't work anymore from that platform.  I get this ...

collin@Varuna-U:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

When I issue this command, but I'm not seeing my Intel video camera either.  I don't know what software can use the camera.  I'm an Ubuntu newbie so there's a lot I don't know.

Anyone have any advice?

Thanks in advance

---

### Post by JC Cheloven on 2008-08-31
With the scanner connected, try the folowing from a terminal:
```
sudo sane-find-scanner
```

This should identify the  scanner (vendor, product, at libsub). That doesn't mean that the scanner is functional or even supported. Only that sane 'sees' the scanner.

If the previous is succesful, try the following
```
scanimage -L
```

This should list the connected scanner(s) that it identifies and supports.

If the previous is succesful, try
```
scanimage > something.tiff
```

This should scan your image right away (the extension may be .tiff, .png. .jpg ...). If this is also succesful, the problem should not be in sane, but in the graphical frontend xsane.

If some of the previous were not succesful, you should have a look in the "supported devices section" of the sane project [www.sane-project.org](www.sane-project.org). Hp have usually good support in linux, but sometimes yoy have to do some weird thing, as to take a .bin file (actually a driver file) from a windowz installation, and copy it somewhere (typically in /etc/sane.d). Instructions, if applicable, are in the sane's web. I would have a look by myself for your 4100c scanner, but for some reason the web seems to be down right now.

---

### Post by Alabamian on 2008-09-01
JC,

Muchas gracias.  Ahora, I get this ...

collin@Varuna-U:~$ lsusb
Bus 005 Device 002: ID 04b0:016b Nikon Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0733:0401 ViewQuest Technologies, Inc. CS330 WebCam
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


Okay, when I issue the commands you direct, I get this ...

collin@Varuna-U:~$ sudo sane-find-scanner
sudo: unable to resolve host Varuna-U

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x0733, product=0x0401) at libusb:004:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
collin@Varuna-U:~$ scanimage -L
device `v4l:/dev/video0' is a Noname Intel Create and Share virtual device

Is the response to find-scanner command the scanner?  The scanimage command responds with my Intel webcam, so that's definitely not right.  Hmmm.

On the other hand, my scanner is definitely in the 'supported' group on the website you have a link to.  Muito obrigado.

---

### Post by cpetercarter on 2008-09-01
It might be worth checking that you (ie your username) has permission to use scanners, since this is not the case by default.

System > Administration > Users and Groups

Highlight your username, click Unlock > Properties > User Privileges and then, if necessary, check the "scanners" option.

---

### Post by JC Cheloven on 2008-09-01
> **Alabamian said:**
> 

collin@Varuna-U:~$ lsusb
Bus 005 Device 002: ID 04b0:016b Nikon Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0733:0401 ViewQuest Technologies, Inc. CS330 WebCam
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
___________________

collin@Varuna-U:~$ sudo sane-find-scanner
sudo: unable to resolve host Varuna-U

found USB scanner (vendor=0x0733, product=0x0401) at libusb:004:002


Well, as you stated, the good news are that your 4100c is fully supported by sane. Things should be as easy as plugging your scanner and just start using it. So don't despair ;-)

The bad news are, as it seems to me, that your webcam is messing around: 004-002 is the usb adress of the webcam, and sane identifies there a scanner. I'd try the following:

- Plug in another usb port the scanner and try again. By the way, are you using a hub? I'd try with a main usb port.

- Check what petercarter said. Perhaps it's as obvious as this.

- Unplug the scanner, disable the webcam (not sure how to do this, I haven't one), perhaps reboot ubuntu, and try scanning again.

Hope this helps.

---

