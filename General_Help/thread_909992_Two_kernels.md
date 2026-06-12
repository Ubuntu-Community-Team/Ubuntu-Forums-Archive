---
title: "Two kernels??"
date: 2008-09-04
forum: General Help
---

### Post by robfranssen on 2008-09-04
Since a few weeks linux-user, so... newbee

I installed xubuntu on an old Compaq laptop and got updates with Update Manager.

With respect to GRUB, i have 3 questions:

1. The grub-menu (Esc) shows
    Ubuntu 8.04.1, kernel 2.6.24-19-generic
    Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
    Ubuntu 8.04.1, kernel 2.6.24-16-generic
    Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
    Ubuntu 8.04.1, memtest86+
    I can boot both kernels (in each case confirmed by echo 'uname -r')
    Do i need 2 kernels or should i (try to) remove one kernel?

2. sudo fdisk -l shows (amoung other details)
     Device           Boot            System
     /dev/sda1                         Linux
     /dev/sda2                         Linux swap / Solaris
     /dev/sda3       *                Compac diagnostics
 
     Partition table entries are not in disk order

    How to include the diagnostics-partition (a.o. used to change settings in BIOS)
    in the Grub-menu? Don't know how to 'translate' sda x to (hd0,y)...

3. How do i edit the file /boot/grub/menu.lst in such a way, that the grub-menu
     (mentioned in my first question) shows up by default?

---

### Post by iaculallad on 2008-09-04
> **robfranssen said:**
> Since a few weeks linux-user, so... newbee

I installed xubuntu on an old Compaq laptop and got updates with Update Manager.

With respect to GRUB, i have 3 questions:

1. The grub-menu (Esc) shows
    Ubuntu 8.04.1, kernel 2.6.24-19-generic
    Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
    Ubuntu 8.04.1, kernel 2.6.24-16-generic
    Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
    Ubuntu 8.04.1, memtest86+
    I can boot both kernels (in each case confirmed by echo 'uname -r')
    Do i need 2 kernels or should i (try to) remove one kernel?

- The only reason you need to have 2 kernel for booting is for a fail-safe in case the new kernel could not work well with your current unit setup.

> **robfranssen said:**
> 
2. sudo fdisk -l shows (amoung other details)
     Device           Boot            System
     /dev/sda1                         Linux
     /dev/sda2                         Linux swap / Solaris
     /dev/sda3       *                Compac diagnostics
 
     Partition table entries are not in disk order

    How to include the diagnostics-partition (a.o. used to change settings in BIOS)
    in the Grub-menu? Don't know how to 'translate' sda x to (hd0,y)...

- I can't get the exact question you're trying to imply in here..

> **robfranssen said:**
> 
3. How do i edit the file /boot/grub/menu.lst in such a way, that the grub-menu
     (mentioned in my first question) shows up by default?

- By default, meaning: to show only a single kernel for booting? You can use Synaptics to do that job for you. Simply search for "linux-image" and mark the kernel you want removed as "Mark for Complete Removal" and click on Apply. This will automatically update your GRUB for you.

---

### Post by pmlxuser on 2008-09-04
to question 1:

every time you do a kernel update. grub adds it to the list
the uppermost is the newest

if you don't like it you could delete the old entry from /boot/grub/menu.lst

(u could use the following command for that)
```

$sudo gedit /boot/grub/menu.lst

```

important:::: READ INSTRUCTION WELL BEFORE EDITING THE FILE

---

