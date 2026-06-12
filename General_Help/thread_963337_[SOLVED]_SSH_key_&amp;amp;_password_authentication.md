---
title: "[SOLVED] SSH key &amp;amp; password authentication"
date: 2008-10-30
forum: General Help
---

### Post by porchrat on 2008-10-30
Greetings people of LinuxLand

I have a question about SSH that isn't referred to anywhere that I can find.  Is it possible to run password authentication and key authentication at the same time?

By this I don't mean that **either** password authentication or key authentication is required to allow a connection.  I mean to set it up so that both password authenitcation **AND** key authentication are required to establish a SSH connection.

Is this at all possible?

When I set the server for 
```
passwordauthenticaton =yes
RSAauthentication = yes 
```
then all it does is use either or.  *i.e.* if you have the password then you don't need the key authentication...I want it to force both.

---

### Post by porchrat on 2008-11-03
bump

---

### Post by brian_p on 2008-11-03
> **porchrat said:**
> Greetings people of LinuxLand

I have a question about SSH that isn't referred to anywhere that I can find.  Is it possible to run password authentication and key authentication at the same time?


Not from ssh directly but Google might help. Search with 'two factor authentication ssh'.

---

### Post by porchrat on 2008-11-04
> **brian_p said:**
> Not from ssh directly but Google might help. Search with 'two factor authentication ssh'.

Thank you, I took a look.  That is very interesting and extremely helpful.

\\:D/

---

