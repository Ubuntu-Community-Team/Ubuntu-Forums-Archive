---
title: "problem clean up disk space"
date: 2008-08-15
forum: General Help
---

### Post by lieja on 2008-08-15
i try to clean up disk space with this command but the result turned out like this..what should i do..??is there other command to clean up unnecessary files

liza@liza-laptop:~$ sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by bingoUV on 2008-08-15
Ubuntu checks for updates periodically (unless you disable this explicitly). During the time Ubuntu is doing this periodic update check, your apt-get commands will result in such an error. It will work after some time if this is the case.

It could also be that an instance of Add/Remove Programs, or Synaptic, or apt-get is running which you have forgotten about. Try looking for it. If it is totally hopeless to look for open instances of such programs, reboot is a simple option.

---

### Post by dexter on 2008-08-15
If you're using 8.04 there's a black icon visible in the system tray when the packet manager is working. If you hover your mouse over it is says something like "A packet manager is working".

---

### Post by lieja on 2008-08-16
fyi...im using ubuntu gutsy..i also faced problem to updates due to limited disk space..so,this might be the reason for my prob

---

### Post by iaculallad on 2008-08-16
> **lieja said:**
> i try to clean up disk space with this command but the result turned out like this..what should i do..??is there other command to clean up unnecessary files

liza@liza-laptop:~$ sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

On your terminal:

```
sudo rm -rf /var/cache/apt/archives/lock
```
and
```
sudo apt-get clean && sudo apt-get autoremove
```

---

