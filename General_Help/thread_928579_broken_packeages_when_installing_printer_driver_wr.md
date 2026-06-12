---
title: "broken packeages when installing printer driver wrapper"
date: 2008-09-24
forum: General Help
---

### Post by dagoth_pie on 2008-09-24
Somehow the printer driver wrapper has gotten corrupt and won't let me go into the package manager at all to try solve it, when I go into the package manager I get the following error
```
E: The package mfc240ccupswrapper needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

when I run the apt-get clean command in the terminal I get
```
E: The package mfc240ccupswrapper needs to be reinstalled, but I can't find an archive for it.

```

after that any help with getting the printer drivers working would be appreciated, but for now any help getting to the point I can reinstall the drivers would be appreciated, thanks

---

### Post by plucky on 2008-09-24
Open a terminal and ```
sudo apt-get purge mfc240ccupswrapper
``` should remove it completely.

If it doesn't,can you specify the command you used to install the .deb driver file.

Are you running Hardy 8.04? If so the Brother drivers are packaged in Synaptic,so open synaptic and search for MFC-240c and install the cupswrapper and lpr drivers.

Good Luck

---

