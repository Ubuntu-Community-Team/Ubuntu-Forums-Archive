---
title: "Screen Fractured"
date: 2011-03-28
forum: Hardware
---

### Post by martini161 on 2011-03-28
I have this problem when installing xubuntu on an old dell latitude laptop I have, I believe c800 is the model. Installs fine other than that I have to use the alternate install disk, but when it boots the screen looks like this:
[IMG]http://oi54.tinypic.com/2n8obpw.jpg[/IMG]
I assume this is a driver issue, but have no idea how to solve it
Thanks in advance

---

### Post by martini161 on 2011-03-29
Bump, haven't made any progress

---

### Post by Tweak42 on 2011-04-25
Assuming there's nothing wrong with the hardware, it looks like the X xorg screen resolution settings are incorrect (example video outputing 1024x768 to a 800x600 screen).  What video chip is it using?  

Run lspci at the command line and look for the VGA controller. You can drop to command line by hitting ctrl-alt-F1 and return to X by ctrl-alt-F7

---

