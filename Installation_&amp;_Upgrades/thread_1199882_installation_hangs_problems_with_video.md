---
title: "installation hangs: problems with video"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by user_cero on 2009-06-29
Im trying to install jaunty on an old computer with a celeron d. The cd boots up with no problem. Then it shows me the selection screen. I can either choose to install ubuntu or to run the live cd but no matter what i choose it starts to load then it simply stops.
 I went to the documentation on installation and it said to run the installation with the option vga=788(or vga=ask) or with fb=false. I did it with both with no result. When it hanged with the vga option i switched to the command line it ran with no problems but i dont know how to install it like that. With the fb option when i tried to switch to the terminal i got the following error:
[INDENT]Loading, please wait...
bogl_init failed: EXPLODE
screen init failed[/INDENT]

Can anyone help fix this in order to use the graphical installation?

---

### Post by lotster on 2009-06-29
I had the same problem; try installing it with "noapic acpi=off nofb".  It worked for me...

---

### Post by user_cero on 2009-06-29
I tried the options but it still didn´t work... anymore ideas?

---

### Post by merlinus on 2009-06-29
First, check your system specs against what is required.  Then you might try the text-based alternate install cd.

---

### Post by user_cero on 2009-06-29
The pc is running a celeron(not d)@2.53 Ghz with 512 of ram. So i have a lil bit more than the recommended specs.

I have to download that other cd?

---

### Post by merlinus on 2009-06-29
Unfortunately, yes.  It is a complelely different download from the live install cd.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by presence1960 on 2009-06-29
> **merlinus said:**
> Unfortunately, yes.  It is a complelely different download from the live install cd.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

+1

did you try safe graphic mode on the install. Hit F4 and choose it. See here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

