---
title: "sftp-protocol in Firefox"
date: 2008-11-20
forum: General Help
---

### Post by orrie on 2008-11-20
How can you add nautlius-support for SFTP in Firefox?

Usage:
Are going to click on a link (ie: sftp://user@host) and then get the link up n running in nautilus.

The question is; how to do this?


Have been googling around a bit without some good answers.. :)

---

### Post by roderikk on 2008-12-03
I also have just ran into this problem. I can access just regular [ftp://ftp.example.com](ftp://ftp.example.com) sites when I type them into the location bar. However, when I try to go to sftp://user@10.0.0.1/ I don't see anything, even though the same address shows up perfectly fine in Nautilus.

This seems to be because Nautilus authenticates with the 'keyring' whereas Firefox doesn't? Does anybody know how I can make Firefox see the same locations as Nautilus?

---

### Post by roderikk on 2008-12-03
Ah, I just found that Firefox does not support the SFTP protocol. I guess I will have to create like an sshfs mount so that I can access them locally.

---

### Post by lemuriaX on 2008-12-03
I think you can use Konqueror for SFTP if that helps.

---

