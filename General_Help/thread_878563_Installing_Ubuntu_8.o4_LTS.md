---
title: "Installing Ubuntu 8.o4 LTS"
date: 2008-08-03
forum: General Help
---

### Post by deathblade82 on 2008-08-03
Can anyone tell me what is the recommended way to install ubuntu 8.04 LTS ?
Is it better to install with an active internet connection so that all updates will be in or can I just do without ?

---

### Post by dexter.deepak on 2008-08-03
you can surely do without an active internet.
you can do an update anytime later, it takes the same time.
before updating, you have to first enable many of the repositories in the /etc/apt/sources.list

---

### Post by jimv on 2008-08-03
You don't need to be on the internet to do the install.  Just pop the CD in and choose the Install Ubuntu option.

Afterwards you can run the Update Manager to install any updates.

---

### Post by Kevbert on 2008-08-03
It's easier to install with a wired (ethernet) connection to the internet when you install as your software sources will be set-up by default and in many cases network connections will be set-up (the cause of a good percentage of problems reported on this forum).

---

### Post by deathblade82 on 2008-08-03
I once tried with an internet connection. But after the installation was completed, when I did a restart, I got error messages terminating my network connection.

Why do I get them ? Can anyone tell me ? Thanks.

---

### Post by Kevbert on 2008-08-05
What's the wireless card (and its' chipset) ?  You can get this information by going to Accessories-Terminal and entering
```
lspci
```
then enter 
```
iwconfig
```
Please copy the resulting information by highlighting the text with the mouse, then go to Edit - Copy.  Paste the information in your next post with Ctrl+V.  It may be that you require firmware to be installed.

---

### Post by deathblade82 on 2008-08-06
> **Kevbert said:**
> What's the wireless card (and its' chipset) ?  You can get this information by going to Accessories-Terminal and entering
```
lspci
```
then enter 
```
iwconfig
```
Please copy the resulting information by highlighting the text with the mouse, then go to Edit - Copy.  Paste the information in your next post with Ctrl+V.  It may be that you require firmware to be installed.

I am talking about a wired (ethernet) connection. Since wireless will not be functioning during installation.

---

