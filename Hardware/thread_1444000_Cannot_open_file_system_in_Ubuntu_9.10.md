---
title: "Cannot open file system in Ubuntu 9.10"
date: 2010-03-31
forum: Hardware
---

### Post by unix1021 on 2010-03-31
I am using Ubuntu 9.10 on my laptop and I am unable to open the file system.
When this happens I cannot right click on the desktop and I cannot see desktop icons. 
But I can open things related to internet like Firefox,Emesene etc.
like when I click Place->Computer  or Document or Place its takes few minutes saying "Opening Computer" and than nothing opens .
I am using Ubuntu for more than 3 months But I dont get this error before.
I started to get this error after installing all the updates which was been specified to install.
If I could get any help please let me know.:)
Thnx.

---

### Post by mikewhatever on 2010-04-01
I'm assuming the problem is, the file browser, Nautilus, doesn't open when you click the links under Places. Hope that's correct. Can you open a Terminal window, type 'nautilus' without the quotes and hit enter. Please post the output here.

---

### Post by unix1021 on 2010-04-04
Yeah...thats correct..here is the output i get :

aastha@aastha-laptop:~$ nautilus

(nautilus:2897): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:2897): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

