---
title: "SONY VAIO MOTION EYE Camera Driver"
date: 2008-06-10
forum: Hardware
---

### Post by SamerBerjawi on 2008-06-10
Guys I have Hardy and my cam doesn't work. I think it needs a driver.
My laptop is Sony VAIO VGN-CR23G.

There are also some multimedia bottoms (Play/Pause, Stop, and Skip) aren't working.

Can anyone help me?

---

### Post by linuxwizard on 2008-06-10
Try using Ekiga see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2 or if it shows V4L2 change to V4L.) 

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga didn't work post results of the command > lsusb

---

### Post by SamerBerjawi on 2008-06-12
LinuxWizard, the cam didn't work with Ekiga..
Here's the lsusb:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 05ca:1839 Ricoh Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 044e:300d Alps Electric Co., Ltd 
Bus 001 Device 001: ID 0000:0000

---

### Post by linuxwizard on 2008-06-12
This is the driver you need than > [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870) > your cam > ID 05ca:1839 Ricoh Co., Ltd  > listed as supported > [http://wiki.mediati.org/Supported_Devices](http://wiki.mediati.org/Supported_Devices).

---

### Post by oyuka on 2010-09-17
HI i am also having same problem with my vaio vgn-cr23g laptop. I installed Ubuntu 10.04 LTS. My camera is not working after installing ubuntu. It shows this when i run 'lsusb' command. please help!


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 044e:300d Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:1839 Ricoh Co., Ltd Visual Communication Camera VGP-VCC6 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

