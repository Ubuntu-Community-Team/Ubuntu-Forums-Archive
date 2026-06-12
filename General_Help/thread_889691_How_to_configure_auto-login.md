---
title: "How to configure auto-login"
date: 2008-08-14
forum: General Help
---

### Post by cyclonedr on 2008-08-14
Hi all,
  I was wondering if it was possible to have ubuntu "automatically" login for me.  I've done this with Windows, but am not sure how to go about this in Ubuntu 7.10.  Thanks for any suggestions.
cyclone

---

### Post by sayakb on 2008-08-14
Goto System->Administration->Login Window->Security Tab
And enable Automatic login.

---

### Post by cyclonedr on 2008-08-14
Ok, Thanks.  I could have figured that out myself, but I always think things are more complicated than they really are.  Thanks again.

---

### Post by kirsis on 2008-08-14
You may be prompted for the keyring password everytime you are automatically logged in, which is very annoying and basically eliminates the point of auto-login.

One solution is to delete (or move away) all the files in ~/.gnome2/keyrings/ (Disclaimer: I think. I did this months ago when I installed Hardy and may've forgotten the actual location. But I'm pretty sure this was it). Then, when you are prompted to enter a password for a new keyring, just leave it blank.

---

