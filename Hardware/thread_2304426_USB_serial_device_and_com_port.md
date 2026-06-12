---
title: "USB serial device and com port"
date: 2015-11-26
forum: Hardware
---

### Post by ocirne94 on 2015-11-26
Hello,
I have a temperature data logger (Escort iMini Plus PDF) and I am trying to make it work under Kubuntu 14.04.
The device comes with an USB cable and Ubuntu correctly opens it in mass storage mode. But to configure the device apparently I have to use com ports: the supplied (windows) software ("Escort Console Pro", available e.g. [here]("http://www.cryopak.com/en/verification-products/software-download/")) complains it can't find serial/com ports, and the manual keeps speaking of serial ports.
Below is the dmesg output when I attach the device.
Could socat be the answer? And if yes, how?
Thank you in advance for your time,
Enrico

```
[ 6127.341524] usb 10-2.1: new full-speed USB device number 5 using uhci_hcd
[ 6127.470512] usb 10-2.1: New USB device found, idVendor=2121, idProduct=0000
[ 6127.470518] usb 10-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 6127.470521] usb 10-2.1: Product: Mini++
[ 6127.470523] usb 10-2.1: Manufacturer: Escort DLS
[ 6127.473599] usb-storage 10-2.1:1.0: USB Mass Storage device detected
[ 6127.473785] scsi host11: usb-storage 10-2.1:1.0
[ 6128.476114] scsi 11:0:0:0: Direct-Access     00008481 EscrtDLSMPP      0000 PQ: 0 ANSI: 4
[ 6128.476537] sd 11:0:0:0: Attached scsi generic sg3 type 0
[ 6128.481587] sd 11:0:0:0: [sdc] 40960 512-byte logical blocks: (20.9 MB/20.0 MiB)
[ 6128.484570] sd 11:0:0:0: [sdc] Write Protect is off
[ 6128.484575] sd 11:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 6128.487523] sd 11:0:0:0: [sdc] No Caching mode page found
[ 6128.487528] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[ 6128.532561]  sdc: sdc1
[ 6128.551535] sd 11:0:0:0: [sdc] Attached SCSI removable disk
```

---

### Post by tgalati4 on 2015-11-26
Try installing *setserial* and using it to set the USB device (probably /dev/ttyS0) to the correct serial parameters, probably 9600,8,1.

```
sudo apt-get install setserial
man setserial
```

Usually these USB/serial devices have a USB-to-serial converter (something like *pl2303*)  make sure you have the correct module loaded:

```
sudo modprobe pl2303
```

---

### Post by ocirne94 on 2015-11-26
Hi, thank you for your answer.
I have successfully run command

sudo setserial /dev/ttyS0 baud_base 9600

Apparently setserial doesn't set data/parity/stop bits ([here](http://forums.fedoraforum.org/showpost.php?p=971311&postcount=6))
No change in the software complaints...

---

### Post by tgalati4 on 2015-11-27
Install *cutecom* and keep playing with the settings.

```
sudo apt-get install cutecom
cutecom
```

Embedded devices take a certain amount of magic to get to work correctly.

If you still have problems, perhaps run the Windows software under WINE to configure your device.  Once configured, then you can run it and just download the data as a USB flash drive.

I don't have experience with this data logger, but I have programmed several with Arduino hardware using a variety of temperature and RH sensors.  Using an SD card shield, and an ethernet shield, you can make an inexpensive, open source data logger for a fraction of the cost of the proprietary loggers.

How much are the Escort Mini's?  If you are in the US, mail me one and I can try to figure it out.

---

### Post by ocirne94 on 2015-11-27
Hi, thank you for your answer.
In fact the "no change in software complaints" refers indeed to the Windows software under WINE: the software can't access the device because it wants to reach it through a com port.
That's why I think I need some sort of virtual port e.g. with socat, apparently it's the norm: see for example [here](http://www.ftdichip.com/Drivers/VCP.htm), [here](http://www.ross-tech.com/vag-com/usb/virtual-com-port.html) and [here](https://portal.motorolasolutions.com/Support/US-EN/Resolution?solutionId=7187).
The Escort Mini's are between 50 and 70 &#8364; (sorry, I'm not from the US).

---

### Post by tgalati4 on 2015-11-27
I don't have experience with com ports under WINE.  Perhaps you can set up a dual boot machine with Windows, or set up a virtual machine with Windows and run the software from there.  It's a lot of work for a simple setup that you will only perform once on a device.

Some reading:

