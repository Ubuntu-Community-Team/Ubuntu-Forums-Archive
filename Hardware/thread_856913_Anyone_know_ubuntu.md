---
title: "Anyone know ubuntu"
date: 2008-07-11
forum: Hardware
---

### Post by magnavox1108 on 2008-07-11
My XP faced a critical system 32 error, so rather reinstall my pirated XP and deal with XP headaches again, i decided to go with ubuntu. I love it except im still getting used to the differences. Now onto the prob, i plugged in my external HDD and it wont recognize it or access it. It says "cannot mount volume" heres a pic (i name my external big boy, lol) [http://img70.imageshack.us/img70/1131/screenshotww9.png](http://img70.imageshack.us/img70/1131/screenshotww9.png) Anyways what can i do so i can access my HDD? any help is greatly appreciated.

---

### Post by magnavox1108 on 2008-07-11
also if i force mount it will i lose my data due to the fact that it used to run on windows?

---

### Post by jonlemur on 2008-07-12
Choice 2 is what I would do.  You shouldn't lose any data due to the file system being NTFS.  Linux can read and write (write as of 8.04 I think) to the NTFS file system.  The only thing I can think of is there may be more complications because Windows did not shut it down properly.  I've never heard of any problems with it, but you may want to wait for someone with more experience than me to respond to this.

---

### Post by matt$2 on 2008-07-12
Choice 2 offered a solution.  Did you try it?   The force option should work.

Alternately,  take an image using partimage.
Format your external drive, either ntfs or fat32.
Inflate you image back on.
If fat32, then you can do an
fsck.vfat
on the file system

That should clean it up.

You can also mount the image file with mount -o loop, copy out your required data and locate it where you like, such as on a freshly reformatted external drive.

---

### Post by bijeeshvs on 2008-07-12
its not a big deal!!!!!!!!. Do one thing, plug it into another windows machine and properly shutdown/disconnect after making a copy paste to that drive(just anything to initiate a read write cycle) and plug it back to linux. It will work without any warning...................

The problem is an unclean shutdown/disconnect from a windows machine.............

---

### Post by matt$2 on 2008-07-12
its not a big deal do one thing plug it into another windows machine

What has happened to people's execution of good grammar.

Am I missing something or is this sample missing full stops and commas and capitals.  Makes it hard to follow.  It's not just you either.

---

### Post by coffeecat on 2008-07-12
> **bijeeshvs said:**
> The problem is an unclean shutdown/disconnect from a windows machine.............

Agreed. NTFS is a journalling filesystem and I guess the journal is inconsistent. That's the trouble with Windows - a ghastly, fiddly way of unmounting drives.

**magnavox1108**, you can repair NTFS from Ubuntu. Check to see if you have ntfsprogs installed - install if you haven't. Plug in your drive. Check the error message to make sure it comes up as /dev/sdb1 again. Then from a terminal do:

```
sudo ntfsfix /dev/sdb1
```

Health warning - I've never had to do this myself. The one time I needed to repair a (shared) NTFS partition Windows did it for me before I could try this out in Linux. Suggest you read man ntfsfix yourself.

---

### Post by bijeeshvs on 2008-07-12
> **matt$2 said:**
> its not a big deal do one thing plug it into another windows machine

What has happened to people's execution of good grammar.

Am I missing something or is this sample missing full stops and commas and capitals.  Makes it hard to follow.  It's not just you either.

Absolutely sorry for that................................

---

