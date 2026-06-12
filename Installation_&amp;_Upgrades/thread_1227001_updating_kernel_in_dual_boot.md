---
title: "updating kernel in dual boot"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by stinkeye on 2009-07-30
I am dual booting with Jaunty and XP.
When ever I get a kernel update I'm unsure about what to do in this dialogue box.
[ATTACH]122927[/ATTACH]
I've been selecting "keep the local version currently installed" and then editing the menu.lst to update to the latest kernel,because I'm worried about messing up my dual boot.
Is there a better way of doing this.

---

### Post by snek on 2009-07-30
I've had the same worries that my menu.lst would get fubard if I let it do it automatically so I also always select "keep current version". It's very easy to change menu.lst to reflect to the new kernel however:

1 - Get a list of all your kernels
```

ls -ahl /boot/vmlinuz*
ls -ahl /boot/initrd-img*

```
(These 2 commands will show you the list you will need for editing menu.lst)
2 - Open menu.lst using nano/pico/gedit/whatever
3 - Copy/paste 2 of the old kernel lines, which usually look like this:
```

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        8b8129b6-ed71-4c57-b6f1-e57296600dc9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b8129b6-ed71-4c57-b6f1-e57296600dc9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        8b8129b6-ed71-4c57-b6f1-e57296600dc9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b8129b6-ed71-4c57-b6f1-e57296600dc9 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

```

So this becomes:
```

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        8b8129b6-ed71-4c57-b6f1-e57296600dc9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b8129b6-ed71-4c57-b6f1-e57296600dc9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        8b8129b6-ed71-4c57-b6f1-e57296600dc9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b8129b6-ed71-4c57-b6f1-e57296600dc9 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        8b8129b6-ed71-4c57-b6f1-e57296600dc9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b8129b6-ed71-4c57-b6f1-e57296600dc9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        8b8129b6-ed71-4c57-b6f1-e57296600dc9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b8129b6-ed71-4c57-b6f1-e57296600dc9 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic


```

Then just change 2 of them to point to your new kernel, making it look like this:
```

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        8b8129b6-ed71-4c57-b6f1-e57296600dc9
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=8b8129b6-ed71-4c57-b6f1-e57296600dc9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        8b8129b6-ed71-4c57-b6f1-e57296600dc9
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=8b8129b6-ed71-4c57-b6f1-e57296600dc9 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        8b8129b6-ed71-4c57-b6f1-e57296600dc9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b8129b6-ed71-4c57-b6f1-e57296600dc9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        8b8129b6-ed71-4c57-b6f1-e57296600dc9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b8129b6-ed71-4c57-b6f1-e57296600dc9 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic


```

Notice that I basically just replace 13 with 14.. and make sure the new kernel is the TOP one.. Grub always boots the first one in the list, so if you want to boot the new kernel make sure it's the top one.

Easy as pie :)

---

### Post by stlsaint on 2009-07-30
very useful thread...i keep at least three kernels just incase one craps on me!

---

### Post by stinkeye on 2009-07-30
Thanks for the reply snek.That's basically what I have been doing.
What I meant to say is if I selected "install the package maintainers version" would I still have to edit the menu.lst to add my Xp install.
or
should I select "do a 3-way merge between available versions"
or
should I just keep doing it the way described in my first post.

Just doesn't seem very clear for new users like me who usually dual boot.
It was only when I installed conky which displayed the kernel version that I realized I wasn't booting with the latest kernel.

---

### Post by snek on 2009-07-31
I'd suggest making a backup of your menu.lst and the next time it asks you try the 3way merger. I'm not exactly sure what it will do either, but with a backup you can always do it manually in case it does screw something up :)

I actually have a backup of most working versions of config files on one of my other drives, always handy to have an example..

---

