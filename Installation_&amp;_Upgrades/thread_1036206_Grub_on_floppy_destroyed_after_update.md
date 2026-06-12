---
title: "Grub on floppy destroyed after update"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by persistentstubborn on 2009-01-10
I checked several similar threads, but couldn't have found the answer to my problem.

I've installed 8.04 updates of 09/01/2009, grub update among them. I selected (as far as I recall) to keep the current version.

The problem is that my bootloader is on floppy, and not on HDD MBR.

The symptom is that I can't boot anything after the update.

I've booted live CD (7.10), to restore it on fdo but 

```

root@ubuntu:/home/ubuntu# mount /dev/fd0 /mnt/floppy
cd /mnt/floppy
ls -l
total 0

```


vmlinuz and menu.lst are safe and intact on /boot folder on HDD.

I did check man grub, mand update-grub, man grub-install, man bootparam, but I still don't get what I should exactly do from live CD, and what files should I exactly restore from the boot folder form my hdd to fd0. Is it menu.lst only, or something else in addition?

Moreover, I do have some hints (and experience) with POSIX systems, so don't waste your time on basics.

Finally, very poor job done with the update. 

Thanks in advance.

---

### Post by caljohnsmith on 2009-01-10
Actually there's another way to accomplish what you want to do: you could install Grub to the boot sector of your floppy, but have Grub point to your HDD for its boot files. That way when you boot your floppy, you will always load the most current menu.lst in your Ubuntu install on the HDD. If that sounds good to you, try doing:
```
sudo grub
grub> find /boot/grub/stage1
```
The find command should return your Ubuntu partition in the form (hd0,X), such as (hd0,4), but use whatever it returns as follows:
```
grub> root (hd0,X)
grub> setup (fd0)
grub> quit
```
Please post the output of the commands prior to doing "quit". Then reboot with the floppy, and let me know how it goes.

---

### Post by persistentstubborn on 2009-01-11
> **caljohnsmith said:**
> Actually there's another way to accomplish what you want to do: you could install Grub to the boot sector of your floppy, but have Grub point to your HDD for its boot files. That way when you boot your floppy, you will always load the most current menu.lst in your Ubuntu install on the HDD. If that sounds good to you, try doing:
```
sudo grub
grub> find /boot/grub/stage1
```
The find command should return your Ubuntu partition in the form (hd0,X), such as (hd0,4), but use whatever it returns as follows:
```
grub> root (hd0,X)
grub> setup (fd0)
grub> quit
```
Please post the output of the commands prior to doing "quit". Then reboot with the floppy, and let me know how it goes.

I did ask for an advice, and not a howto for morons. That's what one usually gets on these fora.

```
grub> find /boot/grub/stage1
```

returns error 15.

Moreover, since I've run grub-install meanwhile on new blank fdd, I've ended with /boot and /boot/boot folders and I'm not sure what to do now.

Instead of instructions for a moron, would you explain to me:

a) Which files I should copy to floppy?
b) Is there a particular fashion for doing that?
c) Possibly a link to probable cause and cure for my problem, if UBUNTU$OFT actually cares to do it.

Or, perhaps, add some extra comments against my rant over frustration [http://ubuntuforums.org/showthread.php?t=1036288](http://ubuntuforums.org/showthread.php?t=1036288)

---

### Post by persistentstubborn on 2009-01-11
@calljohnsmith

Thanks for your attempt to help me.

The final cure I decided to take is to erase and find an OS that better suits my needs.

---

