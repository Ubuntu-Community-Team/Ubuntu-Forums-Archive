---
title: "Login Timeout Problem"
date: 2008-07-24
forum: General Help
---

### Post by CaesarLike on 2008-07-24
Hi All,

I have a problem with the login screen.  As soon as it displays I get an error message about login timeout, and I am unable to login at all as the error message displays constantly.

I originally had the login setup to auto login, but changed it back to normal.  Also, before changing back to the normal login, I changed the /etc/pam.d/gdm file to include this line:

"@include common-pamkeyring"

to auto-authenticate the gnome-keyring at login, as I was getting the keyring login at bootup to enable the wireless PCI adapter.
This is based on this tutorial:
[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/]("http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/")

When I re-booted up came the login error message.

Is adding the above line the problem?  Or maybe I have enabled something else in the past that only now is effecting the login?

---

### Post by DagMan on 2008-07-24
I don't know if that is what caused the error, but removing it should indicate that shouldn't it?
Anyhow, the tutorial is adding something to the login manager so that when you type your password at gdm, it then passes it over to the gnome-keyring and if is the same password it unlocks the keyring without you having to type in the password again.
The tutorial is old, and it is implemented as the default behavour, so it is not something you need to add unless you're running an old version of Ubuntu.

---

