---
title: "[SOLVED] What is the root or su password"
date: 2008-08-14
forum: General Help
---

### Post by newnews on 2008-08-14
Hi, All:

I just installed ubuntu 8 in my PC. I want to set default OS to WinXP when booting. I try to edit "menu.lst", but I have no permission to save it,only user root can do. So, what is the default password for user "root"?

Thanks

---

### Post by perlluver on 2008-08-14
> **newnews said:**
> Hi, All:

I just installed ubuntu 8 in my PC. I want to set default OS to WinXP when booting. I try to edit "menu.lst", but I have no permission to save it,only user root can do. So, what is the default password for user "root"?

Thanks

There is no root password by default, instead use sudo, and the password you supplied when you installed Ubuntu.

```
gksudo gedit /etc/menu.lst
```or```
sudo gedit /etc/menu.lst
```

---

### Post by lisati on 2008-08-14
The "root" user is normally disabled by default in Ubuntu.
If you want to edit your menu.lst, a preferred alternative is to call up your favourite text editor, and give it temporary root privileges with the "sudo" (or gksudo) command. 

An example (enter this at the terminal, Applications->accessories->terminal)
```

sudo gedit /boot/grub/menu.lst

```

---

### Post by newnews on 2008-08-14
Thanks everyone. It works. However, I am not sure how to set default no. I have the following entries in menu.lst:

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=37cd8def-d76d-4ad9-88bb-284675d0a936 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=37cd8def-d76d-4ad9-88bb-284675d0a936 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

so WINXP is at no.4; but if I set default no. to 3, I got error message "Invalid value" or similar text. if I set to "1", it goes to second entry "recovery mode" without problem. so, what should be the correct no. for WINXP?

thanks

---

### Post by diwas on 2008-08-14
Try 5.

---

### Post by newnews on 2008-08-14
I tried different no.s and found #4 is right value. Thanks for all replies

---

### Post by aysiu on 2008-08-15
It's not really "or."

It **is** ```
[color=green]gksudo gedit /boot/grub/menu.lst[/color]
```

It is **not** ```
[color=red]sudo gedit /boot/grub/menu.lst[/color]
```

Read more here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by aysiu on 2008-08-15
Too much misinformation was being thrown around here. Since the OP's problem is solved, I've moved that discussion to [There's no need to set a password for root in Ubuntu](http://ubuntuforums.org/showthread.php?t=890817)

---

