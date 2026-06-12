---
title: "suspend keyboard shortcut not working"
date: 2008-07-15
forum: General Help
---

### Post by 1jackjack on 2008-07-15
hi everyone,
im running a dell xps m1330 with ubuntu 8.04. if i do menu>system>prefs>keyboard shortcuts and set suspend to Alt+2, it doesnt work (nothing happens).

any ideas? or maybe someone has a simple command to replicate what happens when you do menu>quit>suspend?

thanks,
Jack

---

### Post by 1jackjack on 2008-08-26
So just found this old post, and incase it comes up on anyone elses searches, I've found a couple of solutions:

sudo /usr/sbin/pmi action suspend
and
sudo /usr/sbin/pm-suspend

then if you wanted to set one (say the second one) of them to a hotkey (say <Alt>1), you should use metacity:

<Alt>F2
type gconf-editor
go apps>metacity...
keybinding_commands>command_1 to "sudo /usr/sbin/pm-suspend"
global_keybindings>run_command_1 to <Alt>1

But then you would have trouble with permissions running sudo commands without entering your password, so do this:

-run the command:
sudo visudo
-(you will be editing a text file using vi) add this line on end (if your user is called jack):
jack ALL= NOPASSWD: /usr/sbin/pm-suspend

BUT: I don't know the difference between those 2 suspend commands (is one better than the other?) and i don't know how to require a password on wakeup...???

Any ideas?
Cheers,
Jack

---

### Post by FokkerCharlie on 2008-11-10
Hi jackjack

Thanks for posting this.  It works well (with either command) for me on my Acer 5920G.

One thing- when using this method (rather than from the panel applet) the screen is unlocked on resume.  Know anything about this?

Cheers
Charlie

---

### Post by 1jackjack on 2008-11-10
> i don't know how to require a password on wakeup

I'm afraid I still haven't found out how to require a password on wakeup. Would you mind posting here if you find a solution?

Cheers

---

