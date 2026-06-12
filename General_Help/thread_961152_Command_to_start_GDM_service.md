---
title: "Command to start GDM service?"
date: 2008-10-28
forum: General Help
---

### Post by nitin.pant on 2008-10-28
I stopped the GDM service on my Linux Mint and it doesnt come up with the login screen anymore but starts the shell login..

Please tell how to start GDM from the command...?
Recovery mode doesnt fix X11...

---

### Post by Jive Turkey on 2008-10-28
$ sudo /etc/init.d/gdm start

??

followed by:

$ startx

---

### Post by nitin.pant on 2008-10-28
Thanks it works, but now i cant enable desktop effects. When i change the visual effects to anything other than 'none' it gives the error-Desktop effects could not be enabled!:popcorn:

---

### Post by Jive Turkey on 2008-10-31
Did they work before?  You need to have the restricted driver or some proprietary driver installed and driving for desktop effects to work.

---

