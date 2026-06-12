---
title: "Fglrx, Ati X200M &amp; Jaunty ~ An impossible combination?"
date: 2009-05-19
forum: Hardware
---

### Post by StupidWeasel on 2009-05-19
I've recently been gifted a HP Compaq NX6325, and apart from needing to make a few tweaks regarding ALSA and also ACPI everything has been plain sailing. However I'm a greedy little weasel and I'd like to move away from the Radeon drivers and have better more support for 3D graphics. This however is my first ubuntu installation using an ATI graphics card/chip and I've had a few issues.

I initially tried installing the drivers manually and also using envyng. Both methods resulted in me getting graphic corruption & horizontal lines once X had started, and a reboot was required (unable to Ctrl+Alt+# to another terminal). After a little searching around  it appears that [support for the X200M is depreciated]("http://wiki.cchtml.com/index.php/9.4"), so that the most recent ati driver version for it is 9.3. However it also appears that the [9.3 driver is not supported by xserver 1.6]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually"). Is there a workaround for this? I'm guessing it would be either a fix/hack for xserver 1.6 or reverting to xserver 1.5*. How would I go about reverting back to xserver 1.5*, and would it cause any problems with Jaunty?

Thanks in advance folks!

---

### Post by marvlush on 2009-05-20
I have the same question...I am running Jaunty with an ATI x1400 and am in the same boat.

There is a developer who built xserver 1.5 packages for Jaunty...and it seemed to work for some people...but I tried it and could not get everything to install.

You might have better luck. Here is the link: [http://www.kdedevelopers.org/node/3942](http://www.kdedevelopers.org/node/3942)

let us know if it works for you.

/m

---

### Post by eldragon on 2009-05-20
id suggest not to downgrade, its a temp solution and you will eventually be left behind since amd does not plan to release legacy drivers for the newer xorg. just use the open source drivers. or buy something else. its really tough luck, im on the same boat, and dont plan on buying anything ati again. they've been penetrating their customers from their behind constantly....

---

### Post by marvlush on 2009-05-20
Ya, I'd probably say the same thing.

The open source driver worked for me ( sort of, see my bug here: [http://ubuntuforums.org/showthread.php?t=1165347](http://ubuntuforums.org/showthread.php?t=1165347) ) with Compiz and dual screens connected to my laptop....without even having to run a command from the command line.

But of course...it would be nice if someone got Catalyst 9.3 working on Jaunty....**somehow**. For one, because of performance...for two...power management on the open source drivers is not so good...so battery life on my laptop is noticeably worse.


/m

---

