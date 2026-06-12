---
title: "External HardDrive Issues."
date: 2008-12-25
forum: Hardware
---

### Post by Celestika6 on 2008-12-25
For X-mas my family bought me a 500GB "My Book" External Hard Drive from Western Digital. (model WD5000H1U-00) The icon appears on my desktop, I click on it and I get a message that says This Media Contains Software and a button that says "Open Autorun Prompt"... So I press the button and I get an error that says "Error Starting Autorun Program: Permission Denied"

Help?

---

### Post by cariboo on 2008-12-25
The reason you get an error, is it that you are trying to run a windows executable in Ubuntu. It won't work, it probably wants to install a Windows backup program. Just ignore it, or delete it.

Jim

---

### Post by Celestika6 on 2008-12-26
I formatted it using gparted to an ext3... now for some reason it's saying it's read-only... how can I convert it? I'm a total newbie to ubuntu... If using the terminal for this is possible, that'd be the easiest for me.

---

### Post by Celestika6 on 2008-12-26
bumped...

anybody? This read me only thing is driving me nuts... also, what disklabel should I set it to?

---

### Post by taurus on 2008-12-26
If you format it to ext3, then you just need to change the ownership of that mount point from root to your username.  That would let you write to it anytime you want without using sudo/gksudo.

Post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
df -h
id
```

---

