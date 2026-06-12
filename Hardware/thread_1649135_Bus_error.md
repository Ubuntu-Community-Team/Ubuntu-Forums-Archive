---
title: "Bus error"
date: 2010-12-19
forum: Hardware
---

### Post by fmigpaulo on 2010-12-19
Hi,
I've recently switched from (awesome) Ubuntu 9.1 to Ubuntu 10.x

My Ubuntu 10.1 experience was problematic ([http://wwww.ubuntuforums.org/showthr...1601810&page=2](http://wwww.ubuntuforums.org/showthr...1601810&page=2)).

After that, I decided to install a fresh copy of Ubuntu 10.04 with a diferent file system...
My laptop is an HP 530.

I'm troubled again, this time because of an bus error that prevents me from running gimp and software-center. Maybe this errors are connected!?

I've tried to reinstall software-center but i could't because of the same error that prevented me from starting it.

Here's what i've got from log/messages:
```
kernel: [ 4310.860042] ata3.00: configured for UDMA/100
kernel: [ 4310.860062] sd 2:0:0:0: [sda] Unhandled sense code
kernel: [ 4310.860067] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
kernel: [ 4310.860075] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
kernel: [ 4310.860085] Descriptor sense data with sense descriptors (in hex):
kernel: [ 4310.860090]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
kernel: [ 4310.860113]         12 8e da 0c 
kernel: [ 4310.860123] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
kernel: [ 4310.860134] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 12 8e da 06 00 00 08 00
kernel: [ 4310.860188] ata3: EH complete
```


Can anyone please help me?

---

### Post by fmigpaulo on 2010-12-29
bump

---

