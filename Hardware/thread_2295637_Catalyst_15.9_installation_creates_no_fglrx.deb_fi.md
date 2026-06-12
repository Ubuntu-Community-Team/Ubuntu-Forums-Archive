---
title: "Catalyst 15.9 installation creates no fglrx*.deb files"
date: 2015-09-20
forum: Hardware
---

### Post by micha2358 on 2015-09-20
Hi,

I'm trying to install the new Catalyst 15.9 driver.
With the command "sudo ./amd-catalyst-15.9-linux-installer-15.201.1151-x86.x86_64.run --buildpkg Ubuntu/utopic", the system tries to produce the .deb files. But when the system completed the task after about 4 minutes, I can't install the driver with "sudo dpkg -i fglrx*.deb", because there are no .deb files!
It always worked with previous Catalyst packages, so I have no idea why it doesn't work this time.
Why has the Catalyst package problems to save the produced .deb files?
Any ideas?

Would be happy to hear some suggestions!

---

### Post by bernie4 on 2015-09-20
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by Yellow Pasque on 2015-09-20
There's not a lot to go on here. Do you have a log file or any terminal output from the command? Check /usr/share/ati/fglrx-install.log

Also, before anyone else tells you, Utopic/14.10 is now at end of life (EOL).

---

