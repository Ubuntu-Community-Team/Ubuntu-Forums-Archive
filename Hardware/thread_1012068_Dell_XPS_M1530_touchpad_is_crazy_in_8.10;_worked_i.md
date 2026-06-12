---
title: "Dell XPS M1530 touchpad is crazy in 8.10; worked in 8.04"
date: 2008-12-15
forum: Hardware
---

### Post by Xitron on 2008-12-15
I'm running 8.10 on a Dell notebook XPS M1530.  On 8.04 the touchpad worked great.  On 8.10, if I touch it, it starts the cursor jumping all over the screen, clicking on things, and raising general havoc.  If I look at the konsole, I see characters repeating, as though the keyboard were stuck.  If I smack the CTL and ALT keys, the letters stop running amok and I can regain control of my notebook.  Current fix is a wireless mouse.

In 8.04, under System-Preferences-Mouse, there was a 3rd tab for the touchpad, enabling you to turn of clicking on touch, etc.  This setup only has 2 tabs, and no reference to the touchpad.  Aside from that indicating that the OS doesn't know I have a touchpad, it also makes it so I cannot disable the touchpad, so when I accidentally touch it, mayhem ensues.

Google shows that a lot of people are having touchpad issues under 8.10.  Has anyone found any answers that help?

Thanks!

Unca Xitron

---

### Post by nimish on 2008-12-26
***next time please use the search tool and search for key words such as M1530 mouse, or M1530 touchpad.***

first your have to edit the menu.lst in grub

go to /boot/grub: Type **cd /boot/grub** and press enter

then locate the file menu.lst by typing the command **ls**

then type the following command to edit the menu.lst file: **sudo gedit menu.lst**

it will ask you for your password, enter it and gedit will open.

**short-cut to this is: sudo gedit /boot/grub/menu.lst**

Scroll down until you see the following:

**## ## End Default Options ##**

right below that you will find your kernel list

Edit the fist first kernel entry. the line which you will have to edit will start with **Kernel** it's right after the **uuid** and before the **initrd**. 

Next type **i8042.nomux=1** after the **quiet** and before the **splash**


you are done. Save and exit and reboot and your touch pad will be working.

---

### Post by damis648 on 2008-12-26
Actually, this is caused by a BIOS update and a much simpler way of doing this (so you don't have to do it after every kernel update) would be to:
Open a terminal (Applications>Accessories>Terminal) and input the following:
```
gksudo gedit /boot/grub/menu.lst
```
and press enter. You will now see a window open. Press Ctrl+F and search for
```
defoptions
```
. This will lead you to a section looking like this:
```
## additional options to use withsudo update-grub the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```

All you have to do is in the last line of that stanza add the statement
```
i8042.nomux=1
```
So it turns out like this:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash i8042.nomux=1
```
Save the file and close the window now. Back at the terminal, type
```
sudo update-grub
```
and then after a reboot you will be good to go!:popcorn: Cheers!

---

### Post by nimish on 2008-12-26
thanks

---

