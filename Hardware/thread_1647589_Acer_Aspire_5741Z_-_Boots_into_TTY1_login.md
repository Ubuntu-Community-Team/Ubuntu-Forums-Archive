---
title: "Acer Aspire 5741Z - Boots into TTY1 login"
date: 2010-12-17
forum: Hardware
---

### Post by trae329 on 2010-12-17
Ever since I booted Ubuntu 10.10 after installation, it automatically boots into a tty1 login. If I ignore it for a while, it will go into GDM and I can login. It's very annoying and I need help.

Thanks in advance,

Trae

---

### Post by trae329 on 2010-12-17
Bump

Please I need help :(

---

### Post by trae329 on 2010-12-17
Bump again...

Really guys, I need help. Are there any solutions to this problem I'm having? Please help me, as I'm new to Ubuntu.

---

### Post by nmvictor on 2010-12-24
I was  trying to fix my screen brightness adjustment problem yesterday and i bumped into a similar experience. I was doing the fix by appending some lines in the GRUB_CMDLINE_LINUX_DEFAULT= "<my appends here>" in the /etc/default/grub file.I realised that whenever I appended "nomodeset" without the quotes in the <my appends section>, the bootup would take me to the tty1 console, on removing the nomodeset options, the bootup would now take me to the gdm. so you can run the following command and see if you have that option in your GRUB_CMDLINE_LINUX_DEFAULT line.
At the terminal, run:
```

sudo nano /etc/default/grub

```
or if you are a gui guy, <ALT><F2> then[ gksudo  ](without the square brackets) then <ENTER> then [ gedit /etc/default/grub ](without the square brackets):

Check the GRUB_CMDLINE_LINUX_DEFAULT option to see if "nomodeset" is a value appended to it, if so simply erase the "nomodeset" option leaving the others unchanged, something like this:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"

```

to something else like this:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

```

then run:
```

sudo update-grub

```

to make the changes permanent. Reboot and pray. :) Hope that works. 

If you are using [burg]("https://launchpad.net/burg"), Brand-new Universal loadeR from Grub, then you have to replace grub with burg in the above command, that is
```
/etc/default/grub
```
to 
```

/etc/default/burg

```
and 
```

update-grub

```
to 
```

update-burg

```
Hope this helps, if not hope someone else helps, good luck!

---

