---
title: "remapping commands to windows shortcuts?"
date: 2008-08-16
forum: General Help
---

### Post by nintennuendo on 2008-08-16
I want win, or Super as I now know it,+D to show desktop, and Super+E to bring up a nautilus window preferably in home, or computer.  I have ubuntu tweak set to map superE and superD, but I don't know what to tell it to do.

---

### Post by kerry_s on 2008-08-16
open preferences> keyboard short cuts, click on> hide all windows and focus desktop, then press the keys you want. backspace disables.

---

### Post by nintennuendo on 2008-08-16
I don't think I can set Win+D, just WIN with that.  and theres no option for a file browser window.

---

### Post by olejorgen on 2008-08-16
Try wmctl -k on

---

### Post by kerry_s on 2008-08-16
> **nintennuendo said:**
> I don't think I can set Win+D, just WIN with that.  and theres no option for a file browser window.

i see what you mean. i can't seem to get the Super_L key to work with any letter, only by itself. :confused:

---

### Post by aysiu on 2008-08-16
Go to System > Preferences > Keyboard

and set the Win/Super behavior so that Super is mapped to Win (or something like that).

I'm going on memory, since I don't have Gnome in front of me, but this should allow you to do key combinations with the Windows key instead of having the Windows key be a key on its own.

---

### Post by drs305 on 2008-08-16
This will make Super+D show the Desktop:
```
gconftool-2 --set --type string /apps/metacity/global_keybindings/show_desktop '<Super>d'
```

---

### Post by drs305 on 2008-08-16
These commands are shortcuts to the gconf-editor settings under /apps/metacity keybinding_commands and global_keybindings . If command_8 is already used or reserved (try the key command Suoer+E to see if it does anything before running the commands), use an unassigned command number.

This command will set Super+E to open nautilus:

```

gconftool-2 --set --type string  /apps/metacity/keybinding_commands/command_8  'nautilus'
gconftool-2 --set --type string /apps/metacity/global_keybindings/run_command_8 '<Super>E'
```

---

### Post by kerry_s on 2008-08-17
> **drs305 said:**
> This will make Super+D show the Desktop:
```
gconftool-2 --set --type string /apps/metacity/global_keybindings/show_desktop '<Super>d'
```

that works for me, i wonder why it wouldn't work with <Super_L>d ?

---

### Post by drs305 on 2008-08-17
> **kerry_s said:**
> that works for me, i wonder why it wouldn't work with <Super_L>d ?

It's not you! I previously tried for quite a while to get it to work with Super_L and Super_R and just couldn't. It would work with 'Super' or 'Mod4' but not with either Super key individually.

---

### Post by hariks0 on 2009-09-14
Why all this jargon when it could be configured in Compiz or Ubuntu Tweek to show desktop by merely moving mouse cursor to left bottom corner [where the show desktop icon is placed in windoze]

System--> Preferences--> CompizConfig Settings--> General--> General Options--> Key Bindings--> Show Desktop [with a monitor icon]. Click on it and select the edge or corner of the screen to activate show desktop.

THEN

Use value of command 1 "nautilus ~" [without quotes] to open your home folder with Super+e or "nautilus /" [without quotes] to open your root folder.

The other settings i use in compiz are 

"gnome-terminal" with super+r
"gnome-session-save --logout-dialog" with super+l
"xkill" with super+delete


And that is not all. I use 

xvkbd -text "\[Alt_L]\[F1]"

for starting the main menu without using even a single key press of keyboard keys.

To do so goto System--> Preferences--> CompizConfig Settings--> General--> Commands--> Commands--> Command 4 and set the value of Edge binding to 

Left.

Do the same for invoking the Run Application dialog with 

xvkbd -text "\[Alt_L]\[F2]" and set the value of Edge binding to 

Right.

Note : Use xvkbd -text "\[Alt_L]\[F1]" [with quotes and the command starts from xvkbd] You will have to install pckage xvkbd. Code = [sudo apt-get install xvkbd]. The command for Run Application dialog seems to invoke the main menu also. May get corrected after a loggof and logon.

---

### Post by drs305 on 2009-09-14
The user didn't state that he/she uses compiz. I don't except to answer posts. 

But your point should highlight the desired practice of stating in a post of this nature whether you are using compiz or not.

---

