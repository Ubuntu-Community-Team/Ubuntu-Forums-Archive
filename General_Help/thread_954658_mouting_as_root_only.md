---
title: "mouting as root only"
date: 2008-10-21
forum: General Help
---

### Post by sim-value on 2008-10-21
Hi !

Since the lastes update i get an error when trying to  mount my 2nd partition (NTFS) or my external Harddrive (FAT i think)

but it still works as ROOT ...

Greetings /me

---

### Post by Paul41 on 2008-10-21
Did your permissions on the drives change?

---

### Post by sim-value on 2008-10-21
nope

---

### Post by Paul41 on 2008-10-21
What is the error you get?

---

### Post by Titan8990 on 2008-10-21
I don't think you can apply EXT3 partitions to a NTFS drive but you can try:


sudo chown YOURUSERNAME MOUNTPOINT

---

### Post by jerome1232 on 2008-10-21
Is this something that is in you fstab or just a usb drive?

If it's in your fstab try adding the 'user' option

And no permissions don't work on ntfs :)

---

### Post by sim-value on 2008-10-21
Error org.freedesktop.DBus.Error.AccessDenied.

ill try this command but i think its the same as changing owner from Properties menu which does not work..

---

### Post by sim-value on 2008-10-21
> **jerome1232 said:**
> Is this something that is in you fstab or just a usb drive?

Both .

I have the same problem with the NTFS partition of my built-in harddrive and my external HDD ...

EDIT: only difference with the NTFS drive i have acces as normal user after mounting as root on the external i havent

---

### Post by jerome1232 on 2008-10-21
The only thing I can think of is to pop open gconf-editor and make sure your settings for ntfs and ntfs-3g are the same as what I have here.

alt+f2 then type 'gconf-editor'

---

### Post by prshah on 2008-10-21
> **sim-value said:**
>  get an error when trying to  mount my 2nd partition (NTFS) or my external Harddrive (FAT i think)
but it still works as ROOT ...


1st) Can you mount it manually? [Install pmount]("apt://pmount"), then open a terminal, and give the command```
pmount /dev/sdXY
``` (Replace sdXY with actual device name; note, no sudo).

If you can mount it manually, we can proceed further on how to automate it if you post your /etc/fstab.

---

### Post by sim-value on 2008-10-21
Sorry for bothering you guys ...

The problem was that the PC crashed during update ... 

/me

---

