---
title: "[SOLVED] Grub Problem"
date: 2008-09-02
forum: General Help
---

### Post by enderal on 2008-09-02
What is grub?

The computer hung up when I was restarting and after I started it again it comes up with a screen with a grub command line?

How do I get back into ubunto?

Thanks!

---

### Post by mikewhatever on 2008-09-02
Grub is a boot loader, a program responsible for loading your OSs. What exactly do you mean by 'grub command line'? Do you get any errors?

---

### Post by enderal on 2008-09-02
When I boot up I get a black dos screen that says Grub4dos.

It has a command line "grub >" you can hit escape and it will give a few options which I don't know what to do with except for the one that says reboot.

Thanks

---

### Post by enderal on 2008-09-02
I've tried a bunch of commands to boot up but I don't know the right paths. 

Ubuntu is installed on Windows XP but not in the normal way using a partition. The install CD has an option to install "within Windows" but it does do a dual boot.

I do not need grub and would love to get it out of there.

---

### Post by enderal on 2008-09-02
I did track down the boot folder in windows. It won't open because it says it's corrupted so it looks like I get to uninstall and reinstall yet again!

Wonder if I'll ever to actually use ubuntu.

---

### Post by caljohnsmith on 2008-09-02
The "install within Windows" option uses Wubi. So do you still want to use Ubuntu, or do you want to delete it and go strictly back to Windows? 

When you start up your computer, does it give any choice between Windows or "grub4dos"?

---

### Post by Jonie on 2008-09-02
I think you should run chkdsk on your Windows filesystem anyway. If you don't want to use Command Prompt, go to Drive C:'s Properties->Tools->Error Checking->Check Now and tick "Automatically fix file system errors", when asked agree that CHKDSK is to be scheduled on next reboot).

---

