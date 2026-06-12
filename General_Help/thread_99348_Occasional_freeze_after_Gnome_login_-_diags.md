---
title: "Occasional freeze after Gnome login - diags?"
date: 2005-12-05
forum: General Help
---

### Post by zi99y on 2005-12-05
Hi all,

I thought my ubuntu setup was pretty solid but for a while I've booted up and logged into the gnome gui, once the desktop has loaded it seems not to respond to anything. The mouse moves around but clicks have no affect, no hard disk activity. Only thing I can do is hold down the power button for a dirty reboot, then once it comes back up it will usually work first time.

How can I diagnose this problem, I'm a newbie so if someone could point me to the relevant event log files, I would be grateful.

Here's what I have loading on startup: 

* Nautilus (from previous session)
* Konsole 1.5.2 (from previous session)
* firestarter
* gnome panel and a bunch of system monitors

tia!

---

### Post by hedone on 2005-12-05
Do u have ati fglrx driver? i was havin' the same problem from the moment i install fglrx driver...

---

### Post by newuser111 on 2005-12-05
you shouldnt have to ever turn off the power to restart the gui

try pressing ctrl-alt-backspace to restart gnome if it is not responding

or ctrl-alt-f1 to get into the console

are you using any USB peripherals that are turned on when you boot up? do you see any error messages in the console? (try ctrl-alt-f1)

---

### Post by zi99y on 2005-12-05
[QUOTE=hedone]Do u have ati fglrx driver? i was havin' the same problem from the moment i install fglrx driver...[/QUOTE]

YES! I have an X700 and I installed the driver from [this guide]("http://ubuntuforums.org/showpost.php?p=423584")

---

### Post by zi99y on 2005-12-05
[QUOTE=newuser111]you shouldnt have to ever turn off the power to restart the gui

try pressing ctrl-alt-backspace to restart gnome if it is not responding

or ctrl-alt-f1 to get into the console

are you using any USB peripherals that are turned on when you boot up? do you see any error messages in the console? (try ctrl-alt-f1)[/QUOTE]

I have tried ctrl-alt-f1 but I think it quit the gui and stuck on a blank screen. 

No usb devices being used, but there's a built in card reader that doesn't work in ubuntu.

I'm on an ACER Aspire 1694wlmi for the record!

---

### Post by newuser111 on 2005-12-05
if you use ctrl-alt-f1 it will quit the gui and bring you to a login screen, here you login in with your account

you can press startx to get back into the gui after login, but before you do that try typing this in the console

sudo apt-get update
sudo apt-get dist-upgrade

that should upgrade your ubuntu

also which kernel are you using? did you install the restricted modules for your kernel with synaptic? type uname -r in console to show your kernel version

FYI i am also using an x700 pro radeon PCIE, and not experiencing any instability using the fglrx driver, so i doubt that is the cause of your problem, although you can try running sudo fglrxconfig

---

### Post by zi99y on 2005-12-05
right - 

my kernel version is 2.6.12-custom (I have recompiled once to get the acpi stuff working + 1Gb Ram)

I have enabled all the repositories in synaptic (/apt) for a couple of apps that I wanted.

Is it possible to run the ubuntu upgrade from the gui or do I have to drop out of X? I'm not prepared to reboot just yet but I will if necessary.

thanks for helping!

---

### Post by zi99y on 2005-12-06
This morning I booted up as usual, and had the aforementioned problem, when I tried CTRL-F1 I got no response whatsoever. But when I did  CTRL-ALT-Backspace it froze on a completely blank screen.

It might be worth mentioning that although all input devices stop working, there is still activity as my network indicators lights will flash happily while I get frustrated....

Further to this problem, I am unable to logout via the gui. It worked originally (after install) but now it just hangs on a black screen until I forcefully power off.

I might try going back to the old vesa drivers to see how it affects things, but I need the fglrx driver for me games.

Please help!!

---

### Post by Skoezie on 2005-12-06
After installing the newest Ati drivers i'm experiencing the same problem. 

But this happens only when I log out and directly back in. Haven't had this probleem when restarting the pc completely. 

Will try the tip to restart x with ctrl+alt+backspace.

---

### Post by zi99y on 2005-12-06
sorry I didn't mean it happens when I restart - that works fine. Problem happens when I select "logout" from the menu, so I can login to the gui again as a different user

---

### Post by cjazz on 2005-12-06
[QUOTE=zi99y]This morning I booted up as usual, and had the aforementioned problem, when I tried CTRL-F1 I got no response whatsoever. [/QUOTE]

zi99y,

It's Alt-ctrl-F1, not just ctrl-F1 (or any of the function keys 1-6). It should take you to a terminal where you are free to log in or to reboot safely (normally the three-fingered salute of alt-ctrl-del accomplishes this). Much better than simply powering down.

---

### Post by zi99y on 2005-12-06
Sorry that was a typo, I am actually doing ctrl-alt-f1. 

And yes I have tried the three fingered salute which produces disk activity but never shuts down. Actually I just last night installed the ctrl-alt-del task manager feature from automatix (after I had the problem), maybe I'll remove this....

Should I be worried about damaging my filesystem?

---

### Post by cjazz on 2005-12-06
I doubt the task manager feature is a problem, since the three-fingered salute doesn't apply under X. For the sake of file system integrity, it's always a good idea to do a proper shutdown, but if the system has stopped responding (it sounds like that applies to your situation), you may not have a choice. At least a journaling fs like ext3 or reiser gives you an improved fighting chance.

Good luck with the driver problem.

---

### Post by zi99y on 2005-12-07
Woo! I think I've solved it. Not the fglrx driver at all but Firestarter bringing up a sudo login box that then gets buried by the reloaded windows, I just need to type in the root password into the hidden box and hit return then I regain control - phew!! 

So does anyone know how to get firestarter to store the root privelige on loading or is that not wise?

Is it even worth using firestarter or am I still thinking in the windows world too much?

---

