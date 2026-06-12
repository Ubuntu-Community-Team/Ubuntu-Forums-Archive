---
title: "Atheros wifi Ubuntu NO Wired connect"
date: 2009-03-13
forum: Hardware
---

### Post by ki4jgt on 2009-03-13
I recently purchased an aspire one laptop from acer. I don't have a wired eithernet connection and I need HELP!!! I've been through Google, Yahoo, and everywhere else online.

Here are My Troubles:

-My WIFI is not working B/C Ubuntu doesn't recognize the drivers 
-I can't find any drivers that aren't in EXE format for ndiswrapper
-I only get to come to the public library every two weeks or so (I have a 2.0 GB flash drive)
-I can only use public wifi at my house
-The only LAPTOP(computer) I have is stuck on Ubuntu for now which can't read my Atheros AR5BXB63 Wifi

**PLEASE HELP ME** :->

---

### Post by issih on 2009-03-13
If you go to the acer site and download the driver they offer you will probably find that it comes as a zip file, inside that zip file there will hopefully be a .inf, in this case I think you can avoid extracting the .exe, just because acer seem to be quite kind.

I found this out from this thread:

[http://ubuntuforums.org/showthread.php?t=739998](http://ubuntuforums.org/showthread.php?t=739998)

That user has the same chipset as you, and he gets the driver direct from acer, like at this page (for the notebook he mentioned, you don't give your exact model, but it shouldn't matter):

[http://support.acer-euro.com/drivers/notebook/tm_4720.html](http://support.acer-euro.com/drivers/notebook/tm_4720.html)

grab the driver "Wireless_Atheros_XB63_v5.3.0.45_XP" and then extract the zip file, inside that is an inf file.

Use that in ndiswrapper and see how you get on.

N.B. I'd recommend using ndisgtk to make life easier if I was you (its just a little gui front end to ndiswrapper) grab it from synaptic when you next have internet connectivity, or alternatively its on the install disk.

Hope that helps

---

