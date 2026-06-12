---
title: "DSL-G624T, SSH and port forward"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by dudous on 2007-07-22
I can't port forward to a ssh server inside my network even if i change the ssh port from 22 to another number.

There is a ssh server inside the router, and when i try to conect to my computer's ssh server, the router doesn't redirects the solicitation and tries to make the connection with his ssh server. I tried to disable the router ssh server but i didn't find anything in the web management interface or getting inside the router by ssh.

Emule or bittorrent port forwarding works fine. 

A tested the port forward with an old router that a have  and everything was fine.

Please, does someone have overcome this problem with this router ???

---

### Post by zanglang on 2007-07-23
If you can't disable SSH on your router (might have been labeled as 'Remote Administration' on the web interface) perhaps you could try making a port forward from another number (say, 8022) to your SSH server on its original port 22?

---

