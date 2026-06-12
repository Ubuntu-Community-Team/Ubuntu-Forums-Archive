---
title: "Camera Import, accidentally chose PTP, wanted USB"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by Vogateer on 2006-10-30
I was playing around with my camera, and as I tried to import the photos into f-spot, it gave me PTP as an option for importing. I accidentally chose that instead of the USB mass storage, which is what I really wanted. Now I can't get the option back up so I can chose USB mass storage instead. There are no preferences for f-spot that I can find that deal with this, and I can only guess that there is some setting hidden away in gnome-volume-manager, libgphoto, dbus, hal, or some other backend that keeps their settings hidden from view so that I can't find them in /etc or anywhere else.

It drives me nuts when I can't find such settings, and can't find a place that will even give me a hint as to where I should look for them. I don't mind burrowing into a config file, I just need to know where to look. Anyone know a good place to start?

---

### Post by Vogateer on 2006-10-31
Okay, the choice of using PTP over USB Mass Storage must be happening in the f-spot-import script:
```

#!/bin/bash

udi="$1"
#xmessage $udi
mount_point=`hal-get-property --udi="$udi" --key=volume.mount_point`
if [ -n "$mount_point" ]; then
      # USB Mass Storage camera: need to pass f-spot a mount point
     
      f-spot --import "$mount_point"
else
     # Some other camera try GPhoto2

     bus=`hal-get-property --udi="$udi" --key=usb.bus_number`    
     dev=`hal-get-property --udi="$udi" --key=usb.linux.device_number`
     uri=`printf gphoto2:usb:%.3d,%.3d $bus $dev`

     echo $uri

     f-spot --import "$uri"
fi
```

So it must be getting the information from hal, but where do I go to change these hal properites?

---

### Post by Vogateer on 2006-10-31
Okay, I think I was able to find the problem through a search through gconf-editor. There's an xml file in the .gconf directory. I found it while using ssh at work, so unfortunately I can't test my solution until I get home. For reference, though, I'll put the XML file path on here and hopefully remember to update this thread to reflect the outcome when I get home:

```
~/.gconf/apps/gthumb/dialogs/photo_importer/%gconf.xml
```

Crossing my fingers, can't test until I get home late tonight.

---

### Post by Spano on 2006-10-31
Maybe there is a .fspot file in your home folder.
Just delete that and reconfigure your camera?

---

### Post by Vogateer on 2006-10-31
I had a similar thought, but the only thing in the *~.gnome2/f-spot/* folder was the database containing tagging information and such. Moving this file out of the directory unfortunately didn't help. Thank you for the idea, though!

If you look at the f-spot-import script above, you can see it using *hal-get-property* to figure out the mount point, and passing it on to *gthumb* if the camera isn't used a USB device. I'm pretty sure that removing my camera's *<device>* listing from the xml file described above will set things in motion again, but we'll have to wait until I get home to find out!

---

### Post by Spano on 2006-10-31
Hope you are able to solve this.  Look forward to reading the solution.  Good luck.

---

### Post by Vogateer on 2006-10-31
Well, what a failure that was. Didn't do a thing. I can't figure out the uid of my camera with HAL, because I don't know how to use it. I can't figure out where on earth this setting is, and I want to learn how to fix it, and not have to resort to clearing out all my profiles and configuration files every time something goes wrong.

---

### Post by Vogateer on 2006-10-31
Where does HAL store this information? I tried to store a mount point using *hal-set-property*, but this goes away immediately once the camera is off. I'm pretty much given up. I've googled every way I know how looking for information on HAL, but it's usually theoretical or too technical. I just can't get a setting to persist between connections using *hal-set-property*, and can't figure out where it's getting its information when I first turn on the camera.

I absolutely hate it when these settings are effectively set in stone, never to be changed unless you are very knowledgeable or willing to wipe out your home directory...

---

### Post by Vogateer on 2006-12-24
I've still found no good solution to this problem. I imagine I could completely wipe out my .gconf directory and redo all the settings I saved, but then I'm left completely ignorant of the process that caused it, and I don't care to recreate the settings I use every time something like this happens.

Please, I've created a new user, and plugged the camera in, and was able to get the import dialog again, yet even a diff of the .gconf directory of that user and my regular signon didn't reveal where this setting is kept. I'm not sure how I'm supposed to figure this out.

---

