---
title: "Changing Order of OSs on Boot Screen"
date: 2005-11-10
forum: General Help
---

### Post by Ubuntist on 2005-11-10
I'd like to change the order in which OSs are listed on the boot screen from
[INDENT]
Ubuntu 686, other Ubuntu options..., Windows XP
[/INDENT]
to
[INDENT]
Windows XP, Ubuntu 686, other Ubuntu options
[/INDENT]
and to make XP the default (to make life easier for my other half, who's not [yet] a Linux convert).  Is there any reason I can't do this by editing /boot/grub/menu.lst and cutting the the lines
[INDENT]
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1
[/INDENT]
and pasting them ahead of the line
[INDENT]
### BEGIN AUTOMAGIC KERNELS LIST
[/INDENT]
?

How ugly is it likely to be if I screw menu.lst up?  I'm guessing it could be pretty bad, especially for a noob like myself.

---

### Post by Dr. Nick on 2005-11-10
Yeah just re-arrange them in the menu.list. Put Xp above the automatic generated list and it should be the default, if you put it below the auto gen it may dissappear after an update and you will have to add it back. You can just copy/paste in any order i believe. If you mess it up it can be a pain to get back, but not very hard at all. I may sugget making a backup copy before doing it just to be safe.

---

### Post by flower on 2005-11-10
here it is : 

[http://www.ubuntuforums.org/showthread.php?t=84373&highlight=boot+order#4](http://www.ubuntuforums.org/showthread.php?t=84373&highlight=boot+order#4)

---

### Post by Ubuntist on 2005-11-10
Thanx, Dr. Nick.  Are you saying I should just make a back up of menu.lst, or of my whole file system?  What I'm getting at is, is there a risk that if I screw up, I won't be able to boot at all?

Another question: since grub runs before any OS loads, how is it that editing a file inside the Linux file system has any effect on loading?

---

### Post by Dr. Nick on 2005-11-10
[QUOTE=Ubuntist]Thanx, Dr. Nick.  Are you saying I should just make a back up of menu.lst, or of my whole file system?  What I'm getting at is, is there a risk that if I screw up, I won't be able to boot at all?

Another question: since grub runs before any OS loads, how is it that editing a file inside the Linux file system has any effect on loading?[/QUOTE]

Yeah just menu.list. If you screw up real bad which you shouldnt by just re arranging them the worst that would happen is you would be given a comand line and have to know the command to boot it manually, Rarely ever happens. The above link may help you out aswell as XP will be the default but not necessarily at the top of the list.

The menu.list is the file that grub looks at when it loads, thats why it has an effect. Grub is written to the MBR just like windows would be if linux wasnt installed. Thats why it has a effect, the boot.ini file in windows would have the same purpose if you didnt have grub instead.

---

### Post by ThirdWorld on 2005-11-10
its good to know this in case a friend or relative want to boot primarly in XP

---

### Post by Ubuntist on 2005-11-10
Thanks, flower and Dr. N -- it worked perfectly.

---

### Post by missmoondog on 2005-11-11
was just searching for this and here i am. according to ubuntuguide.org, [http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub), you do it like this:
Q: How to change default Operating System boot-up for GRUB menu?

   1. Read General Notes
   2.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst

   3. Find this line

...
default         0
...

   4. Replace with the following line

default         X_sequence

   5. Save the edited file (sample)

didn't work for me. will try the above method.

edit:
simple fix after trying above stuff. simply change default to (4) in my case, as that is where xp is listed.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst

Edit:
i fibbed. you DO have to subtract 1 spot from where windows is listed, as per instructions.

---

