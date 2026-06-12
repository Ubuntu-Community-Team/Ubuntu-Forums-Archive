---
title: "recover password"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by get2shashank on 2009-04-06
hey i am using ubuntu7.10...
i had ubuntu and winXP-pro on my machine...a fresh insatllation of WinXP caused my grub to vanish..then i worked for about 2 months on Win XP itself. During this period the insatllation of ubuntu existed on my machine..it was just that the grub was absent..so i booted WinXP every time...
Of lately, i restored my grub menu last week and booted the ubuntu insatll..now i have forgotten the password to login into the user account..what should i do....????
[PS: Apart from a new fresh ubuntu insatllation...thats the last thing that can be done..i guess...]

---

### Post by Kareeser on 2009-04-06
You'll have to log into the recovery console, which will dump you into the root account.

Then you can change the password with "passwd [username]"

---

### Post by get2shashank on 2009-04-06
will you explain that in a bit...

---

### Post by Didius Falco on 2009-04-06
> **get2shashank said:**
> will you explain that in a bit...

1. When the Grub menu comes up, chose the "recovery console" option. This will log you into Root without a password. It will be a command-line, with no GUI.

2. Type in "passwd username", without the quotes.

3. This will prompt you to input a password. Pick your new password and type it in. It'll ask you to type it in again, so repeat it.

4. Do a hard reboot.

5. When Grub comes up again, pick the regular login, and login using your new password.

---

### Post by get2shashank on 2009-04-08
it worked !!!
thanks Kareeser and Didius Falco...
it was fine for my case but isn't that too easy for a guy to change the login password for a given username...????
or was it just because i had a fresh grub restore...???

---

### Post by wgrant on 2009-04-08
If somebody has physical access to a computer, there's nothing (except encrypting the disk, perhaps) that you can do to prevent them from doing anything they want. If you password-protect GRUB, they can use a live CD. If you password-protect the BIOS, they can reset it or use one of the default passwords. You cannot win if they have physical access.

---

