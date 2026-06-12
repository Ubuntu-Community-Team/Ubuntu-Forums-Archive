---
title: "what does a tilde following a file mean"
date: 2005-06-18
forum: Hardware &amp; Laptops
---

### Post by varla on 2005-06-18
Hi, I was just looking around to find out how to make my laptop hibernate and I found this:
HOARY PM
[https://wiki.ubuntu.com/HoaryPM?highlight=%28hibernate%29](https://wiki.ubuntu.com/HoaryPM?highlight=%28hibernate%29)
I edited the file /boot/grub/menu.lst and when I rebooted, and tried the hibernation, it worked. So that was great. My question is the following:
if I look into /boot/grub I see two files menu.lst and menu.lst~
why do I now have two files and what does a tilde following the file mean?
I totally read about the tilde following a file a long time ago and I can't remember what it means or where I read that.

thanks for your help

---

### Post by Xian on 2005-06-18
[QUOTE=varla]My question is the following:
if I look into /boot/grub I see two files menu.lst and menu.lst~
why do I now have two files and what does a tilde following the file mean?[/QUOTE]
The menu.lst~ is the last _previously_ saved menu.lst file.

---

### Post by varla on 2005-06-18
[QUOTE=Xian]The menu.lst~ is the last _previously_ saved menu.lst file.[/QUOTE]
hey thanks 
so why are these file being created? Is it because I didn't do a back up file before I edited that menu.lst one? or is it because something happen while I was editing my file?

---

### Post by bored2k on 2005-06-18
[QUOTE=varla]hey thanks 
so why are these file being created? Is it because I didn't do a back up file before I edited that menu.lst one? or is it because something happen while I was editing my file?[/QUOTE]
 Backups are automatically made by your text editor. Learn to love them I'd say..

---

### Post by varla on 2005-06-18
[QUOTE=bored2k]Backups are automatically made by your text editor. Learn to love them I'd say..[/QUOTE]
 Hey bored2k
yes I do love the back up file although I wonder why in the file in question, it was backed up with the extra line that I added to that file. So to me it seams like if I was totally out of control and doing all kinds of damaging editing to my files, it would be a lovely thing to be able to recover them intact after my wreck havoc episode. but if the back up file contains what I edited to it then it is not really a back up of that file in question right? So this confuses my love for the backup file.

---

### Post by Xian on 2005-06-18
[QUOTE=varla]but if the back up file contains what I edited to it then it is not really a back up of that file in question right? So this confuses my love for the backup file.[/QUOTE]
It's not intended to be a duplicate backup but is nice for when you save some edits of a particular file, forget what they were, and then find that you need them back. Presto...you got it back. But it is only good for the last edit, so you can only go back one save.

---

