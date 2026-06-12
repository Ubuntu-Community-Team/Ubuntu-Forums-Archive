---
title: "Password Required For Installing a Printer"
date: 2011-03-26
forum: Hardware
---

### Post by theshyguy64 on 2011-03-26
Okay, so i just got a Lexmark Interpret printer. I found the driver from the Lexmark website and it says i need root access to install the printer. I put in my password which is the administrator password and it didn't accept it for root access...any ideas?

---

### Post by Dutch70 on 2011-03-27
Does your password work for everything else? You may want to give a few more details.

Just a thought here, but have you checked your system for additional drivers? System > Admin > additional drivers.

Also you may find something in software center or synaptic for your printer.

---

### Post by theshyguy64 on 2011-03-27
The password does work with everything else. I couldn't find any software for the printer anywhere else but i could be doing something wrong. I'm still kinda new to Ubuntu after years of windows...That's one thing i have to give to windows and thats it's easier to use but this isn't the right place to be talking about this. Anyway, could it be that i accidentally put the wrong version of Ubuntu as my operating system? I just assumed that it wouldn't have brought me anywhere if i didn't have the right version. I guess what they say about assumptions is right...

---

### Post by Dutch70 on 2011-03-27
Guess that depends on what version you installed & what you installed it onto.

---

### Post by snafu006 on 2011-03-27
Root Access From GNOME

To launch a program in GNOME without a command-line (i.e., terminal), press "Alt-F2" (that is, press "F2" while holding down the "Alt" key). A dialogue box will popup.

You will be presented with a line on which to type the command you would like to run and the option to run it in terminal. To gain root access in Ubuntu, enter "gksudo" and the command you would like to use here.

You will then be asked for your password. After you have entered the correct password, and assuming your are registered in the "sudoers" file, the command will be affected. Otherwise, it will fail.

---

