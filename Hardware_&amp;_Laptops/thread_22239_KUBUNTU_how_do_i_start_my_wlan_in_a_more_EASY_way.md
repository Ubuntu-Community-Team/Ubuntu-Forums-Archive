---
title: "KUBUNTU: how do i start my wlan in a more EASY way ?"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by greatshape on 2005-03-26
hi,
i just installed kubuntu and it's great, except from a few little problems.
I've got a usr 54G wireless card which uses the ACX111 texas instruments chipset ( yes,yes i know :sad: )
The card gets recognised fine by kubuntu, but on "an unwired" system startup, the system waits about 1 minute trying to get an ip on the wired nic (which is not connected at that moment)a solution for this would also be nice.
But then, once booted, i open kwifi manager and standard it's looking for an essid "STA558D86" which i never configured, where can i change this? I filled in one of the profiles with my essid, and when i click on activate i get connected to the network, but still get no ip. Then i have to open a shell, become root, and typ "dhclient wlan0" to get an ip and then i can (finally) surf. 
Isn't there a way to make this a little bit more easy to activate?
All help is appreciated!!

Regards, steve
 
PS I prefer not to use ndiswrapper, because before, with suse9.2, it totally locked up the laptop when i downloaded a bigger file. :sad:

---

### Post by alehorb on 2005-03-31
Control Center ---Network Settings.

---

### Post by tomchuk on 2005-04-03
Get rid of the "auto eth0" line in your /etc/network/interfaces (leave "auto lo" alone). If you want a really slick solution, look [here](http://arstechnica.com/columns/linux/linux-20040413.ars/2).

---

