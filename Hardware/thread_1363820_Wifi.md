---
title: "Wifi"
date: 2009-12-24
forum: Hardware
---

### Post by Marvin666 on 2009-12-24
How do I configure my wifi card, and get it to connect?
I know the ssid of the network is Local Network, and i'ts on channel 6.
Running jaunty xubuntu on the top laptop in my signature.

---

### Post by Fir3chi3f on 2009-12-24
You should see an icon like the one below, next to the time and date. If you click on it you should see your wireless and can connect to it. That will change to the second image when it is connected.

If you don't see this, then post the output of:

```
lspci
```

in a terminal

---

### Post by Fir3chi3f on 2009-12-24
oops didn't see the X in front of ubuntu. You might have to install Wicd

```

sudo apt-get install wicd
```

---

### Post by Marvin666 on 2009-12-25
Don't know how to copy and paste in a terminal, so I wrote down the two results that pertained to networking.
```

00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev 1b)
06:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network
```Also, for some reason the network controller in my tray crashed after I installed that program...
Currently using a wired connection.

---

### Post by Fir3chi3f on 2009-12-25
Sorry about that, just something else to try. You can remove it if it doesn't work or you don't like, it anyway...

Atheros cards are not well supported, I feel your pain my friend. 
Give this a try:
```

sudo apt-get install linux-backports-modules-karmic
```
And then a good reboot.

If that doesn't work, you can try this tutorial:

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Of course leaving out the wicd part.

Edit oops! your using 9.04! that code should be:
sudo apt-get install linux-backports-modules-jaunty

---

### Post by Marvin666 on 2009-12-25
No luck...

---

### Post by Fir3chi3f on 2009-12-25
Did sudo apt-get install linux-backports-modules-jaunty give any errors? What happened during the madwifi build?

---

### Post by Marvin666 on 2009-12-25
I don't remember seeing any errors, but some might have popped up...

---

### Post by Marvin666 on 2009-12-25
Okay, tried it again in a terminal from the applications menu, and got the followning errors during madwifi:
step 2:
```
 sudo apt-get update && sudo apt-get upgrade 
```
 ```
Err cdrom://Xubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages                       
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/multiverse Packages                 
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Xubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages                 
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
``````
 W: Failed to fetch cdrom://Xubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Xubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Xubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead. 
```
Step 4: ```
 sudo apt-get install linux-headers-'uname -r' 
```
```
 E: Couldn't find package linux-headers-uname -r 
```

---

