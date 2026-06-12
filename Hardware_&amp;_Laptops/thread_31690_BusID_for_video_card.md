---
title: "BusID for video card?"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by momo66 on 2005-05-04
What command do I use to determine BusID for my video card.  I have two video cards that I need to define in my xorg.conf file.   

See excerpt from a sample xorg.conf file below.  I have one PCI card and one AGP card.  thanks for your help.

Section "Device"
Identifier "G400_1"
Driver "mga"
[COLOR=Blue]BusID "PCI:1:0:0"[/COLOR]
#Screen 0
EndSection

Section "Device"
Identifier "G400_2"
Driver "mga"
[COLOR=Blue]BusID "PCI:1:0:0"[/COLOR]
#Screen 1
EndSection

---

### Post by momo66 on 2005-05-04
Found my answer from a How TO that was just posted.

[http://www.ubuntuforums.org/showthread.php?t=31686](http://www.ubuntuforums.org/showthread.php?t=31686)

see excerpt below

> My first card uses nvidia driver and as such uses nvidia driver specific Options. You can delete that on your secondary if it uses different driver.
Now you need the specific info of your secondary device, the driver and the BusID. First, to figure out the BusID, you have to a specific X command. X creates a lock file on you /tmp directory that don't allow you to run any other X command on top of your X session. To overcome this you run:

```

sudo mv /tmp/.X0-lock ~/.X0-lock

```
[note: I just move the file, so that you can replace it back again after running that specific X command]

Now you run the command to find your info:


```
sudo X -scanpci
```



---

### Post by nad on 2005-05-04
The command: lspci  will show the bus id of all pci connected devices in your system.

---

