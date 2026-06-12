---
title: "Menu.lst text mode"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by argos3016 on 2009-08-23
Isn't a big problem, but before to update the kernel it boot in text mode. I don't remember the option on the kernel in menu.lst.
single?ro?splash?!??

---

### Post by junke1990 on 2009-08-23
does this help? I dont know what you're looking for

```

title		Ubuntu karmic (development branch), kernel 2.6.31-6-generic
uuid		8a91b0a5-36bb-4eea-b638-35b4c1f7921c
kernel		/vmlinuz-2.6.31-6-generic root=UUID=a18b5bbc-97aa-41f7-ad3a-xxxxxxxxx rw splash vga=771 
initrd		/initrd.img-2.6.31-6-generic
quiet

```

---

### Post by fela on 2009-08-23
Do you mean eliminate the usplash (splash image)? In which case you need to remove the 'quiet' and 'splash' from your grub entry, I believe. If you want the usplash with all the text mode info, just get rid of the quiet.

---

### Post by junke1990 on 2009-08-23
> **fela said:**
> Do you mean eliminate the usplash (splash image)? In which case you need to remove the 'quiet' and 'splash' from your grub entry, I believe. If you want the usplash with all the text mode info, just get rid of the quiet.

shouldnt that be nosplash instead of removing splash?

---

### Post by fela on 2009-08-23
> **junke1990 said:**
> shouldnt that be nosplash instead of removing splash?

I've never used nosplash. Removing splash got rid of splash just fine. I don't think you need nosplash.

---

### Post by argos3016 on 2009-08-25
I put in kernel options "single", but when kernel has started appears a menu with:
1 normal boot
2 file system check
3 blablabla
4 etc
How can I disable that menu?

---

### Post by fela on 2009-08-25
> **argos3016 said:**
> I put in kernel options "single", but when kernel has started appears a menu with:
1 normal boot
2 file system check
3 blablabla
4 etc
How can I disable that menu?

The single option means single user, which is, as I see it, a disaster recovery option. You don't want that (if you don't want that annoying dialog), and it's unnecessary. You should be able to have the default: ```
ro splash
```

EDIT: apparently you might want rw instead of ro.

You can also have options such as vga=xxx, but those aren't strictly necessary. You can also have quiet to stop it displaying messages, or you can get rid of the splash to have a CLI bootup.

Hope this helps :)

---

### Post by junke1990 on 2009-08-25
doesnt the **ro** option make your filesystem read only? had the problem lately so changed it to rw and it was fixed

---

### Post by fela on 2009-08-25
> **junke1990 said:**
> doesnt the **ro** option make your filesystem read only? had the problem lately so changed it to rw and it was fixed

I have the ro option and my filesystem isn't readonly. It's a XFS partition on a LVM group.

My theory is that ro makes your boot partition readonly. I have a seperate boot partition as you can't have one on an LVM, so that's probably the answer. Do you have your boot files on the same partition on everything else, or is it a separate partition?

My self-debunk of my theory is that wouldn't it be impossible for me to edit the grub menu and install kernels if my boot partition was readonly...

---

### Post by junke1990 on 2009-08-25
nope separate, boot, home and /

---

### Post by fela on 2009-08-25
> **junke1990 said:**
> nope separate, boot, home and /

That's my own theory debunked twice then :)

I wonder what it could be then...sounds like an unrelated partition. I mean problem. :lolflag:

---

### Post by junke1990 on 2009-08-25
do you perhaps know why the root parameter isnt just simple /dev/sda but a big uuid

---

### Post by fela on 2009-08-25
> **junke1990 said:**
> do you perhaps know why the root parameter isnt just simple /dev/sda but a big uuid

You can have either I think. I think they changed it to use UUIDs because sda/sdb change round sometimes (they do on my machine, that's why I have to give all my partitions labels to mount them by label). That's my 'theory' anyway...:lol:

---

