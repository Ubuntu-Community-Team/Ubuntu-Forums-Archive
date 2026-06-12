---
title: "OverClocking and Ubuntu, temp monitoring."
date: 2008-07-04
forum: Hardware
---

### Post by adaemman on 2008-07-04
Hey guys well I got an e2180 @ 9*333 which should =3.0ghz, but for some reason Ubuntu tells me it's at 3.3ghz. Here are my system specs.

e2180
Gigabyte P35 DS3L board v2
HD 3850 with 256mb ram
160 maxtro 7200rpm 1.5gb/s Sata drive
Samsum 22x dvd burner.

So i'm trying to find an application that can let me monitor my temps. I tried running coretemp .92 with wine but that doesn't even detect any temps. Before I made the switch I was running xp pro sp3. I also have everest which would normally give me all my system stats, but for some reason the temps aren't being detected from the proc or hd's or the fan speeds. 

Sorry if this doesn't fit here, but I didn't really know where to post. 

Appreciate your help and support.

Sorry I might as well ask, where is the disk management section like the one in windows? where you could change the drive letter, format a disk, ect.

---

### Post by ModelM on 2008-07-04
You might try adding "sensors-applet" from within synaptics. After it's installed, right click on your top or bottom panel, select "add to panel" & choose it from the list.

Once it's added, you can right click it & select "preferences" to customize it to taste.

---

### Post by Barriehie on 2008-07-04
Somewhere in the forums I saw that you can enter ***acpi -t*** in a terminal to get your temp(s).  It works on my machine.

Barrie

---

### Post by adaemman on 2008-07-04
Alright well im downloading a bunch of sensor packages i found, hope they help.

Thanks :D.

---

### Post by adaemman on 2008-07-04
Well i found the sensor-applet.. now my question is where the hell do i find it? lol im looking at the installed stuff and i can't find it anywhere... help!

when i run acpi -t i get "no support for device type:thermal".

---

### Post by adaemman on 2008-07-04
holy crap now i'm getting a  "no sensor's found!" message... only changes I made were some fans i swapped, hmm i did work with the pc plugged in once, but it was off and i touched the metal frame before digging in. Processor temp and fan speed come up no problem in bios.

---

### Post by adaemman on 2008-07-04
now "no sensors found" come up..

---

