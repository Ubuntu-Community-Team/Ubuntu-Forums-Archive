---
title: "WUSB54GSC - Need Help - ndiswrapper working - cant find interface"
date: 2009-08-22
forum: Hardware
---

### Post by njhomeowner on 2009-08-22
Hi,

I am having an issue installing a Linksys WUSB54GSC (Version 2) on my Ubuntu 9.04 box. After much cursing, swearing, and stopping to do other things, I got ndiswrapper to stop crashing and recognize the adapter. (the trick was to copy some extra windows files into the ndiswrapper directory as shown here [http://www.linuxquestions.org/questi...solved-664463/](http://www.linuxquestions.org/questi...solved-664463/))


OK, so now the adapter shows up when I do an lsusb, and when I do a ndiswrapper -l it says the device is present, along with the same device ID from the lsusb)

What I need to do now, which I cant figure out is how to get the device to show up in my available list of network adapters (such as wlan0). Right now the only adapters that show up are eth3, and lo) which do not point to the adapter

Can anyone tell me how to install a new wlan0 adapter and point that adapter to the ndiswrapper drivers I just activated.

Thanks.

windows_xp_2003 njhomeowner is invisible   	
Tag This Post 	No tags yet, pleas

---

### Post by TetonsGulf on 2009-08-22
That link didn't work for me nj... did you try this resource? It's helped me on a couple of boxes with wireless problems.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by njhomeowner on 2009-08-22
Hi,

Yes, I tried that post and that was the one that actually got ndiswrapper to work.  Before that post anytime I installed ndiswrapper the machine would freeze and an lsusb would hang.

SO, I believe I have the driver working, I just need to give the driver an adapter that the system can connect to.  Right now - with the driver working, I have the same number of adapters (under ifconfig) that I did before installing the driver.

Thanks,

---

### Post by TetonsGulf on 2009-08-22
Does this how to get you nothing as well? I don't have a usb adapter so I'm not going to be much technical help, but I'll be more than happy to help you look!

[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)

---

### Post by njhomeowner on 2009-08-22
Update:

I believe the problem lies in the power settings of the USB controller.  I seem to remember somewhere that Ubuntu by default does not power USB devices to the fullest extent possible, however there is enough power to get the system to recognize the chipset and make the install.

Does anyone know how to change the power parameters of USB?

Thanks....

---

