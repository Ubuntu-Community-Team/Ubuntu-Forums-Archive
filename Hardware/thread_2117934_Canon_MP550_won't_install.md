---
title: "Canon MP550 won't install"
date: 2013-02-19
forum: Hardware
---

### Post by njKeats on 2013-02-19
I'm trying to set up my Canon MP550 printer to an Ubuntu 12.04 64-bit desktop (using Gnome3). But it simply refuses to work!

I have tried installing drivers from the apt repository, and I have tried installing the drivers that I downloaded directly from the canon website using dpkg --force-architecture --force-depends etc...

Both methods install the drivers perfectly fine. except when I go to settings > printers > add new printer > local printer > mp550 series and click OK, **nothing happens! it just simply doesn't add it to the list of available printers.** I know connection is available to the printer because the SD dock on the printer mounts as external storage on the computer.

matttbe had a good post here [http://ubuntuforums.org/showpost.php?p=8655287&postcount=3](http://ubuntuforums.org/showpost.php?p=8655287&postcount=3)
But I could not find a copy of getlibs anywhere.

does anyone have an idea of what is going wrong??? I have installed similar canon printers without a hitch before...

---

### Post by njKeats on 2013-02-19
Well I have just discovered the answer! some mentioned it here [http://askubuntu.com/questions/100305/unable-to-install-any-printer](http://askubuntu.com/questions/100305/unable-to-install-any-printer)

The Gnome3 interface won't let you install printers. you need to log in as unity to install.

---

### Post by ahallubuntu on 2013-02-19
~

---

### Post by OregonTrail on 2013-02-23
The series of steps taken in this blog post might help you, [Printing with the Canon ip1800 on 64-bit Ubuntu]("http://wordonthestack.com/?p=13").

---

### Post by pdc on 2013-03-04
...............so njKeats............not sure if you are still out there...........

Canon supply a driver for your MP550............packaged in the .deb package that ubuntu uses; it is packaged for a 32bit operating system; 

if you post back if you are still in touch, I can offer to help you install the Canon driver; I would think that should work well; 

as the latest Ubuntu is due out next month as 13.04 you may wish to install that ..........but if you had a 32bit system, the install of the driver would be easier..........

---

