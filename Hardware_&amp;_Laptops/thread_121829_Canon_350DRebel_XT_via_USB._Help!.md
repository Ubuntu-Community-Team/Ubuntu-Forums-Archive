---
title: "Canon 350D/Rebel XT via USB. Help!"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by skp on 2006-01-26
I have a digital SLR camera, Canon 350D (european name) / Rebel XT (US name). I've checked the Canon website and they dosn't support any Linux drivers. I also googled a little in the subject but i didn't really get anyware.

When I connect the camera via the USB interface then nothing happens. I turn on the camera and nada. I go by the 'System Settings -> Digital Camera' and there I have added the 350D found in the list. I tried once more, plugged in the USB-cable and pushed the ON-switch on the camera. Nothing.

So I don't have any other USB device except my mouse which is working properly. 

So, what do I do?  
I ran 't*ail -f /var/log/syslog*' and i got when switching it on:

*'Jan 26 08:23:57 localhost kernel: [4297696.188000] usb 5-5: new high speed USB device using ehci_hcd and address 4'*

Can I just mount /dev/ehci_hcd? And what FS?

---

### Post by skp on 2006-02-02
sorry for bumping, but I still have the same problem :/ 
this is one major problem for me, if I can't get some sort of fix I have to continue to use windows 2k/xp in some way.

---

### Post by hw-tph on 2006-02-02
I have the exact same camera. It works well for me. I installed the gphoto2 packages and I can now import the photos from the camera using gThumb.


Håkan

---

### Post by skp on 2006-02-07
[QUOTE=hw-tph]I have the exact same camera. It works well for me. I installed the gphoto2 packages and I can now import the photos from the camera using gThumb.


Håkan[/QUOTE]


Tack!

Okay, I checked now, via SSH to my computer, and I have the gphoto2 package. I tried a ```
apt-get install gphoto2*
``` and it installed a bunch of libraries. I will try it again when I come home this afternoon.

If I resolve this problem I am truly happy :)

---

### Post by skp on 2006-02-08
this didnot resolve the problem. gtkam dosen't detect the camera when i click the detectbutton. If i choose an USB port in the dropdown menu and my camera in the first dropdown menu, gtkam reports 'Could not initialize camera'.

As written in the first post of this thread the information about which usb port is probably in /var/log/syslog but i don't now what to do with the info.

Help?!

---

### Post by hw-tph on 2006-02-08
First off, does your camera get detected at all? Type **dmesg** and have a look at the last few lines for reference. The plug in the camera and turn it on. Type dmesg again and see if there is any information regarding the camera.


Håkan

---

### Post by skp on 2006-02-08
```
[4591911.395000] usb 5-4: new high speed USB device using ehci_hcd and address 9
```

This is what 'dmesg' reports. It's pretty much the same as what I get when i run ```
tail -f /var/log/syslog
```
and connect the camera (and turn it on) except it isn't in the same USB-port.

Is it possible to mount the camera using 'mount'?

---

### Post by wesman83 on 2006-02-10
Try using a different USB port if you have one.

---

### Post by nymphaeles on 2006-02-10
I don't really have a solution..
However, if you get a USB card reader ($10 USD), it's going to be much easier.  That's how I transfer photos from various cameras to my files server.

Cheer!

---

### Post by skp on 2006-02-15
**I solved it!**

And I can say that it had nothing to do with Ubuntu.

The problem was in the camera. The gphoto2 package only supports the 350D in PTP mode. This picture to picture mode or what's its name has to be enabled in the camera settings. After doing this it worked perfectly fine! I don't now if the restriction to only the PTP protocoll lies in the camera and I should blame Canon for it or if it has something to do with the software and I should blame someone else for it. But in the end it's a clear RTFM on myself. 

(Canon 350D (european) = Canon Digital Rebel XT (US) = Canon EOS Kiss Digital N (japanese)

---

### Post by aCiD99 on 2006-06-10
[QUOTE=skp]**I solved it!**

And I can say that it had nothing to do with Ubuntu.

The problem was in the camera. The gphoto2 package only supports the 350D in PTP mode. This picture to picture mode or what's its name has to be enabled in the camera settings. After doing this it worked perfectly fine! I don't now if the restriction to only the PTP protocoll lies in the camera and I should blame Canon for it or if it has something to do with the software and I should blame someone else for it. But in the end it's a clear RTFM on myself. 

(Canon 350D (european) = Canon Digital Rebel XT (US) = Canon EOS Kiss Digital N (japanese)[/QUOTE]

Awesome, this was my exact issue as well. Great work.

---

