---
title: "USB Doesnt Work"
date: 2011-03-02
forum: Hardware
---

### Post by shanetlbrt on 2011-03-02
I recently installed Ubuntu 10.04 on an old Toshiba Tecra A4, and the usb ports dont work. The ports are in good physical condition, because they worked when I had windows on it, but the Ubuntu installation caused them to not work.
On boot, it says something about disabling IRQ 11. I dont know what 11 is used for or how to enable it.

Any help would be appreciated.:D

---

### Post by jeremyjjbrown on 2011-03-02
IRQ #? is the interrupt request that one of your devices uses to say excuse me I have input to the processor.

I can't tell you how to fix it, you'll have to google.

---

### Post by jeremyjjbrown on 2011-03-02
By the way. Have you booted to all of the kernels on your GRUB list? 

Update and try all Kernels at startup because one of them may not have this problem. You can even install older kernels if you need to there is documentation available online.

---

### Post by shanetlbrt on 2011-03-02
I just updated, and the same problem is still occurring. Also, How to I get to the grub menu?

---

### Post by jeremyjjbrown on 2011-03-02
To try a different Kernel you have to reboot and select from the GRUB menu. The list of options should contain one or more kernels.

Here is a thread on installing older kernels.
[http://ubuntuforums.org/showthread.php?t=1511029](http://ubuntuforums.org/showthread.php?t=1511029)

I can't guarantee an older kernel will fix your issue. But many times it works and it's easy.

---

### Post by shanetlbrt on 2011-03-02
Nope, I tried using an older kernel and it still said disabling irq 11 and the usb still doesnt work.

---

### Post by jeremyjjbrown on 2011-03-02
Does usb work if you boot from a livecd?

---

