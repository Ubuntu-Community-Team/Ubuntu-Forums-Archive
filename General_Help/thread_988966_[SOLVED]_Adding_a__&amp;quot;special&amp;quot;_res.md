---
title: "[SOLVED] Adding a  &amp;quot;special&amp;quot; restricted user"
date: 2008-11-21
forum: General Help
---

### Post by anirvana on 2008-11-21
Hello everyone :-),
                   I have some knowledge of *nix systems but am not a guru and hence the need to post this question.

The problem: I have to hand over a desktop to a person who will store it in their office. I want to maintain admin rights. At the same time, the person who will place it over in their location wants the rights to be able to patch the system periodically.

Possible solution: I can write a cron script to upgrade the system everyday automatically. 

What I am looking for: can I add a "special" user to the system and specify exactly which commands he can run? say I add a user, newuser, I don't want him to look into any directories/files/run any commands except apt-get upgrade etc..

The problem as I see, for newuser to run apt-get.. he needs to be on the sudoers list, which basically makes him an admin, right? this is what I want to avoid.

I have searched this forum and others for an answer, and have found info about ACLs, but I am hoping to find a simple solution.

Thanks in advance for any help,
-A

---

### Post by aysiu on 2008-11-21
You don't need to give that user full *sudo* access. You can give permission by command:

As an admin user, paste this command into the terminal: ```
sudo env EDITOR=nano visudo
``` Then at the bottom of the file add in these lines (where *username* is the username of the special user who doesn't otherwise have administrative privileges): ```
*username* ALL=(ALL) NOPASSWD: /usr/bin/update-manager
*username* ALL=(ALL) NOPASSWD: /usr/bin/gdebi
*username* ALL=(ALL) NOPASSWD: /usr/bin/dpkg
*username* ALL=(ALL) NOPASSWD: /usr/bin/apt-get
*username* ALL=(ALL) NOPASSWD: /usr/bin/gnome-app-install
*username* ALL=(ALL) NOPASSWD: /usr/sbin/synaptic
``` Then save (Control-X, Y, Enter). That should do it.

---

### Post by anirvana on 2008-11-22
awesome! simple and precise! awesome.. thanks.

---

