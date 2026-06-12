---
title: "EEE pc ubuntu won't recognize my 2nd hard disk"
date: 2008-08-22
forum: Hardware
---

### Post by Poeli on 2008-08-22
Hi,
Yesterday i've installed ubuntu eee on my eee pc900. It was on the 4 gb hard disk. If i want to open the 8 gb disk it says all the time' failed to mount the disc'. I installed ubuntu from an external cd station.
Anyone an idea what I can do?
thanks!

---

### Post by lswest on 2008-08-22
try this:

```
sudo mkdir /media/second_hdd/
sudo mount /dev/sda2 /media/second_hdd
```

(I assume here that the second disk is /dev/sda2, but it might not be, check with sudo fdisk -l)

If that works, post the contents of /etc/fstab here, and we'll set up an automount for you.

---

### Post by Poeli on 2008-08-23
Thanks, but I'm totally new to ubuntu and I have no idea what you're talking about, do I have to type that in a terminal window?
But then it asks me to type my password, and it seems i can't type a thing then:confused:
Can anyone help me please?
thanks!

---

### Post by lswest on 2008-08-26
type that into a terminal window, and when it asks for your password, just type it in normally.  It will not show any characters at all, to prevent people from figuring out the length of your password, etc.  Just type it in and hit enter.  Sorry for not replying earlier, didn't remember to subscribe to the thread.

---

