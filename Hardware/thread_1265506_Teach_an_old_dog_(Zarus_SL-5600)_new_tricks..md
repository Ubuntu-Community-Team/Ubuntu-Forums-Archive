---
title: "Teach an old dog (Zarus SL-5600) new tricks."
date: 2009-09-13
forum: Hardware
---

### Post by modmadmike on 2009-09-13
I now have my Zarus SL-5600 working with OpenZarus and Opie 1.2 (although id like to have a newer distro on it but i tried Ångström but many features were broken). I can now get on the Internet through the USB cable to my Karmic box by running ```
sudo ifconfig usb0 192.168.30.1
``` on the host after plugging it in (and setting up fire-starter) and then refreshing the connection on the PDA. With that i can ssh from and to it and wget things from my server (and also use the email client and web browser). But my problem is its running a very old kernel, the repository for .ipkg files is down and so i have problems installing certain pieces of software (like a TV remote) because of endless missing dependencies. Also my AmbiCom WiFi card wont connect to anything for some reason :(. In addition, i was wondering if there was any Linux Zarus sync software for my Karmic box.

---

