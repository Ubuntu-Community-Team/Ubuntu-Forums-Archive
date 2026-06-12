---
title: "Gnome login fails"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by EddieBenton on 2005-05-09
Hi guys, I just attempted to use the "save setup" option on gnome, however after having done so, logging in hangs at the starting metacity stage. This can be circumvented by logging in to the failsafe.
Is there any way I can delete the saved setup data and get gnome to login using the normal session?

TIA,
Ed

---

### Post by samba on 2005-05-22
i have exactly the same problem... anyone knows how to delete the saved data?

cheers :-)
samba

---

### Post by samba on 2005-05-22
Problem solved, but not understood...  :? 

After having logged in a Failsafe Gnome session, go to /home/your login/.gnome2/ and edit the "session" file. Replace everything that is under [Default] by what is under [Failsafe]. In other words, you redefine your Default session to be like the Failsafe session, i.e. you remove all the data that was saved when you saved your session last time.

I don't understand though why it didn't want to login. Probably one of the program that was open when we saved our session has a bug with gnome-session...

ciao
samba

---

