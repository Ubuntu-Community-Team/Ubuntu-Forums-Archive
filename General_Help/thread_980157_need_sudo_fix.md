---
title: "need sudo fix"
date: 2008-11-12
forum: General Help
---

### Post by Robdobbin on 2008-11-12
After upgrading to Hardy and using it awhile I suddenly found that the "file system" icon on desktop had a lock shown on it. I then lost access to many file since when I try to use "sudo" I get this message - "sudo: /etc/sudoers is mode 0666, should be 0440" This also happens for any commands needing root access. I tried to fix this using both chown and chmod but must have goofed the syntax or something as nothing changed. Can any lead me through these two problems??

---

### Post by kerry_s on 2008-11-12
sudoers must always be edited with "sudo visudo" you can not change the permission on the file and edit it as a text file.

boot into recovery mode to fix it.

chmod 0440 /etc/sudoers

---

### Post by Robdobbin on 2008-11-13
KERRY I cannot use any form of sudo as I get the same old message "sudo: /etc/sudoers is mode 0666, should be 0440" Any other suggestions??

---

### Post by sisco311 on 2008-11-13
reboot the computer and select the *recovery mode* option from the grub menu.

restore the file permission from the root shell:
```
chmod 0440 /etc/sudoers
```
reboot in normal mode:
```
reboot
```

---

### Post by Robdobbin on 2008-11-15
Thanks much for the help. I no longer get the message that 660 should be 440. However; when I try to use sudo I get the following:" sudo /etc/sudoers is owned by uid 1000, should be 0". Same when I try to use sudo vi to edit the /etc/sudoers file. I guess I need more help.

---

