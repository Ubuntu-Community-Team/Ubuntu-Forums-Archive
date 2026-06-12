---
title: "USB Mp3/Pendrive Issue"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by El Potro on 2007-09-01
Hello!

Before anything, I'm new in the forum, and also in the Ubuntu world, just came from Fedora.
I think Ubuntu is easier, but I miss some things of my Fedora, for example, that I knew the system relatively well, and if something wasn't working, I knew the way out.

Now in Ubuntu, I need the help of you, please!

I have a pendrive/mp3, and when I plug it, it is automounted, but I do not have permissions to create a folder, nor copy a file, anything. I just can see. But if I do a #cp, I can copy then. In X I can't, logged as my user.

How can I fix this?

I'm sure it ain't big deal,

Thank you a lot!

---

### Post by scrooge_74 on 2007-09-01
Is the pendrive in fat32? That should make things easier

---

### Post by El Potro on 2007-09-02
It is in FAT16

---

### Post by rdwtux on 2007-09-02
drives are mounted as the user who was logged in when they are inserted as far as I'm aware.. but fat16 shouldn't matter.. 

it almost sounds like write-protect is on the memory stick. 

what's the output of the 'mount' command when the device is inserted?

---

