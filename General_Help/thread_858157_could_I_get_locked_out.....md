---
title: "could I get locked out...."
date: 2008-07-13
forum: General Help
---

### Post by Mia_tech on 2008-07-13
is it possible that ubuntu lock out your account and the root account?....I was using my laptop to ssh into my ubuntu box...after trying to login several times, I think I mistyped the password...went to my ubuntu machine to execute command with sudo, and when I type the sudo password I get authentication error, nor I can change my password or the root password, but I'm logged in to the system, I'm afraid that if I reboot the pc I would get locked out....what you guys suggest should be the best thing to do?
I've already backed up my systems, just in case ;0)

thanks in advance

---

### Post by PmDematagoda on 2008-07-13
You may be having a root kit by some chance, try running chrootkit and rkhunter if possible, if they turn up nothing, try booting up Ubuntu in Recovery Mode and try changing your password from there.

---

### Post by pofigster on 2008-07-13
If it isn't possible to run commands under 'sudo' then rkhunter isn't an option (requires sudo to intall and run) and I don't even know how to run chrootkit - it's not installed by default, and I don't even know what package it's in.

---

### Post by Dr Small on 2008-07-13
> **PmDematagoda said:**
> You may be having a root kit by some chance, try running chrootkit and rkhunter if possible, if they turn up nothing, try booting up Ubuntu in Recovery Mode and try changing your password from there.
That is simple to suggest, but if he doesn't have chrootkit or rkhunter installed, he probably won't be able to, seeing as how he can't use sudo.

---

### Post by Mia_tech on 2008-07-13
yes I have rkhunter installed but I can't run it...it requires root privilege...anyhow I'm going to restart my desktop...how could I reset my password entering in recovery mode?.....I've done it before but using the live cd method
never mind...found it [http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html]("http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html")

thanks

---

