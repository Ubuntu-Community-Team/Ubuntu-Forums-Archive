---
title: "[SOLVED] update-grub"
date: 2008-08-15
forum: General Help
---

### Post by EddyS777 on 2008-08-15
I have an old pc and when I shut down it won't power off.It's a problem with acpi=force. too old bios running ubuntu 6.2

 I went into the terminal and typed sudo nano /boot/grub/menu.lst to find a line and add acpi=force. I found the kernel line but I do not know how to make the change permanent/update.(sudo update-grub won't work)

please help

---

### Post by mikewhatever on 2008-08-15
You need root privileges to edit Grub's menu. Use **gksudo gedit /boot/grub/menu.lst**, edit, save and exit.

---

### Post by EddyS777 on 2008-08-17
how do you edit save and exit? with the menus or typing it?

thanks

---

### Post by habtool on 2008-08-17
> **EddyS777 said:**
> how do you edit save and exit? with the menus or typing it?

thanks


Use the menus for now

---

### Post by sisco311 on 2008-08-17
nano is a command line text editor.
You can use Ctrl+o, Enter to save the file and
Ctrl+x to exit.

gedit is a GUI text editor (like notepad in windows).
You can save the file with Ctrl+s and exit with Alt+F4.
Or you can use the *File *menu *Save *and *Exit *options.

You need root privilages in order to edit system files.
sudo and gksu allows you to run applications as root (super user).

---

### Post by EddyS777 on 2008-08-17
the terminal menu does not have save or exit

---

### Post by Elfy on 2008-08-17
No the terminal menu doesn't - 
> nano is a command line text editor.
You can use Ctrl+o, Enter to save the file and
Ctrl+x to exit.

---

### Post by EddyS777 on 2008-08-17
on the terminal I open the file with sudo nano /boot/grub/menu.lst

on the line that starts with # kopt..  I add acpi=force and I can save it and exit but the pc won't power off at shut down. any suggestions. thanks to everyone

---

### Post by sisco311 on 2008-08-17
post the output from:
```
cat /boot/grub/menu.lst
```

try:
```
sudo shutdown -P now
```
to shutdown the pc.

---

### Post by mikjp on 2008-08-17
> **EddyS777 said:**
> on the terminal I open the file with sudo nano /boot/grub/menu.lst

on the line that starts with # kopt..  I add acpi=force and I can save it and exit but the pc won't power off at shut down. any suggestions. thanks to everyone

did you run update-grub after modifying the menu.lst?

mikko

---

### Post by EddyS777 on 2008-08-17
no I did not I'll try it thanks

---

### Post by EddyS777 on 2008-08-17
no i did not , I'll try it now thanks

---

### Post by Sorivenul on 2008-08-17
> **EddyS777 said:**
> on the line that starts with # kopt..  I add acpi=force and I can save it and exit but the pc won't power off at shut down. any suggestions. thanks to everyone

Did you uncomment that line?  
The "#" is probably keeping the addition from being recognized.

---

### Post by EddyS777 on 2008-08-17
where do I type update-grub? any action needed after like enter or such?

---

### Post by Sorivenul on 2008-08-17
Just in a terminal.
```
sudo update-grub
```
Then press enter.

---

### Post by mikewhatever on 2008-08-17
> **EddyS777 said:**
> where do I type update-grub? any action needed after like enter or such?

You shouldn't need this. If you managed to save it after editing, that should be it.

---

### Post by Elfy on 2008-08-17
> **Sorivenul said:**
> Did you uncomment that line?  
The "#" is probably keeping the addition from being recognized.

The # in fron of these lines doesn't comment them out - ## does, the lines with # are read by update-grub I believe.

You don't afaik remove these #

---

### Post by Sorivenul on 2008-08-17
> **forestpixie said:**
> The # in fron of these lines doesn't comment them out - ## does, the lines with # are read by update-grub I believe.

You don't afaik remove these #

Now that you mention it, I believe this is correct.  My mistake.

---

