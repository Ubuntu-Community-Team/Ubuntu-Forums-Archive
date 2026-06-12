---
title: "strange keyboard bug intrepid"
date: 2008-12-02
forum: General Help
---

### Post by synapse88 on 2008-12-02
Hi all,

I've got something strange going on with intrepid on my desktop computer. I'm using a standard USB keyboard, it works fine in the bios and also when the system is up and running in Ubuntu 8.10 (32bit). But when I get the option in grub to press Esc and show the menu, it doesn't work. I also had that problem when booting from the install disk, my keyboard didn't work in the menu so i had no choice but to do a dist upgrade from 8.04 instead of a clean install.

Does anybody have a clue what is going on here? I find it very strange.

Greetings, Bob

---

### Post by synapse88 on 2008-12-02
seems like no one has a clue about the problem :)

---

### Post by silverglade00 on 2008-12-02
I have this problem with lots of computers at my work. Try looking for a USB slot labeled 1, or try the keyboard in the slots underneath the ethernet or PS/2 ports.
```

        --^^^--
[ USB ] |_____| <- ethernet (bear with me)
[ USB ] [ USB ]
[ USB ] [ USB ] <- this one is usually the right one

```

---

### Post by synapse88 on 2008-12-03
thanks a lot, this did help me :)

---

### Post by silverglade00 on 2008-12-03
No sh... I mean, really??! Awesome :)

By any chance, is the computer in question a Dell? They make most of the computers that I have this problem with. When USB first came out, computer makers didn't know how to handle it really well, so they would label one port USB1 and force you to use that one for a USB keyboard. I think after many copy/pastes of code, this bug still crops up from time to time.

---

