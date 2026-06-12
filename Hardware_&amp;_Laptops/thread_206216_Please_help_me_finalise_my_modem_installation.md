---
title: "Please help me finalise my modem installation"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by cubastreet on 2006-06-29
Hi there,
This is the first time I've installed linux in a few years, trying to rid my computer of windows...
I've managed to get my modem to work with a combination of matchless' guide here: [http://www.ubuntuforums.org/showthre...ighlight=536ep](http://www.ubuntuforums.org/showthre...ighlight=536ep) and also the readme that comes with the driver.
matchless' guide does the most of it, but I still need to open a terminal and enter these two commands to get it to work:
sudo mknod /dev/536ep c 240 1
sudo ln -s /dev/536ep /dev/modem
can someone please tell me how to load these commands when the system boots?
Also if you can tell me what the commands and parameters mean perhaps I can understand it better.
Cheers,
Jeremy.

---

### Post by deadgobby on 2006-06-29
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=modem&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=modem&titlesearch=Titles)

---

### Post by cubastreet on 2006-06-29
Thanks, but I already used the search button.

That first link contains all the information for the 536ep driver that was in matchless' post. I followed all that including adding the line to the etc/modules file to load the driver on boot, and creating /etc/udev/rules.d/10-local.rules to create a symlink to the modem. It didn't work.

However, it still didn't work, so I read through hours of online documentation before re-reading the driver's documentation (which doesn't self-compile in ubuntu) and finding the two commands above which enable the modem.

can anyone help?

---

