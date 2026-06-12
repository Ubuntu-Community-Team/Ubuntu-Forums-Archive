---
title: "Support for Visioneer 6100 USB Scanner?"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by tutwabee on 2007-01-17
I have a Visioneer 6100 USB scanner and I'm trying to get it working in Edgy.  I have read that sane drivers don't work for many visioneer scanners, but I found a website which appears to offer support for my scanner.  [Viceo Scanner Driver For Linux]("http://viceo.orcon.net.nz/")  should add support to sane for E3 chipset scanners and the Visioneer 6100 is in the supported scanners list.

I'm not sure if this driver would work for my system nor how I would go about installing it.  The instructions on the website are not very thorough and when it comes to hardware I get a bit lost sometimes.  Does anyone know whether the driver might work in Edgy and how I could go about installing it?

---

### Post by beaulanger on 2007-01-27
I have a Visioneer 8920 USB and checked out that site. In the Hardware section I see mine only listed in white and not green, but at least it's not red. I have no idea how to go about installing a driver from there either.:confused:

---

### Post by Alan_x on 2007-04-18
I haven't had any luck getting my 6100 to work in Ubuntu either, but I have a workaround: Run it from a Win98 Virtual Machine in Ubuntu. Here's how:

1. Install VMWare Player in Ubuntu.

2. Go to easyvmx.com and create a W98 VM. 

3. Edit the VM: Find ethernet[n].connectionType = "nat" . Change "nat" to "bridged".  

4.  Get your old W98 CD and install it into the VM. Also install VMWare tools and enable file sharing in the VM. Then Share a folder where you will save any scans.

5. Open IE in the VM and download the W98 scanner driver:

[http://support.visioneer.com/drivers/6100usb.exe](http://support.visioneer.com/drivers/6100usb.exe)

6 Run the 6100usb.exe. When it tells you to connect the scanner, physically connect it to  a usb port. When the scanner shows up on the VM Player Devices bar, Click it to connect it to the VM. Windows should now install it. You may need to re-start the VM.

7. Open W98 Control Pandl and make sure the scanner shows up in "Cameras and Scanners".

8. Now, you need some  twain-compliant software like IrfanView, etc., and you're good to go. Just scan, save, and then copy the saved file to Linux.

Caveat: After the scanner is installed, don't leave it physically connected when you start or re-start Ubuntu. Only connect it when both Ubuntu and the VM are running. For some reason, if the scanner is connected before that, the installation gets hosed and W98 can only see an unknown USB device.

---

### Post by jointstereotype on 2007-04-27
This is good to know. I've been looking for a way to use my 6100 USB under Linux for 5 years now. LOL The thing still works beautifully using my sister's WinXP-based laptop - but she's not always in the mood to lend it out. ;)

As soon as I can find some free time, I will try this method out - and if anyone else has had luck getting this model to run under Ubuntu, please post your sucess story...

---

### Post by raoul on 2008-02-15
A patch for recent versions of sane-backends has been around recently, which adds the **viceo** driver with support for **libusb**.

The following USB scanners should work:

    * Genius Vivid Pro USB
    * Primax Colorado USB 19200
    * Visioneer OneTouch 7600
    * Visioneer OneTouch 6100
    * IBM IdeaScan 2000 USB
    * LG Electronics Scanworks 600U

Primax 19200 usb has been reported to work with this driver.

Please visit: ***[Viceo backend with libusb support downloads and howto](http://www.g-loaded.eu/2008/01/24/viceo-backend-for-sane-with-libusb-support/)***

---

