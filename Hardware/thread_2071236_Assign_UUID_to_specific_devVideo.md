---
title: "Assign UUID to specific /dev/Video?"
date: 2012-10-14
forum: Hardware
---

### Post by MrDaveInUSA on 2012-10-14
So I am setting up a simple security system with Motion and the issue that I am having is that when the computer is rebooted, the camera that was previously assigned to /dev/video0 is now /dev/video1 and vice versa for the other camera attached.  

My question is whether there is anyway to assign a specific USB port (these are webcams) or UUID to be video0, or video1 (I am assuming that there is a UUID or something similar for webcams).   

Running Xubuntu 64, 12.04 
Thanks.

---

### Post by addison.merchut on 2013-01-24
(Bump)

Ever figure this out?

---

### Post by steeldriver on 2013-01-24
you could write a udev rule to create a custom /dev/xxx symlink for each device - provided there is some device attribute that identifies each uniquely

---

### Post by addison.merchut on 2013-01-24
Yeah, that's exactly what I was thinking. However, I have no idea what attribute I can use that is different between 2 webcams of the same make/model.

Ideas?

Thanks

---

### Post by addison.merchut on 2013-01-24
Just to make this a little more interesting, let's say you're connecting your webcams through a USB hub.

---

### Post by addison.merchut on 2013-01-25
Ok so I finally figured this out. 

To be clear, I wanted to control multiple (usb) webcams of the same make and model. The I ran into problems whenever I unplugged and then plugged back in the webcams; the /dev/video* might change.

Furthermore, in my setup 3 of my webcams are on one USB hub, and the other 2 are on another hub, and all going to the same computer. ...No I'm not a voyeur. 

--Do everything in root--

First you need to use udevadm to find out everything you can about your webcam(s). There's other ways to find out info, but this is what I did

```
udevadm info -a -p $(udevadm info -q path -p /class/video4linux/video0)
```

Where the video0 matches the /dev/video0 webcam I wish to probe. If you probe the wrong location, then your command prompt will return some complaint about "-p".

When you run udevadm correctly it will spit out a ton of info about every physical "thing" that is connect along the video0's path. For me, the devices were as follows:

 ```
 looking at device '/devices/pci0000:00/0000:00:13.2/usb2/2-4/2-4:1.0/video4linux/video0':
    KERNEL=="video0"
    SUBSYSTEM=="video4linux"
    ...

  looking at parent device '/devices/pci0000:00/0000:00:13.2/usb2/2-4/2-4:1.0':
    ...
    
  looking at parent device '/devices/pci0000:00/0000:00:13.2/usb2/2-4':
    ...
    ATTRS{serial}=="520EE700"

  looking at parent device '/devices/pci0000:00/0000:00:13.2/usb2':
    ...
    
  looking at parent device '/devices/pci0000:00/0000:00:13.2':
    ...
    
  looking at parent device '/devices/pci0000:00':
    ...
```

From what I can deduce, the top 3 items are part of the webcam. The 4th item is obviously (part of) the hub, and after that I don't care (I actually don't have to care about the hub either). 

The important parts of this digging are the SUBSYSTEM=="video4linux", in the first grouping. And then the ATTRS{serial}=="520EE700" in the third grouping. The "ATTRS{serial}" was the only item that was different between my webcams (See note at the bottom).

Now to write some udev rules. I made a new file in /etc/udev/rules.d/ and called it "15-addison.rules". Use a lower number like (<20) so that if there is another rule file (say 60-whatever.rules) that talks about your usb, it will be ignored.

The rules I used are of the form: 

```
SUBSYSTEM=="video4linux", ATTRS{serial}=="A52EE700", SYMLINK+="camright"
SUBSYSTEM=="video4linux", ATTRS{serial}=="E966A1E0", SYMLINK+="camtleft"
SUBSYSTEM=="video4linux", ATTRS{serial}=="6903B710", SYMLINK+="cambleft"
SUBSYSTEM=="video4linux", ATTRS{serial}=="520EE700", SYMLINK+="camsec1"
SUBSYSTEM=="video4linux", ATTRS{serial}=="111EE700", SYMLINK+="camsec2"
```

First, check your rules using 

```
sudo udevadm --debug test /sys/class/video4linux/video0
```

I gather that SUBSYSTEM=="video4linux" and ATTRS{serial}=="RandomNumber" are the filters that the rule uses and SYMLINK+="whatever" is the fixed location I've created. IE the rule says, if something is plugged in and it has this SUBSYSTEM and this ATTRS{serial}, then make a symbolic link to "whatever". Now,  I can always find the camera with  ATTRS{serial}=="A52EE700" at /dev/camright.

However, the /dev/video* also exists for each of the cameras also. When using the webcam security program "Motion" I can just point my config files to my custom dev locations. When I tried to use vlc (via the GUI) to look at my custom dev location, it wouldn't work. So yeah, got me. 

The Note: I assume that ATTRS{serial} is something supplied by the webcam and not assigned by my computer. That being said, I have restarted my computer and nothing changed about those serial id's...


I hope this helps people. This was something that was bugging me for a long time and because I also have 6 arduino's hooked up to one computer (solved that one with EEPROM ;) ), it's nice to have a better command of my usb's.

---

