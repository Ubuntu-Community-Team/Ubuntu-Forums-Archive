---
title: "Help Needed on root.disk"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by castona on 2009-05-26
Hi all,
 
 
Sorry for this posting as i m very new to ubuntu.
just installed it an hour ago.
 
 
Currently i have a root.disk img which i need to edit.
how to i edit the file in wubi?
 
i tried mounting it on the terminal but it prompt that i can only mount it on root.
 
how do i login to root in wubi?
is there any other way to edit the root.disk image?
 
Thank you

---

### Post by b@sh_n3rd on 2009-05-26
To mount an image to a certain folder in ubuntu, you *do* have to mount as root. To do so, add "sudo" to the beginning of the line you just typed in the terminal and hit enter. It should ask you for a password, which is the same one you use to login. Hope this helps :D...

Just remember, "sudo" to run a command in the terminal as root, and use "gksudo" to run an application, say for example nautilus (the file manager), as root...

---

