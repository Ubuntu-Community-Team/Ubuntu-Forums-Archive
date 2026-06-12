---
title: "Automatically load WinXP with GRUB"
date: 2008-08-10
forum: General Help
---

### Post by itsjareds on 2008-08-10
How can I set GRUB to load Windows XP automatically? I have heard people say they have done it.

If there is a way, how can I switch to Ubuntu then, if there is no boot menu startup?

Help would be greatly appreciated, my family doesn't know about Ubuntu.. and I'd like to keep it that way :cool:


edit: Ok I uncommented where it said #hiddenmenu, and I changed the timeout to 10, then I did sudo update-grub (not sure if I need to..)

I still see the menu. It's the menu that lets me choose between Windows XP and Ubuntu. Also, the timeout is still at 15 seconds.. it's not changing :-k

---

### Post by lisati on 2008-08-10
You will most likely have to edit grub's menu.lst file to make Windows the default entry. If memory serves correctly, the OS count starts at 0, and will need to be updated if you ever update your Linux kernels.

EDIT: when you boot your machine, are there any messages about GRUB? If so, does pressing "Esc" bring up a menu?

---

### Post by cdtech on 2008-08-10
You just need to change the line that say's "default 0" (within the /boot/grub/menu.lst) to the windows order number listed. If its the forth OS listed it would be "default 3"

---

### Post by dominiquec on 2008-08-10
The simplest way is to edit /boot/grub/menu.lst.  

Look for the line which says 'default' and change the number after that. This points to the operating system / kernel that GRUB will load, as based on the list lower down in menu.lst.  Default value is 0 so you'll want to change this to the numerical order (start counting from 0) of your Windows partition.

You'll want to put in the line 'hiddenmenu'.  This will hide the menu by default, but you can access it by pressing Esc within the timeout period.

The timeout period is specified in the 'timeout' option.

Look up any of the fine documentation on GRUB and menu.lst for further explanations.

---

### Post by ad_267 on 2008-08-10
You should be able to just change the default line to "default saved"

Usually Ubuntu puts saved in the windows entry just to make it easy to make windows the default.

---

### Post by itsjareds on 2008-08-10
thanks, thats what I needed to know. WinXP was already set as the default, but i needed to hide the menu :D

---

### Post by itsjareds on 2008-08-10
Erm.. it didn't work.

Was I supposed to uncomment it?

it was:
```
#hiddenmenu
```

and i removed the #:
```
hiddenmenu
```

---

### Post by itsjareds on 2008-08-10
bump :neutral:

---

### Post by SkonesMickLoud on 2008-08-10
> **itsjareds said:**
> Erm.. it didn't work.

Was I supposed to uncomment it?

it was:
```
#hiddenmenu
```

and i removed the #:
```
hiddenmenu
```

Yes.

---

### Post by lisati on 2008-08-10
> **itsjareds said:**
> Erm.. it didn't work.

Was I supposed to uncomment it?

it was:
```
#hiddenmenu
```

and i removed the #:
```
hiddenmenu
```
That's basically what I did. I still get the chance to push "Esc" to show a menu to choose an OS, but non-technically inclined people might not think to push it, particularly if they're used to turning on the computer and having it go straight to Windows.

---

### Post by itsjareds on 2008-08-10
It still shows the menu.

are we talking about the same menu? The one where it says "Choose your OS: Microsoft Windows XP or Ubuntu".

Sorry if I'm being thick :D

---

### Post by SkonesMickLoud on 2008-08-10
You're editing /boot/grub/menu.lst right?

---

### Post by itsjareds on 2008-08-10
yes

---

### Post by ad_267 on 2008-08-11
I think what you did wrong was run "sudo update-grub". I think if you look at the menu.lst file again it could have reverted back to defaults. You don't need to run this.

---

### Post by SpenceMakesSense on 2008-08-11
Im kind of having trouble understanding but Ill try my best

Get startupmanager

```
sudo apt-get install startupmanager
```

Then go to the boot options tab and change your default operating system to windows

---

### Post by itsjareds on 2008-08-12
Sorry, I think this is really the Wubi OS loader, not Grub.

It comes up at startup, how can I edit that page?

---

### Post by spike.robinson on 2008-08-12
If you are talking about the very first menu, that just says something like

   Windows XP
   Ubuntu

Then that is the bootloader. It's not GRUB so the options given for GRUB won't work. You need to edit boot.ini on the windows disk. I'm not sure of the options, but you can certainly make WindowsXP the default. You can probably set the timeout. Not sure if you can hide the menu. Look on the web for something like "boot.ini parameters" or similar.

---

### Post by itsjareds on 2008-08-12
Ah, thats it. It's in C:\ubuntu\winboot\menu.lst

It doesn't seem very useful, though..

menu.lst:
> debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt


---

### Post by ad_267 on 2008-08-13
I think the one you want might be C:\boot.ini

---

### Post by dgbraun on 2008-08-14
I have tried the suggestions, but it will not let me save the edited file /boot/grub/*menu.lst How do I save the edited file?

---

### Post by ad_267 on 2008-08-15
If you're doing this from Ubuntu you need to have root privilege. Press Alt-F2 then run "gksu nautilus" to get a root file browser then browse to the file and edit it.

---

### Post by SkonesMickLoud on 2008-08-15
> **ad_267 said:**
> If you're doing this from Ubuntu you need to have root privilege. Press Alt-F2 then run "gksu nautilus" to get a root file browser then browse to the file and edit it.

If you do it this way, make sure to close the window after wards.  Opening nautilus as root can be dangerous.

Safer way of doing it would be to enter:

```
gksu gedit /boot/grub/menu.lst
```

Into a terminal.

> **dgbraun said:**
> /boot/grub/*menu.lst

There shouldn't be a * in there.

---

