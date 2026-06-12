---
title: "use microphone from a usb webcam when plugged"
date: 2010-03-20
forum: Hardware
---

### Post by Rommidze on 2010-03-20
Here is the solution on how to switch sound input onto a usb webcam bundled microphone whenever it is plugged in.

Here is the script for the pulse audio which tries to find a first available usb input. In your home directory make a folder named bin and place contents in that directory in the file named pasetvebcam.sh

```
#!/bin/bash

# Wait for the cam to be available for the pulseaudio
sleep 2

# Get the name of the device, since it is the only usb based input on my installation.
NAME=`pacmd list-sources | grep -E 'name: <.*usb.*>' | head -n 1 | sed -e 's/\sname: <\(.*\)>.*/\1/'`

# Volume for the mic to be set on
VOLUME=100000

# Should it be muted?
MUTE='false'

echo "set-default-source $NAME" | pacmd
echo "set-source-volume  $NAME $VOLUME" | pacmd
echo "set-source-mute    $NAME $MUTE" | pacmd
```

Next open the "System > Preferences > Removable Drives and Media" dialog. Activate the "Edit video when connected" and put this as the Command:
```
bash ~/bin/pasetvebcam.sh
```

If you don't have "Removable Drives and Media" option, check that gnome-volume-manager package is installed.

This is all. Mic should switch to the cam one once you plug it in.

---

### Post by Doug11 on 2010-03-21
I don't have a removable media and drives in my preferences menu.

---

### Post by Rommidze on 2010-03-23
> **Doug11 said:**
> I don't have a removable media and drives in my preferences menu.

I've made an update: "If you don't have "Removable Drives and Media" option, check that gnome-volume-manager package is installed."

---

### Post by Doug11 on 2010-03-23
Thanks,,i'll try that and see how it goes.

---

### Post by riseringseeker on 2010-12-08
> **Rommidze said:**
> I've made an update: "If you don't have "Removable Drives and Media" option, check that gnome-volume-manager package is installed."

10.04 no longer has gnome-volume-manager as an installation candidate.  Another perhaps?

---

### Post by Rommidze on 2010-12-08
> **riseringseeker said:**
> 10.04 no longer has gnome-volume-manager as an installation candidate.  Another perhaps?

Unfortunately it looks like there isn't any. So I am left without this nice feature.

---

