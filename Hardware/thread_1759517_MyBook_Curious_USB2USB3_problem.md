---
title: "MyBook Curious USB2/USB3 problem"
date: 2011-05-15
forum: Hardware
---

### Post by Abaddon on 2011-05-15
I've recently built a new system and (after some major dramas) managed to get a new install of natty dual booting with Win7 Pro.

I have an ASRock P67 Extreme6 motherboard with USB3 support, and I have a Western Digital MyBook 2Tb external hard drive.

It works no problems under Windows 7 plugged into one of the USB3 ports on the back of the case, but it doesn't work in Natty.  I have been investigating and have noticed that some people are finding that the cable is too long and are getting volt-drop causing the WD drives not to work.

It does work, though, if I plug it into one of the USB2 ports on the front of my case, but not the USB3 front ports.

This makes me think its a problem with Natty and USB3 rather than the cable or the drive.

Help would be much appreciated.

---

### Post by Hulles on 2011-06-02
See these posts:

[http://ubuntuforums.org/showthread.php?p=10832032](http://ubuntuforums.org/showthread.php?p=10832032)
[http://ubuntuforums.org/showpost.php...8&postcount=15](http://ubuntuforums.org/showpost.php...8&postcount=15)

This worked great. My USB 3.0 port on my ASUS G73SW now functions and handles my external drive. Btw, the second post is the more succinct answer if you know what you're doing. Also btw, I used the "pci=msi" without the "aer" param.

I hope this helps. And I posted the above in a couple other places so people don't go as crazy as I did with this problem. Now I can mop up the drool on the floor....

---

### Post by sarahsharp on 2011-06-02
If you have a problem with USB 3.0, you probably should ask on the linux-usb mailing list instead of the Ubuntu forums:

[http://www.linux-usb.org/mailing.html](http://www.linux-usb.org/mailing.html)

I'm the USB 3.0 kernel maintainer, and someone already reported an issue with the ASRock motherboard (that won't be solved by the suggestion to disable MSI).  Do you think you could recompile your kernel with these patches?

[http://marc.info/?l=linux-usb&m=130696372401437&w=2](http://marc.info/?l=linux-usb&m=130696372401437&w=2)
[http://marc.info/?l=linux-usb&m=130696370101405&w=2](http://marc.info/?l=linux-usb&m=130696370101405&w=2)

I believe that will solve your issues with the USB 3.0 port.

[Hulles]("http://ubuntuforums.org/member.php?u=442467"): not all USB 3.0 host controllers need to have MSI disabled.  Just the Fresco Logic host controllers (the ones with PCI vendor ID 0x1b73 and device ID 0x1000).  I should be able to skip MSI enabling for that host controller in the xHCI driver, and that patch should make it into all the stable kernels.

---

