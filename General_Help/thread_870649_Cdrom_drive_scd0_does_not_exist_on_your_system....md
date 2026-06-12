---
title: "Cdrom drive scd0 does not exist on your system..."
date: 2008-07-26
forum: General Help
---

### Post by dags35 on 2008-07-26
please configure your cdrom drive first. This is the message I get when I open rubyripper. Do I need to do something? The drive reponds through software to open/eject disk. It is an cd-dvd multi recorder, it can burn both CDR and DVD's. I have not tried to burn any disks through any other software.

---

### Post by iaculallad on 2008-07-26
> **dags35 said:**
> please configure your cdrom drive first. This is the message I get when I open rubyripper. Do I need to do something? The drive reponds through software to open/eject disk. It is an cd-dvd multi recorder, it can burn both CDR and DVD's. I have not tried to burn any disks through any other software.

Post whatever displays when you issue the command below on your terminal:

```
ls -l /dev/scd*
```
and
```
ls -l /dev/cdrom*
```

---

### Post by dags35 on 2008-07-26
troy@troy-desktop:~$ ls -l /dev/scd*
brw-rw----+ 1 root cdrom 11, 0 2008-07-26 17:27 /dev/scd0

---

### Post by dags35 on 2008-07-26
troy@troy-desktop:~$ ls -l /dev/scd*
brw-rw----+ 1 root cdrom 11, 0 2008-07-26 17:27 /dev/scd0
troy@troy-desktop:~$ ls -l /dev/cdrom*
lrwxrwxrwx 1 root root 4 2008-07-26 17:27 /dev/cdrom -> scd0
troy@troy-desktop:~$

---

### Post by Lem on 2008-07-29
In preferences change cdrom device from /dev/cdrom to /dev/scd0

Daft, but it works!

---

### Post by dags35 on 2008-07-29
> **Lem said:**
> In preferences change cdrom device from /dev/cdrom to /dev/scd0

Daft, but it works!
You lost me, where? What? I went to system, preferences and then got lost. Help!

---

### Post by mc4man on 2008-07-29
> You lost me, where? What? I went to system, preferences and then got lost He probably meant preferences of rubyripper. Most cd/dvd apps will have a default device set, typically /dev/cdrom for cd apps and /dev/dvd for dvd apps, movieplayers ect.
run ```
lshw -C disk
``` to ck. logical names of your cd/dvd drive(s).
(you can use sudo on above to ck. all your drives)

Adjust your apps to match the drive links (in the apps settings, preferences ect.)

You may find your cd/dvd drive is /dev/scd0 with links of /dev/cdrom1, /dev/dvd1, ect. (or sometimes higher )
If so and you want to set straight (eliminates setting default device in your related apps) post results from above and this (use a full screen terminal to run, easier to read)

```
 cat /etc/udev/rules.d/70-persistent-cd.rules
```

Edit:
Just built and tried rubyripper, works fine but it doesn't work off of /dev links as mentioned by lem. Just specify the device in rubyripperes' preferences, ie. /dev/scd0 or /dev/scd1 ect., whatever is the device you want to use.

---

### Post by Lem on 2008-07-30
> **dags35 said:**
> You lost me, where? What? I went to system, preferences and then got lost. Help!

Sorry.. preferences in RubyRipper, not system>preferences!

---

