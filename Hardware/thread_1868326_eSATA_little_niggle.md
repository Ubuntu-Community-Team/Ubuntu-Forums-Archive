---
title: "eSATA little niggle"
date: 2011-10-24
forum: Hardware
---

### Post by dougalkerr on 2011-10-24
I have an eSATA drive for backups and so on. I use the AWN panel for everything and for the most part everything works fine.
The eSATA drive seems to be the only component that has any niggles in as much that when I first got the drive Ubuntu could not see it when I attached it to the system.
I attached it to a Windows environment to see if Windows would pick it up - it did!! That was a downer...
Anyways, it seemed that it was not initialized when I did a little bit of digging in Windows because although the drive could be seen by the system Windows Explorer could not see it.
I used the Computer Management tools in Windows to look at the disk and saw the option to initialize it and so I did.
After that the system saw the disk and I could work with it in Windows.
I changed back to Ubuntu and now this system too could see the disk.
I have never had a satisfactory explanation as to why this should be so. If anyone can enlighten me about any missing package/s I might need for eSATA on Linux I would be grateful as I think I will be getting more of these very fast little drives for backup.
Now to come to the niggle I have in AWN panel and the connection of the eSATA in general.
When I connect the eSATA drive the icon does not appear on my Desktop till I have opened my File Manager. In AWN the applet is called 'Places'. I cannot open the eSATA drive by clicking on the menu entry but, if I click on the 'Computer' or any other menu entry, the eSATA drive will then appear on the Desktop as well as the File Manager.
Again I would be grateful if anyone has ideas about what might be missing or needing tweaked.
Thanks.

---

### Post by dougalkerr on 2011-10-24
It would appear to be an AWN panel problem because it opens just fine from the Places dropdown menu. Mind you this does not explain why it does not appear on the Desktop till I go into the dropdown menu.

---

### Post by dougalkerr on 2011-10-24
Having said that, I left my eSATA plugged in and had the laptop turned off for a few hours. When I turned the system back on my eSATA is not seen till I physically disconnect and reconnect...
It is a little thing but, we must strive for perfection.

---

### Post by foresthill on 2011-10-24
> **dougalkerr said:**
> Having said that, I left my eSATA plugged in and had the laptop turned off for a few hours. When I turned the system back on my eSATA is not seen till I physically disconnect and reconnect...
It is a little thing but, we must strive for perfection.

So long as the perfect does not become the enemy of the "good enough".  :p

---

