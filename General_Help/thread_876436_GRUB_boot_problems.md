---
title: "GRUB boot problems"
date: 2008-07-31
forum: General Help
---

### Post by FightMankaFight on 2008-07-31
Hey guys, I'm kind of new to the Ubuntu world, so take it easy on me.

I have a MacBook Pro I triple-booted with Leopard, Win XP and Ubuntu Hardy Heron. Everything is working very smoothly, my only problems being the wireless drivers, but that's a different story altogether.

When I boot my computer, I get to this screen

[IMG]http://i3.photobucket.com/albums/y71/Cocasoca/boot.jpg[/IMG]

I select the penguin, and then here's where I get a little confused

[IMG]http://i3.photobucket.com/albums/y71/Cocasoca/grub.jpg[/IMG]

What are all these options for?
I've been using the option at the very top of the screen, but I'm wondering what the other ones do. I know what memtest is, but do I really need all that crap there?

Could you possibly let me know how to get rid of all this stuff if it's not needed?

[IMG]http://i3.photobucket.com/albums/y71/Cocasoca/grub2.jpg[/IMG]

I would really appreciate if you could help, thanks in advance.

---

### Post by Alasdair on 2008-07-31
They are older versions of the linux kernel. I think they are there just encase an update breaks something. You can remove the old kernel versions via synaptic, or just comment them out in your /boot/grub/menu.lst file.

---

### Post by hansdown on 2008-07-31
Hi FightMankaFight.
These are normal. They list all of your upgrades. If you use The up and down arrows, you should be able to boot into the highlighted one.

---

### Post by FightMankaFight on 2008-07-31
I'm sorry to ask again, but could you maybe give me a little rundown of how to do this?

Or maybe send me somewhere that I can get a better looking screen to cover it?

Thanks so much for your help already
:]

---

### Post by nbayiha on 2008-07-31
What do you mean by How to do ?
How to edit your grub ? (do you mean )?
If you want to edit you grub so you will just have one kernel listed just do this . 

```
gksudo gedit /boot/grub/menu.lst
``` go down the files.(till the end)

and instead of those line with the new kernel of Ubuntu, remove other kernel. 
i mean those line starting with Ubuntu and the new kernel should be left , just the old kernel should be remove.

Of course don't remove the line with Windows kernel :d .

above i put how the linux kernel line should look like after you remove the other.

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=01d73f9c-0677-4c0b-9782-eee35f6babab ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=01d73f9c-0677-4c0b-9782-eee35f6babab ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

PS: don't forget to backup your file before modifying it .

---

### Post by FightMankaFight on 2008-07-31
Thank you so much, that was exactly what I was meaning. Sorry for not being specific.

Very much appreciated!

---

### Post by nbayiha on 2008-07-31
No problem you are welcome dude .

---

