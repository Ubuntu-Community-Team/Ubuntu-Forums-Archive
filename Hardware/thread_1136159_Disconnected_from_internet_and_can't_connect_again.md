---
title: "Disconnected from internet and can't connect again on Acer Aspire One"
date: 2009-04-24
forum: Hardware
---

### Post by chris.willis on 2009-04-24
Hi there, just installed Jaunty on an Acer Aspire One and everything worked - was amazing. After using the net (wireless) and getting updates and programs, I used the network connection manager icon and disconnected form the net to save on battery life. Now I cannot connect back to the internet.

I have used the alternative driver. With or without it, I can get to the two circles where it tries to connect, but continues to fail. There are no wireless connections available. It's as if the driver is dead. Using the same machine, I booted into Windows, and can connect so it appears I stuffed something up.

Very new to Ubuntu so excuse the longwinded description. If anybody knows what to do please speak newbie language, and I'd appreciate the help.

Regards
Chris

---

### Post by JoshuaRL on 2009-04-24
Try right-clicking the connection icon and Edit Connections.  From there, delete the one you have, and add another.  See if it can connect to your chosen one that way.

---

### Post by chris.willis on 2009-04-24
Deleted it then clicked Add. I know the SSID name and password, but don't know the mode, BSSID, MAC Address, MTU, and all the other settings.

When it first installed, I clicked the network icon and there were already about 6 networks on there. I selected my SSID, entered the password, and it automatimagically worked. Can't bring anything up at the minute.

---

### Post by chris.willis on 2009-04-24
Going to reinstall the whole thing as I stuffed it up and have 6 different Ubuntus on it. Thanks for your help again Joshua,
Chris

---

### Post by Aearenda on 2009-04-24
Are you sure you didn't use the wireless kill switch on the front of the AA1? There is no proper indicator for whether it is on or off, and if it is off, wireless will never work. It's a toggle switch - you can't tell from its physical position whether it is on or off. If wireless should work, and doesn't, then try toggling it again until you establish whether it is on or off (or boot into Windows to check).

There is good help at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) for installing Jaunty on the AA1.

PS - Network Manager will add automatic connections for any network it finds, so long as the wireless is on. You should not have to create an entry manually in that list, unless your network is hidden.

---

### Post by chris.willis on 2009-04-24
I'm to reinstall to fix all the problems, so hopefully the wireless won't have that problem again. I did fiddle with the button when it stopped working. Still not clear why it happened, anyhow, have marked the thread as solved and if I have any future problems, I'll create a new post. Thanks for the link to the AAO. Great stuff!

---

