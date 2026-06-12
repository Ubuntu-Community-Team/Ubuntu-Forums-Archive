---
title: "Dvorak keyboard"
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by Linforcer on 2005-05-05
I recently switched to a dvorak layout and inside x that's no problem, but when I switch to another tty it still uses the QWERTY layout. Where do I set what keymap ubuntu loads at boot?

---

### Post by kvidell on 2005-05-05
[QUOTE=Linforcer]I recently switched to a dvorak layout and inside x that's no problem, but when I switch to another tty it still uses the QWERTY layout. Where do I set what keymap ubuntu loads at boot?[/QUOTE]

NAME
       install-keymap — expand a given keymap and install it as boot-time keymap

SYNOPSIS
       install-keymap [keymap-name | NONE | KERNEL]
> 40/kvidell: pwd && ls
/usr/share/keymaps/i386/dvorak
ANSI-dvorak.kmap.gz  dvorak-classic.kmap.gz  dvorak-fr.kmap.gz  dvorak.kmap.gz  dvorak-l.kmap.gz  dvorak-r.kmap.gz  mac-usb-dvorak.kmap.gz  pc-dvorak-latin1.kmap.gz

Hope that helps :)
man install-keymap for more info

---

### Post by Linforcer on 2005-05-05
thanks, that did the trick. (forgot to sudo it the first time.) 
now I wish wy BIOS and grub saw it too. Guess I'll have to get a hardwired dvorak keyboard for that >.> ( I rearranged the keys myself on this one )

---

### Post by kvidell on 2005-05-05
[QUOTE=Linforcer]thanks, that did the trick. (forgot to sudo it the first time.) 
now I wish wy BIOS and grub saw it too. Guess I'll have to get a hardwired dvorak keyboard for that >.> ( I rearranged the keys myself on this one )[/QUOTE]
 Ha.. I did that.
Problem was the F and J keys, with their little nubbies, got very annoying.
The other problem is that I'm now on a laptop... aaannnd dvorak's not very universal :-\
So I'm back to qwerty.
Ah well.. some day...
- Kev

---

### Post by Linforcer on 2005-05-05
I used a potato-peal-knife to break the sockets for the f and j keys, as well as the sockets those keys go in. Works like a charm. on laptops you can buy those keyswitch thingers.

---

### Post by kvidell on 2005-05-05
[QUOTE=Linforcer]I used a potato-peal-knife to break the sockets for the f and j keys, as well as the sockets those keys go in. Works like a charm. on laptops you can buy those keyswitch thingers.[/QUOTE]
 *gasp* You say "thinger" too? :-D

Keyswitch thing eh? *looks in to it* Thanks! :)
- K

---

### Post by Linforcer on 2005-05-05
yeah I remember reading SOMETHING about on [http://www.mwbrooks.com/dvorak/](http://www.mwbrooks.com/dvorak/)

but I can't find it now >.>

---

### Post by Domhnull on 2005-05-06
There's an interesting dvorak keyboard at [Typematrix](http://www.typematrix.com/dvorak/).  Note, they have a different design philosophy about ergonomics.  I think they sound interesting and I've read a lot of good things about them but haven't had a chance to pick up one myself yet.

I type in dvorak at home and on my [Alphasmart Dana](http://www.alphasmart.com) but at work I have to use qwerty.  I'm very used to switching back and forth now - I don't even think about it.  I didn't move the keys when I learned dvorak and it made me a better typist - there was absolutely no reason to look at the keyboard!

---

