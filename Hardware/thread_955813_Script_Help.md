---
title: "Script Help?"
date: 2008-10-22
forum: Hardware
---

### Post by hightimesx420 on 2008-10-22
I finally decided to use the ndiswrapper to install the wireless driver for my laptop. Now, i need a little help making a script so that Linux run the driver automatically so i don't have to enable it every time... the driver is a Broadcom 4321/2AG 802.11a/n/g/n and the file name for it is bcmwl6.inf.... another information needed for this to be done?

---

### Post by Sub101 on 2008-10-22
what is the command you normally type into the terminal?

---

### Post by hightimesx420 on 2008-10-22
nm-applet

---

### Post by Sub101 on 2008-10-22
So you don't activate ndiswrapper from the command line?

---

### Post by hightimesx420 on 2008-10-22
i dunno.... here's what i do, when it starts up i go to Hardware Drivers

then i click in the little check box for the Broadcom STA Driver

---

### Post by Sub101 on 2008-10-22
Ok so been looking into it. And:

```
    * Install ndiswrapper-utils if not already installed from previous attempts - as described above (ndisgtk is not needed when using the command line).
    * Create a directory (folder) off your home directory and name it something suitable - (we shall use wifi) and copy the .inf and .sys files from your Windows driver (see above)
    * Open a terminal window and enter the following commands:-
    * cd wifi
    * sudo ndiswrapper -i <name>.inf  (make <name> the name of the .inf file)
    * cd /etc/ndiswrapper/
    * sudo modprobe ndiswrapper
    * sudo echo ndiswrapper >> /etc/modules
    * sudo iwconfig  (from the list get the name of the wireless connection and if not wlan0, replace wlan0 with your system's name in the commands below)
    * sudo iwlist wlan0 scan (look for your access point in the list)
    * sudo iwconfig wlan0 channel <X> essid <ESSID> mode Managed (the X and ESSID should come from the iwlist)
    * sudo ifup wlan0
```

This is from: [http://www.ginad.org.uk/NDISwrapper.html]("http://www.ginad.org.uk/NDISwrapper.html") 

So to create a script from this would be something like:

```

#!/bin/bash
# sudo ndiswrapper -i <name>.inf

```

I would say this would work. However I have never used Ndiswrapper so can not guarantee it.

---

