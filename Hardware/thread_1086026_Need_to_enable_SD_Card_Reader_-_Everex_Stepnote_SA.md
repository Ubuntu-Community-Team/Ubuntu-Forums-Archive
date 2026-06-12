---
title: "Need to enable SD Card Reader - Everex Stepnote SA2050T"
date: 2009-03-03
forum: Hardware
---

### Post by rob_fed on 2009-03-03
My Level = noob

I recently installed Ubuntu 8.10 on my Everex Stepnote SA2050T using the instructions from the website below.  I had to use the "alternate" installation download because of some issues related to Everex and like laptops. 

[http://www.poplarware.com/everexlinux.html](http://www.poplarware.com/everexlinux.html)

During the installation, the "sdhci" and "sdhci_pci" modules are disabled, as they were found to make the installation hang or freeze.  Unfortunately, the SD Card reader operation is directly related to these modules.

There is a "patch", but it requires to a re-compile of the kernel.  This is beyond my capability.  Is there another work around to get the SD card reader to work?

Thanks,

-rob

---

### Post by ddrichardson on 2009-03-04
No, I'm afraid if there's an issue and its patched then you need that patch. Kernel compilation isn't really that difficult though, I mean you've got through everything else - theres a guide [here]("https://help.ubuntu.com/community/Kernel/Compile").

The only thing I can suggest is to check that the memstick module is unloaded then load the required module as this has been known to cause issues on SD.

---

