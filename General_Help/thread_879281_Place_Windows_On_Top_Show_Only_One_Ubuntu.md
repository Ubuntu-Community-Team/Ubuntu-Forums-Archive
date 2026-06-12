---
title: "Place Windows On Top/ Show Only One Ubuntu"
date: 2008-08-03
forum: General Help
---

### Post by mikelmahoo on 2008-08-03
How do I put Windows on the top of the partition list?

How do I make it show only one Ubuntu instead of 5 or 6?

---

### Post by overdrank on 2008-08-03
> **mikelmahoo said:**
> How do I put Windows on the top of the partition list?

How do I make it show only one Ubuntu instead of 5 or 6?

Hi and if you would like to edit your grub menu then this link can help
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
As for the windows partition on top please explain a little more?

---

### Post by mikelmahoo on 2008-08-03
I want windows to be the first listed partition listed in the menu.

---

### Post by mb_webguy on 2008-08-03
In terminal, type "sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup" to make a backup of your current GRUB menu in case you need to restore it later, then type "sudo gedit /boot/grub/menu.lst".

Most of the options are fairly straightforward.  What you're looking for is:```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```
Change the line "# howmany=all" to "# howmany=1".  DO NOT remove the leading "#".

Next, look for the entry for Windows, which should look something like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```
Copy that to the end of the file, after the line "### END DEBIAN AUTOMAGIC KERNELS LIST", if it's not already there.

---

### Post by mikelmahoo on 2008-08-03
I got this from that website.
To change your default OS you can change the number in the menu.lst.

---

### Post by mb_webguy on 2008-08-03
Oops.  I misread your post.  To get Windows on top, cut-n-paste the Windows entry before the line "### BEGIN AUTOMAGIC KERNELS LIST".

---

### Post by mikelmahoo on 2008-08-03
Cool. I found another way on that website.

---

