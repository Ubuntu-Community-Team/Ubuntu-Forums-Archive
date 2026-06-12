---
title: "understanding &quot;groups&quot;: can I be member of a non existing group?"
date: 2008-11-23
forum: General Help
---

### Post by klaasvanschelven on 2008-11-23
Hi,

I'm having some trouble with installing the betavine UMTS drivers and program. It seems to be related to the way the program deals with groups. I'm stuck at trying to understand in general how *nix works with groups.


the program gives an error complaining the group vmc should have read/write access to /opt/vmc/etc/ppp/peers

ls /opt/vmc/etc/ppp/peers fails with Permission denied
sudo ls -l /opt/vmc/etc/ppp/peers shows two files with

-rw-rw---- 1 root vmc ....

the /opt/vmc/etc/ppp/peers itself has
drwxrwx--x 2 root vmc ...


now for my clue:

/etc/group contains a line:
```
vmc:x:1001:klaas
```

running
```
$ groups klaas
```

gives vmc as one of my many groups

however, running 
```
$ groups
```

gives no vmc group at all! (others are present) Where is the group missing?


I'm running ubuntu 8.04.1 as modified for the eee (called eee-ubuntu by its makers, but I understand that's slightly problematic).

---

