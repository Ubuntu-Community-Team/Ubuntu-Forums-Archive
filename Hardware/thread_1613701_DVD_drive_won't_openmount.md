---
title: "DVD drive won't open/mount"
date: 2010-11-04
forum: Hardware
---

### Post by danbaark on 2010-11-04
I'm using Ubuntu 10.10 and the dvd drive fails to open or mount. (It works fine while the laptop is booting but once the OS is loaded does nothing). It does open using the eject command but that's the only way I've been able to make it do anything.

Can anyone help? Thanks very much!

---

### Post by danbaark on 2010-11-04
Turns out other discs work so can only assume I had a dodgy batch of discs or something...

---

### Post by danbaark on 2010-11-09
It seems that all commercial DVDs work fine but DVD-R discs don't mount at all (blank or written) and basically don't do anything. Can reproduce the problem with different discs.

Anyone know what's going on here?

---

### Post by danbaark on 2010-11-09
Trying to mount it manually gives me this error message?

**sudo mount /dev/sr0 /mnt**
```

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: you must specify the filesystem type

```

---

### Post by ppv on 2010-11-09
You could append -t iso9660 to your command.

---

### Post by wojox on 2010-11-09
It sounds like you have a dvd reader and not a dvd writer.

---

### Post by danbaark on 2010-11-09
@ppv Thanks that command works fine! Can you explain why it's necessary though please? It seems like more of a workaround than a solution?

And no it's definitely a DVD+-RW

Thanks very much

---

### Post by ppv on 2010-11-09
> **danbaark said:**
> @ppv Thanks that command works fine! Can you explain why it's necessary though please? It seems like more of a workaround than a solution?

And no it's definitely a DVD+-RW

Thanks very much

It is needed to tell the type of filesystem which is present on the disc. Discs more often then not in general cases use iso9660. There are others such as UDF but it would be needed to specifically use them while creating the discs.

---

### Post by danbaark on 2010-11-09
OK so would adding an entry to my fstab file with that in help? By setting that filetype as a default? There doesn't seem to be any entry for the dvd drive at all at the moment?

---

### Post by ppv on 2010-11-09
Yeah. Also you could use auto instead of iso9660. That way it will try to auto detect the type of filesystem. And if you want in fstab you may also append the word user in the entry so that users other than superuser could mount the disc.

---

### Post by danbaark on 2010-11-10
Could you help me with what the exact fstab entry should be? I tried:

/dev/sr0    /media    auto    user,rw,exec    0    0

But that didn't let it mount automatically either

Thanks

---

### Post by ppv on 2010-11-12
> **danbaark said:**
> Could you help me with what the exact fstab entry should be? I tried:

/dev/sr0    /media    auto    user,rw,exec    0    0

But that didn't let it mount automatically either

Thanks

Could you try something like 
/dev/sr0    /media/dvd    auto    user,ro,exec    0    0

You could replace dvd in /media/dvd with a name of your choice.

---

