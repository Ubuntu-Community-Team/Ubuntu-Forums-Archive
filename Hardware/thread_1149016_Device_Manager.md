---
title: "Device Manager"
date: 2009-05-04
forum: Hardware
---

### Post by gr8108 on 2009-05-04
Hi. I tried the Ubuntu LiveCD and I looked for a device manager (such as windows one) but didn't find it. Is there any kind of it in Ubuntu? Or, how can I know whether all my hardware was recognized propertly?
 
Thanks a lot.
 
nGeeN

---

### Post by jodef on 2009-05-04
If you have managed to configure internet access you could install something similar via Synaptic:

System -> Administration -> Synaptic  do a search for device manager and install the package gnome-device-manager.

If you do not have internet access run the following command from the Terminal:

access the Terminal as follows: Applications -> Accessories -> Terminal

```
sudo lshw
```

HTH:)

---

### Post by mikedep333 on 2009-05-04
Hey,

There is gnome-device-manager, atlhough it is pretty technical I think. You can install that through synaptic package manager, or from the terminal with:
```
sudo apt-get update
sudo apt-get install gnome-device-manager
```

The other option is to just test everything on your system yourself. Run some video and audio files from the example folder under your home/ubuntu directory. Connected to a wired and wireless network. If the bluetooth icon shows up top, that means it's working. Install the program "cheese" to see if your webcam works.

---

### Post by RedSingularity on 2009-05-04
Yeah i would recommend that one also.  It has A LOT of details about your system hardware.

---

