---
title: "help with sftp"
date: 2008-08-03
forum: General Help
---

### Post by CostaRicanQuaker on 2008-08-03
I just installed opensshd-server. 

What do I have to do to allow a buddy of mine who's on a mac computer to download and upload files from me?

---

### Post by CostaRicanQuaker on 2008-08-03
I'm on kde 4.1, just went to the system settings but I can't find the users and groups icon.

---

### Post by geirha on 2008-08-03
Don't know how to create users in kde, but in the terminal you can do ```
sudo adduser newusername
``` The default settings for openssh-server should be fine, your friend just need a username, password and an ssh/sftp-client.

---

