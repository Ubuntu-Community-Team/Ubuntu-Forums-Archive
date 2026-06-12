---
title: "External HD - read but not write"
date: 2013-08-18
forum: Hardware
---

### Post by Windoze Refugee on 2013-08-18
Hi Folks.
I have a 3TB external HD, originally formatted by a friend in Mac OSX. It has files that I can access no problem, but I cant write to it as I get the 'no permission' error.
Ive tried the 'GOD' command    "gksu nautilus" in terminal, and this seemed to give me the access to change permissions I was after, but it wouldnt actually allow me to make the changes in the end.
I really need to be able to both read and write to this. Any help gratefully received.
Cheers
WR

---

### Post by zero2xiii on 2013-08-18
Just to make sure.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Make sure you are mounting the drive with read write (usually rw) rights.

Cheers

---

### Post by Windoze Refugee on 2013-08-18
HI Zero and thanks for your input. However..huh? I just want to be able  to plug my external HD into the usb port and read and write to it. Dunno  what all the rest means tbh :)

---

### Post by zero2xiii on 2013-08-18
Hay,

Well first make sure if you manually mount it (links) making sure to give rw permission, it works. Then you can start to look for why it is not writable while only hot plugged.

Cheers

---

