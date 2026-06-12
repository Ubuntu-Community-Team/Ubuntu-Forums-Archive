---
title: "Simple question!"
date: 2008-08-13
forum: General Help
---

### Post by Maelgwyn on 2008-08-13
If I were to create two new users for my flatmates but I'd like each account to be able to access World of Warcraft, where would be the best place to keep the game?
At present it's in my /home/nik/apps/WorldofWarcraft/..... 
I was thinking somewhere like /usr/ but what would happen for r/w access for things like patches?

Thanks guys :)

---

### Post by decoherence on 2008-08-13
> **Maelgwyn said:**
> If I were to create two new users for my flatmates but I'd like each account to be able to access World of Warcraft, where would be the best place to keep the game?
At present it's in my /home/nik/apps/WorldofWarcraft/..... 
I was thinking somewhere like /usr/ but what would happen for r/w access for things like patches?

Thanks guys :)

I would create a new group, add each of your flatmate's accounts to the group, then assign it to your WoW folder with r/w permissions.

Follow the menus

System>Administration>Users and Groups

add your flatmates, then click the "Unlock" button, then click "Manage Groups" and create a new one, say "wowusers" adding both your flatmate's accounts to it.

now 

```

chgrp -R wowusers /home/nik/apps/WorldofWarcraft/
chmod -R g+rwx /home/nik/apps/WorldofWarcraft/
```

You'll have to create launcher icons on their desktop since they won't be able to browse to the folder (unless they have read access to your home)

---

### Post by Maelgwyn on 2008-08-13
Yeah, the other guys have r access to my /Apps/World of Warcraft folder already, so they *can* play it on their profiles.
Only problem is that it runs really slowly whenever they move, which I'm attributing to being in another user's profile? Which is why I'm thinking it might be better to move it to /usr/ or something...

---

### Post by decoherence on 2008-08-14
i'm not sure about wow in particular but perhaps they need write access to the folder as well? i presume wow caches things from the server... without write access i assume it'd have to keep re-downloading. maybe that's causing the slowness? just a hypothesis.

if the permissions are set as i described (with write access) it shouldn't matter what profile the software is in because linux doesn't have that kind of concept of 'profiles' -- just permissions.

---

### Post by Maelgwyn on 2008-08-14
I've tried it, but WoW still freaks out when it's played on either of the other profiles.. >.<

---

### Post by sujoy on 2008-08-14
you could place it in /opt and give the group proper permissions to it.

---

### Post by sayakb on 2008-08-14
Please give descriptive titles to your thread (unlike "n00b here" or "help needed") -- See point 6 of Forums DO's: [http://ubuntuforums.org/showthread.php?t=885589](http://ubuntuforums.org/showthread.php?t=885589)

---

### Post by Maelgwyn on 2008-08-14
> **sujoy said:**
> you could place it in /opt and give the group proper permissions to it.

So move it into /opt and apply the same group permissions as the previous post?

---

### Post by sujoy on 2008-08-15
yes create a separate group, say wowplayers

and then chgrp the directory to that group

sudo chgrp wowplayers /opt/path/to/wow

sudo chmod g+rwx /opt/path/to/wow

---

