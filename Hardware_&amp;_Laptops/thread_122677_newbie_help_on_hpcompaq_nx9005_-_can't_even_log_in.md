---
title: "newbie help on hp/compaq nx9005 - can't even log in!"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by nmsmith on 2006-01-28
I have installed the 5.04 hp-edition on my laptop today. However I have some non-obvious problems:

The initial portion of the install (CD still in the drive, pre-reboot) goes fine, until I am asked to enter username and password. The password screen shows no text being entered, no asterisks, no nothing! The process seems to cycle round, with the first dialogue box having (!) in the heading bar, and subsequent ones showing (!!) in the title bar. I typed anyway, and moved on to the next step, in the hope that something had been registered.

Post-reboot, with the CD now out, I am asked again to set up the user accounts. However it doesn't seem to think I have typed in my passwords properly. I can however create the root account.

On the login screen, I get no response from the account I have tried to set up, and I am told that I cannot log in as root from that screen.

On subsequent tries, the screen also dies (I get weird interlace effects) after I click in the username box.

This is completely baffling. I don't know where to start. Any help is appreciated.

Nick Smith

---

### Post by nmsmith on 2006-01-28
I have had some progress.

I can boot in failsafe mode and login as root. No user accounts are listed in /home, so I tried creating one. I get:

[FONT="Courier New"]adduser test
[COLOR="DarkGreen"]Adding user 'test'...
Adding new group 'test' (1003).
Adding new user 'test' (1003) with group 'test'.
Creating home directory '/home/test'.
chown 1003:1003 /home/test: Operation not permitted
Cleaning up.
Removing directory '/home/test'
Removing user 'test'.
Removing group 'test'.[/COLOR][/FONT]

Why would chown run into problems like this? The problem recurrs if I try [FONT="Courier New"]chown 1003:1003 /home/test[/FONT] manually too.

I tried making the directories myself and then creating the user account, but not changing the ownership. Now I can log in from the X window pretty screen, but get kicked out after two seconds or so. Clearly the account isn't as it should be.

Nick Smith

---

### Post by nmsmith on 2006-01-28
I have reposted in a different forum, as I have realised this isn't a hardware issue. Apologies!

---

