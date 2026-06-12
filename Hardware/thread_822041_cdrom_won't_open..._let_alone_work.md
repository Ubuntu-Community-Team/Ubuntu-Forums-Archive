---
title: "cdrom won't open... let alone work"
date: 2008-06-07
forum: Hardware
---

### Post by aHungrySponge on 2008-06-07
this has been a problem for a while... my cdrom won't open at all.

i tried opening it manually through the terminal and this is what i got....

```

cole@colejenkins:~$ eject
eject: tried to use `/dev/scd0' as device name but it is no block device
eject: unable to find or open device for: `cdrom'

```

any ideas?

---

### Post by jpkotta on 2008-06-08
Sounds like your drive wasn't detected properly.  Post the output of the following command.
```

lspci
ls -l /dev/scd*
sudo lshw

```

---

### Post by smilingfrog on 2008-06-22
I am having a similar problem on my laptop. The cdrom does not display in /dev and will not mount or be recognized.

I am running feisty on the laptop. It used to work; I don't know when it stopped.

From other reading, I am told this is an error in the GRUB loader. Any other suggestions?

---

