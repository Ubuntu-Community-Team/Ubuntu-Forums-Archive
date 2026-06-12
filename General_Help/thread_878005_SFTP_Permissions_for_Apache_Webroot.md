---
title: "SFTP Permissions for Apache Webroot"
date: 2008-08-02
forum: General Help
---

### Post by neutrino15 on 2008-08-02
My server has the apache web root of /web. This directory is owned by me, is in my group, and has 755 permissions, however I can not write to it. I am using SFTP to edit the files inside of it, logging in as myself.
For some reason, my SFTP client won't let me write to it, and even from the SSH Command Line, i need to invoke "sudo" in order to write to this directory.

I want SFTP access (without sudo) as well as a secure apache webroot. How do I configure this?

Thank You!

---

