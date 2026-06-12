---
title: "OSS/ASLA recognition of USB device: Yamaha RP U100"
date: 2005-02-25
forum: Hardware &amp; Laptops
---

### Post by loninappleton on 2005-02-25
Ok, this will take a minute:

  I loaded Ubuntu Live cd and was looking at options under
'speaker' for volume control.  The volume control panel came up and showed both of my devices: Turtle Beach Santa Cruz and Yamaha USB receiver RP U100.

  What follows is a description of what's on the Volume Control Panel tabs and which ones work, which do not:

==>  indicate a drop down series of sliders

00      indicate no accessibility to the device


   Tab One

00      USB Mixer [OSS Mixer]

    Tab Two

==> Cirrus Logic CS4297a rev 4 Cirrus [OSS Mixer]

     Tab Three

00      Yamaha RP-U100 USB udio [ASLA Mixer]

      Tab Four

==>   Sound Fusion CS46xx [ASL Mixer]


So nu?


      How do I get control of my Yamaha?


Up til now I have had no control or even any info about
the Yam being detected on a Linux load.  The software that comes with the Yam is Windows.  I have not seen anything available for Linux in any flavor and I previously 
asked around about that.  No follow up to my question was received.

---

### Post by r00 on 2005-02-28
try using alsamixer as root in the terminal..
if you read the man page on it, there's an option you can use to check
all your soundcards...

alsamixer -c #     <--the number sign is the possible sound card you have..
                               0 is the default and if you have a second, then 1 is it..

i finally got my onboard ac97 card working (mostly) but the usb extigy still has issues..
good luck with that and hope it helps..

---

