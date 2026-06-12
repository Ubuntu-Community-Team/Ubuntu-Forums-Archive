---
title: "Running &quot;bootinst.sh&quot; on USB from Terminal"
date: 2008-12-11
forum: Hardware
---

### Post by Enigmacat on 2008-12-11
Ok, I am trying to set up my USB to boot Slax. I understand that in order to make it bootable I must run "bootinst.sh" in the terminal. Done. I navigate to my USB via cd /media/UDISK/boot and run ./bootinst.sh , it runs, then at the very end it tells me: 

Flushing filesystem buffers, this may take a while...
Setting up MBR on /dev/sdf...
Fatal: Cannot open /dev/sdf: Permission denied

What gives!?! :confused:

What do I need to do? Please remember to keep it simple, while I have gotten this far with some success, I am still a noob.

F.Y.I. My home system is Ubuntu 8.10

Oops! I got it. The application of "sudo" before the "./bootinst.sh" script will give me the permission needed to allow me to make my USB bootable.

---

