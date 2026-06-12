---
title: "WiFi and Add/Remove problems"
date: 2006-06-21
forum: Hardware &amp; Laptops
---

### Post by supermistry on 2006-06-21
I just installed ubuntu on an old IBM T21 the other night and I have run into a few problems. In advance, I apologize if any of these issues have been covered in the forums before, I have looked, but have not found any solutions.

First off, I can't seem to get my wifi to work (go figure). The wireless card (D-Link DWL-650) is being detected by the system (I can see it in the device manager) and it is lighting up indicating a link. Also, when I set my connection properties to eth1 (that is the name of the wireless connection), I do get a very strong signal from my router. However, for the life of me, I can't get the status to change from disconnected. I have no such problem when I wire into the router directly. (The router is a Linksys WRT54G wireless g router. It is using WEP encryption, and I do know the key for it.)

After looking around the forums and the ubuntu book that was provided in the examples folder in my home directory, I found that I should try using the NetworkManager, so I tried installing that from Add/Remove applications. Unfortunately, I keep getting this error when I check any of the boxes in there:

[INDENT]'network-manager-gnome' is not available in any software channel
The application might not support your system architecture.
[/INDENT]

Doing a search for this type of error led to my trying to modify the sources.list file in /etc/apt. When I tried to do that, however, I found that I do not have permissions to modify the file. Or to rename or delete it. Earlier, I found something that suggested i edit one of the files in the etc/network folder, but again, same problem. I feel really noobish not being able to figure out this last problem, but finally, I decided the best thing to do would be to ask here.

So yeah, I would greatly appreciate any help I can get on trying to figure out these three issues. Hopefully I have provided enough information so that my issues are clear.

Thanks in advance,
Kuran

---

### Post by bukwirm on 2006-06-21
To edit sytem file, you need to use sudo (tyoe 'sudo gedit filename')

---

### Post by supermistry on 2006-06-21
Thanks for the sudo information. Since I wasn't sure what that was, using google led me to this article [http://www.psychocats.net/ubuntu/permissions.php](http://www.psychocats.net/ubuntu/permissions.php) which proved to be most helpful in explaining everything.

I got the Add/Remove Applications to work, and was able to edit the files. However, wireless still doesn't work =/. I'm confused because the device manager still picks up the card and it is getting a strong signal from my router. It just won't connect to it and Network Manager isn't detecting any signals.

---

