---
title: "Fan problem in ubuntu"
date: 2011-09-24
forum: Hardware
---

### Post by Soon2BeLegend on 2011-09-24
I own a Toshiba Satellite L505-S5984 and I installed ubuntu 10.10 on it because i was very sick of Windows and all of its problems. (i.e. programs not responding, internet having trouble connecting etc). well with ubuntu, i have noticed my fan will never run and the bottom of my computer will get really warm. it will only run if i am watching a video for a while. and when it runs, it never turns off. it will keep running forever which will wear the fan out. in Windows 7, the fan will run when it is needed and the computer will stay very cool, but Windows is very slow and unresponsive. I don't want to go back to Windows, but I will to keep my computer from burning up. ive looked up lm-sensors and fancontrol, but there is no explanation on how to install it and configure it. Does anyone know how to get the fan working properly?

---

### Post by Soon2BeLegend on 2011-09-24
Any suggestions?

---

### Post by Soon2BeLegend on 2011-09-25
so nobody knows? or just everyone just wants to ignore me?

---

### Post by Blasphemist on 2011-09-25
Sorry, just saw this. I have a L505-S6946. I add acpi_osi=Linux to the GRUB_CMDLINE_LINUX="" in etc/default/grub as shown below. Add this parameter between the quotes.
> 
**Editing /etc/default/grub**

You can open /etc/default/grub file with the following command,
```
gksudo gedit /etc/default/grub
```

This is what it should look like,
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
# GRUB_INIT_TUNE="480 440 1"


Do run this after the edit to activate the change.
```
sudo update-grub
```

---

### Post by Soon2BeLegend on 2011-09-25
Thank You!!! This worked brilliantly!

---

### Post by Soon2BeLegend on 2011-10-14
After i have been using this for awhile, the fan quit working on me again. it is doing the same thing as before. not running until it gets up to 165 degrees Fahrenheit and it will kick in and never stop running. 165 degrees is a little too hot for the computer.

---

### Post by Blasphemist on 2011-10-14
I'm not 100% with this either on my oneiric partitions. I'm going through some things and will let you know how it goes. I'd be happy to have anything you learn too. I googled it and found something in the arch wiki I'm looking into.

---

### Post by Soon2BeLegend on 2011-10-14
i have found a post on the site that said the problem was solved with an Acer. im going to go ahead and give it a try and ill let you know if it works.

---

