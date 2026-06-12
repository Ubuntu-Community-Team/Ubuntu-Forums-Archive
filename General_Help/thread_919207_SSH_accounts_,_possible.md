---
title: "SSH accounts , possible?"
date: 2008-09-13
forum: General Help
---

### Post by StOoZ on 2008-09-13
I have a computer , which I use it for remotely connection only, it has only one user account , so whenever I need to connect to it via ssh , I use that name and its associated password.
is it possible to create more users on that computer which each user has its own folder (and only this folder , cant see / write on anything else) which then each user will connect to these folders remotely using his own user name and password?

---

### Post by Pro-reason on 2008-09-13
Yes, I don't see why not.  If the existing account has admin rights, then you can ssh to it, and then do “sudo adduser *fred*”, where *fred* is the name of the user you want to create.

---

### Post by StOoZ on 2008-09-14
yes the current account is the admin.
so basically what I need to do , is to create more users on that computer , which each use has its own work space (folder of lets say , 1GB) , so basically its possible?

---

