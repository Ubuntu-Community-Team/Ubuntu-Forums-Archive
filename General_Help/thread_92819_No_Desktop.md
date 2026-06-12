---
title: "No Desktop"
date: 2005-11-20
forum: General Help
---

### Post by syngent on 2005-11-20
Hi all.

I am new to this forum as well as to Linux Ubuntu.  I have just received ver 5.10 and installed onto my IBM Thinkpad 600x.  The installation went fine but after I sign on, there are no icons.  Just a light brown screen and I am able to move the mouse around.

Can someone point me to the right direction in trying to correct this problem?

Thanks,
Perry

---

### Post by Bachstelze on 2005-11-20
There is no problem. You have to add icons for whatever yoou want manually.

---

### Post by syngent on 2005-11-20
[QUOTE=HymnToLife]There is no problem. You have to add icons for whatever yoou want manually.[/QUOTE]

How do I add icons?  Is there a quick documentation on this?

thanks,
Perry

---

### Post by Denis on 2005-11-20
You mean that there are no icons on your desktop? But you do have those menu bars at the top and bottom of your screen, right?

If you mean that your desktop is empty, you can fill it with icons yourself: 

- to add "home", "trash" and others, start system tools > configuration editor. navigate to "apps" > "nautilus" > "desktop" and check ......_icon_visible

- to create you own links, right click on the desktop and select "create launcher" or right click any file in nautilus and select "make link", you can move this link to the desktop if you want. 

I hope this helps you.

---

### Post by installer on 2005-11-20
[QUOTE=Denis]You mean that there are no icons on your desktop? But you do have those menu bars at the top and bottom of your screen, right?

If you mean that your desktop is empty, you can fill it with icons yourself: 

- to add "home", "trash" and others, start system tools > configuration editor. navigate to "apps" > "nautilus" > "desktop" and check ......_icon_visible

- to create you own links, right click on the desktop and select "create launcher" or right click any file in nautilus and select "make link", you can move this link to the desktop if you want. 

I hope this helps you.[/QUOTE]

Or you can drag them to the Desktop from the Ubuntu (Gnome) main menu.

---

### Post by SickTwist on 2005-11-20
[QUOTE=syngent]Hi all.

I am new to this forum as well as to Linux Ubuntu.  I have just received ver 5.10 and installed onto my IBM Thinkpad 600x.  The installation went fine but after I sign on, there are no icons.  Just a light brown screen and I am able to move the mouse around.

Can someone point me to the right direction in trying to correct this problem?

Thanks,
Perry[/QUOTE]

If there are panels at the top and bottom of the screen then there is no problem. Ubuntu is designed to have a very clean look after a default installation. However,  you are able to place as many files, lanchers, and directories on your desktop as you would like.

The desktop displays the contents of a directory called "Desktop" which is in your home directory. You can save and open files from that directory like any other. If you would like to have a launcher on the desktop that can start a  program, click on the program's icon in the applications menu and drag it to the desktop.

---

### Post by syngent on 2005-11-20
I actually have no menu bar.  Nothing.  Just a cursor that I can move around.

---

### Post by ozorba on 2005-11-20
[QUOTE=syngent]I actually have no menu bar.  Nothing.  Just a cursor that I can move around.[/QUOTE]

The best option is to rename .gnome and .gnome2 directories to something else.
There are also 2 additonal files that may cause this problem. These are

.gtkrc and .gtkrc-2.0 

They are in your home directory.

---

### Post by syngent on 2005-11-20
[QUOTE=ozorba]The best option is to rename .gnome and .gnome2 directories to something else.
There are also 2 additonal files that may cause this problem. These are

.gtkrc and .gtkrc-2.0 

They are in your home directory.[/QUOTE]

Thanks, I'll give that a try.

---

