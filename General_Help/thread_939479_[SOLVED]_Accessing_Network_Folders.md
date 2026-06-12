---
title: "[SOLVED] Accessing Network Folders"
date: 2008-10-06
forum: General Help
---

### Post by Altay_H on 2008-10-06
I can't figure out how to access the network folder on campus. In Windows I can access it by typing "\\Ed" in the address bar of the file explorer or by using the run command to open "\\Ed". However, this method doesn't work in Nautilus, and I can't seem to find it under Networks. Is there an easy way to access what Windows calls \\Ed in Ubuntu?

---

### Post by Altay_H on 2008-10-06
Well, I managed to find the folder by going to Network Servers, then Windows Servers, then GCC, and then I finally found ED. The problem is, it's entirely empty. It's the network folder I need, but it shows no contents. Any ideas?

---

### Post by Altay_H on 2008-10-13
Bump.

---

### Post by Altay_H on 2008-10-18
Bump again.

I think the problem is that I need to enter a username and password to access to network folder. However, I'm not prompted for one in ubuntu. Is there any way to access such folders?

---

### Post by ztrange on 2008-10-19
Have you tested Places / Connect to Sever

Service type: Windows share
server: \\Ed
folder: shared_folder_name

It will promp you for a username, password if needed

---

### Post by Altay_H on 2008-10-19
I did, but it didn't work at all. It gives me an error saying:

Can't display location
No application is registered as handling this file

---

### Post by _sAm_ on 2008-10-23
When you try that I believe you use GVFS, witch is totally new in Ubuntu 8.04(gnome 2.22). I tried it to and it didn't work. Lets hope it work in gnome 2.24 witch Ubuntu Ibex will use.

But why don't you just mount the share with cifs, that should work fine.
[http://harryyeh.blogspot.com/2008/02/mounting-windows-shares-in-ubuntu-using.html](http://harryyeh.blogspot.com/2008/02/mounting-windows-shares-in-ubuntu-using.html)

---

### Post by Altay_H on 2008-12-14
Well, I solved the problem by opening Nautilus and entering the location:
smb://Ed/Courses/

This took me to the folder Courses within Ed. I don't know why, but it won't find the files/folders within Ed. However, it allows me to access the folders within Ed, which is what I need.

---

