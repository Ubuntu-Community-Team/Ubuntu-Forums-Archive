---
title: "Intel 4965AGN not working"
date: 2008-09-07
forum: Hardware
---

### Post by riahc3 on 2008-09-07
How can I get this card to work under Ubuntu? It seems to be able to detect my network's SSID but can't use the connection.

---

### Post by riahc3 on 2008-09-07
Anyone?

---

### Post by riahc3 on 2008-09-09
Bumping this thread up

---

### Post by sdenovan on 2008-09-10
I have found that for some unknown reason, the permissions on:

/lib/dhcp3-client/call-dhclient-script

End up broken. This prevents DHCP calls from completing which leaves NetworkManager swirling endlessly. 

Here's the fix (you may need to reboot after making these changes and your user needs to be in the dhcp group):

```
sudo chgrp dhcp /lib/dhcp3-client/call-dhclient-script
sudo chmod 4750 /lib/dhcp3-client/call-dhclient-script
```

Still not working? This is a more brute force solution and allows anyone logged into your machine to re-request DHCP (not much of an issue on a single user laptop):
```
sudo chgrp root /lib/dhcp3-client/call-dhclient-script
sudo chmod 4755 /lib/dhcp3-client/call-dhclient-script
```
Remember, you might need to reboot.

---

### Post by riahc3 on 2008-09-14
> **sdenovan said:**
> I have found that for some unknown reason, the permissions on:

/lib/dhcp3-client/call-dhclient-script

End up broken. This prevents DHCP calls from completing which leaves NetworkManager swirling endlessly. 

Here's the fix (you may need to reboot after making these changes and your user needs to be in the dhcp group):

```
sudo chgrp dhcp /lib/dhcp3-client/call-dhclient-script
sudo chmod 4750 /lib/dhcp3-client/call-dhclient-script
```

Still not working? This is a more brute force solution and allows anyone logged into your machine to re-request DHCP (not much of an issue on a single user laptop):
```
sudo chgrp root /lib/dhcp3-client/call-dhclient-script
sudo chmod 4755 /lib/dhcp3-client/call-dhclient-script
```
Remember, you might need to reboot.

Im gonna try this out (the brute force solution because this laptop has only one user)....

Im gonna post the results in a minute




UPDATE: It worked for about a minute (it seems) but still nothing.

---

### Post by Crafty Kisses on 2008-09-14
Here try downloading the latest drivers [**here**]("http://intellinuxwireless.org/index.php?n=Downloads").

Then you need to install **ndisgtk**:
```
sudo apt-get install ndisgtk
```
After you have the driver, unzip it, and look for the proper files then:
```
sudo ndiswrapper -i drivername.inf
```
Then install the .inf file using **ndisgtk**, and it should work.

---

