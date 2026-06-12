---
title: "KnetworkManager doesn't work"
date: 2008-11-16
forum: General Help
---

### Post by Mackwic on 2008-11-16
Hello,

I'm a user of Kubuntu 8.10 since his beginning... and French. So, I apologize for my approximate English. :)

My problem is visible: no application start at the initialization of KDE. I don't have the basket, KnetworkManager and the other. Only the clock.
However the KnetworkManager demon seem to work because the demon log file indicate some errors.

I don't know why and how it's happened and I don't know how correct this...

An other thing, in recovery mode, it's not possible to have internet access.


Thank you for your help.

---

### Post by Chris Musampa on 2008-11-16
Same problem here, I installed Kubuntu 8.1 on a spare partition, started tinkering with the main panel and somehow the widget display got corrupted (they were outside their panel but still moved relative to it), so I deleted the some widgets (including network icon) and now when I try to run it from the menu nothing happens.

I could probably get around it by installing wicd (knetworkmanager still seemed unable to cope with fixed IP address on my wireless connection and also wouldn't retain setting between sessions - until it stopped working altogether that is) but due to screen flicker I'll stick to hardy and KDE3 for a while longer.

---

### Post by Mackwic on 2008-11-16
Someone can help us?

---

### Post by Mackwic on 2008-11-17
No idea? :(

---

### Post by pluviosity on 2008-11-17
> **Mackwic said:**
> Hello,

I'm a user of Kubuntu 8.10 since his beginning... and French. So, I apologize for my approximate English. :)

My problem is visible: no application start at the initialization of KDE. I don't have the basket, KnetworkManager and the other. Only the clock.
However the KnetworkManager demon seem to work because the demon log file indicate some errors.

I don't know why and how it's happened and I don't know how correct this...

An other thing, in recovery mode, it's not possible to have internet access.


Thank you for your help.
When I'm on a wired connection, Knetworkmanager doesn't start for me (it does for wireless :confused: ), but I do have a connection...is that your case, or do you not have internet either way?

Regardless, you can try adding it to Autostart in SystemSettings.  Click on the advanced tab, then add knetworkmanager there...hopefully that helps.  Do the same thing for Basket.

---

### Post by Mackwic on 2008-11-17
Thank you.

So, yes, I've many connections because I manage some networks. Actually I work under Windows but it's not the same...

I'm adding in auto start KNM, the basket and the other softs... I hope that will work.


Actually I have a strange situation... KNW is working on state bar but not next to the clok.... as a soft as Konqueror. And still nothing next to the clock. :confused:
KNM was start after a "startx" in root shell but the mouse doesn't work. After a hard reboot, KNM was start... as... as the screen. ^^

I really apologize for my poor English. :neutral:

---

### Post by Mackwic on 2008-11-17
ooops, soory, bad attachment.

---

