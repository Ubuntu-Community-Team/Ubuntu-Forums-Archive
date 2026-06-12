---
title: "issue with synaptic"
date: 2008-08-28
forum: General Help
---

### Post by mschraier on 2008-08-28
I am running 8.04.1 Kubuntu with KDE 4.1.  For the most part it is running well.  However the Synaptic Package Manager is giving me some heartburn.  It will do everything well except close.  I check the box to close when complete.  But it wont.  Nor can I "X" out of the program.  I have to power off and reboot.  Most time the application has been installed and works, but Synaptic hangs u p when it needs to close.  Any thoughts??  Also, besides ppa.laucnhpad, are there any other repositories I should add to the list?

Thanks

:guitar:

---

### Post by kellemes on 2008-08-28
> **mschraier said:**
> I am running 8.04.1 Kubuntu with KDE 4.1.  For the most part it is running well.  However the Synaptic Package Manager is giving me some heartburn.  It will do everything well except close.  I check the box to close when complete.  But it wont.  Nor can I "X" out of the program.  I have to power off and reboot.  Most time the application has been installed and works, but Synaptic hangs u p when it needs to close.  Any thoughts??  Also, besides ppa.laucnhpad, are there any other repositories I should add to the list?

Thanks

:guitar:

Try running synaptic from a terminal window and watch the output when you try to close it.
```
gksudo synaptic
```

---

### Post by mschraier on 2008-08-28
that way worked perfect.  was it the same synaptic installed already or something else?

---

### Post by pbhj on 2008-09-04
I think the issue is how you start synaptic. If I start it from the K-menu (in KDE) and then enter the password at the prompt it runs fine until it comes to close (after running ldconfig) at which point synaptic hangs. If you do Ctrl-Esc and check in the task manager you see a child process of synaptic is now a zombie.

However if I start synaptic using "kdesu synaptic" from the Alt-F2 "run application prompt" (or from a console using sudo for example) then everything runs without a hitch.

Incidentally you didn't need to reboot to quit out of synaptic only to kill the synaptic process. You can do that from the Ctrl-Esc taskmanager or using a utility like xkill or on the command line (eg "sudo killall synaptic" then enter password).

HTH

---

### Post by Anlace on 2008-10-07
I've been having trouble with Synaptic in KDE 4.1 as well.  Thank you for this information!

Should this be reported to the Synpatic team as a bug report?

---

### Post by PocketDog on 2008-10-07
Not really, it's a Gnome application, issues under KDE can be expected. KDE has Adept

---

