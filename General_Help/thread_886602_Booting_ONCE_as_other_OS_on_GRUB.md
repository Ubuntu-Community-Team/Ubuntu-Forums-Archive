---
title: "Booting ONCE as other OS on GRUB?"
date: 2008-08-11
forum: General Help
---

### Post by Fixman on 2008-08-11
I currently have GRUB configured to ask me if to boot from an Ubuntu partition or a Vista partition, and a timeout of 5 secs from where the Ubuntu partition is booted. I know how to set it so Vista is booted instead of Ubuntu after those 5 secs.

My question was if I could timeout to Vista one time, so next time I boot GRUB its timeouted to Ubuntu?

---

### Post by logos34 on 2008-08-11
The closest thing I can think of is the ['savedefault' option.]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")

---

### Post by estyles on 2008-08-11
I can give more detailed instructions if you need them, but here's the simple version.  Edit your /boot/grub/menu.lst file as root.

Near the top, there should be a line that says "default 0".  Change that to "default saved".

Next, figure out which number is each of your OSes.  Frex:  say you have entries for:

Ubuntu
Ubuntu recovery mode
OpenSUSE
OpenSUSE recovery mode
Windows

in that order.  In that case, Ubuntu is #0, and Windows is #4.  At the end of your Ubuntu entry, add "savedefault 4".  At the end of your Windows entry (I tend to put it before "chainloader +1", since I think that chainloader might immediately exit and load up Windows, so put it before that line), add "savedefault 0".  Adjust according to which number each OS is.

I think that's what you're looking for... I call it "crossbooting", so that when you restart from Vista it boots into Ubuntu and when you restart from Ubuntu it boots into Vista.

---

### Post by cariboo on 2008-08-11
I t would be way easier just to change the line for default boot in menu.lst press Alt-F2 then type:

```
gksu gedit /boot/grub/menu.lst
```

edit this line to reflect which so you want to boot by default:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default		0

change default    0 to the number your chosen os is in the list. Start counting from 0 for example ubuntu is 0 then on from there to Windows. If you haven't updated the kerenel windows should be #4 on your list.

Jim

---

