---
title: "Nvidia black screen fix"
date: 2010-12-13
forum: Hardware
---

### Post by eGelor on 2010-12-13
This is a back up post.
So after 10 months my 01:00.0 VGA compatible controller: **nVidia Corporation G98 [GeForce 9200M GS]** (rev a1)
WORKS. 
1) I make the xorg_preworks conf file and my nvidia works in a bad way. I open nvidia-settings and my DFP-O monitor was there. I fix the parameters and 
i mv /etc/X11/xorg.conf xorg_preworks
save nvidia-settings xorg file. a save window opens i mv /etc/X11/xorg_preworks /etc/X11/xorg.conf and save.
Cheers.

---

### Post by eGelor on 2010-12-13
Yesterday i did
$sudo apt-get install read-edid
$sudo apt-get install ghex
i open the edid.bin that i had save from nvidia-settings
zero all the values and paste it on /etc/X11/
as the file xorg_preworks saws.

other things i works with. 
$get-edid |parse-edid

---

### Post by eGelor on 2010-12-15
The Solution to save nvidia-settings
-------------------
1- Run: cd /etc/X11 && sudo mv xorg.conf xorg.conf.backup && sudo nvidia-xconfig
2- Run: gksu nvidia-settings
3- Setup some video parameters like resolution or activate twinview 
4- click on [Save to X configuration file] buttom
5- Enjoy

---

