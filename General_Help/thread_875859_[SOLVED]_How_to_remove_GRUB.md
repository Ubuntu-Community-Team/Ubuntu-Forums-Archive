---
title: "[SOLVED] How to remove GRUB?"
date: 2008-07-31
forum: General Help
---

### Post by Joselito84 on 2008-07-31
Hi guys, i was just wondering how to remove the GRUB boot loader. Basically I'm happy with using the original loader which im guessing is the windows boot loader.

Basically whats happening for me is GRUB loads up, it comes up with  about 4 different linux selections, and also XP. When i choose XP it then loads up the original loader i had which has XP and Ubuntu, which is the one i would like to keep.

any ideas? will i need to fdisk my mbr? if so what is the exact command i would have to type?

thanks heaps people!

---

### Post by Dr Small on 2008-07-31
You can do that, but if you do so, you will not be able to boot the linux partitions.

---

### Post by Joselito84 on 2008-07-31
In other words, i've gotta keep GRUB?

well in that case is it possible to change the order of the menu?

so i can have XP at the top?

---

### Post by DGortze380 on 2008-07-31
There are a number of things you can change in GRUB, include the default OS to boot and whether or not it shows all your options. You can set it up to load GRUB 'quiet' so it's a blank screen for say 3 seconds, press esc to enter the menu or let it load straight to your default OS.

So you like you want do something like what I described, then remove Ubuntu from your XP bootloader.

EDIT: start with this command to backup your original configs

```

cp /boot/grub/menu.list /boot/grub/menu.list.old

```

Edit the menu.list file with the text editor of your choice to make changes to grub.

---

### Post by Joselito84 on 2008-08-02
that sounds perfect! thats actually exactly what i want to do.

i'm gonna do a quick google search on how to remove the bootloader for xp and just use GRUB as you've described. Thanks for your help mate!

if i have any dramas i'll be sure to reply to this post again!


thanks!

---

### Post by Joselito84 on 2008-08-02
Ok well i got GRUB set up how i wanted it, even got it hidden.

One thing however that i didnt like was the Pause for about 8 seconds as it counts down and says "Press ESC for menu" is there any way of changing that? i mean can i get rid of that completely?

---

### Post by DGortze380 on 2008-08-02
> **Joselito84 said:**
> Ok well i got GRUB set up how i wanted it, even got it hidden.

One thing however that i didnt like was the Pause for about 8 seconds as it counts down and says "Press ESC for menu" is there any way of changing that? i mean can i get rid of that completely?

There should be a line in menu.list to control that. You don't want to get rid of it completely, but change it to like 2 or 3 seconds.

---

### Post by OutOfReach on 2008-08-02
The line that controls that is the following:
```
timeout xx
```
xx being the number of seconds, you can change that number so If you want it to be like say 5 seconds it would be:
```
timeout 5
```

---

### Post by Joselito84 on 2008-08-03
ok thanks heaps people!
problem solved!

---

