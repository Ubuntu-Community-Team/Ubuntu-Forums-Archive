---
title: "Garmin Quest"
date: 2008-04-29
forum: Hardware
---

### Post by Rohnny on 2008-04-29
I have been running Linux Ubuntu for some years now and are very pleased. Some troubles on the way but they have been solved. 
After I upgraded to Hardy I can't use my Garmin Quest in wine anymore. It can find my device. Can't find any /dev/ttyUSBx. Is there someone that can help me get it back on "track" ;)
output from dmesg-
--snip
[138273.309534] usb 2-3: new full speed USB device using ohci_hcd and address 8
[138273.513468] usb 2-3: configuration #1 chosen from 1 choice

--snap

Regards Rohnny

---

### Post by RangeTech on 2008-05-03
I've just installed "Hardy" and it doesn't seem to have picked up my Garmin GPSMAP 60Csx on boot at all.  Looking at your details, they seem to be devoid of any reference to a "Garmin" device.  Excuse my ignorance in matters Linux, but I thought that there should be a reference in the boot log which shows a Garmin driver has been invoked?  It seems like there may have been a change of device file naming conventions in this new version of the OS, I see in /dev file names like "usbdev1.1_ep00", "usbdev1.1_ep82" etc.

---

### Post by RangeTech on 2008-05-03
Cheers Rhonny!  OK...an update on my particular quest...I found out about a utility called lsusb I can run in a terminal that will list the USB devices found on the system.  It appears the GPS was detected...it's listed as on:

Bus 004 Device 002: ID 091e:0003 Garmin International GPSmap (various models).

Now I need to work out what goes from here??? 

RangeTech.

---

### Post by Rohnny on 2008-05-03
Found the answer. modprobe garmin_gps and everything is back to normal :guitar:

---

### Post by RangeTech on 2008-05-04
Cheers Rohnny...thanks for the solution.  For anyone wishing to know what instructions to apply in a terminal window to get the OziExplorer mapping software (installed in WINE) communicating with the Garmin GPS, I applied:

$sudo modprobe garmin_gps
sudo ln -sb /dev/ttyUSB0 /dev/ttyS3   .......(to map the USB port to COM4,)

and under the Com tab inside of the Configuration menu in OziExplorer I unchecked the Garmin USB option and set the COM port in the General COM Settings area to 4.

Everything seems to work fine...I can download and upload waypoints and tracks OK.

RangeTech.

---

### Post by Rohnny on 2008-05-04
Forgot the link part. But it's the same here. Wine is working ok with mapsource and Garmin Quest. Upload map, waypoint, routes and logs


Regards Rohnny

---

