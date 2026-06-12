---
title: "How to reclaim ownership of a harddrive with reiserfs"
date: 2012-03-01
forum: Hardware
---

### Post by redaxe90 on 2012-03-01
Howdy folks, I'm back with a smallish (I hope) problem.

I've been searching the interweb, high and low, for a way to reclaim ownership of one of my hard drives. It's formatted with reiserfs and has quite a bit of data on it, which I want to rescue, before using the hard drive as a system disk for a clean installation. This is something I want to do from the LiveCD of Ubuntu 10.04.

I've tried your basic copy/paste from the drive to the rescue location, only getting the permission denied response, so the data is stuck there until I get this sorted. Is there an easy way for a complete and utter n00b to do this without losing all the precious data?

---

### Post by winh8r on 2012-03-01
Basically, yes!


```
sudo apt-get install testdisk
```

you can find out more from here:

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

read through it and if you have any questions make sure you ask them before you attempt anything!

Hope this helps you.

---

### Post by redaxe90 on 2012-03-01
Thanks for the reply

I don't have a problem in having deleted the files or lost the partition. I can see all the files without a problem. My problem is copying them from one location to another without the darn lack-of-permission message interfering.

Is that also possible without any great hassle??
I'm running out of time with the rescue, so any help on this would be greatly appreciated.

---

### Post by redaxe90 on 2012-03-01
> **winh8r said:**
> Basically, yes!


```
sudo apt-get install testdisk
```you can find out more from here:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

read through it and if you have any questions make sure you ask them before you attempt anything!

Hope this helps you.

Thanks for the reply, though there was a smallish problem, due to my running of only the LiveCD, the computer has no OS at all apart from that.

```

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk

```So as you can see, I can't install this program in the LiveCD session.

---

### Post by winh8r on 2012-03-01
Can you try:

```
gksudo nautilus
```

and navigate to the drive that way, then move them to another medium.

---

### Post by redaxe90 on 2012-03-02
> **winh8r said:**
> Can you try:

```
gksudo nautilus
```and navigate to the drive that way, then move them to another medium.

Again, no joy :(

```

Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```Any other ideas?

[UPDATE]
It seems that the Nautilus session is partly active, at least it seems like I can copy some of the data, though quite a bit is inaccessible due to permission lacking. Any idea on how to get around that?

[Another Update]
Another message from Nautilus popped up in the terminal
```
** (nautilus:15964): WARNING **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files

```

---

### Post by winh8r on 2012-03-02
Okay, run the live cd , locate the files that you cannot move and then open a terminal and try this:

```
sudo chown -R ubuntu <path/to/file>
```

You can enter the path to the file by clicking on the file and selecting copy then paste the filename into the terminal at the appropriate point.

When you copy a pathname like this remember to change the file:///media part to just /media/rest/of/path/to/file (remove the first 2 slashes  and the file: part)

then hit enter.

This should change the ownership of the file to ubuntu -Live Session User and allow you move them.

Hope this helps.

---

### Post by redaxe90 on 2012-03-02
> **winh8r said:**
> Okay, run the live cd , locate the files that you cannot move and then open a terminal and try this:

```
sudo chown -R ubuntu <path/to/file>
```You can enter the path to the file by clicking on the file and selecting copy then paste the filename into the terminal at the appropriate point.

When you copy a pathname like this remember to change the file:///media part to just /media/rest/of/path/to/file (remove the first 2 slashes  and the file: part)

then hit enter.

This should change the ownership of the file to ubuntu -Live Session User and allow you move them.

Hope this helps.
Thanks for the idea, but unfortunately the terminal rejected the idea outright. But it seems like the files have still managed to move across. In any case, I'll try my luck with what's already saved and moved and now I'll install the OS. Thanks for bouncing the ideas off on me, I'm just sorry they didn't pan out :(

---

