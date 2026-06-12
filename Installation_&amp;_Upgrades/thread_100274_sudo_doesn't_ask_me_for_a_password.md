---
title: "sudo doesn't ask me for a password"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by bertilow on 2005-12-07
Everybody seems to be asking how to make sudo work without a password. I have the opposite problem. I can do sudo without a password, but that doesn't seem safe to me. How can I change that? I want to be asked for a password.

Actually I don't even need to do sudo at all. If I just click on e.g. the synaptic icon, the program starts without asking me anything, and allows me to do anything.

No, I'm not running as root. But when I installed I chose expert mode (to be able to de create a separate home partition), so a root account was created.

My sudoers file has this:

Defaults	!lecture,tty_tickets,!fqdn
root	ALL=(ALL) ALL
%admin ALL=(ALL)  ALL

Strangely though the visudo command does not work when started from kde or gnome. It comes up with an empty file ("/tmp/sudoers.tmp"). I can edit it directly with vim or gvim though. But what should I put in to change things to the better?

---

### Post by earobinson on 2005-12-07
can you type who in the command line and give us the results. A who -r would also be nice!

Also did you need to type in a password the first time (sudo will remember your password for 15 minutes after its been typed in)

---

### Post by bertilow on 2005-12-07
[QUOTE=earobinson]can you type who in the command line and give us the results. A who -r would also be nice![/QUOTE]

~: who
bertilow tty1         Dec  7 22:02
bertilow :0           Dec  7 22:46

~: who -r
         run-level 2  Dec  7 20:48                   last=S

~: whoami
bertilow

[QUOTE=earobinson]Also did you need to type in a password the first time (sudo will remember your password for 15 minutes after its been typed in)[/QUOTE]

There is no first time. The only time I need to type my password is at login.

I just checked again. It's been hours since I used any program that ought to ask for my password. I just clicked on Synaptic, and it started without asking anything. This is the same in KDE and in Gnome.

But if I type "synaptic" in a console, it says I need to run it as root!

---

### Post by raublekick on 2005-12-07
Although this doesn't answer your question, you can create a /home partition without using the expert install. You just need to manually edit the partition table during the install instead of choosing the auto-option.

---

### Post by bertilow on 2005-12-07
[QUOTE=raublekick]Although this doesn't answer your question, you can create a /home partition without using the expert install. You just need to manually edit the partition table during the install instead of choosing the auto-option.[/QUOTE]

Thanks for the tip. At the time though it just seemed like the simplest route to take. I saw no info anywhere that using expert mode would force me to create a root account.

---

### Post by bertilow on 2005-12-18
In case someone else has the same problem, I found the answer in the list <ubuntu-users@lists.ubuntu.com>. My user name had somehow been added to the group "sudo". Removing me from that group solved the problem.

---

