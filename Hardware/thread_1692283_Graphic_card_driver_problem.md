---
title: "Graphic card driver problem"
date: 2011-02-21
forum: Hardware
---

### Post by alcoder on 2011-02-21
Hello

I have Ati raedon HD2400XT graphic card.

I have tried to install the proprietary driver using "System->Administration->Additional drivers". But something went wrong because after restarting the computer the graphical system did not load. I only had a black screen and some text on it saying me to to log in. So I have tried to revert back somehow and I followed the instructions in [http://ubuntuforums.org/showthread.php?t=1573177](http://ubuntuforums.org/showthread.php?t=1573177). I also removed the xorg.conf. After removing xorg.conf everything worked as originally.

I tried to install the driver manually by this tutorial: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)
After restarting my computer I did get again the black text screen.
I have logged in. I wanted to view the xorg.conf file. When I started to type "cat /etc/X11" somehow the graphical system has loaded. I don't know how.. I didn't press [enter]. 
I have restarted my computer and the black text screen has loaded again :(, but after logging in and typing "cat /etc/X11/" the graphical system has loaded again.

So I think there is only a little error somewhere. Could anyone help me? :confused:

---

### Post by alcoder on 2011-02-21
So.. after turning on the computer the GUI wont load. The whole screen is only a terminal. But after 3-4 minutes the GUI automatically loads and my new driver is used.
But why is this happening?
Why isn't the GUI loaded immediately?

I have tried to add

```
$ start on filesystem
$
$ script
$    chmod 0666 /dev/null
$    chmod 0666 /lib/udev/devices/null
$ end script
```or setting tls to 0 as explained here [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Problems_Starting_Xserver](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Problems_Starting_Xserver) but nothing helped.

---

### Post by alcoder on 2011-02-21
Please, can someone help?

---

### Post by alcoder on 2011-02-21
Owww

This is a bug...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/631933](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/631933)

---

### Post by alcoder on 2011-02-21
The workaround/solution [https://bugzilla.novell.com/show_bug.cgi?id=634642](https://bugzilla.novell.com/show_bug.cgi?id=634642) works!!! I hope that no more problems will occur.
:D:D:D:D:D:D:D

---

