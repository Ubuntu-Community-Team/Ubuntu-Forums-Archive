---
title: "[SOLVED] How to change the default boot?"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by healee on 2009-07-15
On a dual-boot or multi-boot situation, where and how we can change the default boot up?  At present it boots up ubuntu by default?  I want to change to Windows by default if the boot-up process is unattended.  Can we also change the waiting time as well?

---

### Post by starcraft.man on 2009-07-15
Open a terminal. And input this command:



```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup1
```

then

```
gksudo gedit /boot/grub/menu.lst
```

This will open your GRUB menu list file in the text editor.

Scroll down until your past all the commented out instructions.

You should see sections like this: 
```

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		27c75af4-a835-4e7a-b9b8-c37679d7c2f4
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=27c75af4-a835-4e7a-b9b8-c37679d7c2f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet
```

These basically are listed in the order they appear in your list. Then just copy the XP one to the top of the list and rearrange as desired. If I recall, it's listed ins a slightly separate section titled windows, just copy the whole entry to the top of the list.

As for the waiting time, look back up to top of the list (or use the find function) and look for timeout option somewhere near the top. Set the number to desired.

The backup if you have any booting trouble, you can just load up a live CD and copy back the old file by reversing the command, i.e.:

```
sudo cp /boot/grub/menu.lst.backup1 /boot/grub/menu.lst
```

---

### Post by running_rabbit07 on 2009-07-15
Or you can install Startup Manager Via Synaptic Package Manager. Then make your selection as in the screenshots below. Then you will be in control.

---

### Post by running_rabbit07 on 2009-07-15
Let's try again...

---

### Post by aysiu on 2009-07-15
> **running_rabbit07 said:**
> Let's try again...
Or [http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

---

### Post by starcraft.man on 2009-07-15
> **running_rabbit07 said:**
> Or you can install Startup Manager Via Synaptic Package Manager. Then make your selection as in the screenshots below. Then you will be in control.

Bah, if ya wanna be cool, ya use a text editor :p.

---

### Post by running_rabbit07 on 2009-07-15
> **starcraft.man said:**
> Bah, if ya wanna be cool, ya use a text editor :p.

Too much like work to me. Seems like every text command I find doesn't work so I gave up on them for a while. I texted my previous Debian install so bad that when I restarted, it would only boot to text made and then I was stuck with writing over with Ubuntu. Then I learned that Ubuntu is built on Debian and figured I would do fine to stick with GUI programs to make the small things work happily.

---

### Post by running_rabbit07 on 2009-07-15
> **aysiu said:**
> Or [http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

That works, too. Whenever I do a search for stuff like that I come up empty handed.

---

### Post by healee on 2009-07-16
Thanks a lot!

---

