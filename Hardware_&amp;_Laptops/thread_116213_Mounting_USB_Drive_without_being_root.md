---
title: "Mounting USB Drive without being root"
date: 2006-01-12
forum: Hardware &amp; Laptops
---

### Post by Viro on 2006-01-12
I left my USB drive plugged in when I was installing Ubuntu on a new machine. Now, it doesn't allow me to mount the drive as a normal user. Everytime I want to mount/unmount/write to the drive, I need to drop to the terminal and use sudo to perform those actions.

What settings do I need to change to allow a normal user to access my USB drive? I've tried editing the entry in /etc/fstab and adding the option 'user' but it doesn't seem to do anything.

What else can I do?

---

### Post by mcduck on 2006-01-12
You could try removing the line from fstab completely. After that your drive would be automounted when you plug it in.. :)

---

### Post by Viro on 2006-01-12
Oh.... now why didn't I think of that. :eek: Thanks for the tip.

---

