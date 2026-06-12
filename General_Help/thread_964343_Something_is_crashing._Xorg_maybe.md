---
title: "Something is crashing. Xorg maybe?"
date: 2008-10-30
forum: General Help
---

### Post by Eredeath on 2008-10-30
After some time on the computer i will find that when i try to open a new program for example Terminal, it will not load completely (the window pops up for it but no courser or text) and i have to force quit it. Then other programs start to follow, i can't load them completely and have to force quit. I tried alt+ctrl+del to restart Xorg only to find that i can't get back into my desktop after signing back in.
At first i thought it might be compiz, so i turned off all effects, but that doesn't help either. I'm open to any suggestions.
Don't make me switch to Slackware :rolleyes:

---

### Post by Sam the Wizer on 2008-10-30
Did you upgrade today?  Have an nVidia video card?  The newest release of Xorg included in 8.10 doesn't support some older nVidia cards.  You may need to roll bax Xorg.

---

### Post by Eredeath on 2008-10-30
Thanks for the quick reply. This has been a problem over the last couple weeks, so i don't think it's due to any upgrades. Also I have an Intel graphics card.

---

### Post by Eredeath on 2008-10-30
Extra though... maybe gnome is crashing?

---

### Post by Yellow Pasque on 2008-10-30
My only suggestion would be to try loading programs from the terminal and see if they produce any meaningful error messages.

---

### Post by Eredeath on 2008-10-30
> **Temüjin said:**
> My only suggestion would be to try loading programs from the terminal and see if they produce any meaningful error messages.

that's the thing terminal wont work just like any other program

---

### Post by Sam the Wizer on 2008-10-30
Can you run the system just from the CLI?  Select it from Sessions before you login.  Do you have another DE besides gnome that you can run, and if so do you get the same errors?

---

### Post by Eredeath on 2008-10-30
I don't have any other DE to run, But the next time i get the error i will try to use the CLI. When that happens what should i do? remember to i can use alt+ctrl+F1 to get to command line also.

---

### Post by Sam the Wizer on 2008-10-30
If you can get to the command line (not a terminal emulator as that is running within x) try:

startx

This will run the X server, and if the problem occurs when you do so you'll know that this is what's causing the issue.

If start X works it might indicate a problem with Gnome.

---

### Post by agathian on 2008-10-30
Well.. if nothing really works.. 

you should check if you are even able to login thru command line - the ctrl-Alt-F1 route you had mentioned yourselves..

if you can, you should checkout the log files..
~/.xsession-errors
/var/log/messages
/var/log/syslog
etc.. for any meaningful errors.

i would check to see if you are running out disk space, via df command.

if you cant login as yourselves, you can try as root [ assuming you had set password for it earlier ]..

also try selecting failsafe session before logging in..

Hope this helps...

---

### Post by Eredeath on 2008-10-30
Both syslogs and messages are clean, .xsession-errors is wierd... The time is off its already saying it's tomorrow for the date. But besides that it doesn't seem to have any major errors listed that would crash my Desktop.

---

