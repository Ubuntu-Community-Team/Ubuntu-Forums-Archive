---
title: "Suspend problem solved?"
date: 2005-11-23
forum: General Help
---

### Post by Cannedbread on 2005-11-23
First and foremost, Ubuntu rules.
I was a hardcore windows user since 3.1 and now i am 100% ubuntu.
Here is my story.

Breezy's suspend function has worked fine on my laptop if i invoke it from the logoff menu.  But it does not happen when i close my lid.

If i run acpi_listen i get
```
button/lid LID 00000080 00000001
```

So.. I know my lidbutton works

searching this forum told me that i should edit the lidbutton script to invoke the sleep script. so i "sudo gedit /etc/acpi/events/lidbtn" and make the file look like this 
```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/sleep.sh
```

This worked for some guy on another thread. but when i do it i get nothing. Others were having this problem too. So i decided to see what exactly /etc/acpi/sleep.sh does, then I notice this block of code in the script. 

```
# If PowerManager is running, let it handle policy
if [ "`pidof PowerManager`" ] && [ x$1 != xforce ] && [ x$1 != xsleep ]; then
    exit;
fi
```

I figured this check was probably getting a false positive or something. So i modified it to look like this

```
# If PowerManager is running, let it handle policy
if [ "`pidof PowerManager`" ] && [ x$1 != xforce ] && [ x$1 != xsleep ]; then
    echo "ASDASDASDASDASDASDASASDAS"
    exit;
fi
```

Upon running "sudo sh /etc/acpi/sleep.sh"
the terminal says to me...

```
ASDASDASDASDASDASDASASDAS
```
So the script thinks i am using some kind of power manager or something

i proceed to check my task manager thing and i see no "PowerManager" and there is no "PowerManager" installed with synaptic, so i dont know wtf is going on here.

So... I comment out this block of code like so

```
# If PowerManager is running, let it handle policy
#if [ "`pidof PowerManager`" ] && [ x$1 != xforce ] && [ x$1 != xsleep ]; then
#    exit;
#fi
```

After making these changes you must run ```
sudo /etc/init.d/acpid restart
``` or just reboot.

Now the lid thing works and so does my suspend button!


Questions that remain:
what is this this "PowerManager" phantom that seems to be inhabiting my computer and how can i destroy it?

at some point i had the gnome-power-manager installed, but it didnt work so i removed it a long time ago. does that have something to do with it?

---

### Post by WanderingStar on 2005-11-23
I've been going through this as well - and seem to have it worked out.  You need to look for PowerManager - note the capitals.  It starts on boot, and should show up in a "ps aux | grep Power" to kill it.  Odd that its not showing in Synaptic however.  In mine its listed as Power-Manager, it gets pulled down with Gnome-Power-Manager (its the backend for that).  It seems to be busted - for me at least.

Jeff

---

### Post by grinias on 2005-11-25
[QUOTE=WanderingStar] Odd that its not showing in Synaptic however.  In mine its listed as Power-Manager, it gets pulled down with Gnome-Power-Manager (its the backend for that).  It seems to be busted - for me at least.

Jeff[/QUOTE]

 You can see, that is included as 

/usr/sbin/PowerManager 

 in the package power-manager.  In Synaptic Package Manager, find the package "power-manager" and right click on it, then select "Poperties", then "Installed Files" and there it is. "power-manager" is the backend of "gnome-power-manager". So if you don't want to use them either you have to completely delete them or alter

 /etc/acpi/sleep.sh

as Cannedbread suggested.

See you

---

