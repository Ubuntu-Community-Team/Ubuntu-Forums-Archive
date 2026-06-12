---
title: "Windows Driver for Ubuntu"
date: 2010-02-27
forum: Hardware
---

### Post by vader95 on 2010-02-27
Hi,

I have a lexmark printer that all i can find is the windows driver.  Is there a way to let this driver work in ubuntu.  I'm trying to set up a print server over top of my file server.  I do have the ubuntu-desktop installed if there is a gui.

Thanks,
vader95

---

### Post by Ozymandias_117 on 2010-02-27
Most printers will "just work" in ubuntu, you don't need drivers. Although some printers you have to use some kind of work around to get them, and others just aren't supported for one reason or another. 

Have you tried to just plug it in and see if it works yet? If it doesn't, googling your particular model with "ubuntu" after it generally pulls up information on getting it working if it is possible. Or if you post back with the model number we may be able to help you.

---

### Post by vader95 on 2010-02-28
Hi,


Thanks for the response.  I have a Lexmark Z705. I also found [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714). I finish the command and when i go to ./z600 i get an error.
```
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```I am running as su. Any ideas? UBUNTU VERSION: 9.10


Thanks
vader95

---

### Post by vader95 on 2010-02-28
Ok,

I got the printer installed and i go to print a test page and it says cups-insecure-filter.


Any ideas?

Thanks,
vader95

---

### Post by vader95 on 2010-02-28
Nevermind, i got it to print.


Thanks,
vader95

---

### Post by Nutria on 2010-02-28
> **vader95 said:**
> Nevermind, i got it to print.

Could you tell us how?

---

### Post by vader95 on 2010-02-28
> **Nutria said:**
> Could you tell us how?
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters) 

If anything come up about cups insecure filter try this```
sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend
``` Taken from ubuntuforums.org
The only thing i haven't gotten to work yet is the color shading, i'm working on that now and will get back to you. And go to the lexmark website to get the z605 driver, the link is not there anymore.

---

