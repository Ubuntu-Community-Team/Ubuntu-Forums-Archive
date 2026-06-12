---
title: "Bluetooth Headset Support"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by aeg1s on 2007-11-11
After weeks of trying to get my PLT 510 Bluetooth headset working with Ubuntu 7.10 Gutsy Gibbon, I've determined that the capability is broken.  From my research, it appears to have worked in Fiesty Fawn.  That was utilizing an application by Stephane Graber called 'gbtsco' and forcing Fiesty to accept it.  Unfortunately, it appears that the necessary module snd_bt_sco is not part of Gutsy anymore, so it rendered that work around useless.  Never having tried it on Fiesty, I do not have first hand knowledge of how well gbtsco worked, but from all reports it did so satisfactorily.

Is blueooth headset support something that most users of Ubuntu would like to see?  Maybe if there is enough interest they will incorporate it into the next release.  Bluetooth on Ubuntu is almost as painful as setting up the video driver (thank God for Envy!), which is only slightly less difficult than configuring the sound card drivers.

I realize that most of the problems lie with hardware manufacturers not supplying drivers for Linux...  But until it doesn't take a week to get the video working properly, or the sound to work (crippled at best), and there is at least SOME workable solution for bluetooth, then I think there will continue to be a reason to maintain a windows machine/partition.  

My Pocket PC can do all of those things better. =)

---

### Post by John Jason Jordan on 2007-11-13
> **aeg1s said:**
> Is blueooth headset support something that most users of Ubuntu would like to see?  Maybe if there is enough interest they will incorporate it into the next release.  Bluetooth on Ubuntu is almost as painful as setting up the video driver (thank God for Envy!), which is only slightly less difficult than configuring the sound card drivers.
I am currently looking for bluetooth stereo headphones. I want them studio quality for music, not for a phone. I have listened to the Sony DR-BT50 at a local Sony store and the sound is awesome. However, they demonstrated them to me using a Sony Vaio laptop with Vista. Since the demo I have searched the net from top to bottom looking for any reports of using these headphones with Linux, but nada. I do have bluetooth on my Thinkpad T61 with Gutsy, and it appears to be working. I just don't want to spend $141 (best price, Amazon) for the DR-BT50 only to discover that they are worthless.

There is another store here that sells them and they'll give me a 30-day return privilege. They're 30 km in a distant suburb and there is no bus service. But I might make the trip just to see if they work.

Meantime, I wish I knew more about how bluetooth works, and I wish there were better online lists of products that work and products that don't work.

---

### Post by MrFSL on 2007-11-13
> After weeks of trying to get my PLT 510 Bluetooth headset working with Ubuntu 7.10 Gutsy Gibbon, I've determined that the capability is broken. From my research, it appears to have worked in Fiesty Fawn. That was utilizing an application by Stephane Graber called 'gbtsco' and forcing Feisty to accept it. Unfortunately, it appears that the necessary module snd_bt_sco is not part of Gutsy anymore, so it rendered that work around useless. Never having tried it on Feisty, I do not have first hand knowledge of how well gbtsco worked, but from all reports it did so satisfactorily.

gbtsco never worked for me. I use a iogear GBU211 USB BlueTooth dongle with a Nokia BH-300 bluetooth headset. I worked hard using every howto I could find but could not get it working.

In particular I was trying to get this working for Skype. Finally, I wrote a script that works every time on my machine. Part of it just outputs information for me to make sure things are detected and my settings haven't changed. I don't know about Gutsy but perhaps it can be adjusted to work for you as well.
```

echo Skype Bluetooth Headset 
echo              by.fsl
echo

# Restart Bluetooth
sudo /etc/init.d/bluetooth restart
sleep 3

# Load The Module For Voice
sudo modprobe snd-bt-sco

# Scan For BlueTooth Devices
hcitool scan

# Channel Of Device - Ex. *sdptool search --bdaddr 11:22:33:44:55:66 HS | grep -i chan*
sdptool search --bdaddr ***<MAC ADDRESS FROM ABOVE>*** HS | grep -i channel

# Put It Together - Ex. *btsco 11:22:33:44:55:66 8*
btsco ***<MAC ADDRESS FROM ABOVE>*** ***<CHANNEL# FROM ABOVE>***
bash
```

---

