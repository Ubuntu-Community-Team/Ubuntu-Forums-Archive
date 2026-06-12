---
title: "How enforce to work canyon cnrw 43 web camera with skype"
date: 2009-11-20
forum: Hardware
---

### Post by lleming on 2009-11-20
I have (Ubuntu karmic).
I have a problem with my webcam it doesnt want to work with skype. And actiually this is not just one problem thats is a set of problem. It works with cheese but not always. From beginning cheese able to show and even cupture a photo but not in video capturing, since i press "capture" video sceen become: half left side blue and right side gray (strange but on grey side i can see my face :), but its creepy, very pale and inproper color as well). Then i google a lot, and found that need gspca driver or v4l. Now the result after this play cheese able to capture video as well. Problem only with skype, and camorama as well doesnt work.
lsusb showing in proper way: Microdiva chip and it suppose gspca support this camera but, from ubuntu threads if i understood right, gspca project moves to l4l2 project and include in kernel sinse 2.6 .
modprobe gspca tell me there is no driver gspca
from this area i have a lots of question
i have /dev/video0 (which is my web cam)
how to get information which video driver been uses by this device. How to change driver. How to get list of availble drivers?
if i will press modprobe gspca it will tell me: there is no such driver (but should be in kernel 2.6-xxx)?
modprobe v4l2 will replace driver for this session or permanently?
need to upload driver modprobe -r before to use another or not ?

---

### Post by lleming on 2009-11-20
I have (Ubuntu karmic).
I have a problem with my webcam it doesnt want to work with skype. And actiually this is not just one problem thats is a set of problem. It works with cheese but not always. From beginning cheese able to show and even cupture a photo but not in video capturing, since i press "capture" video sceen become: half left side blue and right side gray (strange but on grey side i can see my face :), but its creepy, very pale and inproper color as well). Then i google a lot, and found that need gspca driver or v4l. Now the result after this play cheese able to capture video as well. Problem only with skype, and camorama as well doesnt work.
lsusb showing in proper way: Microdiva chip and it suppose gspca support this camera but, from ubuntu threads if i understood right, gspca project moves to l4l2 project and include in kernel sinse 2.6 .
modprobe gspca tell me there is no driver gspca
from this area i have a lots of question
i have /dev/video0 (which is my web cam)
how to get information which video driver been uses by this device. How to change driver. How to get list of availble drivers?
if i will press modprobe gspca it will tell me: there is no such driver (but should be in kernel 2.6-xxx)?
modprobe v4l2 will replace driver for this session or permanently?
need to upload driver modprobe -r before to use another or not ?[/QUOTE]

---

### Post by lleming on 2009-11-20
additional news some of the threads in internet info that this web camera work just after plugin in.
mostly from fedora distributive threads

and the second lsusb Microdia PC Camera (SN9C325 + OM6802)

---

### Post by Kangarooo on 2010-05-05
heres also this camera [http://ubuntuforums.org/showthread.php?t=1442626](http://ubuntuforums.org/showthread.php?t=1442626)

---

