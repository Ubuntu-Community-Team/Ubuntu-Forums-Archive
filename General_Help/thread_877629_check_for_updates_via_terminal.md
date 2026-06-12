---
title: "check for updates via terminal"
date: 2008-08-02
forum: General Help
---

### Post by survient on 2008-08-02
I need a way to check for updates via the terminal, and for it to return a list of available updates, or at least return something that says updates are available. I can't use something like sudo aptitude, I need it to spew out the list as return arguments. Anybody know something that does this?

---

### Post by Locutus_of_Borg on 2008-08-02
apt-get --no-act upgrade

?
that should just present a list of what it would do without the no-act option

i dont know exactly though

---

### Post by p_quarles on 2008-08-02
```
sudo apt-get update; sudo apt-get upgrade
```
will update the cache, calculate changes, and ask you to confirm or deny before it actually does anything. That's one way.

---

### Post by Locutus_of_Borg on 2008-08-02
> **p_quarles said:**
> ```
sudo apt-get update; sudo apt-get upgrade
```
will update the cache, calculate changes, and ask you to confirm or deny before it actually does anything. That's one way.

i have noticed in the past that i did not always get asked for confirmation before it began...

---

### Post by p_quarles on 2008-08-02
> **Locutus_of_Borg said:**
> i have noticed in the past that i did not always get asked for confirmation before it began...
I think there's a threshold for number of bytes of changes before it asks for confirmation. As you say, though, the --no-act (or just -s) argument will prevcent it from doing anything under any circumstance.

---

### Post by survient on 2008-08-02
:popcorn:

found it. it's:
sudo /usr/bin/apt-get -q -y --allow-unauthenticated -s dist-upgrade | /bin/grep ^Inst | /usr/bin/cut -d\  -f2 | /usr/bin/sort

gotta love apticron scripts D:

---

