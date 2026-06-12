---
title: "Trouble with External Drive"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by nthpro on 2007-01-08
I have re-formatted a drive in Partition Magic 8.0 in order to make it ext2.  On my windows side of things I can read and write to this drive fine using the proper windows drivers...however once I log into Ubuntu I am unable to write to this drive...only view.  When I select permissions it says root only can set these permissions.  How do I go about changing these?  

Thanks,
Ty

---

### Post by Simanek on 2007-01-08
You need to be the root user in order to change those properties. You have to be careful, but a handy trick is to run Nautilus as super user.

Open a terminal.

Type this:

sudo nautilus

and press 'enter'. You will be asked for your administrator password. Enter it and press 'enter'. Nautilus will start a new window. Nothing is different about the program except that you are running as super user (note that your left-hand short cuts are gone and that you have started in /root/Desktop).

With this window browse to /media/ and right-click on your drive, go to Properties, switch the properties to your liking. You should now be able to Read/Write with your regular user account.

---

