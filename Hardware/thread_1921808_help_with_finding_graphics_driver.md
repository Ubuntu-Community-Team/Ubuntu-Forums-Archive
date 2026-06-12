---
title: "help with finding graphics driver"
date: 2012-02-07
forum: Hardware
---

### Post by VideoAddicted on 2012-02-07
I recently purchased the AMD Radeon HD 6800 Series GPU for my system, and am not sure how to get the driver onto my Ubuntu partition, nor am I sure where to acquire an Ubuntu version of this driver.

Any help with would be greatly appreciated.

---

### Post by Mark Phelps on 2012-02-08
If you're seeing a desktop, and you probably would say if you were NOT, then you already HAVE video drivers installed.

Unless you are doing 3D Gaming, then you don't need to mess around with installing restricted video drivers.

---

### Post by VideoAddicted on 2012-02-12
All I'm getting is a full screen terminal window

---

### Post by jcolyn on 2012-02-12
First off uninstall the driver you installed through extra drivers if you installed one here. Reboot..............

Then go here [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) and fill in the boxes. It will then show the driver available for your card. Download it to an empty folder. Right-click the driver and choose open a terminal. Enter ```
sudo sh ./name of driver.run
```In place of name of driver enter the full name of the driver you downloaded. Follow on screen info. Choose automatic install when asked. Once done reboot and the latest driver will now be working..

---

### Post by Yellow Pasque on 2012-02-12
It is better to build packages than run the install sscript directly (and make sure the dependencies are installed).
See: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

---

### Post by VideoAddicted on 2012-02-12
@jcolyn The link that you gave me's button is non-responsive on my computer, do you know another way to find the driver

Also the page for installing drivers is for Oneiric and my system is using Maverick, do you know if the information on that page will apply?

---

