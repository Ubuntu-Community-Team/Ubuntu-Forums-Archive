---
title: "Grub dual boot list order"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by YawnGnome on 2009-01-20
I know this isn't really a big deal, but i dual-boot ubuntu and vista and was wondering if it is possible to reorder the list that comes up when grub starts running?

I would like to have vista as my primary OS so that when i reboot it goes into windows if I am not there to select one.

---

### Post by WatchingThePain on 2009-01-20
Hi, 

Check this out  [http://fosswire.com/2008/08/09/reorder-your-boot-menu-manually/](http://fosswire.com/2008/08/09/reorder-your-boot-menu-manually/)

I believe this should do it.

---

### Post by taurus on 2009-01-20
Just edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
and change the **default** from 0 to whatever your windows is.  Remember, count each title as 1 and you start counting from 0.

In other words, if title for windows is the fifth entry, than the default should be 4.

---

### Post by 73ckn797 on 2009-01-20
> **taurus said:**
> Just edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```and change the **default** from 0 to whatever your windows is.  Remember, count each title as 1 and you start counting from 0.

In other words, if title for windows is the fifth entry, than the default should be 4.


The section referred to wil be at the top of the "menu.lst" file and look like this:
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        2
```The number at the end of this section is what you will change.

---

### Post by YawnGnome on 2009-01-20
Thanks all that worked!

---

### Post by powerwatt on 2009-01-20
I'm also trying to do this.

However when it opens the gedit is blank.

Am I doing something wrong?

---

### Post by taurus on 2009-01-20
> **powerwatt said:**
> I'm also trying to do this.

However when it opens the gedit is blank.

Am I doing something wrong?

Make sure you type it the way it is.

```
gksudo gedit /boot/grub/menu.lst
```

Otherwise, post the output of this command from a terminal.

```
ls -la /boot/grub
```

---

### Post by powerwatt on 2009-01-20
> **taurus said:**
> Make sure you type it the way it is.

```
gksudo gedit /boot/grub/menu.lst
```

Otherwise, post the output of this command from a terminal.

```
ls -la /boot/grub
```


Sorry, I may be being stupid. I have tried the first option.

How do you mean "post the output of this command"?``

---

### Post by taurus on 2009-01-20
Run the second command from a terminal.  Then, paste the output here.

---

### Post by powerwatt on 2009-01-20
Aha. 

I copied and pasted it and it has worked.

I have no idea what I was typing wrong.

Thanks for your help. Sorry for being a muppet.

---

