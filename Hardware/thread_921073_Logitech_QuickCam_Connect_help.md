---
title: "Logitech QuickCam Connect help"
date: 2008-09-15
forum: Hardware
---

### Post by logicalyrandom on 2008-09-15
I recently purchased a Logitech QuickCam Connect, and after installing gspca, camstream, and Camorama, I still can't get it to work. Camorama returns the error message: 
> "could not connect to video device (/dev/video0). Please check connection." I've transfered the camera to three different USB ports, to the same result. Camstream just shows up as a grey screen, and doesn't recognize the camera either. I'm running 8.04. Any suggestions on getting the thing to work would be greatly appreciated, and thank you in advance.

---

### Post by Crafty Kisses on 2008-09-15
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by logicalyrandom on 2008-09-16
ok, I tried the Ekiga to no avail, and here is the lsusb output: 

> 
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 03f0:6511 Hewlett-Packard 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:089d Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


---

### Post by logicalyrandom on 2008-09-17
bump.

---

### Post by logicalyrandom on 2008-09-18
bump again. 

Also, I tried skype, and under "video devices" none were found, but the sound-in and sound-out recognise the presence of the built-in microphone. They don't work during a call though, so I'm wondering if I have a bad camera.

---

### Post by logicalyrandom on 2008-09-20
bump

---

### Post by IntuitiveNipple on 2008-09-21
Did you build the gspca driver with the device ID patched in [as discussed in this thread](http://forums.quickcamteam.net/showthread.php?tid=310&pid=1949#pid1949)?

---

### Post by IntuitiveNipple on 2008-09-21
I've created a [gspca DKMS package for Hardy](http://ubuntuforums.org/showthread.php?t=926101) with support for this camera, try it with your camera.

---

