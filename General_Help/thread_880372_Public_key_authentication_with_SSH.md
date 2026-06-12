---
title: "Public key authentication with SSH"
date: 2008-08-04
forum: General Help
---

### Post by Frostmourne on 2008-08-04
Hello, I am running an SSH/SFTP server on a Windows machine and attempting to log into it from my Ubuntu laptop using keys rather than passwords. I generated the key pair using the Seahorse GUI, copied the public key onto the server, and configured the server to use it. However, after I ran ssh from the terminal in Ubuntu and Seahorse asked me to unlock my private key "id_rsa," I am prompted to enter a password. Neither the pass phrase I supplied for the private key nor anything else allows me to log into the server. I am pretty sure it's a problem on Ubuntu's end since on another Windows machine I opened up Putty, specified my private key, unlocked the private key, and connected without problems. Any suggestions?

---

