---
title: "Amarok collection.db help :("
date: 2008-08-26
forum: General Help
---

### Post by Cardcaptor Stacey on 2008-08-26
Hi

I just upgraded my Ubuntu (from 7) to 8. Last time I changed from Debian to Ubuntu 7 and just copy and pasted by collection.db into the folder and everything was fine but not this time. I think my previous version of Amarok was 1.4.7 but I'm now 1.4.9.1. Can you help me restore my collection? I don't mind making changes to my SQL Lite db to get it to work

Thanks

---

### Post by Elfy on 2008-08-26
Is sqlite not the default collection database - what problems do you have with the collection.db?

I didn't get any problems when I changed.

---

### Post by Cardcaptor Stacey on 2008-08-26
Amarok isn't reading my collection.db :( It's all blank. It's showing the first time user thing "Hello Amarok user!". I've checked my collection in a SQ Lite browser and it's all there.

---

### Post by Elfy on 2008-08-26
It was just the original database yes - I mean you didn't do anything other than let amarok build the database in the first place.

Also I assume that the database is in the correct place in your /home.

---

### Post by Cardcaptor Stacey on 2008-08-26
> **forestpixie said:**
> It was just the original database yes - I mean you didn't do anything other than let amarok build the database in the first place.

Also I assume that the database is in the correct place in your /home.
Yes, it's the original database. Just copied and pasted it into  .kde/share/apps/amarok

---

### Post by Cardcaptor Stacey on 2008-08-26
Nevermind. I let it create all it's files again, then copied and pasted collection.db then left Amarok open for a little while. While I was away from the comp, my collection came back :S Well, it's fixed now! :D

It has lost most of its cover art, but I can do that again :P

forestpixie - Thanks for your help :D

---

### Post by Elfy on 2008-08-26
Aaah.. maybe it updated it's database then - cover art though is a different file, in ~/.kde/share/apps/amarok/albumcovers

Bit odd though, never had a problem at all with it recognising old collection.db's

---

