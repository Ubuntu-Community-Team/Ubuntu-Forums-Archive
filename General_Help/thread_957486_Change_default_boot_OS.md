---
title: "Change default boot OS"
date: 2008-10-24
forum: General Help
---

### Post by walpoles93 on 2008-10-24
Hi, I've just install Ubuntu and want it to be my default boot OS because at the minute Vista boots automatically if i leave it.

Is there any way to make ubuntu boot automatically?
Thanks.

---

### Post by Mazin on 2008-10-24
Go to run application, type in:
```
gksu gedit /boot/grub/menu.lst
```

and then move the section
```
title		Windows Vista Whatever
root		(hd0,0)
makeactive
chainloader	+1
```

to the bottom of the file (after "### END DEBIAN AUTOMAGIC KERNELS LIST") so that the Ubuntu entries will be first.

OR

add the line "savedefault" to Ubuntu's entry, and change the line
```
# savedefault=false
```
to
```
# savedefault=true
```

which will make Grub automatically boot your *last selected* OS.

---

### Post by pytheas22 on 2008-10-24
If you installed Ubuntu using wubi (which I suspect because otherwise Ubuntu should already be the default boot option), then you have to boot to Windows, open a command-prompt, type 'msconfig', click on the 'boot.ini' tab, and look at the boot entries there.  Find the one for Ubuntu (it should be obvious) and click the button that says 'default' to make it the default selection.

This is how it works on XP, at least.  I've never used Vista but I presume it's pretty much the same.  If you need more help, let us know.

---

### Post by sdennie on 2008-10-24
> **Mazin said:**
> Go to run application, type in:
```
gksu gedit /boot/grub/menu.lst
```

and then move the section
```
title		Windows Vista Whatever
root		(hd0,0)
makeactive
chainloader	+1
```

to the bottom of the file (after "### END DEBIAN AUTOMAGIC KERNELS LIST") so that the Ubuntu entries will be first.

OR

add the line "savedefault" to Ubuntu's entry, and change the line
```
# savedefault=false
```
to
```
# savedefault=true
```

which will make Grub automatically boot your *last selected* OS.

There are a few more steps to the "savedefault" route.  You will also need to go to the top of menu.lst and change:

```

default 0

```

to

```

default saved

```

Then, you will need to manually add the "savedefault" keyword to the Vista section mentioned above.  It should look something like this (I'm basing this on what was written above so, I'm not sure if it's correct):

```

title		Windows Vista Whatever
root		(hd0,0)
makeactive
chainloader	+1
savedefault

```

The last step is to run:

```

sudo update-grub

```

That will update the default generated kernel entries to have the savedefault keyword.

---

