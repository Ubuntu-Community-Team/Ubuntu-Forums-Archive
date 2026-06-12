---
title: "apache2 server setup, but I can't add or remove files?"
date: 2008-09-27
forum: General Help
---

### Post by ajwak95 on 2008-09-27
I am under an Admin account, doing everything that I can, meaning, I have full ability to do anything on here really. So now that I want to get into my Apache2 server, it is only root that can do this, so, what can I do to get around this and change file permissions?

---

### Post by Iowan on 2008-09-27
I must be missing something... **sudo** isn't working?  Are you at console, SSH'ed, or remote'd somehow?  Virtual servers let you put a website under a directory that isn't root-owned, (unlike the default) - such as, your home directory.

---

