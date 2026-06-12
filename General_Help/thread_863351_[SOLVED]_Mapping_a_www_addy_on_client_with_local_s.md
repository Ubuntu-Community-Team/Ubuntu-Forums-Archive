---
title: "[SOLVED] Mapping a www addy on client with local server"
date: 2008-07-18
forum: General Help
---

### Post by jmorris1161 on 2008-07-18
I have my own web servers up and running. Currently they are windows boxes but plan to change them to Ubuntu soon. I have Ubuntu Hardy on my pc but don't know how to change the reference for my web domains to my local server. In windows I would go to windows/system32/drivers/etc and open host and put a redirect for a virtual server in there. How do I do this in Ubuntu? 

Thanks

Figured it out, found another post fixing another problem I had and the file was the same that I needed.

FYI gksudo gedit /etc/hosts will open the file you need to edit to change host names i.e.

192.168.2.2 [www.mywebsite.com](www.mywebsite.com)

---

