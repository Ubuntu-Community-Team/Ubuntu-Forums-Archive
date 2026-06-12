---
title: "Full Partition"
date: 2008-09-12
forum: General Help
---

### Post by broken tibula on 2008-09-12
I'm a stupid newbie who messed something up.  *sigh*

I've been using Wubi for the last three months or so and loved Ubuntu.  Then today, I did something phenomenally stupid called "system backup", which essentially double the space that Ubuntu was taking up--completely filling up the partition.  I can get on, (sometimes) but it won't let me run any programs or administrative commands.  Nothing.  I get the error message: "
Unable to copy the user's Xauthorization file. "

I also can't delete the backup file, as I need administrative permission to do that.  I have Partition Manager, but I can't tell which one is my Linux partition.  None of them are the right size.  

What should I do?  I pulled off all my personal files from the Ubuntu partition, so complete reinstallation is an option I'm considering.  If there's an easier fix, though, I'm desperate to hear it.  Please help me!

---

### Post by Bucky Ball on 2008-09-12
Have you tried, in a terminal:

**sudo nautilus**

That should open a window and give you permission to delete the backup. Or open a terminal and:

**cd /name_of_directory_your_backup_file_is_in** (which could be backupdir or whatever you've chosen)

That will change you to the directory your backup file is in, then type:

**dir **

To make sure it is there then remove it. Or:

[B]locate name_of_backup_file
[/B] 
... and cd to that if you don't know where it is.

Then remove that file. That is a start ...

All this depending on if you can get the system up. There is probably a way to reclaim your X authorisation but I'm not sure of it. You could try googling 'reset X authorisation ubuntu' and see what pops up.

---

### Post by cdtech on 2008-09-12
To do anything with **Administration** privileges you must include the "sudo" in front of the command, such as:
**sudo rm /backupfile**

I would boot into the "recovery mode", if you feel brave, and locate the backup and remove it as above.

---

### Post by broken tibula on 2008-09-12
Thanks for the tips, but now it's doing something else.  I shut down my computer, started it up, picked Ubuntu at the GRUB screen, but instead of loading, it brought me to a shell.  Text reads: 

> BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)

It doesn't recognize sudo, locate, cd, or a few other basic commands that I typed in.  When I typed in 'help', it brought up a list of commands that I'd never seen before.  There were quite a lot, so I didn't write them down, but if you need to see that I can get them for you.  

Anway, I really appreciate your answers, but I can't try it yet until I solve this new problem.  Anyone have any ideas?  Should I ask in another forum?

---

### Post by Bucky Ball on 2008-09-12
Have you tried, from the shell:

**startx**

?

---

