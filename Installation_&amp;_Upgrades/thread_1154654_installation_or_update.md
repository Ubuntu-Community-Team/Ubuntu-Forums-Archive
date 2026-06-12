---
title: "installation or update"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by marioinchina on 2009-05-10
hi,
i'm a newbie in linux and i've got a problem installing any version over 8.04..
so i've installed 8.04 and try an upgrade to 8.1 with the final goal to update to 9.04.
after update to 8.10 complete, i got the error message attached.
the strange thing is that both 8.1 and 9.04 installation fails the same, but in cd mode it works well with both.
any help?
i'm working almost ok with 8.04 386 on my desktop.

sorry for the poor picture, but is done with my mobile phone.

thanks in advance and Best Regards
Mario

---

### Post by Partyboi2 on 2009-05-10
Hi, try adding rootdelay=90 as a boot option. When you boot and see something like "grub loading" press ESC to get to the  grub menu, then highlight the kernel you are using and press "e" to edit then highlight the line starting with "kernel" and press "e" again then at the end of the line add
```
rootdelay=90
``` then press "enter" followed by "b"

If this works you will need to add it to your /boot/grub/menu.lst so that it boots with that option every time.

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation)

---

### Post by marioinchina on 2009-05-11
> **Partyboi2 said:**
> Hi, try adding rootdelay=90 as a boot option. When you boot and see something like "grub loading" press ESC to get to the  grub menu, then highlight the kernel you are using and press "e" to edit then highlight the line starting with "kernel" and press "e" again then at the end of the line add
```
rootdelay=90
``` then press "enter" followed by "b"

If this works you will need to add it to your /boot/grub/menu.lst so that it boots with that option every time.

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation)


unlikely it doesn't work: the strange thing is that is working if i launch 2.26.24-24 kernel, but not 2.6.27-7.
thanks for your help anyhow.

---

### Post by marioinchina on 2009-05-13
hi,
please nobody can help me?
thanks in advance
Mario

---

