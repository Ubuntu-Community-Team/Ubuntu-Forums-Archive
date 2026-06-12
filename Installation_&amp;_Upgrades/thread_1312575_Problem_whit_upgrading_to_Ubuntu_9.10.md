---
title: "Problem whit upgrading to Ubuntu 9.10"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by roelvh on 2009-11-03
Hellow, 

I'am a Ubuntu (9.04) user since 2 months, I just like it !
Yesterday I upgraded to Ubuntu 9.10 with Update Manager (Update beheer, I'am using a Dutch Ubuntu). I had no problems during the upgrading process, he only asked me what I want to do with "debconf". (I answered something like this: do nothing, use the installed one).
When i did a reboot grub didn't give me the option of starting in ubuntu 9.10, only ubuntu 9.04 (2.6.28-15). 
When i boot this 9.04 he boots with the background of 9.10, also the login screen is from 9.10. I can't use my mouse (touchpad) but I can use my keyboard.
Does anyone know what I need to do ?

Thanks a lot.

P.S. I'am using a Dell Studio 17, and my USB-mouse is broken :(

Edit:

I have tried to use recovery mode, when i'am in the recovery menu he place the text:
```
mountall: Cancelled
  General error mounting filesystems.
  A maintenance shell will now be started.
  CONTROL-D will terminate this shell and re-try. 
  Give root password for maintenance (or type Control-D to continue):

```
over the menu on random places. This results is that i can't move the cursor in the menu.
I'am using my laptop for school and I don't want the install all the programs again (it costs me a small week last time).

---

### Post by roelvh on 2009-11-03
I have found the solution:

First rename menu.lst
```

sudo mv /boot/grub/menu.lst /boot/grub/backup

```
Next update the grub list
```

sudo update-grub

```

Reboot and it should be working.

If you can't use your mouse (like me) you can use ALT-F1 to navigate in the menu's or use CTRL-ALT-F1 to go in text-modus (use CTRL-ALT-F7 to go back to normal modus)

---

### Post by dvandok on 2009-11-03
H'm, sounds like you've got a mixed setup somehow. You should check with aptitude what's the status of some packages; look at /etc/apt/sources.list and /boot/grub/menu.lst if everything is ok.

---

