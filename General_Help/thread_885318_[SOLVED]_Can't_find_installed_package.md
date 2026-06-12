---
title: "[SOLVED] Can't find installed package"
date: 2008-08-10
forum: General Help
---

### Post by rocknzen on 2008-08-10
Okay I'm at my wits end. I installed cairo-dock using deb. I realized I made a mistake. There are 2 packages to install and I realized I installed the wrong one first. Of course I didn't realize it right away. 

I realized it when I tried to configure the dock. It runs and looks okay but I cant really customize it. 

I searched for it in every imaginable way. I finally found it in the applications folder. I scoured different forums and such and tried every command possible to remove it. When I try add/remove it does not show up in Synaptic.

By the way, I am running Hardy Heron and I have 20+ years of experience with PC's but only about 5 days with Linux.Yeah I finally made the jump and I couldn't be happier, except maybe when I solve my current dilemma.

---

### Post by Stemp on 2008-08-10
They want to hide ? 
Ok, let use the mighty Terminal !
And use this command :
```
aptitude search cairo-dock
```

---

### Post by rocknzen on 2008-08-10
> **Stemp said:**
> They want to hide ? 
Ok, let use the mighty Terminal !
And use this command :
```
aptitude search cairo-dock
```
Okay this is the output - 

bob@MyLaptop:~$ aptitude search cairo-dock
i   cairo-dock                      - A light and eye-candy dock to launch your
b

---

### Post by Stemp on 2008-08-10
```
sudo aptitude purge cairo-dock
```

That's it ;)

---

### Post by rocknzen on 2008-08-10
Fantastic thank you. I imagine that working with this for a little while it will become old hat as they say. By the way can you recomend a good firewall. I am not very familliar with iptables and things like that. So something simple and easy to set up. Maybe with a graphical interface:) ???????

---

### Post by Stemp on 2008-08-10
You're welcome.
For the Firewall I recommend Firestarter which is a graphical front-end to iptables.
It's available in the repositories.
[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)
Have fun.

---

### Post by rocknzen on 2008-08-10
Many thanks for your quick reply and good advice.

---

