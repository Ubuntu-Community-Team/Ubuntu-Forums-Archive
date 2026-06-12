---
title: "Activating swapfile swap [fail] after 9.04 upgrade"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by daqron on 2009-05-02
Hello! Fresh off an upgrade from 8.10 to 9.04 (NOT wubi, just the regular updater) and I'm having an issue at boot. I have the pretty boot screen turned off, so I see all the various system checks as they progress. Everything is [OK] until I get to ...

[FONT="Courier New"]Activating swapfile swap ...      [COLOR="Red"][fail][/COLOR][/FONT]

So far it doesn't seem to affect usage of any software or system functionality, but obviously I do not like for things to fail at boot and I suspect not having a working swap file is going to be an issue sooner or later. 

Cheers in advance for any suggestions.

---

### Post by logos34 on 2009-05-02
maybe the upgrade formatted the swap, changing the UUID..just a guess...

Does swap entry in

sudo blkid

match that in /etc/fstab?

---

### Post by daqron on 2009-05-02
> **logos34 said:**
> Does swap entry in
sudo blkid
match that in /etc/fstab?
Cheers for the fast reply! Perhaps you're on to something; the UUIDs match but the drive does not. However, the drive identifier in fstab is just a comment, so I don't really understand how that could be the issue. Here's what I have (red shows different drive identifiers):

blkid:
```
[COLOR="Red"]/dev/sdb5[/COLOR]: TYPE="swap" UUID="3bcc00b8-6d9f-4f39-bf6a-aab6d7c8edce"
```

fstab:
```
# Entry for [COLOR="Red"]/dev/sdc5[/COLOR] :
UUID=3bcc00b8-6d9f-4f39-bf6a-aab6d7c8edce none swap sw 0 0

```

Can I just run mkswap /dev/sdb5 or will I blow something up?

---

### Post by logos34 on 2009-05-02
no, the drive letter change doesn't affect it since it's using the uuid to find the partition

check [here]("https://help.ubuntu.com/community/SwapFaq#Troubleshooting") for possible solutions

---

### Post by daqron on 2009-05-02
Thanks for the link. I don't know why I couldn't find that when I was searching for a solution earlier. Anyway, here's what ended up fixing the problem:

```
sudo swapoff -a
sudo mkswap -U <UUID> /dev/sdb5
sudo swapon -a
```

Thanks again! Now if someone can tell me how to mark this [SOLVED] I'd be all done here.

---

### Post by logos34 on 2009-05-02
> **daqron said:**
> 
Now if someone can tell me how to mark this [SOLVED] I'd be all done here.

for some reason they removed that option from thread tools. dunno why

good luck

---

### Post by iamkain on 2009-05-18
so i just installed xubuntu and on start up it gets to "swapfile swap" and then it just stops

---

### Post by ottosykora on 2009-09-04
I also wound be interested how to solve the problem when I can not start the system due to this problem at all.

It is nice to says enter sudo and what ever, but my system hangs during the boot and does not recover. I tried the recovery mode, also here nothing.

How to continue and correct something here?

I think this must be a big bug in the 9.04 version, since it comes again and again, even after a new installation, not more then abt 20 starts are possible, then all ends up in swap file.

Installtion with wubi seems not to be possible for that either any more.

---

### Post by ottosykora on 2009-09-04
have just noticed:

there is an infinite size swap file created on boot.

After some trying, managed to delete it and create new one according to the hwto.
But on next boot, again system will hang with activating swap file...

and creating infinitely big file for swap, going for ever apparently.


Please can somebody help me to stop this swapfile thing to enable me to boot into ubuntu again?

I can only remove the file by boot from CD, then setting all up again, just to find that on next boot it is back where it was.

Any help appreciated.

---

### Post by ottosykora on 2009-09-04
so far steps I done:

managed to run the repair mode. Th eonly way to start it was to press ctrl+alt+del when the activating swap came up.

Somehow managed to delete the swap file. 
Followed howtos to create new swap file, format it and made sure it is so in the fstab.
 swapon gives however kind of loop for ever, it simply seems to never end.

before free -m gives all 0

on next boot again it seems that there is an huge swap file created.

Pls help

---

### Post by PieterJ on 2009-10-22
I have the same problem with Ubuntu 9.04 jaunty.
The swap file exists, and all tests show that it is working fine, but is never used.

The problem is that free memory is never released by the kernel, so the system gets really slow, and has to reboot to clear the memory.

I added a cronjob to reboot the server everyday at 5am.

# swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       3903752 0       -1

I recreated the swap partition, but did not help.

This is a serious problem now, and we are considering moving back to 8.04.2 which was the last version that utilized swap.

Please help.

---

### Post by ottosykora on 2009-10-22
After lot of trying I relized that 9.04 tries to use swapfile and all gets confused when swap partition is present. If you remove swap partition, this would be the brute force cure.
But I manged to solve it by

```
sudo swapoff -a
sudo mkswap -U <UUID> /dev/sdb...
sudo swapon -a
```

somehow to get rid of the swapfile.
Delted then the swapfile and all seemed ok.

---

### Post by sdrkee on 2010-06-20
I do get this "activating swapfil swap Fail" on my linux VPS. on top of that when I type any command, it ask me for password. Now i am very confused what password do I need to put.

---

