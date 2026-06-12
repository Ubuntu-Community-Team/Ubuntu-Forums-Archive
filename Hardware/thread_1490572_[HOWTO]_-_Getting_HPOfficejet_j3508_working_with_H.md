---
title: "[HOWTO] - Getting HPOfficejet j3508 working with HPLIP in Kubuntu"
date: 2010-05-22
forum: Hardware
---

### Post by santam on 2010-05-22
This howto relates to a recently available Indian model of the HPOfficejet j3508 printer. The printer is detected automatically but scanner and fax dont work. 
After installing the official HP-LIP package from the HPLIP website the installation proceeds smoothly. Running hp-setup however fails to find the printer despite giving the USB bus and device id in the HP printer detection dialog that pops up. The reason behind this is that the printer description is lacking the HPLIP printer database. Noteworthy is the fact that printing works with the Officejet 3600 series driver (ppd) though you have to change the default output from color to black and white / grayscale (which is logical since this is not a color printer). 

The question thread to this in the HP-LIP website is [here]("https://answers.launchpad.net/hplip/+question/107658")

The basic steps in troubleshooting the problem are:
[LIST=1]
[*]Find the USB device and Bus id for the device after turning it on and getting it connected to USB using the command lsusb
[*]Open the file /usr/share/hplip/data/models/models.dat in the superuser mode. Just find the Officejet J 3600 series information and then copy the whole section and paste it above or below the original section.
[*] Change all the places where officejet j3600 or variant comes with 3500 and variant in the pasted section including the header.
[*] Run hpsetup again and your printer should get detected. Your Scanner and Fax will work but not the printer. The reason is that for some reason the driver gets defaulted to the Officejet j4500 driver. 
[*] In kubuntu you can use the system settings > printer dialog to modify the ppd file to use the officejet j3600 ppd and set it to print in gray scale
[/LIST]

Your all in one will work nicely. 
Please remember this is a hack and mileage may vary. I am waiting for offical support from HPLIP which should not be too hard.

---

