---
title: "Please Help, Serious Issue..."
date: 2008-12-20
forum: Hardware
---

### Post by krad54 on 2008-12-20
Well, I have a serious problem on my hands. I was trying to have a dual display config running on a laptop with the 8.10 version of ubuntu, and for some reason, everytime  I log in I get to the normal screen for about a second and then a white screen comes up.
I had 7.4 and the dual display worked perfectly. I think [pretty sure] that the problem now is that if I have Compiz running as the windows manager and try to dual screen, I get the white screen. Since then I have been trying to figure out a way to get the normal Metacity windows manager back. By the way, the messed up account is an admin account, and I do have another non-admin account. Do any of you know how to make non-admin, into admin w/o main account active.
I know that this was a bit long and wordy, but it is of the utmost importance that I have my laptop running again. BTW I have a Dell e1505 w/ integrated graphics, 1 gb ram, and a Dual-Core processor. 

Thanks For Your Help [in advance]

---

### Post by Ehtetur on 2008-12-21
You'll need to start up in recovery mode and then go into your autostart folder to remove the shortcut that's launching compiz.

Here are details if you need 'em:

Reboot your machine.
When you get to the grub menu, select (recovery mode).

When you get to the Recovery Menu, arrow down to 'root - Drop to root shell prompt' and press the Enter key. This will take to a root shell.

Change directory to the user's autostart directory. On my machine I would use this command:
> cd /home/ehtetur/**.**config/autostart/

List the files in the directory:
> ls -l

You should see one or more files in there that end in .desktop
One of those files is what's starting compiz when you login.

Delete or move the file that's starting compiz.
move:
> mv <WhatEverYouNamedTheFileThatStarsCompiz>.desktop /home/ehtetur/

delete:
> rm <WhatEverYouNamedTheFileThatStarsCompiz>.desktop

Type in the word exit and press Enter. You'll be taken back to the Recovery Menu. Arrow down to 'Resume - resume normal boot' and press the Enter key.

You should now be able to login without compiz starting. :twisted:

---

### Post by krad54 on 2008-12-21
Well, now I am re-messed up. I mean thank for the help and all, but now when it starts all I get is my desktop screen w/ the icons. I dont get the panels or anything. How do I start the compiz settings manager so I can change the window manager back to default?

---

### Post by Ehtetur on 2008-12-21
> **krad54 said:**
> I dont get the panels or anything.
Hrmmm... if you mean the gnome panels - one on the top and one at the bottom of your desktop - compiz should have no effect on them starting or not... maybe someone remove those panels, eh? :twisted:

If those are the panels you're talking about, amauk posted a [good and quick howto]("http://ubuntuforums.org/showpost.php?p=6252187&postcount=2") for restoring default Gnome panels.

To start compiz, you can do **Alt-F2 --> compiz --replace** or if you have fusion-icon installed, do **Alt-F2 --> fusion-icon**.

---

### Post by krad54 on 2008-12-21
Well the panel reset did not work. I did find something out though. I think my entire dektop stretches across the display, too far. Therefore I cannot see what is to my left or something. What I need to do now is to figure out how to get two screens up. Would you happen to know the command to get the screen resolution window up?

---

### Post by schimschone on 2008-12-21
It sounds like your system still believes you're hooked up to 2 displays.. and the primary display is the one off screen to your right. It allow you to fiddle with stuff on your laptop before showing it to the people your speaking to.

Go to system=>preferences=>screen resolution.. and set your monitor as your primary display.

Hope that helps.

schim

---

### Post by krad54 on 2008-12-21
Well I would but the problem is that I have no panel to do so. If you look at the pprevious posts, my panels are not working, even when I tried the panel fix. But thanks for trying

EDIT: Problem fixed. I booted the computer w/ another monitor plugged in. Both monitors worked and my "extended" desktop was shown. I then cloned the screens, and unplugged the extra monitor. After that I changed my resolution back to the maximum. So..now everything works. 
THANKS everyone for trying to help me. I'll press thanks and +rep [if possible].

---

