---
title: "Ubuntu with 2xXeon E5420"
date: 2015-12-05
forum: Hardware
---

### Post by sean104 on 2015-12-05
Hello, I just setup Xubuntu 15.10 on a server running on 2 Xeon E5420s. The install went smooth but I am getting really poor performance on the GUI. Windows lag behind when dragged mainly. I opened additional drivers and where it normally has the driver for intel microcode, it says that the device is using another driver. Is there something I need to install of setup to have the gui run smooth?

---

### Post by mörgæs on 2015-12-07
It's normal for server hardware to have weak GPU's.

Let's take a closer look. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

