---
title: "LiveCD Troubles"
date: 2008-10-05
forum: General Help
---

### Post by @xi0m on 2008-10-05
I've setup a system that will automatically log in with a certain account and then launch rdesktop and connect to a server I have running.  I've accomplished this via bash script that I placed in /etc/init.d/.

I wanted to create a live cd with this configuration so I installed remastersys and created the iso image.  The problem I'm having is when I test the iso image from within VMware, it boots directly to the desktop and doesn't execute the bash script.  I checked to be sure that the bash script is still located in /etc/init.d on the live cd and it is.  When I execute the script manually it works just fine.  The script is marked as executable and it's able to be read and written to by the appropriate account.

Why would this work perfectly on the source machine but not within the live cd image?

---

### Post by @xi0m on 2008-10-06
Bump

---

