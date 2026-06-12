---
title: "Hard drive failure"
date: 2013-02-18
forum: Hardware
---

### Post by Peterfc on 2013-02-18
Hi All

During a recent power failure when i got power back i tried to switch one of my desktops on. Nothing would happen the machine just seems dead. both other machines are working as they should all are running 12.10. Below is an image of a message i get when connecting the machine via an external Hard Drive cradle to a laptop.

Sorry don't know what else to put that may help you give me an answer.

[IMG]http://i348.photobucket.com/albums/q345/peterfc1/Harddriveerror_zps586a07d8.jpg[/IMG]

---

### Post by papibe on 2013-02-18
Hi Peterfc.

It doesn't look promising. I would start a process of repairing the partitions, or even recovering data if that does not work.

[Here]("https://help.ubuntu.com/community/DataRecovery")'s a good point to start.

Let us know how it goes.
Regards.

---

### Post by tgalati4 on 2013-02-18
Open a terminal:

```
dmesg | tail -100
```

Look for clues as to why the drive isn't mounting.

---

### Post by krizna on 2013-02-18
Try this command 
```

e2fsck -j ext4 /dev/sdb1

```

---

### Post by ahallubuntu on 2013-02-19
~

---

### Post by Peterfc on 2013-02-19
Hi Guys 

Thanks for the help.

I was hoping that the screen shot would say enough as i wasn't sure what else to put. 

Seems i have a lot of work ahead but thanks to you i may get it sorted.

Peter

---

