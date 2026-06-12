---
title: "Grub Error 8"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by millsy74 on 2006-01-11
i did a quick search but couldnt find anything. i tried installing ubuntu on a Creative Zen Micro and everything worked well until it asks to remove the cd and reboot.  It says loading grub then comes up error 2 and doesnt do anything. no buttons do anything except ctrl-alt-delete witch restarts it. if anyone knows what this is any help would be mcuh appreciated.
Thanks

---

### Post by fourchannel on 2006-01-11
[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting]("http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting")

error 8 is that the kernel isn't being loaded. gotta go to class now, but see if you can check over your /boot/grub/menu.lst file and see if the kernel names match up and what not. you will need a live cd for this.

---

### Post by millsy74 on 2006-01-12
its error 2 which is Bad file or directory type
    This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. But how do you fix it. i have tried reinstalling ubuntu and it keeps doing the same thing. i need help.

---

