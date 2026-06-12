---
title: "quickcam ultra vision"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by ironwoodcarver on 2007-05-12
I have a logitech quickcam ultra vision 5mps I can't find any drivers for this I don't know how to compile anything so I'm hoping that some one has figured out how fix this it would be a great webcam if it would work

thanx

---

### Post by Kobalt on 2007-05-12
You could use the UVC drivers maybe... But we need to make sure before : can you please plug in and turn on your webcam and then run the command line *lsusb* from the Terminal. Then post the output here.

---

### Post by ironwoodcarver on 2007-05-12
Bus 002 Device 004: ID 03f0:2f11 Hewlett-Packard 
Bus 002 Device 005: ID 046d:08c9 Logitech, Inc. 
Bus 002 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 002: ID 045e:00f6 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I tried starting it but it wont start

---

### Post by Kobalt on 2007-05-13
You can try [this]("https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy") first, maybe it'll work but I'm not sure, your webcam seems to be abit different from the quickcam 5000 which is mentioned in the link.

---

### Post by ironwoodcarver on 2007-05-13
thank I will try that

---

### Post by ironwoodcarver on 2007-05-13
thanks but that does not work. does anyone know why logitech refuses to support linux? :(

---

### Post by evnglion on 2007-09-26
Yeah I agree, this is driving me crazy.  I picked up a Logitech QuickCam Ultra Vision Special Edition last week, and I really would like to use it in Linux as well.  For some reason it seems to take way more resources in Windows than I would like to believe is neccesary.  I am just sick of having to switch out of Linux for Windows every time I need to jump on Skype.

---

### Post by altariel on 2007-11-28
no idea if this might help or not, but I stumbled over this when googling
[http://blog.nicolargo.com/2007/09/webcam-logitech-ultra-vision-sous-ubuntu.html](http://blog.nicolargo.com/2007/09/webcam-logitech-ultra-vision-sous-ubuntu.html)

in french but I think you  can get the idea anyway

---

### Post by GlennW on 2007-12-16
> **altariel said:**
> no idea if this might help or not, but I stumbled over this when googling
[http://blog.nicolargo.com/2007/09/webcam-logitech-ultra-vision-sous-ubuntu.html](http://blog.nicolargo.com/2007/09/webcam-logitech-ultra-vision-sous-ubuntu.html)

in french but I think you  can get the idea anyway

Hi,

Despite my complete lack of a French language skill set, I muddled through your suggested site and got my Logitech QuickCam Ultra Vision on and running. Thanks. The fps were consistently running 20-30. 

My remaining challenge is to sync with Skype and be able to use this wonderful piece of technology.

If you have any suggestions, I'd be grateful

---

### Post by toddbmobile on 2008-02-02
I to went thru the French walk through but get this:

 luvcview -s 640x480
luvcview version 0.2.1 
 size width: 640 height: 480 
Video driver: x11
A window manager is available
video /dev/video0 
ERROR opening V4L interface 
: No such file or directory

could not quite understand his PS in the how to, did you do anything related to the PS in the how to?

---

