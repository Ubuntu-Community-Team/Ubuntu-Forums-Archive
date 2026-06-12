---
title: "[SOLVED] Just need a simple Yes or No..."
date: 2008-10-03
forum: General Help
---

### Post by DivinityX on 2008-10-03
I'm wanting to make a partition in my laptop's Hard Drive to install Windows XP as a second OS. Will resizing my hard drive in gparted wipe my data?

---

### Post by binbash on 2008-10-03
You cant wipe the data, NO, but you cant resize a partiton which is mounted.So if you want to resize the partiton which gparted runs, you gonna do it via gparted LIVE CD.

---

### Post by Sef on 2008-10-03
> I'm wanting to make a partition in my laptop's Hard Drive to install Windows XP as a second OS. Will resizing my hard drive in gparted wipe my data?


**Back up **your data before resizing.   There are no guarantees that all will go well.

---

### Post by DivinityX on 2008-10-03
coolness, that's what i thought. i will back up as well! ^_^

[SOLVED]

---

### Post by cariboo on 2008-10-03
Remeber that NTLDR needs to be on the first partition or Windows won't boot.

Jim

---

### Post by Herman on 2008-10-03
Err...
That's not correct in my experience, you just need to be able to edit boot.ini and you should be able to get Windows to boot in any partition. I'm sorry for contradicting anyone, but it will save the OP a lot of time if they only have to resize the Ubuntu partition from the right.

---

