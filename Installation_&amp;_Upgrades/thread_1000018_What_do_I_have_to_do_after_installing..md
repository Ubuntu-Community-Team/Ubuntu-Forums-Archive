---
title: "What do I have to do after installing."
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by JJ_the-user on 2008-12-02
I installed Ubuntu 8.10 on my pc, along with Windows XP. The first time I runned it, I got some sort of Command Prompt. The place where you type says "grub:". Can anyone help please?

---

### Post by zwygart on 2008-12-02
You probably installed grub not the right way. Does it says any other thing at boot like GRUB boot error?
For the manual of GRUB look at this [http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html")
To boot windows try this commands and let me know what happens
```
rootnoverify (hd0,0)
chainloader +1
makeactive
boot
```

To boot Ubuntu
type find /vmlinuz
it should write something like (hdX,Y), where X and Y are numbers
then type 
```
root (hdX,Y)
kernel /vmlinuz
initrd /initrd
boot
```
May you should replace initrd with initramfs. Any way type 'initrd /ini' then press tab. This should complete the command.

---

### Post by linux_tech on 2008-12-02
Try typing in ```
startx
```

---

