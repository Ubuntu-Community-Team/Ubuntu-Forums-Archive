---
title: "Remote Login"
date: 2008-10-12
forum: General Help
---

### Post by Eviltechie on 2008-10-12
This may have already been covered before, but this is what I need.

My parents keep taking away parts of my computer so I don't use it. (keyboard this time)

So I can maintain access to my computer, I want to be able to login to my computer from another windows computer in the house. The thing is, I can't install anything on the windows computers. I was hoping to login with this thing.

[http://blandname.com/wp-content/uploads/2006/09/rdp6-sshot-71.png](http://blandname.com/wp-content/uploads/2006/09/rdp6-sshot-71.png)

Thanks in advance.

---

### Post by Absorbed on 2008-10-12
You could use VNC to log in to your computer, or OpenSSH:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

If you just want to connect to your computer from your home network, then make sure you disable access to VNC/SSH from the Internet so that you don't have to be concerned about people trying to crack your computer.

---

