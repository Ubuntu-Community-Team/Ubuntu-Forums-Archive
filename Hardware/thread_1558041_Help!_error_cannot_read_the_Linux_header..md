---
title: "Help! error: cannot read the Linux header."
date: 2010-08-21
forum: Hardware
---

### Post by sheepfunk on 2010-08-21
I foolish shutdown my laptop while synaptic was updating my linux headers and now I cannot boot. 

When I boot I get: 

```

error: cannot read the Linux header.
error: you need to load the kernel first.

  Failed to boot both default and fallback entries.

Press any key to continue...

```

Pressing a key just gives me the same message.

I would eternally grateful if anyone can tell me how to repair this, it's my work laptop, and it has a bunch of data on it I need. Thank you in advance.

---

### Post by sheepfunk on 2010-08-21
Now I'm trying to repair my file system with fsck -y and here is the output I get 

ubuntu@ubuntu:~$ sudo fsck -y /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

I don't know what this means...

---

