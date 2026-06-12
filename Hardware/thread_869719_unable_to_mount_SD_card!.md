---
title: "unable to mount SD card!"
date: 2008-07-25
forum: Hardware
---

### Post by robertchahine on 2008-07-25
hi guys.My brother has a laptop( fujitsu Siemens) , and he's using ubuntu gutsy 7.10. He doesn't want to install hardy heron, he want to wait till interpid Ibex released.His laptop contain a built-in  memory card reader.
When i plug the SD card, nothing happens.

Here's the output of the fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=709a59c9-b02d-41ec-8222-f5e0d10e22cc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=74a62fec-4490-4c16-82c0-8bfa5a4afb79 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```.

and here the output of lspci | grep MemoryCard

```

02:0b.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
02:0b.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
02:0b.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator

```.

how to mount the memory card?
Thanks in advance.

---

### Post by argail1980 on 2008-07-25
plug the sd card in and type ```
dmesg
``` in a terminal. is there any output that could refer to the sd card?

if not, also try typing```
tail -f /var/log/messages
```

then unplug the card and replug it. Post the output, if any.

---

### Post by robertchahine on 2008-07-25
> **argail1980 said:**
> plug the sd card in and type ```
dmesg
``` in a terminal. is there any output that could refer to the sd card?

if not, also try typing```
tail -f /var/log/messages
```

then unplug the card and replug it. Post the output, if any.
thanks for your reply, but nothing refers to the SD card.
but i noticed, that at the /media directory, there's a folder called "cfcard"

---

### Post by argail1980 on 2008-07-25
hmm, judging from this thread here

[http://ubuntuforums.org/showthread.php?t=468485]("http://ubuntuforums.org/showthread.php?t=468485")

you just ran across a card reader that has no support yet. Sorry, this is beyond what I can solve.

---

### Post by robertchahine on 2008-07-25
thank you so much for your replies

---

### Post by argail1980 on 2008-07-25
found something. there seems to be a kernel module

[http://www.denraf.be/category/tagcloud/o2micro]("http://www.denraf.be/category/tagcloud/o2micro")

---

### Post by Janus23 on 2008-09-08
I have an inspiron 1420n running gutsy.  I am also having trouble mounting an sd card.  here is the output - can anyone help me do what I need to? I am new at linux

[   13.013987] Driver 'sd' needs updating - please use bus_type methods
[   13.019308] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   13.019324] sd 0:0:0:0: [sda] Write Protect is off
[   13.019328] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.019350] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.019412] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   13.019419] sd 0:0:0:0: [sda] Write Protect is off
[   13.019421] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.019433] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.019435]  sda:<6>usb 1-2.2: new full speed USB device using uhci_hcd and address 5

---

