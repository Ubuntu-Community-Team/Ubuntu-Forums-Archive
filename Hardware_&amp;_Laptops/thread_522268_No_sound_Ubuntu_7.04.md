---
title: "No sound Ubuntu 7.04"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by LHoT on 2007-08-10
Hello everyone!

I am having some sound problems. (i.e. no sound)

My sound card used to work in Ubuntu 7.04, then I accidentally wiped my drive with a partitioner. So I reinstalled 6.06 and upgraded to 7.04 again, now it doesn't work. Im not sure what info you need, so....

[img]http://i99.photobucket.com/albums/l290/LHoT10820/screencap1.png[/img]

---

### Post by fredj on 2007-08-10
Open a terminal and type
cat /proc/asound/card0/codec\#*
the first line of output from this should give you the full name of your sound chip.
Also open the Alsa mixer (double click on the speaker icon). Look at the File->Change Device
menu and make sure that your stac soundchip is selected as the default device.
Then use the Edit-Preferences menu to add all the possible volume controls and switches for
both Playback and record. Make sure that everything is unmuted and suitable volume levels
are set. You can always get rid of controls you don't use later on.
Then reboot to make sure the new setting are being used.

---

