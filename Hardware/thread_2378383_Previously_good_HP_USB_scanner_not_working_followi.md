---
title: "Previously good HP USB scanner not working following upgrade to 17.10"
date: 2017-11-22
forum: Hardware
---

### Post by Mark_Dear on 2017-11-22
Following a recent upgrade of Kubuntu from 17.04 to 17.10 my Hewlett Packard PSC-1317 All-in-one printer/scanner/copier is now a Some-in-one printer/copier: I can no longer scan. I have had a similar problem with at least one previous upgrade and have somehow managed to resolve it with advice from existing forum threads etc, although I cannot of course now remember how . This despite the fact that this printer is not on the list of sane supported devices [here]("http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD").


Attempting to scan from the HP Device Manager yields error message:


    ```
Failed to open device ‘hpaio:/usb/psc_1310_series?serial=UA4CICB26QT5’: Operation not supported.
```


Note that the device-uri per HP Device Manager console > View Printer and Device Information is slightly different ```
hp:/usb/psc_1310_series?serial=UA4CICB26QT5
```. I checked file /etc/sane.d/dll.conf and `hpaio` - the last entry - is *not* commented out. The serial *does* match the sticker on the machine (although the last two characters are missing, for some reason).


Attempting to run any scanning utility, eg Skanlite or Xsane, simply results in a message that no devices are found or available, however, running sudo sane-find-scanner from console gives


    ```
found USB scanner (vendor=0x03f0 [hp], product=0x3f11 [psc 1310 series ]) at libusb:003:005 [usb coordinates vary].
```


I have hplip-3.17.10 installed, I have installed both automatically and with the manual process adapted from the somewhat out-of-date advice from HP [here]("https://ubuntuforums.org/developers.hp.com/hp-linux-imaging-and-printing/install/manual/distros/ubuntu"). 


Adapting advice from [here]("http://searchitchannel.techtarget.com/feature/Configure-USB-devices-to-Linux-task-24") according to files and directories I actually have/can find, and the instructions within them, I have created two new files: 


 1. File /etc/udev/rules.d/hp-psc1317.rules (to augment /lib/udev/rules.d/60-libsane1.rules):


    ```
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="psc1317_rules_end"
    \#Hewlett-Packard All-in-one PSC1317
    SYSFS{idVendor}=="03F0", SYSFS{idProduct}=="3F11", SYMLINK+="HP-PSC1317", MODE="0664", OWNER="root", GROUP="scanner"
    LABEL="psc1317_rules_end"
```



 2.  File  /etc/udev/hwdb.d/psc1317.hwdb (to augment /lib/udev/hwdb.d/20-sane.hwdb):
    
     ```
usb:v03F0p3F11*
      libsane_matched=yes
```


Even after dis-/reconnecting the USB printer cable and even rebooting, no dice.  Note that the file (pseudofile?) /dev/bus/usb/003/005 was already in place, I guess because the printer function is already good - I’m not really clear whether the scanner and printer, for all that they are the same physical device, should have the same USB coordinates?


That’s everything I can think of that’s relevant. Glad for any advice.

---

### Post by kkaemail on 2018-01-16
I downloaded latest hplip.run and these instructions.. replaced/updated.. just keep saying yes.. during install.. it works fine now. 
[https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index](https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index)

---

