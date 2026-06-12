---
title: "[SOLVED] URGENT help needed!!!"
date: 2008-07-25
forum: General Help
---

### Post by s13vin4t0r on 2008-07-25
I am dual booting vista and hardy heron. I installed wine in ubuntu and when I open it, it kind of split and mirrored the screen and distorteted it badly. I had to shut down by holding the power button on my laptop becuase i couldnt shut down normally. Now when I boot into ubuntu, it checks the disks and comesup with an error message, saying smething about "fsck" failing. Then it says something like "bash" command couldn't not be found. I can't get into ubuntu at all!!

Please help!!! :(

---

### Post by s13vin4t0r on 2008-07-25
anyone!?!? i really need help here!

---

### Post by sdennie on 2008-07-25
Please don't bump your threads every 11 minutes.  It makes it less likely that someone will see them on these forums: [http://ubuntuforums.org/showthread.php?t=82471](http://ubuntuforums.org/showthread.php?t=82471)

---

### Post by s13vin4t0r on 2008-07-25
well i need help!!

i know its against the rules, but i really want to fix this! i just got ubuntu working today and its ALREADY broken! :(

---

### Post by forger on 2008-07-25
You have to check your hard drives

1) fire up the ubuntu live cd - **[COLOR="Red"]Do not mount the hard drives or double their icons on desktop![/COLOR]**
2) head to applications > accessories > terminal
3) type:
```
ls -1 /dev/sd* /dev/hd*
```

The above command will show you your hard drive devices/partitions
e.g.
/dev/sda1
/dev/sda2
/dev/sdb1
etc.

You get them one by one and type the following command:
```
e2fsck -fp /dev/sda1
```
where you replace /dev/sda1 with the partition you want.

It might ask you some things during checkup, press yes (y) and enter to confirm that you want the program to do that

---

### Post by forger on 2008-07-25
..what happened with the urgency? :)

---

### Post by s13vin4t0r on 2008-07-25
sorry i had to sleep. thanks a lot ill try it in a little bit.

---

