---
title: "Nvidia driver not showing"
date: 2008-11-11
forum: Hardware
---

### Post by Cuttysark on 2008-11-11
I just fitted the Geoforce 9500GT to take the place of the onboard graphics in my machine. I used EnvyNG to download and install the driver. Everything went smoothly and I recieved no error messages, I even have an entry in System/Administration called Nvidia x Server Settings, but when I open Hardware Drivers, I get an empty box and it tells me that no proprietory drivers are in use, and I still getting the same greying out of open windows from time to time. I'm running Hardy and Compiz is active.

---

### Post by phidia on 2008-11-11
If you install through envy I don't believe the package manager and therefore the hardware driver applet will recognize that install method.

You could look at the driver listed in the device section of /etc/X11/xorg.conf it may or may not be listed in 8.04. It's not listed in 8.10 anymore.

---

### Post by Cuttysark on 2008-11-12
Okay, I took a look and there is a section that says

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"

so I have to assume it's installed (please don't laugh, I really am that much of a novice). If this is the case though, why do I still get windows greying out sometime. When I first installed 8.04, my computer had only 500Mb memory and onboard graphics. I've since upgraded my memory to 2Gb and fitted the graphics card, which has 500Mb of its own memory

---

### Post by phidia on 2008-11-12
You're lucky you are running 8.04 because with a manually installed video driver in 8.10 I don't know where you would look to see the driver-it isn't in xorg anymore.

Anyway with 500MB of video ram I don't know why you would have any trouble.
Maybe the driver you are using isn't the right match for the 9500 card?

See the [Ubuntu nvidia video wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") for more detailed help and also the the Nvidia Manual from the section titled "See Also".

I have also seen problems with 8 & 9 series nvidia cards so if none of the above works perhaps you should search the multimedia & video forum. My search for 'nvidia 9500" is [here]("http://ubuntuforums.org/search.php?searchid=51402701").

---

