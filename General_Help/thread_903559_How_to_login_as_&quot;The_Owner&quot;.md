---
title: "How to login as &quot;The Owner&quot; ?"
date: 2008-08-28
forum: General Help
---

### Post by CremeSoda on 2008-08-28
...

---

### Post by tuxxy on 2008-08-28
The owner? if you mean superuser then open a terminal and type su , then enter password, or type root as username and the admin password at login, you must of enabled root user account to do this.

---

### Post by snowpine on 2008-08-28
When you are installing and it asks you for a username, enter "TheOwner", LOL! There is no "owner" in Ubuntu, I think you are a little confused. :)

---

### Post by mellowd on 2008-08-28
The owner?

---

### Post by CremeSoda on 2008-08-28
Thanks tuxxy your the best !

---

### Post by CremeSoda on 2008-08-28
Aww ok another prob. lol , when i type su they ask for my password, i type it and that said "su: Authentication failure".

Sorry for my bad english :)

---

### Post by Joeb454 on 2008-08-28
To temporarily login in to a terminal as root, enter ```
sudo -i
```

If you wish to login as root permanently (bad idea). You will have to look elsewhere as it is not supported on these forums.

---

### Post by toni_uk on 2008-08-28
well, instead of su - that is the root account (you call it owner) use 'sudo' infront of a command. This will also ask you for a password but this time it is your username's password. That should work.

If you really need su - root access then you need to set up the password first. In system/administration user/group management you should put a password against root. Then you can use that using su.

---

### Post by scalywag66 on 2008-09-10
> **snowpine said:**
> When you are installing and it asks you for a username, enter "TheOwner", LOL! There is no "owner" in Ubuntu, I think you are a little confused. :)

I hate it when people answer like this when I'm sure they know what the person is asking for.

In case you really do know a bit more than the usual Ubuntu rookie, but for some odd reason still don't know what the hell 'owner' is, than I shall help explain.  

I get the same issue sometimes where I may want to copy & paste some info from a particular folder( lets says from a folder on Windows to a folder on Ubuntu), but often I wont get the Paste option highlighted, so I'll right click, check properties, and under Permissions tab I usually see.... 

"You are not owner, you can not change permissions."

I don't really know my way around this because most fixxes posted on various forums still leaves me helpless since they don't do much in terms of recognizing me as 'owner', especially since I'm the only account on Ubuntu.

---

### Post by snowpine on 2008-09-10
> **scalywag66 said:**
> I hate it when people answer like this when I'm sure they know what the person is asking for.

In case you really do know a bit more than the usual Ubuntu rookie, but for some odd reason still don't know what the hell 'owner' is, than I shall help explain.  

I get the same issue sometimes where I may want to copy & paste some info from a particular folder( lets says from a folder on Windows to a folder on Ubuntu), but often I wont get the Paste option highlighted, so I'll right click, check properties, and under Permissions tab I usually see.... 

"You are not owner, you can not change permissions."

I don't really know my way around this because most fixxes posted on various forums still leaves me helpless since they don't do much in terms of recognizing me as 'owner', especially since I'm the only account on Ubuntu.

Apologies for the snarky post earlier. :)

If you want unlimited access to copy, paste, delete, move files anywhere (be careful!), you can open your file manager as the root user:

```
gksu nautilus
```

---

### Post by billgoldberg on 2008-09-10
One reason Ubuntu is safer than other distro's and more noob proof is because it doesn't allow a root login by default.

There is really no reason you can't use sudo instead (for normal users).

If you have to ask how to enable the root account in Ubuntu, you are not "qualified" to use it.

---

### Post by kiming on 2008-09-12
hi snowpine

thanks for this " gksu nautilus " its helping me :D

---

### Post by theultimatejhagdu on 2010-07-05
> **snowpine said:**
> Apologies for the snarky post earlier. :)

If you want unlimited access to copy, paste, delete, move files anywhere (be careful!), you can open your file manager as the root user:

```
gksu nautilus
```
it finally said like it has failed to do so after i used the command

---

### Post by Iowan on 2010-07-05
Old thread - closed.

---

