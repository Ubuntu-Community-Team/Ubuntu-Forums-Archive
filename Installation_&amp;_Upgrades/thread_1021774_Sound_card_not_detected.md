---
title: "Sound card not detected"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by zapree on 2008-12-25
So my sound card has been working fine for about 6 months it diddnt work at first but after some tweaking i got it to perform perfectly.  It is a diamond sound card that doesnt have an ALSA driver.  Now getting to my problem i was having problems with my graphics card so i fixed that by installing these from the synaptic package manager 
Nvidia-Settings
linux-restricted-modules
after i installed these and then re-activated the driver my resolution/graphics problem was fixed but i lost sound...
I went into the ALSA control and i click on the list of devices but it doesnt give me anything as if it no long detects the card?
can someone help me out? 
Thanks Patrick

---

### Post by abn91c on 2008-12-25
in a console type aplay -l

---

### Post by zapree on 2008-12-25
btw i get this when i try and test the sound audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

---

### Post by zapree on 2008-12-25
no soundcards found :P

---

### Post by albinootje on 2008-12-25
> **zapree said:**
> So my sound card has been working fine for about 6 months it diddnt work at first but after some tweaking i got it to perform perfectly.  It is a diamond sound card that doesnt have an ALSA driver.  

Your output of "lspci" please, Sir. Thank you. :)

---

### Post by zapree on 2008-12-25
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:10.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:11.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:16.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
04:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
04:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by abn91c on 2008-12-25
try sudo modprobe snd-cm8738

---

### Post by albinootje on 2008-12-25
> **zapree said:**
> 
00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)


Here is a possible solution :
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/240094](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/240094)

And which Ubuntu release are you using by the way ?

Is your mobo listed here maybe ?
[http://hardware4linux.info/manufacturer/1690/88/](http://hardware4linux.info/manufacturer/1690/88/)

---

### Post by zapree on 2008-12-25
for the command sudo modprobe snd-cm8738 i get
[sudo] password for patrick: 
FATAL: Module snd_cm8738 not found.

That bugs thing that i checked out diddnt seem to be what i was looking for, i dont want to upgrade my kernal so that wouldnt be a good route XD but thanks all the same.

---

### Post by abn91c on 2008-12-25
> **zapree said:**
> for the command sudo modprobe snd-cm8738 i get
[sudo] password for patrick: 
FATAL: Module snd_cm8738 not found.

That bugs thing that i checked out didnt seem to be what i was looking for, i don't want to upgrade my kernal so that wouldnt be a good route XD but thanks all the same.
what about aplay -l
also try sudo modprobe snd-, hit th TAB key then enter and see if it lists your soundcard somewhere, write down the driver name then do sudo modprobe snd-yoursouncard name

---

### Post by zapree on 2008-12-26
Got asked the same thing earlier
aplay: device_list:205: no soundcards found...

---

### Post by abn91c on 2008-12-26
> **zapree said:**
> Got asked the same thing earlier
aplay: device_list:205: no soundcards found...
follow this guide, just page one.  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by executorvs on 2009-06-24
I know this thread is a bit old but if you have a C-Media card you may want to try 'lsusb' some of their chipsets go thru the usb bus and ubuntu blocks usb audio devices from grabbing the default slot.

---