### Post by Thanoulis on 2008-09-04
Here we go:
1. You only need one kernel, but i prefer to have more than one installed.
2. Not sure what is a diagnostics partition (i never had a laptop), but sda3 is hd(0,2). GRUB begins counting at 0, not 1, and the fist number is the physical drive, the second the partition.
3. Just uncomment (delete the # sign) in front on the *hiddenmenu* option in menu.lst (Its in the 23 line of the default configuration).

---

### Post by iaculallad on 2008-09-04
> **pmlxuser said:**
> to question 1:

every time you do a kernel update. grub adds it to the list
the uppermost is the newest

if you don't like it you could delete the old entry from /boot/grub/menu.lst

(u could use the following command for that)
```

$sudo gedit /boot/grub/menu.lst

```

important:::: READ INSTRUCTION WELL BEFORE EDITING THE FILE

This should not be a complete solution considering that the OLD (or kernel you want deleted) kernels you deleted in the menu list still remains in your HDD consuming precious disk spaces. Use Synaptics instead so as to get rid of the kernel traces as it should also update your GRUB menu list.
Try to always stick on using sudo with terminal commands and use gksudo/gksu/kdesu/kdesudo on GUI applications that needs privilege.

i.e:

```
sudo vi /boot/grub/menu.lst
```

and

```
gksudo gedit /boot/grub/menu.lst
```

EDIT: Same applies with GNOME and KDE

---

### Post by arubislander on 2008-09-04
> **iaculallad said:**
> - The only reason you need to have 2 - By default, meaning: to show only a single kernel for booting? You can use Synaptics to do that job for you. Simply search for "linux-image" and mark the kernel you want removed as "Mark for Complete Removal" and click on Apply. This will automatically update your GRUB for you.

I think the OP meant 'by default': without pressing the ESC key. There is a line in /boot/grub/menu.lst that says 'hiddenmenu' or something like that off the top of my head. If you comment that out by adding a #-character at the beginning of the line you'll get the grub menu to show by default.

---

### Post by robfranssen on 2008-09-04
Hi guys; thanks for the speedy reply.

Will do my homework (arissen from your replies) first and inform you on progress.

---

### Post by robfranssen on 2008-09-04
So far, so good...

I commented 'hiddenmenu' in menu.lst and that made the menu appear without hitting 'Esc'

I added
title Compaq Diagnostics
root (hd0,2)
makeactive
chainloader +1
and that did the job as well, although i have no clue what 'chainloader +1' is about...

As for the 2 kernels, i can now remove the menu-entries for the nr-16 kernel,
but i don't understand iaculallad's remark that i should use Synaptics to get rid of the kernel traces.
If a new kernel (say nr 20) will become available in the future, will then the old kernel nr 16 be removed automatically - and if so - by which program?

---

### Post by regala on 2008-09-04
> **robfranssen said:**
> So far, so good...

I commented 'hiddenmenu' in menu.lst and that made the menu appear without hitting 'Esc'

I added
title Compaq Diagnostics
root (hd0,2)
makeactive
chainloader +1
and that did the job as well, although i have no clue what 'chainloader +1' is about...

As for the 2 kernels, i can now remove the menu-entries for the nr-16 kernel,
but i don't understand iaculallad's remark that i should use Synaptics to get rid of the kernel traces.
If a new kernel (say nr 20) will become available in the future, will then the old kernel nr 16 be removed automatically - and if so - by which program?
> f a new kernel (say nr 20) will become available in the future, will then the old kernel nr 16 be removed automatically

nope. Never ever would any package system take that chance. Kernels must explicitly be purged by the user thru their package manager frontend because of their being critical in the boot process.

---

### Post by robfranssen on 2008-09-04
hi regala

Of course one question leads to the next
I found the 2 kernels in Synaptics/Base System and (for the time being :-) try not to mess around with them

The new question then is:
Under my Xubuntu 8.04 Applications/Systemen-menu, i find
- Add/Remove
- Synaptic Packige Manager
- Update Manager
which seem to have similar tasks; could you tell me which program is doing what and/or should be used when?

---

### Post by regala on 2008-09-04
> **robfranssen said:**
> 

The new question then is:
Under my Xubuntu 8.04 Applications/Systemen-menu, i find
- Add/Remove
- Synaptic Packige Manager
- Update Manager
which seem to have similar tasks; could you tell me which program is doing what and/or should be used when?



well, I am not a Ubuntu user myself, but I guess:
- Add/Remove launches synaptics context frontends specialized in the Package Manager relevant actions, with more comprehensive choices than bare package names, like "Video player", "CD/DVD Burning"....
- Synaptics launches the full Package Manager frontend, with the complete package list (with names less trivial than "Video Player" as xine-ui :))
- Update Manager launches a frontend specialized in updates, not cherrypicked packages installation.

This is all possible because Synaptics is "just another frontend" to the APT system, and makes the calls it has to make (corresponding to apt-get install bidule) and Update Manager makes the ones it has to make (corresponding to apt-get upgrade).

So:
Synaptics is used when you want to add a package of which you know the name, and which you explicitly want. Add/Remove is used to add "features" and Update Manager to perform security/system upgrades on a daily basis.

---

### Post by robfranssen on 2008-09-04
Thanks for the info

---

