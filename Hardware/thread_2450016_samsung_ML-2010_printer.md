---
title: "samsung ML-2010 printer"
date: 2020-09-05
forum: Hardware
---

### Post by cmcanulty on 2020-09-05
I have tried installing this with cups, with the printers  section of xubuntu and with a windows driver via wine with no luck . I get an error about a missing print filter The samsung web page has a lister 64 bit deb file but it doesn't work either. I tried all 3 debs from this web page. Should I give up or is there something else to try? The printer is detected with 

```
lsusb
```

[http://www.openprinting.org/printer/samsung/samsung-ml-2010]("http://www.openprinting.org/printer/samsung/samsung-ml-2010")

 it will start up like it's going to print but won't actually print anything. Thank you

---

### Post by kurt18947 on 2020-09-05
I have a Samsung Laser MFD. It's seen automagically but doesn't print properly with all apps. Some work, some will produce 1 or a few lines of gibberish per page and will keep going until it runs out of paper. I'm not sure why some apps work - Libreoffice is one - and others don't, like Firefox. If you search HP's support site (HP bought Samsung's printer business) you should be able to find a universal printer driver for Linux. The only odd thing I found about installing it is that I could not install with the ULD folder on the desktop, I had to unpack the folder to another destination - I used Downloads then run the script from there. This is 20.04 with the new Desktop which may account for the change in behavior. I used to have a Brother folder and a Samsung folder on my desktop containing files required to install printers. I would cd to Desktop/Brother for example and run the install script from there. That no longer works, at least for Samsung.

---

