---
title: "gnome-terminal will not work in ubuntu 8.10"
date: 2008-11-24
forum: General Help
---

### Post by Gengus Khan on 2008-11-24
Hello I have just switched over from XP. The problem I have is the gnome-terminal will not launch! I get a quick flash but that is it. I am very pleased with ubuntu so far, but it's things like this that shows how strange changing from XP can be..:confused:

---

### Post by ibutho on 2008-11-24
Thats a strange one. Try ALT-F2 and enter the command "xterm" (without quotes). After that enter the command **gnome-terminal** in xterm and post back any error messages.

---

### Post by Gengus Khan on 2008-11-24
Thanks for your help ibutho. I can get xterm to work but when I put in gnome-terminal there is the same flash of the gnome-terminal but no error message.

---

### Post by ibutho on 2008-11-25
Does gnome-terminal work if you are logged in as a different user?

---

### Post by Gengus Khan on 2008-11-25
Hi Guest account terminal works. Using the live cd works. I tried installing gnome desk top and terminal again, but that didn't work. So I installed Guake terminal instead that seems to be working. But haven't had the chance to use it. I'm so new to Linux that I'm using a book to get used to it. Thanks ibutho

---

### Post by ibutho on 2008-11-26
It could be that your profile is corrupt. You can reset GNOME back to the defaults by logging out of GNOME, logging into the CLI and then deleting your ~/.gnome* directories (after backing them up first). After that log back into GNOME again and see if GNOME Terminal works for you. If you are happy with another terminal, then you don't have to follow the steps above and just use the terminal of your choice.

---

### Post by Gengus Khan on 2008-11-26
Hi I will keep using what I have until I feel a bit more at home with Linux.

Thanks ibutho

---

