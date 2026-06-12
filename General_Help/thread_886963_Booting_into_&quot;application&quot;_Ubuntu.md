---
title: "Booting into &quot;application&quot; Ubuntu"
date: 2008-08-11
forum: General Help
---

### Post by Calicoo on 2008-08-11
I recently installed the "application" ubuntu onto my D drive. After I reboot I am given a choice between XP and ubuntu. After selecting ubuntu it gives me a grub loader screen. I'm stuck as to what I need to do to actually boot up ubuntu here.

I've tried find /boot/grub/menu.lst but it said the file was not found. I'm pretty sure it installed correctly because I have ubuntu files on my D drive.

Can anyone help?

---

### Post by lisati on 2008-08-11
Question 1: What happens if you leave your computer alone while the Grub menu is showing on the screen? 
Question 2: Do you actually get to see a choice between Ubuntu and Windows?

---

### Post by WRDN on 2008-08-11
How did you install Ubuntu, as the single letter drive name (in this case, D) convention is used in Windows only as far as I know?

---

### Post by Calicoo on 2008-08-11
[QUOTE=lisati]Question 1: What happens if you leave your computer alone while the Grub menu is showing on the screen? 
Question 2: Do you actually get to see a choice between Ubuntu and Windows?[/QUOTE]

A1. The screen sits there with a grub command prompt like so:
grub >

A2. Yes. Like I said earlier I'll pick ubuntu and it'll give me the grub boot loader. If I choose xp it'll boot up xp normally.

[QUOTE=WRDN]How did you install Ubuntu, as the single letter drive name (in this case, D) convention is used in Windows only as far as I know?[/QUOTE]

It gave me the choice of hard drive like that in the install menu.

---

### Post by eriqjaffe on 2008-08-11
> **WRDN said:**
> How did you install Ubuntu, as the single letter drive name (in this case, D) convention is used in Windows only as far as I know?The install was done with WUBI.

You won't be able to find the menu.lst file from within Windows, since the Ubuntu filesystem is stored inside a virtual disk file on your D: drive.

You shouldn't need to do anything at the Grub screen aside from wait a few seconds, or just choose the appropriate Ubuntu option.

---

### Post by Calicoo on 2008-08-14
It just sits there if I leave it alone. Is there any way to manually boot into ubuntu?

---

