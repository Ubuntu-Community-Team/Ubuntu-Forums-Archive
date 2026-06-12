---
title: "install resolution die"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by alfotis on 2007-03-13
Hi all.

i am trying to install ubuntu edgy on a pc with nvidia 6200 and an LG L1919S monitor but installer dies after the splash screen (the loading bar).

Monitor says that picture is "Out of range". I tried all the possible resolutions but nothing worked

Can you please help?

---

### Post by dreadlord_chris on 2007-03-13
I just had to deal with a similiar issue today  ](*,) . To solve it I had to edit my menu.lst file

boot into the Recovery Console

```
~# nano /boot/grub/menu.lst
```

this will open the nano editor. Now scroll down to near the bottom, look for the Title line that's the same as what you boot into. Now look down 2 lines to Kernel

mine looks like this:

kernel          /boot/vmlinuz-2.6.20-10-generic root=UUID=0d9bd4d3-7a17-4f00-af6a-c89697eb5d0d ro splash vga=791

see at the end **vga=791**, that's the code for 1024x768

To proceed, you'll need to know the framebuffer code for your desired resolution: 

vga=785 	
640x480 

vga=788 	
800x600 

vga=791 	
1024x768 

vga=794 	
1280x1024

Just change yours to the desired resolution. Save the file - Control-X and _yes_ to the Save dialog. Reboot....

Hope this helps....[-o<

---

### Post by Eicca on 2007-11-16
> **dreadlord_chris said:**
> I just had to deal with a similiar issue today  ](*,) . To solve it I had to edit my menu.lst file

boot into the Recovery Console

```
~# nano /boot/grub/menu.lst
```

this will open the nano editor. Now scroll down to near the bottom, look for the Title line that's the same as what you boot into. Now look down 2 lines to Kernel

mine looks like this:

kernel          /boot/vmlinuz-2.6.20-10-generic root=UUID=0d9bd4d3-7a17-4f00-af6a-c89697eb5d0d ro splash vga=791

see at the end **vga=791**, that's the code for 1024x768

To proceed, you'll need to know the framebuffer code for your desired resolution: 

vga=785 	
640x480 

vga=788 	
800x600 

vga=791 	
1024x768 

vga=794 	
1280x1024

Just change yours to the desired resolution. Save the file - Control-X and _yes_ to the Save dialog. Reboot....

Hope this helps....[-o<Thanks for the help <3 Highly appreciated :)

---

