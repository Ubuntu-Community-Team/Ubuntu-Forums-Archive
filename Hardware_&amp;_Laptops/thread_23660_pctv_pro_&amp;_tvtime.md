---
title: "pctv pro &amp; tvtime"
date: 2005-04-03
forum: Hardware &amp; Laptops
---

### Post by bassMonkey on 2005-04-03
Hi again,
I'm fighting with tvtime to get my tv-card working, what do I have to do to accomplish that? I installed tvtime with 'sudo apt-get install tvtime' I then did a 'sudo modprobe bt878'. Then I started tvtime as root but all it says is no signal so i guess the driver is not working, also /dev/video0 does not exist.  ](*,) 

anyone feel like helping a noob out?

Update: Apparently the card is detected: 
```
root@bassstation:/home/fgrano # lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
0000:00:0c.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
0000:00:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 01)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06 )
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4400] (rev a3)
root@bassstation:/home/fgrano # lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
[B]0000:00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)[/B]
0000:00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
0000:00:0c.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
0000:00:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 01)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4400] (rev a3)
root@bassstation:/home/fgrano #
```

---

### Post by humanity_to_others on 2005-04-08
You should add your card number in /etc/modules

---

### Post by lin-ex on 2005-06-10
The previous message on this thread was true, but did not completely tell you what to do. The message stated that the card must be added to the /etc/modules.conf, but did not say how. Furthermore that is only half the equation.  Yes, the appropriate modules must be added for the card to work.  You were loading the module that as far as I am aware does not exist, the modules that are needed for the card to work are bttv and tuner.  This modules are for the video capture portion of the card.  This modules will probably also need to be passed the appropriate options in order to work properly.  (eg. bttv -card=xx - tuner=x -automute=0) Add this line to /etc/modules.conf, or pass them as commandline parameters to modprobe. To find out the values for card and tuner, refer to the bttv cardlist.  The second half is the audio which is unfortunately much tricker then the video portion.  If you are lucky, the bttv module will scan for known audio muxers when loaded and initialize it.  If this is not the case then you can try other modules, but I cannot guarenttee the results since manufactuers of these cards did not standardize on the chipsets, memory locations and precisely how the audio is captured.  For instances, many manufacts. capture audio via a four pin audio cable, some capture audio in mono format and others in stereo.  In any case the relevant modules here are tvaudio, msp3400, tea6400 among others.  I would suggest reading the description for these by executing #modinfo tvaudio etc.  Lastly you mention that the /dev/video0 does not exist, and indeed it would not without the appropriate modules loaded, but the device might not show up on its own unless you are running devfs. If the device does not appear, you might have to create it with the mkdev command.

Hope that you this was helpful and that I did not type this in vain.

---

