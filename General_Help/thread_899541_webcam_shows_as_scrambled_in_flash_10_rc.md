---
title: "webcam shows as scrambled in flash 10 rc"
date: 2008-08-24
forum: General Help
---

### Post by KhaaL on 2008-08-24
Hi all

I just managed to get latest flash (10,0,0,569) and got it to work under my 64bit installation. everything works pretty well, except for my webcamera which shows up as scrambled. it works fine in cheese and skype and it would be *really* good if it could work with flash too. Anyone who can help me figure out the problem?

---

### Post by Crafty Kisses on 2008-08-25
Post the output of > lsusb

---

### Post by KhaaL on 2008-08-25
```
$ lsusb
Bus 002 Device 006: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 004: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 001 Device 003: ID 06a3:8021 Saitek PLC 
Bus 001 Device 002: ID 046d:c041 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000
```

---

### Post by Crafty Kisses on 2008-08-25
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

I want to see if it's still scrambled in Ekiga.

---

### Post by KhaaL on 2008-08-25
I made an intresting find with Ekiga. With V4L, i had two devices, the webcam and "Asus P7131 4871" (dont ask me what it is, i have no idea). In V4L the webcam works correctly. Though in V4L2, the Asus device shows, but instead of the webcam I get /dev/video1 which once selected makes ekiga spit out a error message saying "Error while opening video device /dev/video1". 

Thanks for the help so far codename :)

---

### Post by KhaaL on 2008-08-29
bumping

---

