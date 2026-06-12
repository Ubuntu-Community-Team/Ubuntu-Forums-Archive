---
title: "Broadband connection"
date: 2005-11-30
forum: General Help
---

### Post by canadianwriterman on 2005-11-30
For some reason, whenever I reboot my computer, I lose my broadband connection. In Windows, I have to go into the **Control Panel > Network Connections**, delete my broadband ISP connection, then create a new connection. The connection will then work until I reboot. The ISP tech worked on it for several hours and gave up, saying there must be something wrong with the computer and recommending I just leave it running to retain the connection.

When I boot into Ubuntu, the broadband connection also does not work. If I'm going to leave the computer running to maintain my broadband connection, I'd rather do it in Ubuntu, but I can't where there is a utility similar to Windows that will allow me to create a broadband connection,** including entering a user name and password**. I've looked at the properties of my network eth0 connection, but there's nowhere for a username and password.

Does anyone know where I could find it? Thanks a million in advance.

---

### Post by Kapre on 2005-11-30
[QUOTE=canadianwriterman]For some reason, whenever I reboot my computer, I lose my broadband connection. In Windows, I have to go into the **Control Panel > Network Connections**, delete my broadband ISP connection, then create a new connection. The connection will then work until I reboot. The ISP tech worked on it for several hours and gave up, saying there must be something wrong with the computer and recommending I just leave it running to retain the connection.

When I boot into Ubuntu, the broadband connection also does not work. If I'm going to leave the computer running to maintain my broadband connection, I'd rather do it in Ubuntu, but I can't where there is a utility similar to Windows that will allow me to create a broadband connection,** including entering a user name and password**. I've looked at the properties of my network eth0 connection, but there's nowhere for a username and password.

Does anyone know where I could find it? Thanks a million in advance.[/QUOTE]

canadianwriter - did you try using "sudo pppoeconf" (without quotes) from the terminal? This is what I use to connect to my ADSL and after the setup (one time) it will be automatically log me in (stays connected).

K

---

### Post by canadianwriterman on 2005-12-01
[QUOTE=Kapre]canadianwriter - did you try using "sudo pppoeconf" (without quotes) from the terminal? This is what I use to connect to my ADSL and after the setup (one time) it will be automatically log me in (stays connected).

K[/QUOTE]

I did try running pppoeconf, but there are more options within its setup than I have when I use the setup utility in Windows. I may have made the wrong guesses as to which settings to chose, because I wasn't able to connect successfully using it.

---

