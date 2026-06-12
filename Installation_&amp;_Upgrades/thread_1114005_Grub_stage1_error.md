---
title: "Grub stage1 error"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by Felix Lionheart on 2009-04-02
Grub recently stopped detecting my Windows partition and whenever I try to reinstall Grub I get error code 15. It seems I'm missing stage1.

```

grub> find /grub/stage1

Error 15: File not found

grub> 

```

Edit: Finally got it to reinstall Grub but it still doesn't detect Windows.

---

### Post by dandnsmith on 2009-04-02
I don't know how you tried to re-install grub, but it needs to be somewhere where it can (during installation) find the stage1 and other files. There is, I think, an option to show what happens during the install process.

The only way grub can find Windows to start it is if the entry exists in the menu.1st or grub.conf which it is using.

---

### Post by Felix Lionheart on 2009-04-02
> **dandnsmith said:**
> I don't know how you tried to re-install grub, but it needs to be somewhere where it can (during installation) find the stage1 and other files. There is, I think, an option to show what happens during the install process.

The only way grub can find Windows to start it is if the entry exists in the menu.1st or grub.conf which it is using.

I've added an entry in menu.lst but when I select windows I get the message "BOOTMGR is missing".

---

### Post by ronparent on 2009-04-02
So far so good. All your missing BOOTMGT message is telling you is that there is no operating system installed in the drive you are referencing. If you had done a normal install of windows it is probably (hd0,0).

---

### Post by Felix Lionheart on 2009-04-02
> **ronparent said:**
> So far so good. All your missing BOOTMGT message is telling you is that there is no operating system installed in the drive you are referencing. If you had done a normal install of windows it is probably (hd0,0).

I originally used (hd0,0).

---

### Post by ronparent on 2009-04-02
Verify the location of windows and use that location. If verified, then windows might have to be reinstalled or fixed via the original windows install disk. Either process will invalidate the hd0 boot record and you will have to reconfigure grub to access both ubuntu or windows.

---

### Post by Felix Lionheart on 2009-04-03
> **ronparent said:**
> Verify the location of windows and use that location. If verified, then windows might have to be reinstalled or fixed via the original windows install disk. Either process will invalidate the hd0 boot record and you will have to reconfigure grub to access both ubuntu or windows.

Thanks for the help. fixing the startup on Windows worked :)

---

