---
title: "Warning In Snaptic (Solved)"
date: 2005-11-14
forum: General Help
---

### Post by Drifter on 2005-11-14
I opened snaptic to look for a program and got this warning:

W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/all Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_all_binary-i386_Packages) - stat (2 No such file or directory)


What do I do to correct it.

---

### Post by XDevHald on 2005-11-14
[QUOTE=Drifter]I opened snaptic to look for a program and got this warning:

W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/all Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_all_binary-i386_Packages) - stat (2 No such file or directory)


What do I do to correct it.[/QUOTE]
have you entered this command in your terminal as root?

> gpg --keyserver subkeys.pgp.net --recv-keys 1135D466 
 gpg --export --armor 1135D466 | sudo apt-key add -

If not then you need to. Let us know if that resolves it. 9x's out of 10 it's usually a package down and is being updated or the gz is not available at the moment.

---

### Post by Drifter on 2005-11-14
Steve, I went into sources list and put # in front of the line that had reference to that and it does not come up when I open snaptic now.  Is that a fix or should I use your suggestion.

---

### Post by Drifter on 2005-11-14
This is what I got when using terminal with your commands:

I did undo what I had done in my previous post.

root@ubuntu5:/home/david#  gpg --keyserver subkeys.pgp.net --recv-keys 1135D466 gpg: directory `/root/.gnupg' created
gpg: new configuration file `/root/.gnupg/gpg.conf' created
gpg: WARNING: options in `/root/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/root/.gnupg/secring.gpg' created
gpg: keyring `/root/.gnupg/pubring.gpg' created
gpg: requesting key 1135D466 from hkp server subkeys.pgp.net
gpg: /root/.gnupg/trustdb.gpg: trustdb created
gpg: key 1135D466: public key "Dennis Kaarsemaker (Package signing key) <dennis@kaarsemaker.net>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
root@ubuntu5:/home/david#  gpg --export --armor 1135D466 | sudo apt-key add -
OK

---

### Post by XDevHald on 2005-11-14
[QUOTE=Drifter]This is what I got when using terminal with your commands:

I did undo what I had done in my previous post.

root@ubuntu5:/home/david#  gpg --keyserver subkeys.pgp.net --recv-keys 1135D466 gpg: directory `/root/.gnupg' created
gpg: new configuration file `/root/.gnupg/gpg.conf' created
gpg: WARNING: options in `/root/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/root/.gnupg/secring.gpg' created
gpg: keyring `/root/.gnupg/pubring.gpg' created
gpg: requesting key 1135D466 from hkp server subkeys.pgp.net
gpg: /root/.gnupg/trustdb.gpg: trustdb created
gpg: key 1135D466: public key "Dennis Kaarsemaker (Package signing key) <dennis@kaarsemaker.net>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
root@ubuntu5:/home/david#  gpg --export --armor 1135D466 | sudo apt-key add -
OK[/QUOTE]
Correct, then it is added, now do an apt-get update to clerify the key.

---

### Post by Drifter on 2005-11-14
Steve, I downloaded Automatix earlier today, and snaptic does'nt have hardly anything in it now.  Should I run aptget update with Automatix installed or what.  I really don't understand much about linux yet, but I am trying to learn as I go.

---

### Post by XDevHald on 2005-11-14
[quote=Drifter]Steve, I downloaded Automatix earlier today, and snaptic does'nt have hardly anything in it now. Should I run aptget update with Automatix installed or what. I really don't understand much about linux yet, but I am trying to learn as I go.[/quote] Synaptic has all of the repos and libs that it from the archives of ubuntulinux's mirrors. You can search synaptic by going to the "Search" button at the top and searching the packages from there.

Automatix is a pretty nifty tool and is really easy to use if you know what you're needing. Automatix does not come from the archives, but is a single user development application and does do some touching of updating from the archives to catch any new updates or upgrades for the libs and etc.

Apt-get update will contact all of the mirrors in your /etc/apt/sources.list and tell those mirrors to give you all of the new updates and upgrades that the applications you run on your system, are needing in order for them to run correctly and stable.

I hope this helps you a bit, if not please let us know :)

---

### Post by Drifter on 2005-11-14
What is the correct apt-get update command.  If you would put on her so I could copy paste it I would appreciate it. Thanks

---

### Post by Drifter on 2005-11-14
Steve I got, snaptic is updated and all is well for now.  Thanks

---

