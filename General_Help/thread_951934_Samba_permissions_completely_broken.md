---
title: "Samba permissions completely broken?"
date: 2008-10-18
forum: General Help
---

### Post by FeraTech on 2008-10-18
So I'm having a very strange problem. I create a directory set it to be readable and writable by all. Set the samba permissions so it can be accessed by everybody and any time somebody creates a new file you can't modify it.

I have to recursively chmod 777 the folder EVERY time somebody creates a new folder or file.

This is absurd! I've tried looking through the documents and came up 
inherit permissions = yes
but this does not work. I've gone through the smb.conf file a million times and nothing...

Please somebody help. I just need to know how to make folder permissions inheritable.

---

