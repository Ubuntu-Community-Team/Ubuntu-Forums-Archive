---
title: "Itrepid, &quot;Segmentation fault&quot;"
date: 2008-11-20
forum: General Help
---

### Post by kostovnet on 2008-11-20
Hello guys,
I've noticed something strange recently: So far several applications have failed to start, printing "segmentation fault" when run from a terminal.
First it was Firefox both 3.0.3 and 3.0.4, then Skype and Pidgin.

This is not a permanent problem - everything seems fine, but sometimes one of the applications above (so far) crashes and I am unable to start it again without rebooting (a reflex from my time with windows). 

When I attempt to start an application from the terminal, after several seconds it just prints "segmentation fault".

Could anyone help me deal with this ?

Running Ubuntu 8.10 with backports updates.

Thanks

---

### Post by kostovnet on 2008-11-20
Ok, I have a theory... I've just noticed that I was out of free disk space on my /home drive. After I've deleted some files, the crashed application started without showing the "segmentation fault" error preventing it to start a few minutes ago.

If this is not a bug, is there a more comprehensive (user-friendly) way to know that I am simply out of diskspace ?

---

### Post by cooljeff3000 on 2008-11-22
I don't know if this helps, but im on hardy and something made pidgin segfault. After a bit of fooling around I got it to work by running it as root

---

### Post by kostovnet on 2008-11-26
I filled my /home drive on purpose leaving 0 MB of free disk space and the segmentation err. appeared again. Actually every time an application attempted to write to the /home directory it just crashed or showed some strange behavior and then crashed.

---