[https://www.winehq.org/docs/wineusr-guide/misc-things-to-configure](https://www.winehq.org/docs/wineusr-guide/misc-things-to-configure)

[http://ubuntuforums.org/showthread.php?t=714390](http://ubuntuforums.org/showthread.php?t=714390)

[http://www.witch.westfalen.de/Wine-HOWTO/ch-serial.html](http://www.witch.westfalen.de/Wine-HOWTO/ch-serial.html)

---

### Post by ocirne94 on 2015-11-27
Hi, thank you for your answer.
In fact I'd just like to be able to communicate with (or even just view) the device (not just in mass storage mode) in ubuntu; as you can see in the dmesg log, the device isn't being attached to any tty port and I think that's the main problem.

---

### Post by tgalati4 on 2015-11-27
The device will not be connected to a serial port until you load the USB-to-serial driver.  Post:

```
lsmod
```

Then 

```
sudo modprobe pl2303
```

Then

```
lsmod
```

*pl2303* may not be the correct module.  You will have to research the exact USB-to-serial chip that your device uses.  Since you referenced FTDI chips, there are several flavors available--which FTDI chip does your data logger have embedded into the device.

It is my hunch that this device reads the *.CVT file and if the file is new and the device has not been used, then you can simply delete the old file and replace it with a fresh *.CVT file and then reuse the datalogger.  The customized *.CVT file can be created using the ConsolePlus software (run in Windows).  Perhaps you don't need to connect to the device directly to upload the file, just use Nautilus or the terminal to copy the file over.

I presume that since these are single-use devices that are programmed at the factory using the requirements sheet that you provide with the temperatures and time intervals, that you are looking for a way to reprogram these devices so you can use them multiple times?

If that is the case, there is a procedure to short the battery for 1 second to reset the device.  This presumably rereads the *.CVT file so you can perhaps use the device again with the preprogrammed data requirements.  Otherwise, put in a different *.CVT to modify it.  Is the *.CVT a text (xml) file or a binary file?

---

### Post by ocirne94 on 2015-11-27
I actually don't know if that's FTDI - it was just an example.
Yes, I hope I only need to configure once, but I would like to do that from ubuntu+WINE.
Actually the device is one of the multi-use type - with replaceable battery. I'm just trying to get it as a ttyUSB0.
I've tried to modprobe all of the modules listed as "serial" inside /lib/modules/<uname>/modules.dep, with no luck.

---

### Post by tgalati4 on 2015-11-27
Can you look at the files on the device?  What format is the *.CVT file?

Looking at page 7 of the ConsolePlus user manual, there is a graphic that shows a Windows driver being loaded (Silicon Labs CP2010x).    There is a *[cp210x]("http://http://www.etheus.net/CP210x_Linux_Driver")* module, so try loading that.

More info:  [https://www.silabs.com/products/mcu/Pages/USBtoUARTBridgeVCPDrivers.aspx](https://www.silabs.com/products/mcu/Pages/USBtoUARTBridgeVCPDrivers.aspx)

---

### Post by ocirne94 on 2015-11-28
```
$ ls
CONTROL.BIN  COREDUMP.LRF  RECORD.PDF
```

I think CVT (Cryopak Verification Technologies) files are used only by the iMini series, not the iMini Plus PDF.
The control.bin file is always 1024 bytes, all zeros but the first 17.
coredump.lrf (lrf="logger recorded file") is where the logged data are stored. It can be read with Console software.
record.pdf contains data and statistics.

I have tried loading cp210x module:

```
sudo modprobe cp210x
```

Then I have plugged in the device with no luck.
I have tried
```
sudo echo 2121 0000 > /sys/bus/usb-serial/drivers/cp210x/new_id
```
no luck either.

---

### Post by tgalati4 on 2015-11-28
Edit control.bin with *hexedit* and change the values, then run the logger and see what the differences are.  These are simple devices, so the configuration can be packed into a few bytes.

I don't know what else to try.  There are a lot of usb-serial modules to try.  You sometimes need the get the Vendor/Product ID to match to get the module loaded.  

> 
tgalati4@Mint17 /lib/modules/3.13.0-24-generic/kernel/drivers/usb/serial $ ls
aircable.ko   cypress_m8.ko       io_edgeport.ko  keyspan.ko      mos7720.ko  oti6858.ko      sierra.ko            usbserial.ko          xsens_mt.ko
ark3116.ko    digi_acceleport.ko  io_ti.ko        keyspan_pda.ko  mos7840.ko  pl2303.ko       spcp8x5.ko           usb-serial-simple.ko  zte_ev.ko
belkin_sa.ko  empeg.ko            ipaq.ko         kl5kusb105.ko   navman.ko   qcaux.ko        ssu100.ko            usb_wwan.ko
ch341.ko      f81232.ko           ipw.ko          kobil_sct.ko    omninet.ko  qcserial.ko     symbolserial.ko      visor.ko
cp210x.ko     ftdi_sio.ko         ir-usb.ko       mct_u232.ko     opticon.ko  quatech2.ko     ti_usb_3410_5052.ko  whiteheat.ko
cyberjack.ko  garmin_gps.ko       iuu_phoenix.ko  metro-usb.ko    option.ko   safe_serial.ko  usb_debug.ko         wishbone-serial.ko


I would hack the control.bin file first.  If you figure out the configuration code, then you can write your own little Python utility to program the devices.  Many times these config files have a checksum at the end, so you need to consider that as well.

Send an email to the company asking for the protocol and your willingness to write a linux configurator.  They may give you the details.

---

### Post by ocirne94 on 2015-11-28
According to the user manual, "CONTROL.BIN file is used for communication purposes with Escort software". So changing it shouldn't affect the device's own behavior. In fact I have re-programmed the device using Escort Console Pro on windows, and the CONTROL.BIN file hasn't changed. I will try and contact the company.

---

