---
title: "Installed wifi in ndiswrapper and can't login."
date: 2006-02-10
forum: Hardware &amp; Laptops
---

### Post by slavik on 2006-02-10
whenever I log in into gnome, I get the following message:

"Your session lasted only less than 10 seconds. if you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. try logging in with one of the failsafe sessions to see if you can fix the problem."

Even using the failsafes, it still logs me out.

In the session log it says something about not being able to find the transport protocol tcp and that it can't create /dev/X and then that it can't read the ICE authority file ...

---

### Post by slavik on 2006-02-10
has been fixed on ubuntu irc channel by booting into failsafe console and deleting the .ICEAuthority and the .Xauthority files.

---

