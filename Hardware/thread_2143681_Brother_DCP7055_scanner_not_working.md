---
title: "Brother DCP7055 scanner not working"
date: 2013-05-09
forum: Hardware
---

### Post by skippybaker on 2013-05-09
My Brother DCP 7055 AIO will not scan. I can print ok, but the scanner won't work. I have installed brscan -4.0.4.1-4.i386.deb, & brscan-skey-0.2.4-0.i386.deb following the terminal instructions given on the forum ([http://ubuntuforums.org/showthread.php?t=590793&](http://ubuntuforums.org/showthread.php?t=590793&)), but it still won't install. I have tried uninstalling, then re-installing, but still get the same outcome.

For some reason in Synaptic Package Manager, the only entries under Brother are the lpr, cupswapper, & brscan-skey files, the Br scan file is not listed.

Simple scan reports "unable to connect to scanner, & XSane reports " failed to open device 'brother 4: bus 11; dev1': Invalid Argument.

I have tried numerous times to get the scanner running, to no avail.

On the installation thread [http://ubuntuforums.org/showthread.php?t=590793&](http://ubuntuforums.org/showthread.php?t=590793&), when i get to step 6 ([COLOR=#000000][FONT=Ubuntu Mono]sudo gedit /etc/udev/rules.d/45-libsane.rules) the 45-libsane.rules opens but is entirely blank.
Any help greatly appreciated

Nick

[/FONT][/COLOR]

---

### Post by gifford on 2013-05-09
What version of Ubuntu are you using? Is the printer connected to your computer via USB or is it on a network?
Without knowing any of the above, I would suggest you uninstall then go to the Brother website here:[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)
and follow the instructions they give for scanner installs. Also, first try the install without the brscan skey.
In my experience, the information given at the Brother site has always been the best.
The link you used is a bit outdated.

---

