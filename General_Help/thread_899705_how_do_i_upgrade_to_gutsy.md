---
title: "how do i upgrade to gutsy"
date: 2008-08-24
forum: General Help
---

### Post by IrunoHatake on 2008-08-24
whenever i upgrade to gutsy it freezes and the same spot so can some1 tell me a good easy terminal based way to upgrade from feisty to gutsy

---

### Post by raphaelr on 2008-08-24
I think it is 'sudo apt-get dist-upgrade'
By the way, when exactly is it freezing? Maybe it won't work in the terminal either.

---

### Post by cariboo on 2008-08-24
I would try in a terminal:

```
update-manager -d
```

then use the update manager to update your distribution.

Jim

---

### Post by IrunoHatake on 2008-08-24
> **raphaelr said:**
> I think it is 'sudo apt-get dist-upgrade'
By the way, when exactly is it freezing? Maybe it won't work in the terminal either.

it freezes on wvdial on the installing part (i download 3 times and messes up on that each time) i used howtogeek's guide so idk.

---

### Post by IrunoHatake on 2008-08-25
> **cariboo907 said:**
> I would try in a terminal:

```
update-manager -d
```

then use the update manager to update your distribution.

Jim

i tried that and didn't work

---

### Post by mellowd on 2008-08-25
```
sudo aptitude dist-upgrade 
```

---

### Post by IrunoHatake on 2008-08-25
i tried it and it said nothing upgraded nothing installed etc... so sudo aptitude dist-upgrade didn't NOTHING... any other ideas?

---

### Post by IrunoHatake on 2008-08-26
> **IrunoHatake said:**
> i tried it and it said nothing upgraded nothing installed etc... so sudo aptitude dist-upgrade didn't NOTHING... any other ideas?

any ideas at all?

---

