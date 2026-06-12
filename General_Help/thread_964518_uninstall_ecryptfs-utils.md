---
title: "uninstall ecryptfs-utils"
date: 2008-10-31
forum: General Help
---

### Post by Queue29 on 2008-10-31
First of all, ecryptfs-utils seems pretty useless. Cryptkeeper did what I wanted it to in 8.04, which is to keep a hidden directory and only allow access when I give it a password. Ecryptfs allows access anytime I'm logged in, and puts its folder right there on the desktop in plain view. :confused:

Now, I tried uninstalling ecryptfs (via synaptic), but the "Private" directory is still on the desktop, and not even sudo powers can remove it.

```
seth@SLinux:~$ sudo rm -r Private/
rm: cannot remove directory `Private': Device or resource busy

``` 

How do I get rid of it?

---

### Post by cariboo on 2008-10-31
Have you also removed the hidden files in your home directory I don't have the private directory installed right now but if I remember correctly there is one called .Private and the other is ecrypt*

I tried installing the ecryptrd softwsre, but the repositories are so busy right now that I can't even update my sources.list.

Jim

---

### Post by tyroeternal on 2008-11-01
Thank you, this worked for me! :D  There should really be a straightforward method for removing that directory.  If they are going to make it a click to setup, it should be just a click to remove as well.

---

