---
title: "terminal server client and VNC"
date: 2008-10-31
forum: General Help
---

### Post by Comzee on 2008-10-31
I have server running VNC, and I have an Ubuntu workstation that needs to connect to it. It seems that "terminal server client" could, but under the protocol tab VNC is grayed out. Is there some dependency I need to install to use "terminal server client" for VNC connections?

Also, I don't have to use "terminal server client". Is there any other solution for VNC? The client has to support 128bit AES encryption because thats what the server is set too. 

Thanks in advance for any help!!

:popcorn:

Well I got TSC to work with the VNC protocol but I don't think it supports the encryption type (It says "to many security failures"). I've tried a host of VNC clients and none of them seem to work. I'm pretty sure it's because of the encryption. I have RealVNC enterprise server running on the machine. So idk if I need a special client that supports 128bit AES or not?

---

### Post by Comzee on 2008-10-31
bump

---

### Post by peterx14 on 2009-07-11
You've probably figured it out by now, but just in case.... I had the same problem and only figured it out when I found [this thread](http://ubuntuforums.org/showthread.php?t=1008819).

If you look in the Applications->Internet menu, there's "Remote Desktop Viewer" which is the VNC client. The "Terminal Server Client" which is there purely to confuse both you and I! ;)

(In my defence, I'm 99% sure that I could use the Terminal Server Client as a VNC client under Gutsy... although I still can't believe I missed the other Remote Desktop Viewer!)

---

