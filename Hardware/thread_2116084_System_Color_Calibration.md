---
title: "System Color Calibration"
date: 2013-02-14
forum: Hardware
---

### Post by l6griffin on 2013-02-14
Color calibration doesn't(?) work, dispcalGUI does work.
 I have an HP2000z-300 laptop, AMD Wrestler 6310 video, Ubuntu 12.1, fglrx installed per - [Alexislavie]("http://ubuntuforums.org/member.php?u=1138228") thread 1930450, using AMD driver 13.2 Beta3, and a DataColor Spyder3 Colorimeter,

Problem - System Setting, Color, select the HP laptop, click 'Add  Profile', a profile(?) is added. I select the profile, but the  'Calibrate' button is greyed out. I place the cursor on Calibrate, and  get the message 'The  measuring device is not detected. Please check  that it is turned on, and correctly connected', The Spyder3 is USB, I  run *lsusb*, and it shows it as ID 8.

I install dispcalGUI from the Ubuntu Software Center it found the Spyder3, and seems to work. It is an old version and took over an hour to run calibration. Is there a fix to get system color calibration to see the Spyder3?

Larry

---

### Post by lunaphiles on 2013-03-20
There seems to be no solution

---

### Post by l6griffin on 2013-03-20
> **lunaphiles said:**
> There seems to be no solution

The solution (work around) was to load DisplcalGUI. I have other issues now like having to adjust brightness on every boot, and unstable WIFI, I haven't found time to work on.

Larry

---

