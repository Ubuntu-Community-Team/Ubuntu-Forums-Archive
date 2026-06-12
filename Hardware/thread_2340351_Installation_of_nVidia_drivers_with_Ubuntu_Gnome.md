---
title: "Installation of nVidia drivers with Ubuntu Gnome"
date: 2016-10-17
forum: Hardware
---

### Post by jallain on 2016-10-17
I was having trouble loading nVidia drivers wtih Gnome. After rebooting I would come up to a blank screen and was unable to even launch a terminal. I found that if you edit grub and delete the "splash" argument from the linux line, your system will boot up and login just fine. It worked for me.

---

