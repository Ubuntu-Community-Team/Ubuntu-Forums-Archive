---
title: "Booting Problem"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by kbagher on 2009-02-10
Hello.
I'm Using Ubuntu 8.04LTS on my Dell inspiron 1525 Notebook

and i saw a tutorial how to install Ubuntu on a flash driver.

so i Bought 16 MB USB flash Driver and installed ubuntu on it with no problems till now.

but the big problem is that i can't start Ubuntu on my notebook without the USB Flash Driver , because i think the boot files are on it!!!


so how can i put a boot files on my notebook an boot files on my USB flash ,so that booth will work with no problems?

thanks :P

---

### Post by jimv on 2009-02-10
The problem is that each drive (your computer and the thumbdrive) needs it's own copy of grub.  So first we need to set your computer to boot from it's own drive again.  To do that, boot your computer without the thumbdrive and press "C" on your keyboard when you see the GRUB screen.  Type these commands:
```

root (hd0,0)
setup (hd0)
reboot
```

Your machine should boot up like it used to.  Once you are in Ubuntu, plug in the thumbdrive.  Open a terminal (Applications > Accessories > Terminal) and type:

```
sudo grub
```

This will give you a prompt that looks like this:

```
grub>
```

Type this command:

```
find /boot/grub/menu.list
```

It should give you two entries back, (hd0,0) and something else.  We're after the one that is not the (hd0,0) entry, which is the thumbdrive.  Now we want to set up GRUB on the thumbdrive, so type in these commands:

```
root (hd1,0)  <--- substitute whatever the line was from the previous command for hd1,0
setup (hd1)  <--- once again, substitute the first part of the previous line for hd1
quit
```

Now you can reboot and try booting from your thumbdrive.

---

### Post by kbagher on 2009-02-10
Thanks so much , that helped :)

but i would like to point to this step

```
find /boot/grub/menu.list
```

i had to change the word

```
list
```

to

```
lst
```

thanks a lot Mr.Jim :popcorn:

---

